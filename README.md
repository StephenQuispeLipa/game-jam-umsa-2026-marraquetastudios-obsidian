# 🏰 Notaría de Aventureros (El Vacío Legal)
### GUILD Game Jam 2026 — Bóveda de Documentación Oficial

> **Temática:** *"Al otro lado de la ley"*  
> **Género:** Puzzle Lógico / Simulador de Gestión Burocrática (Estilo *Papers, Please*)  
> **Motor:** Godot Engine 4.x (2D Pixel Art)  
> **Plataforma:** Windows `.exe`  

---

## 📖 Sinopsis

Eres un oficial de aduanas en un reino de fantasía medieval opresivo. Tu labor cotidiana consiste en inspeccionar el botín que traen los aventureros para cobrar impuestos, arrestarlos o confiscar sus bienes según las directivas del **Libro de Reglas**. Sin embargo, tu salario miserable apenas mantiene con vida a tu familia: puedes aprovechar tu posición para manipular el **Formulario Universal**, mentir legalmente y ejecutar la acción prohibida: **Robar** objetos valiosos para enriquecerte, operando al margen de la ley desde las entrañas del propio sistema.

---

## 🕹️ Mecánicas Principales

1. **El Escritorio de Inspección:**
   - **El Lente (La Verdad):** Lupa física con 3 espectros ópticos (*Espectro Mágico*, *Biológico* y *Rayos X*) que revelan propiedades ocultas sin texto.
   - **El Formulario Universal (La Coartada):** Tres menús desplegables (*Material*, *Estado*, *Propósito*) para definir legalmente el objeto o mentir creando vacíos legales.
   - **El Libro de Reglas:** Normativas y prohibiciones que se actualizan cada mañana.
2. **4 Resoluciones del Trámite:**
   - `Cobrar` (Día 1+): Trámite legal ordinario que garantiza el sueldo base.
   - `Arrestar` (Día 1+): Comisión por captura si estaba justificado por la ley.
   - `Confiscar` (Día 3+): Incautación para la Corona con bono estatal.
   - `Robar` (Día 3+): Acción oculta de transgresión moral para embolsarse el botín.
3. **Meta-Juego y Moralidad:**
   - **Sistema de Honor Oculto (-100 a +100):** Feedback inmediato sin barra de UI mediante viñetas sutiles (blanca/roja) y acordes sonoros (limpio/disonante).
   - **Economía Doméstica:** Gastos familiares y el **Soborno al Guardia Gato**, que se dispara si robas bajo su mirada.
   - **Game Over:** Inanición familiar inmediata si el dinero cae a 0.
4. **Progresión de 5 Días & 4 Finales:**
   - Campaña de 5 jornadas (8-10 objetos por día, ~40-50 objetos en total).
   - Eventos clave con el **Libro de Alquimia** (Día 3, nota de la hija) y el **Libro de Carpintería** (Día 4, el hijo compra madera).
   - **4 Finales:** *El Buen Ciudadano Muerto*, *El Corrupto Descubierto*, *El Burócrata Gris (Burguesía)* y *El Imperio Familiar (Final Secreto)*.

---

## 🗺️ Estructura de la Bóveda en Obsidian

- `00_Inicio/`: [[00_Inicio/Dashboard|Dashboard Principal]] y [[00_Inicio/Reglas y Entregables|Reglamento Oficial de GUILD 2026]].
- `01_Planificacion_y_Tareas/`: [[01_Planificacion_y_Tareas/Kanban|Tablero Kanban]] y [[01_Planificacion_y_Tareas/Cronograma|Cronograma & Hitos]].
- `02_Game_Design_Document_GDD/`:
  - [[02_Game_Design_Document_GDD/Mecánicas Core|Mecánicas Core & Resoluciones]]
  - [[02_Game_Design_Document_GDD/Historia y Personajes|Historia, Personajes y Familia]]
  - [[02_Game_Design_Document_GDD/Diseño de Niveles|Progresión (5 Días) y 4 Finales]]
- `03_Arte_y_UI/`: [[03_Arte_y_UI/Diseño de Interfaz|Diseño de Interfaz (Mesa de Trabajo)]], [[03_Arte_y_UI/Lista de Assets Visuales|Lista de Assets Visuales]] y [[03_Arte_y_UI/Moodboard|Moodboard]].
- `04_Audio/`: [[04_Audio/Lista de SFX|Lista de SFX]] y [[04_Audio/Referencias Musicales|Referencias Musicales & BGM Dinámico]].
- `05_Programacion/`: [[05_Programacion/Convenciones|Arquitectura Godot & Convenciones]], [[05_Programacion/Flujo de Git|Flujo de Git]] y [[05_Programacion/Bugs y Fixes|Bugs y Fixes]].
- `06_Brainstorming_y_Notas/`: [[06_Brainstorming_y_Notas/Ideas y Notas de Reunión|Ideas y Actas de Reunión]].
- `99_Plantillas/`: Plantillas para assets, personajes y reportes de bugs.
