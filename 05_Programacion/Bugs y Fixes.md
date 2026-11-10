# 🐛 Bugs y Fixes

> [!WARNING] **Regla de oro previo al empaquetado final**
> Si un bug no rompe el juego ni congela la partida, y faltan 3 horas para el cierre, **no lo toques**. El riesgo de introducir un bug peor de última hora es altísimo.

---

## 🔥 Bugs Críticos (Bloqueantes / Crashes)

*Deben ser resueltos antes de generar la build de entrega.*

- [ ] **[BUG-01]** El jugador se queda atascado entre esquinas al saltar cerca de una pared.
  - *Severidad:* Crítica
  - *Estado:* 🟡 Investigando
  - *Notas:* Revisar el raycast de suelo y el margen de colisión (`margin` o `skin width`).
- [ ] **[BUG-02]** La música no reinicia al hacer clic en "Reintentar" tras Game Over.
  - *Severidad:* Media
  - *Estado:* 🔴 Pendiente

---

## ⚠️ Bugs Menores / Glitches Cosméticos

*Solucionar solo si sobra tiempo tras tener la build básica lista.*

- [ ] Parpadeo de 1 frame en el sprite de salto al aterrizar.
- [ ] El texto de puntuación no centra correctamente cuando supera los 999 puntos.

---

## 📝 Registro de Errores Solucionados (Fixed)

- [x] **[FIXED]** La build WebGL se quedaba en pantalla negra al cargar escenas.
  - *Causa:* Formato de textura no compatible con WebGL 2.0.
  - *Solución:* Se cambió la compresión a DXT / WebGL standard en los ajustes del proyecto.
