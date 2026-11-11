# 🎵 Referencias Musicales - Notaría de Aventureros

> [!NOTE]
> **Responsable:** Michael *(Música y Composición)*.
> Atmósfera: Marcha medieval fronteriza, lúgubre, rítmica y satírica. La música no es un simple fondo, sino que reacciona a las decisiones morales y al estado del juego.

---

## 🎧 Estilo y Concepto Musical

- **Tema Principal de Mesa (BGM):** Arreglo de ***Gnossienne No. 1* de Erik Satie**.
  - **Instrumentación:** Guitarra acústica limpia con cuerdas de nailon, laúd medieval y un pulso rítmico suave de percusión seca (como un metrónomo burocrático).
  - **Sensación:** Rutina agotadora, atmósfera de oficina arcaica y un humor subyacente que pregunta al jugador: *"¿hasta dónde te rebajarás por unas monedas?"*.
- **Variación Dinámica (Libro de Reglas):**
  - Procesada en Godot mediante un bus de audio secundario con efecto **Low-Pass Filter (Filtro Pasa-Bajos)** (`cutoff_hz = 550`). Se activa suavemente al desplegar el compendio de normas, transmitiendo concentración mental.
- **Micro-Intervenciones de Honor (Conectadas a la Armonía):**
  - Los destellos de Honor Positivo y Negativo lanzan arpegios o acordes que coinciden armónicamente con la tonalidad de la canción de fondo (ej. Re menor):
    - *Honor Positivo:* Resuelve en un acorde brillante y limpio de Re mayor o Fa mayor.
    - *Honor Negativo:* Introduce una disonancia con un tritono o séptima disminuida tensa.

---

## 🎼 Pistas de Audio y Finales Requeridos

| ID de Pista | Momento / Escena | Duración / Formato | Estilo / Sensación | Estado |
| :--- | :--- | :--- | :--- | :---: |
| `bgm_mesa_aduanas` | Gameplay en el escritorio | 1:30 - 2:00 min (Seamless Loop) | Arreglo de *Gnossienne No. 1*, guitarra y percusión sutil | 🟡 En Progreso |
| `bgm_resumen_noche` | Pantalla de Resumen Diario | 40s (Loop suave) | Tonos nocturnos íntimos, tintineo de monedas y tensión por sobornos | 🔴 Pendiente |
| `jingle_gameover_quiebra`| Bancarrota familiar | 6s - 8s (Jingle) | Cuerdas desgarradas y viento fúnebre | 🔴 Pendiente |
| `bgm_final_1_ciudadano` | Final 1: Buen Ciudadano Muerto | 30s | Requiem melancólico minimalista en guitarra sola | 🔴 Pendiente |
| `bgm_final_2_corrupto` | Final 2: El Corrupto Descubierto| 30s | Redoble militar marcial opresivo y golpe de rejas | 🔴 Pendiente |
| `bgm_final_3_burguesia` | Final 3: El Burócrata Gris | 45s | Vals refinado de clavecín y laúd con aires de aristocracia | 🔴 Pendiente |
| `bgm_final_4_imperio` | Final 4: El Imperio Familiar | 45s | Fanfarria festiva, opulenta e irónica de poder absoluto | 🔴 Pendiente |

---

## ⚙️ Implementación en Godot (Para AudioManager)

- Configuración en `default_bus_layout.tres`:
  - `Master` $\rightarrow$ `BGM` $\rightarrow$ `BGM_Muffled` (con `AudioEffectLowPassFilter`).
  - `Master` $\rightarrow$ `SFX` $\rightarrow$ `Honor_SFX` (con bus prioritario para que nunca se enmascare el feedback de honor).
- Al abrir el libro de reglas:
  ```gdscript
  var bus_idx = AudioServer.get_bus_index("BGM")
  # Tween para alternar el volumen o la activación del filtro pasa-bajos
  ```
