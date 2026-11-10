# 💻 Convenciones y Arquitectura Godot - Notaría de Aventureros

> [!NOTE]
> Todos somos programadores en el equipo. La clave para avanzar en paralelo sin pisarnos es dividir el proyecto en escenas independientes desacopladas mediante **Señales** (*Signals*) y un Singleton de datos.

---

## 🛠️ Entorno y Motor de Juego

- **Motor:** Godot Engine (4.x)
- **Lenguaje:** GDScript
- **Plataforma objetivo:** Ejecutable de escritorio (Windows `.exe`)
- **Configuración de Render:** Texturas en modo `Nearest` (Pixel Art nítido).
- **Resolución Base:** Proyecto en formato 16:9 con escalado `canvas_items` y aspect `keep`.

---

## 🏗️ Arquitectura de Escenas Principales

```text
res://
├── Scenes/
│   ├── Core/
│   │   ├── GameManager.tscn       # Autoload (Singleton) de persistencia y estado
│   │   └── AudioManager.tscn      # Manejador de buses, Low-Pass y SFX
│   ├── Desk/
│   │   ├── Desk_View.tscn         # Escena raíz del gameplay de oficina
│   │   ├── Counter_Window.tscn    # Ventanilla con NPC y guardia
│   │   └── Table_Surface.tscn     # Mesa con slots de objetos
│   └── UI/
│       ├── Rulebook.tscn          # Libro de reglas desplegable
│       ├── Declaration_Form.tscn  # Formulario con OptionButtons
│       ├── Tool_Lens.tscn         # Lente de inspección (Area2D / Drag)
│       └── Stamp.tscn             # Sellos de madera arrastrables
├── Scripts/
│   ├── Data/
│   │   └── ItemsDatabase.gd       # Diccionario con propiedades de botines y reglas
│   └── ...
└── Assets/ (Art, Audio, Fonts)
```

---

## 👥 Reparto de Tareas de Programación

Dado que **Michael, Lucas, Daniel y Esther** tienen perfil de programación, nos distribuimos por módulos:

| Programador(es) | Módulo / Escenas | Responsabilidades Clave |
| :--- | :--- | :--- |
| **Daniel & Esther** | **Sistemas de UI y Drag & Drop** (`Tool_Lens.tscn`, `Stamp.tscn`, `Declaration_Form.tscn`) | - Lógica de arrastrar y soltar herramientas (`_gui_input` o `Area2D`).<br>- Animaciones de documentos con `create_tween()`.<br>- Lógica de selección con `OptionButton`. |
| **Michael & Esther/Daniel** | **Core Logic y Validación** (`GameManager.gd`, `ItemsDatabase.gd`) | - Diccionario de objetos y propiedades (visibles y ocultas).<br>- Algoritmo booleano que compara la Declaración Jurada vs. Libro de Reglas del día.<br>- Cálculo de sobornos, multas y balance final. |
| **Michael** | **Audio & Buses Dinámicos** (`AudioManager.gd`) | - Transición de música con filtro Low-Pass al abrir el Rulebook.<br>- Disparador de SFX con variaciones de tono (pitch jitter). |
| **Lucas** | **Integración de Animaciones y Sprites** | - Conexión de `AnimatedSprite2D` para el guardia, burócrata y aventureros.<br>- Feedback visual en mesa. |

---

## 🏷️ Convenciones de GDScript

- **Nombres de archivos / escenas:** `PascalCase.tscn` para escenas (`DeskView.tscn`), `snake_case.gd` para scripts (`game_manager.gd`).
- **Nombres de nodos en árbol:** `PascalCase` (`TextureButton`, `RunicLens`).
- **Variables públicas / serializadas:** `@export var item_id: String = ""`
- **Variables privadas:** `var _current_money: int = 100`
- **Constantes:** `const MAX_CLIENTS_PER_DAY: int = 5`
- **Señales:** En pasado indicativo: `signal stamp_applied(verdict_type)`, `signal item_inspected(item_data)`

---

## 🌿 Flujo de Git

> [!TIP]
> Consulta la guía visual detallada en [[Flujo de Git]].

- Rama `main`: Solo builds estables que compilan sin errores.
- Ramas por módulo: `feature/lens-drag`, `feature/rulebook-ui`, `feature/validation-logic`.
- Siempre hacer `git pull origin main` antes de iniciar cambios.
