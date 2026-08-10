---
tipo: regla
dominio: animacion
idioma: es
revision: 2026-08
plataformas: web, escritorio, video
---

# Reglas de Animación — Estética Kurzgesagt

> Conjunto de reglas de **movimiento**: tiempos, curvas (easing), microinteracciones, transiciones, estados y efectos de marca. Pensado principalmente para **web y escritorio**, con una sección específica para **vídeo** (donde la marca nace). Este documento es autocontenido y portable; las referencias `A-###` remiten a este archivo, `V-###` a diseño visual, `U-###` a UX y `G-###` al índice.
>
> Niveles de obligatoriedad: `[IMPERATIVO]` no negociable · `[RECOMENDADO]` preferible · `[CONTEXTO]` apoyo. Identificadores `A-###`.

---

## 1. Principios de movimiento

### A-001: Movimiento con propósito
[IMPERATIVO] Toda animación debe cumplir una función: dirigir la atención, comunicar un estado, dar feedback, o reforzar la marca. Prohibido animar "porque sí". Antes de animar algo, responder: *¿qué comunica este movimiento?* Si no hay respuesta, no se anima.

### A-002: Sistema único de tiempos
[IMPERATIVO] Todo el proyecto usa **un solo sistema de duraciones y curvas** (definidos en `A-005` y `A-006`), sin excepciones por elemento o vista (ver `G-007`). Registrar las duraciones como tokens del proyecto, igual que los colores.

### A-003: Frenada suave, no aceleración brusca
[IMPERATIVO] Los elementos **desaceleran** al llegar (ease-out) o llegan con un ligero rebote contenido. Prohibido el movimiento lineal constante o acelerar hacia el final (ease-in) para entradas; el ease-in solo es aceptable para salidas (el objeto "sale" ganando velocidad, como un elemento que se desliza fuera).

### A-004: Rebote como firma, con moderación
[RECOMENDADO] El "salto suave" (overshoot) es la firma del estilo: un elemento llega, pasa un poco su destino y vuelve. Aplicarlo solo a entradas de elementos destacados (títulos, tarjetas protagonistas, resultados) y nunca a más de 1–2 elementos a la vez. El overshoot excesivo en todo resulta caricaturesco.

### A-005: Sistema de duraciones (referencia)
[IMPERATIVO] Escala base de duraciones para web/escritorio. Los tiempos de vídeo se tratan aparte (ver `A-032`):

```
Escala base (web/escritorio)
  Feedback de hover/tap        80–120 ms   (inmediato, casi imperceptible)
  Microinteracción             150–250 ms   (hover con elevación, iconos, toggles)
  Aparición de elemento        200–400 ms   (entrada con rebote de un elemento)
  Cambio de estado/transición  300–500 ms   (panel, sección, foco)
  Transición entre pantallas   350–500 ms   (cambio de vista completo)
  Elementos de marca           600–1200 ms  (personaje, partículas, bobbing)
```

Regla: si el movimiento debe sentirse *instantáneo*, usar 80–120 ms. Si debe sentirse *suave*, 200–400 ms. Nunca superar 500 ms para UI funcional salvo elementos decorativos de marca.

### A-006: Sistema de curvas (easing)
[IMPERATIVO] Curvas de referencia para web/escritorio (formato cubic-bezier, equivalente a curvas de velocidad en cualquier motor de animación):

```
Curvas del sistema
  Entrada estándar (frenada suave)  cubic-bezier(0.22, 1, 0.36, 1)   ← la más usada
  Entrada rápida (expo)             cubic-bezier(0.16, 1, 0.3, 1)     ← apariciones elegantes
  Rebote controlado (overshoot)     cubic-bezier(0.34, 1.56, 0.64, 1) ← firma "In a Nutshell"
  Salida estándar                   cubic-bezier(0.5, 0, 0.75, 0)     ← elementos que se van
  Movimiento de marca (float)       senoidal / ease-in-out suave      ← bobbing, partículas
```

Regla: el 80 % de las animaciones funcionales usan la **entrada estándar**; el rebote controlado se reserva para momentos de marca y énfasis. Prohibido el ease lineal para entradas.

### A-007: Retardo en cascada (stagger)
[RECOMENDADO] Cuando aparecen varios elementos a la vez (lista, grid, tarjetas), secuenciar su entrada con un desfase de 30–80 ms entre elementos, en el orden de lectura (arriba→abajo, izquierda→derecha). El desfase nunca supera 80 ms en UI, o el conjunto se siente lento.

### A-008: Movimiento paralelo = caos
[IMPERATIVO] No más de **2–3 elementos animándose simultáneamente** en la misma zona. Si hay demasiados, el ojo no sabe dónde mirar. Para entradas masivas, usar stagger (`A-007`) y mantener el resto quieto.

### A-009: Rendimiento: transform y opacidad
[IMPERATIVO] Para web/escritorio, animar solo **transform** (traslación, escala, rotación) y **opacidad**. Prohibido animar propiedades de layout (width, height, margin, top/left) o filtros en caliente: provocan reflow y saltos (jank). Si hay que cambiar tamaño, animar `transform: scale` o separar la capa.

### A-010: Respeto por la reducción de movimiento
[IMPERATIVO] Si la plataforma o el usuario solicita **reducir el movimiento** (web: `prefers-reduced-motion: reduce`; escritorio: ajuste del sistema), desactivar o simplificar: sustituir desplazamientos y rebotes por fundidos de opacidad cortos (≤ 150 ms) o estados instantáneos. Las animaciones de marca (bobbing, parallax) se desactivan por completo.

---

## 2. Microinteracciones

### A-011: Hover → el elemento flota
[IMPERATIVO] Al pasar el cursor, el elemento **se eleva**: se traduce en que su sombra plana crece y su offset aumenta (ver `V-017`), opcionalmente escala 1.02–1.04. Nunca cambia su forma ni su color de fondo de forma dramática; la elevación es la señal.

### A-012: Presión → el elemento se hunde
[IMPERATIVO] Al presionar (ratón abajo / toque), el elemento **baja y se apoya**: la sombra plana se reduce o se anula y el offset llega a 0. La sensación es de botón físico que se presiona. El contraste hover (flota) ↔ activo (hunde) es clave en el estilo.

### A-013: Foco de teclado visible
[IMPERATIVO] El foco de teclado se marca con un anillo o halo del color de acento dominante (nunca negro) y una micro elevación; nunca con un simple cambio de opacidad. Mantener visible mientras dura la navegación por teclado (ver `U-016`).

### A-014: Botones y elementos accionables
[IMPERATIVO] Los botones y elementos clicables usan hover (`A-011`) + presión (`A-012`) con duración 80–150 ms. La acción de confirmación (p. ej. "hecho") puede cerrar con un "squish" breve de escala 0.98 y un rebote final. Los estados deshabilitado y cargando son estáticos (ver `U-018`, `A-019`).

### A-015: Tarjetas y contenedores
[RECOMENDADO] En hover, una tarjeta se eleva un nivel (sombra crece) y su contenido puede desplazarse 1–2 px hacia arriba. El contenido interno (icono, título) se mueve a la vez que la tarjeta, nunca independientemente (evita el despegue).

### A-016: Datos y contadores animados
[RECOMENDADO] Los números protagonistas (ver `V-027`) se animan con conteo rápido (300–500 ms) y terminan con un rebote controlado del número o una partícula de celebración (ver `A-026`). El dato debe verse completo al instante: animar el conteo, no ocultar el valor.

### A-017: Iconos vivos con moderación
[RECOMENDADO] Un icono aislado puede tener animación de marca (rotar levemente, latir, flotar) **solo en momentos de énfasis** (onboarding, resultados, encabezados). Los iconos funcionales en botones/menús no se animan en reposo; solo reaccionan a hover (escala 1.05–1.1, 100–150 ms).

---

## 3. Estados y carga

### A-018: Cargando con estilo "In a Nutshell"
[RECOMENDADO] El indicador de carga por defecto es una **órbita de puntos o círculo con partículas**: un círculo central pequeño que gira con 3–5 puntos alrededor (ver `V-043`, `V-032`). Evitar la rueda giratoria genérica. El loader usa los acentos de la paleta y dura en bucle 800–1200 ms por vuelta.

### A-019: Barras de progreso
[RECOMENDADO] La barra de progreso es una píldora (ver `V-005`) cuyo relleno crece con la **entrada estándar** (`A-006`). La cabeza del relleno puede rematar en un círculo de acento que "rebota" al completarse. Al llegar al 100 %, mostrar una partícula o tilde con rebote controlado.

### A-020: Notificaciones y toasts
[RECOMENDADO] Entran deslizándose desde el borde con la **entrada rápida** (200–250 ms), se mantienen 3–5 s y salen con la **salida estándar** (150–250 ms). El cierre manual se confirma con un squish de escala. Los toasts usan píldora y el color semántico de su tipo (éxito/error/aviso, ver `V-012`).

### A-021: Modales y superpuestos
[IMPERATIVO] Los modales entran con **escala 0.95→1 + fundido + elevación de sombra** en 200–300 ms; el fondo oscurecido se funde en 150–200 ms. Salen a la inversa con la **salida estándar** (150 ms). El contenido nunca "entra a ráfagas" elemento a elemento salvo que sea una lista corta (ver `A-007`).

### A-022: Estados vacíos con personaje
[RECOMENDADO] En estados vacíos, el personaje (ver `V-034` a `V-039`) puede hacer un gesto único de entrada (saluda, parpadea, se encoge de hombros) en 400–600 ms. Un gesto, una vez; después permanece estático (ver `V-039`, `A-032`).

---

## 4. Transiciones entre pantallas y secciones

### A-023: Transición de pantalla
[RECOMENDADO] Para cambiar de pantalla o vista: fundido + ligera traslación del contenido entrante (10–16 px hacia arriba) en 350–500 ms, usando la **entrada estándar**. El contenido saliente se funde/desplaza en sentido contrario en 150–200 ms. Prohibido fundido a negro (es marca de vídeo, no de UI) salvo efecto de marca puntual.

### A-024: Aparecer al hacer scroll (web)
[RECOMENDADO] Los bloques entran al hacer scroll con la **entrada rápida** (200–400 ms) y stagger por sección (ver `A-007`). No usar parallax ni zoom de scroll agresivos en elementos funcionales (ver `A-025`).

### A-025: Parallax y profundidad sutil
[RECOMENDADO] El parallax es **exclusivo del fondo decorativo** (textura de puntos, ilustración de escenario) y nunca del contenido funcional. Desplazamiento máximo del fondo: 10–15 % de la velocidad del contenido. Prohibido el parallax en el contenido de texto o tarjetas: provoca mareo y rompe la legibilidad.

### A-026: Celebración y partículas
[RECOMENDADO] Las partículas de celebración (estrellas de 4 puntas, puntos, cruces — ver `V-043`) solo en: completar una acción clave, logros, resultados positivos o datos protagonistas (ver `V-027`). Máximo 3–5 partículas, duración 400–800 ms, aparecen desde el punto de origen del éxito (botón, número). No repetir en cada interacción o pierden valor (ver `G-009`).

### A-027: Cambio de color/estado suave
[RECOMENDADO] Los cambios de color de fondo o de acento (hover, cambio de tema, segmentos) se animan en 150–300 ms con la **entrada estándar**. Prohibido el cambio de color instantáneo sin transición en elementos interactivos.

---

## 5. Movimiento de marca (web/escritorio)

### A-028: Flotación suave (bobbing)
[RECOMENDADO] Personajes y elementos decorativos pueden flotar con un vaivén vertical senoidal de 4–8 px, duración 2–3 s por ciclo, con ease-in-out. Un solo elemento flota por zona. El bobbing se desactiva con `prefers-reduced-motion` (ver `A-010`).

### A-029: Título con entrada de marca
[RECOMENDADO] Los títulos principales pueden entrar con la **entrada rápida** (400–500 ms) desde abajo (16–24 px) con un rebote controlado pequeño (overshoot). Máximo un título con esta entrada por pantalla; el resto usa entrada estándar.

### A-030: Motivos que respiran
[RECOMENDADO] Los motivos de marca (órbitas, planetas, estrellas — ver `V-032`) pueden girar o "latir" (escala 1→1.05) en ciclos lentos de 3–5 s, **solo en zonas decorativas** y con intensidad muy baja. Nunca en la misma zona que el bobbing (ver `A-008`).

### A-031: Sonido y haptics (si la plataforma los permite)
[RECOMENDADO] Los efectos de sonido son opcionales y sutiles (un "pop" corto al completar, un chasquido al presionar). En escritorio, desactivar el sonido por defecto o conmutarlo con respeto; en móvil, usar haptics cortos en vez de sonido. La animación nunca depende del sonido para comunicar su estado.

---

## 6. Vídeo y plataforma

> El vídeo es el medio originario del estilo: las reglas funcionales de UI se **relajan** en vídeo, donde el movimiento puede ser más expresivo, pero el lenguaje de formas y colores es el mismo.

### A-032: Timing narrativo en vídeo
[RECOMENDADO] En vídeo (24–25 fps) cada escena dura 2–5 s y la acción clave ocurre en los primeros 0.5–1 s de la escena. Los rebotes y overshoots pueden amplificarse (es parte de la firma), pero cada escena mantiene **una sola idea en movimiento**.

### A-033: Vídeo con autoridad de las curvas
[RECOMENDADO] En vídeo, las curvas de `A-006` se aplican a la posición/rotación de los elementos; la diferencia es la duración (2–4× más larga que en UI). Un movimiento de marca en vídeo puede rebotar 2–3 veces; en UI, solo 1 (ver `A-004`).

### A-034: Storyboard mínimo por escena
[RECOMENDADO] Para piezas de vídeo (intro, explicadores, transiciones de marca), escribir un mini storyboard de 3–5 golpes por escena: *elemento entra → acción → rebote → sale*, con tiempos estimados. Esto evita animaciones "infinitas" sin resolución.

### A-035: Web/escritorio: 60 fps, no más
[IMPERATIVO] En web/escritorio el objetivo es **60 fps constantes** (en pantallas de 120 Hz, mantener al menos el refresco del dispositivo). Si una animación cae de forma sostenida por debajo de 50 fps, se simplifica: menos elementos, duraciones más cortas o se elimina (ver `A-009`).

### A-036: Presupuesto de animación por vista
[RECOMENDADO] Cada vista web/escritorio admite un máximo de 3–4 animaciones "con identidad" (entradas con rebote, parallax, partículas). El resto usa entradas estándar de 200 ms. Más que eso, la interfaz se siente lenta y saturada (ver `A-008`, `G-009`).

---

## 7. Recursos y herramientas (dominio animación)

> Recursos integrados en este archivo (ver índice para el resto de dominios).

### A-101: Lottie y LottieFiles
- **Lottie** (Airbnb, `https://airbnb.design/lottie/`): animaciones vectoriales exportadas desde After Effects a un JSON que se reproduce en web, escritorio y móvil. Es el puente natural entre el vídeo y la UI.
- **LottieFiles** (`https://lottiefiles.com`): biblioteca gratuita de animaciones Lottie estilo plano; buscar términos como "bouncy", "orb", "planet", "star" y recolorear a la paleta.

### A-102: Web — CSS Transitions y Keyframes
- **Transitions** para hover/presión/estado (`transition: transform 180ms cubic-bezier(0.34, 1.56, 0.64, 1)`).
- **Keyframes** para entradas, bobbing y partículas. Respeta `@media (prefers-reduced-motion: reduce)` (ver `A-010`).
- Nota: en web usar siempre `transform` + `opacity` (ver `A-009`).

### A-103: Web — librerías de animación (referencia)
- **GSAP** (`https://gsap.com`): curvas de rebote (`Back.easeOut`), timeline y stagger potentes; la más usada para animaciones de marca en web.
- **Framer Motion / Motion** (`https://motion.dev`): animaciones declarativas para interfaces; soporta springs y `useReducedMotion`.
- **Anime.js / Popmotion / The GreenSock Webflow**: alternativas según el framework del proyecto (lenguaje neutro: la regla es elegir una y mantener las curvas del sistema `A-006`).

### A-104: Escritorio — motores por plataforma
- **Qt / QML**: animaciones `SpringAnimation`, `NumberAnimation` con `easing.type: OutBack` (equivalente al overshoot `A-004`).
- **.NET (WPF/WinUI)**: `EasingFunctionBase` personalizada o `CubicEase`/`BackEase` con curvas equivalentes a `A-006`.
- **Electron/Tauri**: usar las mismas técnicas web (CSS/JS) dentro del contenedor.
- Regla: sea cual sea el motor, registrar las curvas y duraciones como constantes (ver `A-002`, `G-007`).

### A-105: Vídeo
- **After Effects** (pago): estándar de la industria; usar los asistentes de easing ("Easy Ease") y rebotes (expresiones de `overshoot`) para la firma.
- **Lottie exportación**: exportar piezas de marca a Lottie (`bodymovin`) para reutilizarlas en la UI (ver `A-101`).
- **Blender / DaVinci Resolve** (gratuitos): alternativas para piezas de vídeo 2D vectorial.

### A-106: Herramientas de curvas y prueba
- **cubic-bezier.com** (`https://cubic-bezier.com`): construir y copiar las curvas de `A-006`.
- **easings.net** (`https://easings.net`): catálogo visual de curvas; elegir las "easeOut*" para entradas y "backOut" para el rebote.
- **keyframes.app**: generador visual de keyframes y curvas.
- **LottieFiles — player y preview**: probar el JSON Lottie antes de integrarlo.

---

## 8. Checklist de animación

- [ ] Cada animación tiene un propósito comunicable (A-001).
- [ ] Duraciones y curvas pertenecen al sistema del proyecto (A-002, A-005, A-006).
- [ ] Entradas con frenada suave (ease-out) o rebote controlado; sin ease-in para entradas (A-003).
- [ ] Máximo 2–3 elementos animados a la vez por zona (A-008).
- [ ] Web/escritorio: solo `transform` y `opacity`; sin animar layout (A-009).
- [ ] `prefers-reduced-motion` / ajuste de sistema respetado (A-010).
- [ ] Hover flota (sombra crece) y presión hunde (sombra desaparece) en todos los elementos interactivos (A-011, A-012).
- [ ] Foco de teclado visible con halo de acento (A-013).
- [ ] Loaders con estilo de órbita/partículas, no ruedas genéricas (A-018).
- [ ] Parallax solo en fondo decorativo, desplazamiento ≤ 15 % (A-025).
- [ ] Partículas de celebración solo en acciones clave y en pequeñas cantidades (A-026).
- [ ] 60 fps sostenidos en web/escritorio (A-035).
- [ ] Vídeo: escenas de 2–5 s, una idea en movimiento por escena (A-032).
