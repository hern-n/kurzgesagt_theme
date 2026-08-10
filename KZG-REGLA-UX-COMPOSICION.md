---
tipo: regla
dominio: ux-composicion
idioma: es
revision: 2026-08
plataformas: web, escritorio, movil, multiplataforma
---

# Reglas de UX y Composición — Estética Kurzgesagt

> Conjunto de reglas de **composición, jerarquía, componentes, estados, accesibilidad y adaptación por plataforma**. Pensado para web, escritorio y móvil. Autocontenido y portable; `U-###` remite a este archivo, `V-###` a diseño visual, `A-###` a animación y `G-###` al índice.
>
> Niveles de obligatoriedad: `[IMPERATIVO]` no negociable · `[RECOMENDADO]` preferible · `[CONTEXTO]` apoyo. Identificadores `U-###`.

---

## 1. Layout y composición

### U-001: Retícula base
[IMPERATIVO] Todo el layout se apoya en una **retícula de columnas** y en los ritmos de espaciado del sistema (`U-004`). Prohibido colocar elementos por coordenadas libres o espaciados arbitrarios; cada elemento se alinea a la retícula.

### U-002: Márgenes y áreas de respiro
[IMPERATIVO] El contenido nunca toca los bordes de la ventana/pantalla: margen base mínimo equivalente a 2 pasos del sistema de espaciado (`U-004`). Las tarjetas y superficies mantienen su propio padding interno (1 paso al menos).

### U-003: Formas compuestas alineadas
[IMPERATIVO] Cuando se superponen formas (icono en un círculo, número en una píldora, ver `V-007`), todas comparten centro o eje. Un elemento descentrado entre formas compuestas rompe la lectura del conjunto.

### U-004: Sistema de espaciado (ritmo)
[IMPERATIVO] Un único sistema de espaciado para todo el proyecto, derivado de la escala base: pasos de 4 px (4, 8, 12, 16, 24, 32, 48, 64). Toda separación, padding y margen es un múltiplo de la escala; prohibidos valores sueltos (p. ej. 10, 14, 21) (ver `G-007`).

### U-005: Aire antes que densidad
[RECOMENDADO] El estilo prefiere el espacio en blanco (o de color de fondo) a la saturación. Si una vista tiene más de ~7–8 bloques de contenido simultáneos, se agrupa o se pagina. El aire es parte de la estética, no espacio desperdiciado.

### U-006: Una acción primaria por pantalla
[IMPERATIVO] Cada vista destaca **una** acción primaria (el "siguiente paso"). Solo esa usa el acento dominante en su forma completa; el resto de acciones se presentan en superficies o como acciones secundarias. Dos acciones primarias compiten y ninguna gana.

### U-007: Jerarquía visual
[IMPERATIVO] La jerarquía se marca en este orden de prioridad: **tamaño → peso → color → forma** (nunca color solo, ver `U-014`). El elemento protagonista es el más grande, grueso y con el acento dominante; los de apoyo decrecen.

### U-008: Texto legible
[IMPERATIVO] Longitud de línea de lectura entre 45–75 caracteres por línea en textos continuos. Interlineado de al menos 1.4× en cuerpo. El texto justificado se prohíbe salvo en columnas muy anchas; preferir alineación izquierda.

### U-009: Títulos y datos protagonistas
[RECOMENDADO] Los títulos de sección y los datos protagonistas (ver `V-027`) se presentan grandes y gruesos; en pantallas pequeñas se reducen por escala tipográfica (`V-022`), no por compresión del texto.

### U-010: Etiquetas y metadatos
[RECOMENDADO] Las etiquetas cortas (badges, categorías, versiones) van en **píldoras** (ver `V-005`) con texto grueso y colores de acento suaves. Máximo 3–4 píldoras juntas; a partir de ahí, un único bloque de texto.

### U-011: Orden de lectura
[RECOMENDADO] Orden de lectura coherente: para web/escritorio de izquierda a derecha y arriba abajo; la información más importante entra en los primeros 3 segundos. Usar el stagger de animación (`A-007`) respetando este orden.

---

## 2. Componentes

### U-012: Botones y acciones primarias
[IMPERATIVO] Los botones primarios son **píldoras** con sombra plana (ver `V-005`, `V-014`), texto grueso claro y el acento dominante de fondo. Botones secundarios: superficie elevada con texto/accento de color y sin relleno vibrante. El botón primario se ve, el secundario acompaña. Estados según `U-015` a `U-019`.

### U-013: Iconos con etiqueta o tooltip
[IMPERATIVO] Todo icono funcional lleva etiqueta visible o tooltip accesible (ver `V-033`). Un icono sin texto ni tooltip solo se permite si su significado es universal y redundante con un texto cercano.

### U-014: Contraste y no dependencia del color
[IMPERATIVO] La información nunca se comunica solo con color: acompañar con forma, icono, texto o patrón (ver `G-002`). Contraste de texto mínimo **AA (4.5:1)** en texto normal y **AAA (7:1)** preferible en texto pequeño; el contraste de elementos de interfaz (bordes de estado, indicadores) mínimo 3:1 frente a su fondo.

### U-015: Estados — reposo y hover
[IMPERATIVO] Todo elemento interactivo tiene estado de **reposo** y de **hover** (web/escritorio con ratón). El hover flota el elemento (sombra crece, ver `A-011`); el reposo es estático. En táctil no hay hover: el estado se salta a presión (ver `U-031`).

### U-016: Estados — foco de teclado
[IMPERATIVO] El foco de teclado siempre es visible: anillo o halo del acento dominante, sin depender de hover. Se activa por tabulación y se mantiene durante la navegación por teclado (ver `A-013`).

### U-017: Estados — activo/presionado
[IMPERATIVO] En presión, el elemento se hunde (sombra anulada, offset 0, ver `A-012`). El estado activo (seleccionado/pulsado en reposo) se marca con el relleno de acento dominante o una píldora de acento, de forma persistente mientras la selección esté activa.

### U-018: Estados — deshabilitado
[IMPERATIVO] Un elemento deshabilitado se marca reduciendo su opacidad a ~40–50 % y eliminando su sombra plana; **no** se rellena de gris (el gris neutral no existe en la paleta). Debe verse "apagado" pero reconocible, y nunca recibe foco ni acción (ver `A-014`).

### U-019: Estados — cargando y error
[IMPERATIVO] Cargando: sustituir el contenido del elemento por el loader de marca (`A-018`) manteniendo el tamaño del elemento (sin saltos de layout). Error: borde o halo del color semántico de error (`V-012`) + mensaje de texto explícito; nunca solo color (ver `U-014`). Los mensajes de error usan lenguaje claro y una acción de recuperación.

### U-020: Tarjetas y contenedores
[RECOMENDADO] Las tarjetas son píldoras/rectángulos redondeados con elevación (ver `V-016`). Contenido: icono o figura (opcional), título, breve descripción y una acción. Las tarjetas en grupo se separan por el ritmo de espaciado (`U-004`); no apilar más de 3 niveles de profundidad visual por vista.

### U-021: Modales, diálogos y superpuestos
[IMPERATIVO] El modal usa elevación máxima (`V-016`), esquinas redondeadas y sombra plana grande. El fondo se oscurece con un velo índigo translúcido (~60 %). La acción primaria del modal cumple `U-006`. Cierre por botón explícito, tecla Escape y clic fuera (ver `A-021`).

### U-022: Toggles, checks y formularios
[RECOMENDADO] Los toggles son **píldoras** con un círculo (perilla) que se desplaza y con cambio de color suave (ver `A-027`). Los campos de formulario son rectángulos redondeados con borde del tono del fondo y foco de acento (`U-016`). Las casillas (checks) son cuadrados con esquinas muy redondeadas y marca de verificación gruesa.

### U-023: Barras de progreso e indicadores
[RECOMENDADO] Las barras de progreso son píldoras con relleno de acento y círculo final de acento (ver `A-019`). Los indicadores de paso (wizard) se representan como círculos numerados conectados por una línea punteada. Los indicadores no usan solo color para su estado (ver `U-014`).

### U-024: Menús y navegación
[RECOMENDADO] La navegación principal usa pestañas en píldora o una barra con la sección activa marcada por píldora de acento (`U-017`). Los menús desplegables son tarjetas elevadas con esquinas redondeadas; cada ítem se resalta con hover de elevación (`A-011`). No más de 5–7 ítems de navegación por nivel.

---

## 3. Accesibilidad

### U-025: Movimiento reducido y bienestar
[IMPERATIVO] Respetar la preferencia de reducción de movimiento de la plataforma (web: `prefers-reduced-motion`; escritorio: ajuste del sistema; móvil: reduce motion del SO). En ese modo: sin desplazamientos ni rebotes, solo fundidos cortos o estados directos (ver `A-010`). Los parpadeos y flashes rápidos están prohibidos (WCAG 2.3.1: nada que parpadee > 3 veces/segundo).

### U-026: Semántica y texto alternativo
[IMPERATIVO] La estructura semántica se mantiene aunque el estilo sea decorativo: encabezados, listas, landmarks y orden de tabulación coherentes. Todo icono sin texto lleva `aria-label`/equivalente; toda ilustración informativa tiene texto alternativo; las decorativas se marcan como ignorables.

### U-027: Objetivos táctiles y teclado
[IMPERATIVO] Tamaño mínimo de objetivo táctil: **44×44 px** (web/móvil) y **32×32 px** en escritorio con ratón. La navegación completa es posible solo con teclado (Tabulador, Enter, Escape, flechas). Prohibido el "hover-only": ninguna información esencial solo aparece al pasar el ratón.

---

## 4. Plataformas

### U-028: Principios comunes entre plataformas
[IMPERATIVO] Las reglas de este conjunto son idénticas para web, escritorio y móvil: misma paleta (`V-009`), mismas formas, mismos tiempos (`A-005`, `A-006`), mismos estados (`U-015` a `U-019`). Lo que cambia es la ergonomía y el layout (retícula), no la estética (ver `G-006`).

### U-029: Web
[RECOMENDADO] Layout fluido: la retícula (`U-001`) se adapta por puntos de quiebre; los bloques de contenido se reordenan a una columna en pantallas pequeñas. La barra de navegación pasa a menú plegable por debajo del punto de quiebre. Priorizar `transform`/`opacity` en animaciones (ver `A-009`).

### U-030: Escritorio
[RECOMENDADO] Aprovechar el espacio: soportar redimensionado de ventana, paneles laterales y atajos de teclado. El hover tiene más protagonismo (ver `U-015`). Las superficies pueden ser más numerosas sin saturar, pero respetando el aire (`U-005`) y el límite de animaciones simultáneas (`A-008`).

### U-031: Móvil y táctil
[IMPERATIVO] Objetivos de toque ≥ 44×44 px (ver `U-027`). Sin estados hover: reposo → presión (`U-017`). La acción primaria (`U-006`) se coloca al alcance del pulgar (zona inferior en móvil). Gestos: deslizar para volver y para cerrar modales, siempre con alternativa visible.

### U-032: Adaptación y densidad por superficie
[RECOMENDADO] Densidad de contenido: escritorio puede alojar 3–4 columnas, móvil 1, tablet 2. Los datos protagonistas y las tarjetas escalan por la retícula y la escala tipográfica (`V-022`), nunca se encogen por deformación (aspect ratio preservado).

---

## 5. Recursos y herramientas (dominio UX)

> Recursos integrados en este archivo (ver índice para el resto de dominios).

### U-101: Validación de accesibilidad
- **WAVE** (`https://wave.webaim.org`): análisis automático de accesibilidad web.
- **axe DevTools / Lighthouse** (navegadores): auditoría de contraste, semántica y ARIA.
- **WebAIM Contrast Checker** (`https://webaim.org/resources/contrastchecker/`): contraste AA/AAA (ver `U-014`).
- **WCAG 2.2** (`https://www.w3.org/WAI/WCAG22/`): referencia normativa; aplicar criterios de contraste, movimiento y teclado.

### U-102: Sistema de diseño y tokens
- **Tokens Studio / Figma Tokens** (`https://tokens.studio`): definir espaciado (`U-004`), colores (`V-009`), duraciones y curvas (`A-005`, `A-006`) como tokens compartidos.
- **Style Dictionary** (`https://amzn.github.io/style-dictionary/`): exportar los tokens a cualquier plataforma (web, escritorio, móvil) sin tocar estética.
- **storybook / playroom** (según plataforma): documentar los componentes de este archivo y sus estados.

### U-103: Prototipado y testing
- **Figma** (prototipos interactivos con los tiempos y curvas del sistema).
- **Playwright / Testing Library** (web) y **Appium / Maestro** (móvil): automatizar checks de estados y foco.
- **Motion-agnostic UI tests**: verificar que los estados (`U-015` a `U-019`) existen en el árbol de accesibilidad.

### U-104: Layout por plataforma (referencia)
- Web: sistemas de retícula en CSS (grid/flexbox) o el equivalente del framework; respetar `U-001` y `U-004`.
- Escritorio: layouts de Qt, WinUI/WPF o Electron; las tarjetas y paneles siguen las mismas reglas de elevación (`V-016`).
- Móvil: grids de SwiftUI/Compose/React Native con las mismas proporciones de la retícula base (`U-001`).

---

## 6. Checklist de UX y composición

- [ ] Todo el espaciado es múltiplo del sistema de 4 px (U-004).
- [ ] Contenido con márgenes de respiro; sin tocar bordes (U-002).
- [ ] Una única acción primaria destacada por pantalla (U-006).
- [ ] Jerarquía por tamaño → peso → color → forma; nunca solo color (U-007, U-014).
- [ ] Longitud de línea 45–75 caracteres e interlineado ≥ 1.4× (U-008).
- [ ] Botones: primarios en píldora con acento dominante y sombra plana (U-012).
- [ ] Todo icono funcional tiene etiqueta o tooltip (U-013).
- [ ] Contraste de texto AA verificado; información no dependiente del color (U-014).
- [ ] Estados definidos: reposo, hover, foco, activo, deshabilitado, cargando y error (U-015 a U-019).
- [ ] Foco de teclado visible con acento (U-016).
- [ ] Objetivos táctiles ≥ 44×44 px (U-027).
- [ ] Navegación completa por teclado; sin información "hover-only" (U-027).
- [ ] `prefers-reduced-motion` y límite de parpadeos respetados (U-025).
- [ ] Estética idéntica entre plataformas; solo cambia ergonomía y retícula (U-028).
