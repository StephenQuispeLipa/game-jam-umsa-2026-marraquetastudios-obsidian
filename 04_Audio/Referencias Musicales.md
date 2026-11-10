# 🎵 Referencias Musicales - Notaría de Aventureros

> [!NOTE]
> **Responsable:** Michael *(Música y Composición)*.
> Atmósfera: Marcha medieval fronteriza, lúgubre pero rítmica y satírica.

---

## 🎧 Estilo y Concepto Musical

- **Tema Principal (BGM):** Arreglo de ***Gnossienne No. 1* de Erik Satie**.
  - **Instrumentación:** Guitarra acústica o eléctrica limpia, con sutiles toques de percusión medieval o bombo seco marcando el ritmo de paso de aduana.
  - **Sensación:** Rutina pesada, misterio de oficina arcaica, aire satírico de "¿realmente estoy haciendo esto por unas monedas?".
- **Variación Dinámica (Libro de Reglas):**
  - La misma pista base pero procesada en Godot mediante un bus de audio con efecto **Low-Pass Filter (Filtro Pasa-Bajos)** que se activa gradualmente cuando el jugador abre el Libro de Reglas a pantalla completa. Simula la concentración mental y la inmersión en la lectura.

---

## 🎼 Pistas de Audio Requeridas

| ID de Pista | Momento / Escena | Duración / Loop | Estilo / Sensación | Estado |
| :--- | :--- | :--- | :--- | :---: |
| `bgm_aduanas_main` | Mesa de Juego (Gameplay) | 1:30 - 2:00 min (Seamless Loop) | Arreglo de *Gnossienne No. 1*, guitarra rítmica | 🟡 En Progreso |
| `bgm_cierre_dia` | Resumen Financiero | 30s - 45s (Loop suave) | Conteo de monedas, sensación de descanso efímero | 🔴 Pendiente |
| `jingle_multa_fatal` | Game Over / Quiebra | 4s - 6s (Jingle) | Acorde disonante con toque de campana fúnebre | 🔴 Pendiente |
| `jingle_semana_superada` | Victoria (Fin Día 4) | 8s - 12s (Jingle) | Fanfarria irónica y festiva de taberna | 🔴 Pendiente |

---

## ⚙️ Implementación en Godot (Para Programación / Audio)

- Configurar en `default_bus_layout.tres`:
  - Bus `Master` $\rightarrow$ Bus `BGM` $\rightarrow$ Bus `BGM_Muffled` con efecto `AudioEffectLowPassFilter` (`cutoff_hz = 600`).
  - Al abrir el libro de reglas: `AudioServer.set_bus_effect_enabled(...)` mediante un `Tween` suave de volumen.
