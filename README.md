# Estética Kurzgesagt (In a Nutshell) — Reglas de Diseño

> Conjunto de reglas de diseño autocontenido para construir interfaces gráficas — web, escritorio, móvil, embebido, CLI con TUI, realidad mixta, etc. — con la estética de los vídeos de **Kurzgesagt – In a Nutshell**: diseño vectorial plano (flat design) con toque de profundidad, paletas vibrantes, formas geométricas simples y animación fluida.

El proyecto incluye documentación de reglas (para humanos y agentes de IA), dos demos HTML funcionales que muestran la estética aplicada y el material de licencia. No está atado a ningún lenguaje de programación: cualquier fragmento de código que aparezca es solo ilustrativo.

---

## Contenido del repositorio

| Archivo | Tipo | Qué es |
| --- | --- | --- |
| `KZG-REGLA-DISENO-VISUAL.md` | Documentación | Reglas de estética estática (`V-###`): formas, color, profundidad, bordes, tipografía, iconografía, personajes y texturas. Incluye 6 paletas listas para usar. |
| `KZG-REGLA-ANIMACION.md` | Documentación | Reglas de movimiento (`A-###`): easing, tiempos, microinteracciones, transiciones y efectos de marca. |
| `KZG-REGLA-UX-COMPOSICION.md` | Documentación | Reglas de experiencia de usuario (`U-###`): layout, jerarquía, estados, accesibilidad, adaptación por plataforma y componentes. |
| `KZG-DEMO-DASHBOARD.html` | Demo | Dashboard estético autocontenido (CSS + JS inline) que muestra la estética aplicada a la interfaz. |
| `KZG-DEMO-SISTEMA-SOLAR.html` | Demo | Sistema solar en 3D (Three.js vía CDN) con cámara libre y control de velocidad orbital. |
| `README.md` | Documentación | Este documento: entrada, mapa, convenciones, reglas globales `G-###`, demos y checklist de revisión rápida. |
| `LICENSE` | Legal | Licencia MIT (código abierto). |
| `.gitignore` | Configuración | Patrones de archivos ignorados por Git. |

---

## Cómo usar este conjunto

- **Para humanos:** leer este README primero, luego el documento del dominio en el que estés trabajando (visual, animación o UX). Usar los checklists al final de cada documento y el checklist de 1 minuto de la sección *Checklist de revisión rápida* como control de calidad.
- **Para agentes (IA):** este conjunto es portable a cualquier sistema de agentes (`AGENTS.md`, `CLAUDE.md`, skills, etc.). Se puede copiar entero o por archivo. Cada regla tiene un identificador `PREFIJO-NNN` referenciable: `G-###` (global), `V-###` (visual), `A-###` (animación), `U-###` (UX/composición). Antes de generar una interfaz, cargar este documento y los dominios relevantes; al revisar, comprobar cada checklist.
- **Orden de lectura recomendado:** `README.md` → `KZG-REGLA-DISENO-VISUAL.md` → `KZG-REGLA-ANIMACION.md` → `KZG-REGLA-UX-COMPOSICION.md`.

---

## Convenciones

| Convención | Regla |
| --- | --- |
| Identificador de regla | `PREFIJO-NNN` (3 dígitos). Ej.: `V-007`, `A-012`, `U-021`, `G-003`. |
| Referencia cruzada | `(ver V-007)` dentro del texto. Un agente debe poder resolverla. |
| Nivel de obligatoriedad | `[IMPERATIVO]` = no negociable. `[RECOMENDADO]` = preferible, justificable desviarse. `[CONTEXTO]` = información de apoyo. |
| Do / Don't | Cada regla importante incluye lista de "Hacer" y "No hacer" para evitar ambigüedad. |
| Valores hex | Los colores hex son **representativos** de la estética, no la paleta oficial de la marca (propiedad de Kurzgesagt). Úsalos como base y ajusta a tu producto. |
| Código de ejemplo | Solo ilustrativo; no introduce un lenguaje obligatorio. |

---

## Mapa de documentos

| Archivo | Dominio | Contenido |
| --- | --- | --- |
| `README.md` | Global | Entrada, convenciones, mapa, reglas globales `G-###`, demos, checklist de 1 minuto. |
| `KZG-REGLA-DISENO-VISUAL.md` | Visual | Formas, color, profundidad plana, bordes, tipografía, iconografía, personajes, texturas + recursos de ese dominio. |
| `KZG-REGLA-ANIMACION.md` | Animación | Movimiento, easing, tiempos, microinteracciones, transiciones, efectos de marca + recursos. |
| `KZG-REGLA-UX-COMPOSICION.md` | UX | Layout, jerarquía, estados, accesibilidad, adaptación por plataforma, componentes + recursos. |

---

## Reglas globales (G-###)

Estas reglas aplican a todos los dominios y son la primera línea de control de calidad.

### G-001: Vectorial por defecto

[IMPERATIVO] Todo elemento visual debe ser construido como vector (SVG, vector drawable, paths, primitivas geométricas), nunca como imagen de mapa de bits rasterizada (PNG/JPG/BMP), salvo fotografías o texturas intencionales. Un vector escala infinitamente sin perder nitidez.

### G-002: La forma comunica antes que el color

[IMPERATIVO] La silueta y la geometría de un elemento deben permitir reconocer su función aunque se elimine el color. Si un botón solo se distingue por su color, el diseño está roto (ver `U-014`).

### G-003: Profundidad, no perspectiva

[IMPERATIVO] Representar la profundidad exclusivamente mediante sombras planas, capas y superposición. Prohibido usar degradados de iluminación 3D realista, perspectiva forzada o biselados metálicos. (ver `V-014`)

### G-004: Consistencia sobre novedad

[IMPERATIVO] Si ya existe un patrón definido en este conjunto para un elemento (color, esquina, sombra, duración), reutilízalo. No inventar variantes por elemento; la variación solo se permite para marcar jerarquía o estado.

### G-005: Paleta bloqueada

[IMPERATIVO] Definir una paleta finita (ver `V-010`) y registrarla como token/constante del proyecto. Prohibido introducir colores sueltos fuera de la paleta, incluso "provisionalmente". (ver `V-008` a `V-013`)

### G-006: Lenguaje neutro de plataforma

[IMPERATIVO] Las reglas de este conjunto deben aplicarse por igual a web, escritorio, móvil y otras superficies. Las diferencias entre plataformas se gestionan en `U-028` y siguientes, no renegociando la estética por plataforma.

### G-007: Un solo sistema de ritmo

[IMPERATIVO] Todo el proyecto usa un único sistema de espaciado y de duración de animación (definidos en `U-004` y `A-002`). No mezclar escalas.

### G-008: Todo estado visible

[IMPERATIVO] Todo elemento interactivo debe tener estado visual definido para: reposo, hover/sobre, presionado/activo, foco de teclado, deshabilitado, cargando y error. (ver `U-015` a `U-019`)

### G-009: Marca con moderación

[IMPERATIVO] Los elementos de marca (personajes, partículas, textura de puntos, motivos) se usan como acentos. Un personaje es un refuerzo de mensaje, no un relleno. Si cada pantalla está saturada de motivos, la marca pierde impacto.

### G-010: Coherencia entre vídeo e interfaz

[RECOMENDADO] Si el producto acompaña contenido de vídeo, la UI debe usar el mismo lenguaje de color, formas y movimiento que el vídeo, pero más sobrio: la interfaz enmarca al contenido, no compite con él.

---

## Demos

Ambas demos son archivos HTML autocontenidos que implementan las reglas de este conjunto. Ábrelos en cualquier navegador para verlas en acción. La del sistema solar requiere conexión a internet (carga Three.js desde CDN).

### KZG-DEMO-DASHBOARD.html — "Misión Control"

Dashboard estético con la paleta **Índigo Nocturno** (fondo `#211D3D`, naranja dominante `#FF9A47`). Muestra la estética aplicada a:

- KPIs con icon-chip y deltas
- Gráficos de barras y de línea/área (SVG)
- Barras de progreso, anillo de combustible y loader indeterminado
- Botones (primario, secundario, icono, deshabilitado), pestañas y búsqueda
- Toggles, checks, chips, tabla de estados y alertas semánticas
- Planetita flotante decorativa, entrada en cascada y microinteracciones

Incluye interactividad mínima: tabs, toggles, checks y un botón con contador animado.

### KZG-DEMO-SISTEMA-SOLAR.html — Sistema solar en 3D

Simulación del sistema solar con Three.js y estética Kurzgesagt (esferas low-poly facetadas):

- 8 planetas con colores de la paleta, anillos de Saturno y Luna orbitando la Tierra
- Sol pulsante con halo
- **Cámara libre:** `WASD` mover · `Q`/`E` subir/bajar · `Shift` turbo · arrastrar para mirar · rueda para zoom
- Panel de control: slider de velocidad orbital (`0–5×`), pausa/reanudar, botón `0×`, reiniciar cámara
- Toggles de órbitas, etiquetas, estrellas y Luna
- Etiquetas HTML proyectadas que se ocultan cuando un planeta queda detrás de la cámara

**Referencias a reglas en las demos:** ambos HTML muestran en la práctica `G-001` (geometría vectorial/3D como primitivas), `G-003` (profundidad por capas), `G-005` (paleta bloqueada como tokens CSS), `G-008` (estados interactivos) y los easings/duraciones de `A-002`. Para un análisis guiado, recorre cada demo con las reglas `V-###`, `A-###` y `U-###` de los documentos de dominio.

---

## Checklist de revisión rápida (1 minuto)

Antes de entregar cualquier interfaz, comprobar:

- [ ] Todos los elementos son vectoriales o primitivas geométricas (G-001).
- [ ] No hay contornos negros; los bordes usan tonos del mismo color (V-018).
- [ ] Los colores usados pertenecen todos a la paleta bloqueada (G-005).
- [ ] La profundidad se logra con sombras planas, no con 3D realista (G-003).
- [ ] Tipografía sans-serif geométrica de trazo grueso; legibilidad confirmada (V-024).
- [ ] Esquinas: rectángulos redondeados o formas totalmente redondeadas (V-004).
- [ ] Todos los estados interactivos están definidos (G-008).
- [ ] Los tiempos de animación pertenecen al sistema de duraciones (A-002).
- [ ] El diseño funciona en blanco y negro o con visión reducida (U-014).
- [ ] El espaciado usa la retícula del sistema (U-004).

---

## Licencia

Licencia **MIT** — uso comercial y personal libre, con atribución. Consulta `LICENSE` para los términos completos.

Los valores estéticos documentados son representativos e inspirados en el estilo de Kurzgesagt; la marca, su identidad visual y su contenido son propiedad de sus respectivos titulares.

---

## Estado

- [x] Conjunto de reglas completo (3 documentos + README, referencias cruzadas verificadas)
- [x] Demos de estética (dashboard + sistema solar 3D)
- [x] Licencia MIT
- [ ] Verificación visual final de las demos en navegador
