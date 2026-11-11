# 🖥️ Diseño de Interfaz (UI / UX) - Mesa de Aduanas

> [!NOTE] **Enfoque de UI & Diegesis**
> Al ser un simulador estilo *Papers, Please*, la interfaz **ES** el juego. La mesa de aduanas, los pergaminos, los instrumentos de análisis y los botones de trámite componen un entorno físico reactivo. Para maximizar la inmersión, el jugador **no tiene barras de estadísticas tradicionales en pantalla**; todo se comunica mediante el entorno y feedback sensorial.

---

## 🖼️ Prototipo de la Mesa de Trabajo

![Prototipo de Interfaz y Mesa de Trabajo](adjuntos/mockup_mesa_juego.jpg)

---

## 🧭 Distribución de la Escena (`Desk_View.tscn`)

```text
+-----------------------------------------------------------------------------------+
| [Menú / Pausa]                 [Ventanilla: Arco & Aventurero]                    |
|                                                                                   |
|                                [Bandeja de Botín]               [Guardia Gato]    |
|                                (Ítem en Inspección)             (Vigilante)       |
|                                                                                   |
| -------------------------- MESA DE TRABAJO -------------------------------------- |
|                                                                                   |
| [Formulario Universal]          [El Lente]                 [Panel de Trámites]   |
| • Material [Desplegable]        • 3 Filtros:               • [ 💰 COBRAR   ]     |
| • Estado   [Desplegable]          1. Mágico (Púrpura)      • [ ⛓️ ARRESTAR ]     |
| • Propósito[Desplegable]          2. Biológico (Verde)     • [ 📦 CONFISCAR] (D3)|
|                                   3. Rayos X (Cian/Hueso)  • [ 🤫 ROBAR    ] (D3)|
|                                                                                   |
| [ 📖 Libro de Reglas ]                                                            |
+-----------------------------------------------------------------------------------+
| >>> [Bordes de Pantalla: Viñeta Blanca / Roja para Feedback de Honor Oculto] <<<  |
+-----------------------------------------------------------------------------------+
```

| Elemento | Posición en Pantalla | Tipo de Nodo | Función / Comportamiento UX |
| :--- | :--- | :--- | :--- |
| **Menú / Pausa** | Superior Izquierda | `TextureButton` | Pausa, reanudación, reinicio de jornada y ajustes de audio. |
| **Ventanilla / Exterior** | Fondo Superior | `TextureRect` | Marco de piedra medieval con vista a la fila de aventureros en espera. |
| **Aventurero (Cliente)** | Centro Fondo | `AnimatedSprite2D` | Cliente actual; animaciones de espera, alivio o pánico al ser arrestado. |
| **Guardia Gato** | Centro-Derecha Media | `AnimatedSprite2D` | Vigila la mesa. Si ejecutas la acción `Robar`, cambia su sprite a una mirada cómplice y socarrona. |
| **Bandeja de Botín** | Centro de la Mesa | `Area2D` / `Marker2D` | Espacio físico donde descansa el objeto confiscado a inspeccionar. |
| **El Lente (La Verdad)** | Centro Inferior Mesa | `Area2D` (Draggable) | Lupa con 3 filtros de espectro óptico que se arrastra sobre el botín. |
| **Selector de Filtro** | Integrado en El Lente | `TextureButton` / Input | Dial giratorio para conmutar entre Espectro Mágico, Biológico y Rayos X. |
| **Formulario Universal** | Inferior Izquierda Mesa | `Control` (Scroll/Card) | Pergamino con 3 menús `OptionButton` (Material, Estado, Propósito). |
| **Libro de Reglas** | Esquina Inf. Izquierda | `TextureButton` | Abre en pantalla completa el manual de leyes del día (`Rulebook_Popup.tscn`). |
| **Botones de Resolución** | Inferior Derecha Mesa | `VBoxContainer` / `Buttons`| Acciones del trámite: `Cobrar`, `Arrestar`, `Confiscar` (D3+) y `Robar` (D3+). |
| **Viñeta de Honor** | Pantalla completa (CanvasLayer)| `ColorRect` con Shader | Flash sutil de viñeta blanca (honor positivo) o roja (honor negativo). |

---

## 🔍 Mecánica Visual de El Lente (3 Filtros)

El Lente utiliza un shader de máscara circular que revela texturas y capas ocultas sobre el sprite del objeto:

```mermaid
flowchart TD
    BaseItem["Objeto Base en Mesa (Sprite Visible)"] --> LensOverlap{"¿El Lente está encima?"}
    LensOverlap -- Filtro 1: Mágico --> ShaderMagic["Shader Púrpura/Azul: Revela runas, glifos y auras de encantamiento"]
    LensOverlap -- Filtro 2: Biológico --> ShaderBio["Shader Verde Tóxico: Revela venenos, sangre seca, esporas y parásitos"]
    LensOverlap -- Filtro 3: Rayos X --> ShaderXRay["Shader Cian/Hueso: Revela hojas ocultas, compartimentos y mecanismos secretos"]
```

---

## 📝 Formulario Universal (La Coartada)

- **3 Menús Desplegables (`OptionButton`):**
  1. `Material`: Hierro, Madera, Oro, Hueso, Cuero, Cristal arcano, etc.
  2. `Estado`: Inerte, Flamígero, Tóxico, Encantado, Roto, etc.
  3. `Propósito`: Agrícola, Médico, Doméstico, Bélico, Estudio Pedagógico, etc.
- **Interacción:** El jugador puede reflejar con fidelidad lo que revela El Lente o mentir alterando los campos para evadir las prohibiciones del Libro de Reglas del día.

---

## ⚡ Botones de Resolución de Trámite

Aparecen alineados a la derecha de la mesa:
1. **`💰 Cobrar` (Disponible Día 1 a 5):** Estampa un recibo fiscal, entrega el botín al cliente y suma tu sueldo base.
2. **`⛓️ Arrestar` (Disponible Día 1 a 5):** Hace sonar una campana de alarma; guardias apresan al aventurero. Otorga comisión si el libro lo exigía.
3. **`📦 Confiscar` (Disponible Día 3 a 5):** El objeto se traslada a la caja fuerte del Reino. Da bono de incautación si la ley lo ordenaba.
4. **`🤫 Robar` (Disponible Día 3 a 5 - Mecánica Oculta):**
   - Un botón o cajón falso bajo el escritorio, sin explicación en el Libro de Reglas.
   - El objeto cae en tu inventario personal oculto.
   - La pantalla emite una **viñeta roja** con tono disonante (baja de honor).
   - El Guardia Gato guiña un ojo o sonríe de perfil (se entera del robo).

---

## 🌙 Pantalla de Fin de Jornada (`DaySummary_View.tscn`)

Al terminar de procesar los 8-10 clientes del día:

```text
+-------------------------------------------------------------------+
|                    BALANCE CONTABLE - DÍA [X]                     |
+-------------------------------------------------------------------+
|  INGRESOS:                                                        |
|    • Sueldo Base de la Jornada ...................... +50 Oro     |
|    • Comisiones por Captura ......................... +30 Oro     |
|    • Bonos de Incautación Real ...................... +15 Oro     |
|    • Venta de Botines Robados ....................... [+ Vender?] |
|        [Ítem Robado A] -> [Vender por ?? Oro] / [Conservar en Baúl]
|                                                                   |
|  GASTOS OBLIGATORIOS:                                             |
|    • Manutención & Alimentos Familiares ............. -35 Oro     |
|    • Alquiler de Buhardilla ......................... -20 Oro     |
|    • SOBORNO AL GUARDIA GATO ........................ -60 Oro 🐱  |
|      (¡Aumenta drásticamente si robaste durante el turno!)        |
|                                                                   |
|  ---------------------------------------------------------------  |
|  BALANCE FINAL DEL DÍA: [ XXX Oro ]                               |
|                                                                   |
|  DIARIO FAMILIAR / CARTAS:                                        |
|  "Día 3: Tu hija se pasa las noches leyendo sobre transmutación..."|
|  "Día 4: Tu hijo compró un cargamento masivo de madera..."        |
|                                                                   |
|                 [ CONTINUAR AL SIGUIENTE DÍA ]                    |
+-------------------------------------------------------------------+
```

---

## 🔀 Flujo Global de Pantallas

```mermaid
flowchart TD
    Title["Pantalla de Título<br>(Notaría de Aventureros)"] --> IntroDay["Comienzo del Día (1 al 5)<br>(Actualización del Libro de Reglas)"]
    IntroDay --> Desk["Mesa de Aduanas (`Desk_View.tscn`)<br>• Lente (3 Filtros)<br>• Formulario Universal<br>• 4 Acciones (Cobrar/Arrestar/Confiscar/Robar)"]
    Desk --> Feedback["Feedback Sensorial de Honor<br>(Viñeta Blanca o Roja + Acorde)"]
    Feedback --> Desk
    Desk --> DaySummary["Pantalla de Resumen Nocturno<br>(Sueldo, Soborno del Guardia Gato, Notas Familiares)"]
    DaySummary --> BalanceCheck{"¿Dinero > 0?"}
    BalanceCheck -- No --> GameOver["💀 Game Over:<br>Inanición Familiar"]
    BalanceCheck -- Sí (Día < 5) --> IntroDay
    BalanceCheck -- Sí (Fin Día 5) --> EndingsEvaluator{"Evaluación Final<br>(Dinero, Honor, Libros)"}
    EndingsEvaluator --> End1["🪦 Final 1: El Buen Ciudadano Muerto"]
    EndingsEvaluator --> End2["⛓️ Final 2: El Corrupto Descubierto"]
    EndingsEvaluator --> End3["🍷 Final 3: El Burócrata Gris / Burguesía"]
    EndingsEvaluator --> End4["👑 Final 4: El Imperio Familiar (Secreto)"]
```
