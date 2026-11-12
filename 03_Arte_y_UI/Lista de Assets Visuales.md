# 📦 Lista de Assets Visuales - Notaría de Aventureros

> [!TIP]
> **Estilo:** Pixel Art (paleta fantasía medieval lúgubre, texturas nítidas `Nearest`).
> **Responsable Principal:** Lucas *(Sprites, Animaciones y Mockups)*.

---

## 👤 Personajes (Sprites Pixel Art)

| Asset                     | Dimensiones | Animaciones / Estados                                                                        | Responsable |    Estado    |
| :------------------------ | :---------- | :------------------------------------------------------------------------------------------- | :---------- | :----------: |
| `char_guardia`            | ~80x80 px   | Idle con armadura (4f), hablar/murmurar (3f), **Reacción cómplice al robar** (guiño/sonrisa) | Lucas       | 🔴 Pendiente |
| `char_burocrata_manos`    | ~64x64 px   | Manos del oficial en primera persona (manipular herramientas, sellar, abrir cajón secreto)   | Lucas       | 🔴 Pendiente |
| `npc_aventurero_guerrero` | ~64x64 px   | Idle nervioso / porte rudo / reacción arresto                                                | Lucas       | 🔴 Pendiente |
| `npc_aventurero_maga`     | ~64x64 px   | Idle altiva / disimulo arcano                                                                | Lucas       | 🔴 Pendiente |
| `npc_aventurero_picaro`   | ~64x64 px   | Mirada esquiva / pícaro goblin o enano                                                       | Lucas       | 🔴 Pendiente |
| `npc_anciano_erudito`     | ~64x64 px   | Anciano encorvado que porta el Libro de Alquimia (Día 3)                                     | Lucas       | 🔴 Pendiente |
| `npc_artesano_viajero`    | ~64x64 px   | Carpintero que porta el Libro de Carpintería (Día 4)                                         | Lucas       | 🔴 Pendiente |

---

## 🪑 Escenario y Fondos

| Asset | Formato | Descripción | Responsable | Estado |
| :--- | :--- | :--- | :--- | :---: |
| `bg_mesa_aduana` | PNG (~320x180 o base) | Mesa de madera vista frontal/ligeramente cenital con textura de vetas | Lucas | 🟡 En Progreso |
| `bg_arco_castillo` | PNG | Arco de piedra de la ventanilla con vista al exterior y siluetas en fila | Lucas | 🔴 Pendiente |
| `bg_cajon_secreto` | PNG | Hendidura / cajón oculto bajo la mesa para la acción de `Robar` | Lucas | 🔴 Pendiente |

---

## 🛠️ Herramientas e Instrumentos de Mesa

| Asset | Tipo | Uso en Gameplay | Responsable | Estado |
| :--- | :--- | :--- | :--- | :---: |
| `tool_lente_inspector` | Sprite PNG | Lente de aumento con mango de bronce y dial giratorio de 3 posiciones | Lucas | 🔴 Pendiente |
| `shader_espectro_magico` | Godot Shader | Tinte púrpura/azul traslúcido que revela texturas con runas y auras arcanas | Lucas / Dev | 🔴 Pendiente |
| `shader_espectro_biologico`| Godot Shader | Tinte verdoso fosforescente que resalta venenos, parásitos y esporas | Lucas / Dev | 🔴 Pendiente |
| `shader_espectro_rayosx` | Godot Shader | Tinte cian/monocromático que expone el interior, mecanismos y huesos | Lucas / Dev | 🔴 Pendiente |
| `ui_formulario_universal` | 9-slice / Texture | Base de pergamino encuadernado con 3 ranuras para menús `OptionButton` | Lucas | 🔴 Pendiente |
| `ui_libro_reglas` | Sprites / Textura | Libro encuadernado en cuero con pestañas laterales para abrir y hojear | Lucas | 🔴 Pendiente |
| `btn_accion_cobrar` | TextureButton | Botón estilizado con monedas / timbre oficial de arancel | Lucas | 🔴 Pendiente |
| `btn_accion_arrestar` | TextureButton | Botón estilizado con grilletes de hierro | Lucas | 🔴 Pendiente |
| `btn_accion_confiscar`| TextureButton | Botón estilizado con cofre / sello de incautación real (Día 3+) | Lucas | 🔴 Pendiente |
| `btn_accion_robar` | TextureButton | Botón sutil / hendidura de bolsillo oculta (Día 3+) | Lucas | 🔴 Pendiente |

---

## 🗡️ Objetos de Puzzle (Botines de Aventureros: 40-50 Ítems)

Los objetos cuentan con su sprite base visible y capas revelables bajo cada filtro:

| Ítem / ID | Propiedad Visible | Espectro Mágico 🔮 | Espectro Biológico 🧬 | Rayos X 💀 | Rol / Día |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `item_espada_corta` | Espada común | Inerte | Limpia | Hoja sólida | Día 1 (Tutorial) |
| `item_hacha_pesada` | Hacha de batalla | Inerte | Manchas de óxido | Mango hueco (ilegal) | Día 1 (Arresto obvio) |
| `item_bastón_roble` | Bastón de madera | Runa de ignición oculta | Limpio | Núcleo sólido | Día 2 (Magia prohibida) |
| `item_frasco_jarabe` | Frasco medicinal | Inerte | Toxina de basilisco | Cristal grueso | Día 2 (Veneno bio) |
| `item_daga_ornamental`| Daga decorativa | Inerte | Limpia | Compartimento con ganzúa | Día 2 (Rayos X) |
| ⭐ `item_libro_alquimia` | Libro con grabados arcanos | Flujo continuo de transmutación | Piel de quimera | Glifos metálicos internos | **Día 3 (OBJETO CLAVE)** |
| `item_calavera_relicario`| Cráneo de adorno | Aura nigromántica prohibida | Esporas fúngicas | Núcleo de gemas robadas | Día 3 (Confiscar o Robar)|
| ⭐ `item_libro_carpinteria`| Manual de ebanistería | Inerte | Aserrín inofensivo | Hojas prensadas con diagramas | **Día 4 (OBJETO CLAVE)** |
| `item_reloj_mecanico` | Reloj de bolsillo de lujo | Sin magia | Limpio | Mecanismo de detonación | Día 4 (Caso trampa) |
| `item_corona_profanada` | Corona dorada | Maldición milenaria activa | Parásito latente en gema | Oro hueco rellenado de plomo | Día 5 (Clímax) |
| *(40+ ítems adicionales)*| Reliquias, gemas, pociones, armas, cálices, anillos | Variaciones de runas | Variaciones de toxinas | Variaciones de contrabando | Días 1 a 5 |

---

## 🎭 Efectos Visuales y UI de Meta-Juego

| Asset / Shader | Tipo | Propósito | Estado |
| :--- | :--- | :--- | :---: |
| `shader_vineta_blanca` | CanvasLayer Shader | Destello periférico blanco suave al ganar honor (acción justa/legal) | 🔴 Pendiente |
| `shader_vineta_roja` | CanvasLayer Shader | Destello periférico rojo/oscuro al perder honor (robo o arresto injusto) | 🔴 Pendiente |
| `ui_pantalla_resumen` | 9-slice / Panel | Fondo de escritorio nocturno con vela encendida para el balance diario | 🔴 Pendiente |
| `ui_epilogo_final1` | Ilustración Pixel | Final 1: El Buen Ciudadano Muerto (habitación vacía y helada) | 🔴 Pendiente |
| `ui_epilogo_final2` | Ilustración Pixel | Final 2: El Corrupto Descubierto (calabozo y rejas) | 🔴 Pendiente |
| `ui_epilogo_final3` | Ilustración Pixel | Final 3: El Burócrata Gris (salón burgués con copas y chimenea) | 🔴 Pendiente |
| `ui_epilogo_final4` | Ilustración Pixel | Final 4: El Imperio Familiar (palacio real con estatuas de madera y oro) | 🔴 Pendiente |
