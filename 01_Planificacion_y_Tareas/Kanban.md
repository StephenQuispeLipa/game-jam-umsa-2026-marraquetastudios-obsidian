---

kanban-plugin: board

---

## 💡 Backlog & Stretch Goals (Opcionales)

- [ ] **Lucas / Equipo:** Ampliación del catálogo a 35-50 objetos si sobra tiempo tras el Freeze #arte #stretch
- [ ] **Lucas / Daniel:** Efecto de distorsión de lente cóncava al arrastrar la lupa sobre la mesa #arte #polish
- [ ] **Lucas / Daniel:** Partículas arcanas y humo verde flotante al conmutar filtros de El Lente #arte #polish
- [ ] **Daniel:** Animación de temblor sutil de pantalla (screen shake) al presionar Arrestar o Confiscar #dev #juice
- [ ] **Lucas / Michael:** Cartas manuscritas ilustradas adicionales para la familia en resúmenes nocturnos #arte #narrativa
- [ ] **Michael:** Variaciones adicionales de balbuceos vocales modulados (`vox`) para diferentes arquetipos de clientes #audio


## ⏳ To Do — Fase 1: MVP Core de Inspección (Días 1 y 2)

- [ ] **Daniel:** Programar `Tool_Lens.tscn` con drag & drop suave, límites de mesa y máscara circular (`lens_mask.gdshader`) #dev #p1 #mvp
- [ ] **Daniel:** Implementar los 3 shaders de espectro óptico (`spectrum_magic.gdshader`, `spectrum_bio.gdshader`, `spectrum_xray.gdshader`) #dev #p1 #mvp
- [ ] **Esther:** Crear `Universal_Form.tscn` con los 3 `OptionButton` (Material, Estado, Propósito) y emisión de señales de coartada #dev #p1 #mvp
- [ ] **Esther:** Implementar `DailyRulesDatabase.gd` con normativas, excepciones y criterios de arancel/arresto para Días 1 y 2 #dev #p1 #mvp
- [ ] **Michael:** Configurar `GameManager.gd` como Autoload: persistencia de Día (1-5), Dinero acumulado y Honor (-100 a +100) #dev #core #mvp
- [ ] **Daniel / Equipo:** Ensamblar escena de juego `Desk_View.tscn` integrando ventanilla, bandeja de inspección y panel con botones `Cobrar` y `Arrestar` #dev #p1 #mvp
- [ ] **Lucas / Esther:** Crear catálogo MVP inicial de 8 a 10 objetos con sus capas para Días 1 y 2 (tutorial, contrabando evidente y casos legales) #arte #dev #p1 #mvp


## ⚡ To Do — Fase 2: Progresión, Economía & 4 Finales (Días 3 al 5)

- [ ] **Daniel / Esther:** Habilitar botones `Confiscar` y la acción oculta transgresora `Robar` en `Action_Panel.tscn` a partir del Día 3 #dev #p1
- [ ] **Esther:** Expandir `DailyRulesDatabase.gd` con leyes de incautación real, prohibiciones avanzadas y vacíos legales de Días 3 a 5 #dev #p2
- [ ] **Lucas / Equipo:** Diseñar e integrar con prioridad absoluta los dos ítems clave: ⭐ **Libro de Alquimia** (Día 3) y ⭐ **Libro de Carpintería** (Día 4) #arte #dev #p1
- [ ] **Lucas / Esther:** Diseñar e integrar lote de objetos intermedios para Días 3 a 5 (alcanzando 18-22 objetos variados y testeados) #arte #dev #p2
- [ ] **Michael:** Crear pantalla de Resumen Nocturno (`Day_Summary.tscn`): cálculo de sueldo, comisiones, venta/retención de botines y gastos familiares #dev #ui #p1
- [ ] **Michael:** Programar la cuota de **Soborno al Guardia Gato** (aumento exponencial si robas botines) y eventos narrativos (cartas de la hija y el hijo) #dev #p1
- [ ] **Esther / Michael:** Programar evaluador de los 4 Finales y pantalla de derrota por inanición en `Endings_Screen.tscn` según Dinero, Honor y Libros conservados #dev #flow #p1


## 🎛️ To Do — Fase 3: Menús, Audio & Game Feel (Pulido de Jam)

- [ ] **Daniel:** Crear Menú Principal (`MainMenu.tscn`) con botones Jugar, Opciones, Créditos y Salir estilizados en pixel art #dev #ui #p2
- [ ] **Daniel:** Implementar Menú de Opciones reutilizable (`OptionsMenu.tscn`) con sliders de volumen (`AudioServer`) y selector de Pantalla Completa #dev #ui #p2
- [ ] **Daniel:** Programar Menú de Pausa in-game (`PauseMenu.tscn`, Tecla ESC, Process Mode: Always) que permita reanudar, abrir opciones o reiniciar jornada #dev #ui #p2
- [ ] **Daniel:** Crear pantalla de Créditos (`CreditsMenu.tscn`) con lista de integrantes, roles, atribuciones y mención formal de GUILD Game Jam 2026 #dev #ui #reglamento
- [ ] **Daniel:** Configurar `SceneTransition.tscn` (Autoload CanvasLayer) para fundidos suaves a negro entre menús, jornadas y resúmenes #dev #core #p2
- [ ] **Esther:** Crear pantalla de inicio de jornada (`Day_Intro.tscn`) con pregón matutino y lectura del Decreto Real del día #dev #flow #p2
- [ ] **Michael:** Programar `Honor_Vignette.tscn` (shader de viñeta CanvasLayer) con destellos inmediatos blanco (honor positivo) y rojo (honor negativo) #dev #juice #p1
- [ ] **Michael:** Diseñar foley de oficina (`sfx_accion_cobrar`, `sfx_accion_arrestar`, `sfx_accion_confiscar`, `sfx_accion_robar`) y acordes de moralidad (consonante vs disonante) #audio #p1
- [ ] **Michael:** Implementar síntesis de voz modulada estilo Animal Crossing (`vox`) para el Guardia Gato y los aventureros #audio #p2
- [ ] **Lucas:** Diseñar sprites reactivos del Guardia Gato: idle con armadura, mirada de sospecha y pose cómplice/guiño al presenciar un robo #arte #p2
- [ ] **Lucas:** Dibujar las 4 estampas ilustradas en pixel art para los 4 Finales y la pantalla de Game Over #arte #p2


## 🚀 In Progress

- [ ] **Michael:** Arreglo musical adaptativo de *Gnossienne No. 1* y buses de audio Master/BGM/SFX con filtro Low-Pass dinámico #audio #en-progreso
- [ ] **Lucas:** Arte pixel art de la mesa de aduanas (`bg_mesa_aduana`) y props principales de la oficina #arte #en-progreso
- [ ] **Equipo:** Prototipado y ensamble de la escena principal `Desk_View.tscn` #dev #en-progreso


## 🧪 Testing, Balance & Freeze (Cierre Limpio)

- [ ] **Michael / Design:** Balancear la economía doméstica diaria (sueldo base vs manutención familiar vs sobornos del gato): evitar quiebra prematura injusta en Días 1 y 2 #design #balance
- [ ] **Esther / Dev:** Verificar mediante pruebas unitarias/manuales que los **4 Finales** se disparen con exactitud matemática según Dinero, Honor y posesión de los dos libros #dev #qa
- [ ] **Daniel / Design:** Comprobar la legibilidad óptica de los 3 filtros de El Lente en todos los objetos (evitar ambigüedad visual en deducciones) #qa #design
- [ ] **Equipo:** Sesión de pruebas de estabilidad: verificar que el bucle completo (Menú -> Día 1 a 5 -> Resúmenes -> Finales -> Reinicio) no tenga memory leaks ni congelamientos #qa #estabilidad
- [ ] **Equipo:** **FEATURE FREEZE ESTRICTO (8 horas antes de la entrega):** Cero código o mecánicas nuevas; dedicación exclusiva a corregir fallos críticos y empaquetar #freeze #hito


## 📦 Requisitos de Entrega & Reglamento (Cero Riesgo de Descalificación)

- [ ] **Michael (Rep):** Completar formalmente la tabla de declaración de recursos de terceros y uso de IA generativa en [[00_Inicio/Reglas y Entregables|Reglas y Entregables]] #reglamento #urgente
- [ ] **Equipo:** Verificar que Michael, Lucas, Daniel y Esther hayan enviado su formulario individual de inscripción con exactamente el mismo nombre de equipo #admin #reglamento
- [ ] **Daniel / Michael:** Generar exportación de ejecutable para Windows `.exe` y verificar ejecución fluida en una PC limpia sin Godot instalado #dev #qa
- [ ] **Michael:** Grabar y editar video de demostración de gameplay de 30 a 60 segundos para la exhibición del jurado #marketing #entrega
- [ ] **Michael / Esther:** Redactar ficha de entrega para Itch.io: título definitivo, sinopsis, controles (ratón/ESC), integrantes y notas de instalación #admin #entrega
- [ ] **Equipo:** Coordinar logística para la asistencia presencial obligatoria el **21 de noviembre de 2026** a la exhibición y premiación #admin #presencial
- [ ] **Michael:** Preparar memoria USB con build `.exe` testeada, video demo y respaldo offline de contingencia para la presentación #admin #contingencia


## ✅ Done

- [x] Creación de la estructura de la bóveda de Obsidian para el equipo
- [x] Registro y análisis del reglamento oficial de GUILD Game Jam 2026
- [x] Aprobación unánime del GDD final: *Notaría de Aventureros* / *El Vacío Legal* (5 días, 4 resoluciones, El Lente con 3 filtros, Honor y 4 Finales)
- [x] Documentación de la arquitectura modular y árbol de escenas en Godot 4.x (`Convenciones.md`)
- [x] Definición del flujo de Git por ramas para evitar colisiones entre desarrolladores (`Flujo de Git.md`)
- [x] Mockup visual del escritorio de aduanas aprobado (`mockup_mesa_juego.jpg`)
- [x] Reestructuración integral del Kanban orientada a MVP, contingencia y entrega limpia


%% kanban:settings
```
{"kanban-plugin":"board"}
```
%%
