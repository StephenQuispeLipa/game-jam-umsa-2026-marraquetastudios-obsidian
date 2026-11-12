# 🐛 Bugs y Fixes - Notaría de Aventureros

> [!WARNING] **Regla de oro previo al empaquetado final (Feature Freeze)**
> Si un bug no rompe el juego ni congela la partida, y faltan pocas horas para el cierre, **no lo toques**. El riesgo de introducir un bug peor de última hora es altísimo. Durante las últimas 8 horas solo se atienden **Bugs Críticos Bloqueantes**.

---

## 🔥 Bugs Críticos (Bloqueantes / Crashes)

*Deben ser resueltos antes de generar la build final de entrega para Windows.*

- [ ] **[BUG-01]** Verificar que arrastrar `Tool_Lens.tscn` fuera de los límites de la pantalla no cause excepciones por puntero nulo o bloqueo de entrada del ratón.
  - *Severidad:* Crítica
  - *Estado:* 🟢 En pruebas
  - *Notas:* Asegurar `clamp` en las coordenadas globales de arrastre en `tool_lens.gd`.
- [ ] **[BUG-02]** Asegurar que tras Game Over o completar un Final, el reinicio de partida limpie completamente las variables en `GameManager.gd` (Día, Dinero, Honor, Baúl).
  - *Severidad:* Crítica
  - *Estado:* 🔴 Pendiente
  - *Notas:* Implementar método formal `reset_game_state()` en el Autoload `GameManager.gd`.

---

## ⚖️ Bugs de Lógica Burocrática & Finales

*Verificaciones de gameplay para garantizar que la experiencia sea coherente con el GDD.*

- [ ] **[QA-01]** Comprobar que conservar el **Libro de Alquimia** y el **Libro de Carpintería** en el baúl active inequívocamente el **Final 4 (El Imperio Familiar)** al concluir el Día 5.
  - *Severidad:* Alta
  - *Estado:* 🔴 Pendiente
- [ ] **[QA-02]** Validar que la cuota de **Soborno al Guardia Gato** no genere números negativos ni quiebre al jugador si este no cometió ningún robo durante la jornada.
  - *Severidad:* Alta
  - *Estado:* 🔴 Pendiente
- [ ] **[QA-03]** Verificar que la acción `Robar` reste efectivamente los puntos de honor estipulados y active la viñeta roja junto con el acorde disonante.
  - *Severidad:* Media
  - *Estado:* 🔴 Pendiente

---

## ⚠️ Glitches Menores / UI y Shaders

*Solucionar solo si sobra tiempo tras tener la build básica completamente operativa.*

- [ ] Asegurar que el shader de máscara circular de El Lente (`lens_mask.gdshader`) no deje artefactos visuales al superponerse sobre los bordes de la mesa.
- [ ] Ajustar el z-index de los desplegables de `Universal_Form.tscn` para que la lista flotante no quede oculta detrás de la bandeja de botines.
- [ ] Verificar que los sliders del menú de opciones modifiquen instantáneamente los buses de `AudioServer` sin saltos bruscos de volumen.

---

## 📝 Registro de Errores Solucionados (Fixed)

- [x] **[FIXED]** Descarte de scripts y prefabs obsoletos del prototipo inicial de plataformas.
  - *Causa:* Migración conceptual y formal al GDD de *Notaría de Aventureros* para la GUILD Game Jam 2026.
  - *Solución:* Estructura de carpetas y convención de nombres adaptada al simulador de aduanas 2D en Godot 4.x.
