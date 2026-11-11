# 💻 Convenciones y Arquitectura Godot - Notaría de Aventureros

> [!NOTE]
> Dado que todos en el equipo tenemos perfil de desarrollo, la clave para maximizar la velocidad y evitar conflictos de Git es desacoplar el proyecto en escenas independientes mediante el patrón **Señales hacia arriba, llamadas hacia abajo** (*Signals up, calls down*) y un Singleton de gestión de estado (`GameManager.gd`).

---

## 🛠️ Entorno y Configuración del Motor

- **Motor:** Godot Engine 4.x (2D)
- **Lenguaje:** GDScript
- **Resolución Base:** `1280x720` (o resolución nativa pixel art `640x360` escalada con `viewport` / `canvas_items`).
- **Modo de Texturas:** Filtro `Nearest` en configuración de proyecto para un pixel art perfectamente nítido.
- **Export Objetivo:** Ejecutable de escritorio Windows `.exe`.

---

## 🏗️ Árbol de Escenas y Arquitectura Modular

```text
res://
├── Scenes/
│   ├── Core/
│   │   ├── GameManager.tscn         # Autoload: Día (1-5), Dinero, Honor (-100 a 100), Baúl
│   │   ├── AudioManager.tscn        # Autoload: Buses de audio, Low-pass y SFX de honor
│   │   └── Endings_Evaluator.tscn   # Computa los 4 finales al cerrar el Día 5
│   ├── Desk/
│   │   ├── Desk_View.tscn           # Escena raíz del gameplay diario
│   │   ├── Counter_Window.tscn      # Marco exterior, aventurero actual y guardia gato
│   │   ├── Inspection_Area.tscn     # Bandeja física donde se aloja el botín actual
│   │   ├── Tool_Lens.tscn           # Lente arrastrable con dial de 3 filtros de shader
│   │   ├── Universal_Form.tscn      # Formulario fijo con los 3 OptionButtons
│   │   ├── Rulebook_Popup.tscn      # Manual de leyes a pantalla completa
│   │   └── Action_Panel.tscn        # Botones: Cobrar, Arrestar, Confiscar y Robar
│   ├── UI/
│   │   ├── Honor_Vignette.tscn      # CanvasLayer con shader de destello blanco/rojo
│   │   ├── Day_Summary.tscn         # Resumen nocturno (ingresos, soborno del gato, notas)
│   │   └── Endings_Screen.tscn      # Pantalla narrativa para los 4 finales y Game Over
├── Scripts/
│   ├── Data/
│   │   ├── ItemsDatabase.gd         # Diccionario de los 40-50 objetos y sus propiedades
│   │   └── DailyRulesDatabase.gd    # Leyes y prohibiciones específicas para cada día (1 a 5)
│   ├── Desk/
│   │   ├── tool_lens.gd             # Lógica de arrastre y conmutación de shaders
│   │   ├── universal_form.gd        # Lectura de los 3 desplegables
│   │   └── action_panel.gd          # Emisión de resoluciones de trámite
│   └── Core/
│       ├── game_manager.gd          # Máquina de estados global y persistencia
│       └── audio_manager.gd         # Control de música dinámica y SFX reactivos
└── Shaders/
    ├── lens_mask.gdshader           # Máscara circular para El Lente
    ├── spectrum_magic.gdshader      # Revelación de runas arcanas
    ├── spectrum_bio.gdshader        # Revelación de toxinas y esporas
    ├── spectrum_xray.gdshader       # Revelación de hojas ocultas y mecanismos
    └── honor_vignette.gdshader      # Viñeta periférica blanca/roja
```

---

## 👥 Reparto de Tareas Técnicas (Módulos)

| Desarrollador | Módulos Clave | Responsabilidades Específicas |
| :--- | :--- | :--- |
| **Daniel** | **El Lente & Shaders de Inspección** (`Tool_Lens.tscn`, `Shaders/`) | - Programar el sistema de arrastre (`Area2D` / `_input`).<br>- Crear e integrar los shaders para los 3 espectros (Mágico, Biológico y Rayos X) revelando las capas ocultas del objeto sin texto. |
| **Esther** | **Formulario Universal & Validación Burocrática** (`Universal_Form.tscn`, `DailyRulesDatabase.gd`) | - Implementar los 3 menús `OptionButton` (Material, Estado, Propósito).<br>- Algoritmo de comparación lógica: Formulario vs. Libro de Reglas del Día para dictaminar legalidad, contrabando o justificación de arresto/confiscación. |
| **Michael** | **Meta-Juego, Economía & Audio Reactivo** (`GameManager.gd`, `Day_Summary.tscn`, `AudioManager.gd`) | - Máquina de estados de los 5 Días y balance financiero (sueldo, bonos, venta de robos y soborno creciente al Guardia Gato).<br>- Lógica del Sistema de Honor (-100 a +100) y disparo del feedback sonoro (acorde limpio vs tono disonante).<br>- Algoritmo de resolución de los 4 Finales en Día 5. |
| **Lucas** | **Integración Visual, Animaciones & UI** (`Counter_Window.tscn`, `Endings_Screen.tscn`) | - Conectar `AnimatedSprite2D` del Guardia Gato (reacción cómplice al presionar `Robar`).<br>- Montaje visual de los 40-50 objetos y sus sprites de capas reveladas.<br>- Integración estética de las pantallas de epílogo y menús. |

---

## 💾 Estructura del Estado Global (`GameManager.gd`)

```gdscript
extends Node

# Variables de Progresión
var current_day: int = 1                     # Día actual (1 a 5)
var current_client_index: int = 0            # Cliente actual de la jornada (0 a 9)

# Variables Financieras y Meta
var money: int = 100                         # Dinero acumulado (GameOver si <= 0)
var honor: float = 0.0                       # Escala oculta de -100.0 a +100.0
var stolen_inventory: Array[Dictionary] = [] # Objetos robados en posesión
var steals_today_count: int = 0              # Conteo de robos del día para el soborno

# Señales de Sistema
signal honor_updated(new_honor: float, is_positive: bool)
signal client_processed(resolution: String, item_data: Dictionary)
signal day_completed(day_stats: Dictionary)
signal game_over_triggered(reason: String)

func apply_resolution(action: String, item: Dictionary, form_data: Dictionary) -> void:
    match action:
        "cobrar":
            _handle_charge(item, form_data)
        "arrestar":
            _handle_arrest(item, form_data)
        "confiscar":
            _handle_confiscate(item, form_data)
        "robar":
            _handle_steal(item)

func _handle_steal(item: Dictionary) -> void:
    stolen_inventory.append(item)
    steals_today_count += 1
    # Robar siempre penaliza el honor
    adjust_honor(-25.0, false)
```

---

## 🏷️ Convenciones de Código GDScript

- **Archivos:** `snake_case.gd` para scripts (`game_manager.gd`), `PascalCase.tscn` para escenas (`DeskView.tscn`).
- **Nombres de Nodos:** `PascalCase` (`UniversalForm`, `InspectionBowl`, `GuardCat`).
- **Tipado Estricto:** Siempre tipar variables y retornos: `var client_name: String = ""`, `func get_tax() -> int:`
- **Constantes:** `const MAX_CLIENTS_PER_DAY: int = 10`
- **Señales:** En pasado indicativo: `signal item_inspected(item_data)`, `signal resolution_selected(action_name)`.
