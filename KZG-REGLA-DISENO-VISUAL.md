---
tipo: regla
dominio: diseno-visual
idioma: es
revision: 2026-08
---

# Reglas de Diseño Visual — Estética Kurzgesagt

> Conjunto de reglas de estética estática: formas, color, profundidad, bordes, tipografía, iconografía, personajes y texturas. Este documento es autocontenido y portable a cualquier sistema (humano o agente). Referencias cruzadas como `V-014` remiten a reglas de este archivo; `G-###` al índice, `A-###` a animación y `U-###` a UX.
>
> Niveles de obligatoriedad: `[IMPERATIVO]` no negociable · `[RECOMENDADO]` preferible · `[CONTEXTO]` apoyo. Identificadores `V-###`.

---

## 1. Principios fundamentales

### V-001: Diseño vectorial plano
[IMPERATIVO] Todo elemento se construye con geometría vectorial simple (círculos, rectángulos redondeados, polígonos regulares, líneas, arcos) y rellenos sólidos. Ausencia de degradados volumétricos, sombreado fotorrealista, biselados, texturas de material o relieve 3D.

### V-002: Sencillez expresiva
[IMPERATIVO] Cada elemento debe poder explicarse con una frase de geometría ("un círculo naranja sobre una tarjeta redondeada índigo"). Si un elemento necesita varios degradados o un trazo complejo para explicarse, se simplifica.

### V-003: Lectura en dos planos
[IMPERATIVO] La composición se organiza en dos planos como máximo por zona: **fondo** (plano de escenario, más oscuro o más claro y desaturado) y **primer plano** (elementos funcionales, saturados). Un tercer plano solo como acento efímero (partículas, sombra de hover).

---

## 2. Formas y geometría

### V-004: Tres formas primarias
[IMPERATIVO] El lenguaje de formas se limita a: **círculos/elipses**, **rectángulos con esquinas muy redondeadas** y **líneas limpias** (rectas, o curvas suaves de una sola dirección). Prohibidas formas orgánicas complejas, manos alzadas, garabatos o siluetas con muchos vértices en la UI funcional.

### V-005: Radio de esquina
[IMPERATIVO] Usar esquinas totalmente redondeadas (píldora: radio = 50 % de la altura) para elementos de acción y etiquetas. Usar un radio grande pero fijo (≈ 30–40 % de la altura, o 16–24 px en escala base) para tarjetas y contenedores. Prohibido el radio 0 (esquinas rectas) para superficies, salvo la ventana/recorte general de la aplicación.

### V-006: Jerarquía de formas por tamaño
[RECOMENDADO] Las formas grandes tienden a la píldora y al círculo; las formas pequeñas de detalle también. Las formas intermedias (paneles, campos) usan el radio fijo. Mantener una sola familia de formas evita ruido visual.

### V-007: Composición a base de formas superpuestas
[RECOMENDADO] Componer mediante superposición y agrupación de las tres formas primarias (un círculo dentro de una píldora, un grupo de círculos como decoración). Evitar contenedores anidados profundos: máximo 2 niveles de superposición por elemento compuesto.

---

## 3. Color

### V-008: Paleta tipo "Pop"
[IMPERATIVO] La paleta combina **fondos oscuros índigo/violeta o pasteles muy claros** con **acentos extremadamente vivos** (neón suave: naranja, rosa/magenta, cian, verde lima, amarillo). La tensión entre fondo apagado y acento vibrante es la firma del estilo.

### V-009: Paletas listas para usar
[CONTEXTO] Todos los valores hex son **representativos**, no oficiales de la marca (ver G-005). A continuación se ofrecen 6 paletas completas listas para usar (3 oscuras y 3 claras), con fondo, superficies, acentos, semántica y texto definidos. Cada paleta cumple las reglas de este documento (60/30/10, un acento dominante, semántica de color, contraste AA). Las sombras planas de cada color se derivan oscureciendo el color ~20–35 % manteniendo el tono (ver `V-015`).

```
PALETA 1 — "Índigo Nocturno" (oscura, la clásica)
  Fondo #211D3D  ·  Superficies #2A2454 / #352D63 / #3E3670  ·  Texto #FFFFFF
  Dominante: naranja #FF9A47
  Secundarios: rosa #FF5FA2 · cian #45E0D5 · verde lima #9BE23E
  Semántica: éxito #9BE23E · error #E8485A · aviso #FFD145 · info #45E0D5
```

```
PALETA 2 — "Nebulosa Cósmica" (oscura, violeta-cian)
  Fondo #1A1B3C  ·  Superficies #262554 / #31306B / #3D3A82  ·  Texto #FFFFFF
  Dominante: violeta eléctrico #8C54E0
  Secundarios: cian #45E0D5 · amarillo #FFD145 · coral #FF6B6B
  Semántica: éxito #45E0D5 · error #FF6B6B · aviso #FFD145 · info #4F8BFF
```

```
PALETA 3 — "Bosque Electrónico" (oscura, teal-verde)
  Fondo #14242A  ·  Superficies #1C3340 / #26474D / #2F5A60  ·  Texto #FFFFFF
  Dominante: turquesa #2BD9C6
  Secundarios: verde lima #9BE23E · amarillo #FFD145 · rosa #FF5FA2
  Semántica: éxito #9BE23E · error #E8485A · aviso #FFD145 · info #2BD9C6
```

```
PALETA 4 — "Crema Cálido" (clara, crema-naranja)
  Fondo #FFF6E9  ·  Superficies #FFEBD0 / #FADDB9 / #F5D0A5  ·  Texto #242135
  Dominante: naranja #FF9A47
  Secundarios: rosa #FF5FA2 · turquesa #2BD9C6 · morado #A85BDB
  Semántica: éxito #2BD9C6 · error #E8485A · aviso #FFB300 · info #4F8BFF
```

```
PALETA 5 — "Rosado Glaciar" (clara, rosa-menta)
  Fondo #FBEFF6  ·  Superficies #F6E0EF / #F0D2E8 / #E8C4E0  ·  Texto #242135
  Dominante: rosa/magenta #FF5FA2
  Secundarios: cian #45E0D5 · amarillo #FFD145 · verde lima #9BE23E
  Semántica: éxito #9BE23E · error #E8485A · aviso #FFB300 · info #45E0D5
```

```
PALETA 6 — "Menta Fresca" (clara, menta-turquesa)
  Fondo #EAF6F1  ·  Superficies #DDF0E8 / #CBE8DC / #BADFCF  ·  Texto #242135
  Dominante: turquesa #2BD9C6
  Secundarios: naranja #FF9A47 · morado #A85BDB · coral #FF6B6B
  Semántica: éxito #2BD9C6 · error #FF6B6B · aviso #FFB300 · info #4F8BFF
```

### V-009a: Cómo crear una paleta personalizada
[IMPERATIVO] Estas 6 paletas son el punto de partida, pero se pueden crear paletas personalizadas siguiendo este procedimiento (cumple siempre las reglas `V-008` a `V-013`):

1. **Elige el modo base**: oscuro (fondo índigo/violeta profundo) o claro (fondo crema o pastel muy claro).
2. **Construye la escalera de fondo/superficies**: 3–4 tonos del mismo matiz que suban en luminosidad 2 pasos cada uno (los oscuros hacia arriba, los claros hacia abajo).
3. **Elige un acento dominante**: el color más vibrante del proyecto, el que marcará la acción principal (ver `V-011`).
4. **Añade 2 acentos secundarios**: toma de la rueda cromática colores opuestos o complementarios al dominante (cian↔naranja, violeta↔amarillo, turquesa↔rosa).
5. **Asigna semántica estable** a verde/rojo/amarillo/cian/morado y no la cambies entre vistas (ver `V-012`).
6. **Deriva las sombras planas**: oscurece cada color ~20–35 % manteniendo el tono (ver `V-015`).
7. **Verifica contraste de texto** AA sobre cada superficie (ver `V-024`).
8. **Registra el resultado como tokens** del proyecto; prohibido introducir colores fuera de la paleta (ver `G-005`).

Colores de referencia del catálogo base (para mezclar tu propia escalera):

```
Fondos oscuros   #211D3D #2A2454 #352D63 #3E3670 · #1A1B3C #262554 #31306B · #14242A #1C3340 #26474D
Fondos claros    #FFF6E9 #FFEBD0 #FADDB9      · #FBEFF6 #F6E0EF #F0D2E8 · #EAF6F1 #DDF0E8 #CBE8DC
Acentos          #FF9A47 #FF6B6B #E8485A #FF5FA2 · #A85BDB #8C54E0 #4F8BFF
                 #45E0D5 #2BD9C6 #FFD145 #9BE23E
Texto            sobre claro #242135 · sobre oscuro #FFFFFF
```

### V-010: Proporción 60/30/10
[IMPERATIVO] Por pantalla: ~60 % fondo, ~30 % superficies/soporte (en tonos del fondo o neutros), ~10 % acentos vibrantes. Si los acentos superan el 10–15 %, la pantalla pierde legibilidad y satura la vista.

### V-011: Un acento dominante por pantalla
[IMPERATIVO] Elegir **un** color de acento dominante por vista (que marca la acción principal) y, como máximo, **dos** acentos secundarios de apoyo. No usar 4+ vibrantes juntos; reservarlos para iconografía/ilustración narrativa.

### V-012: Asociación semántica de color
[IMPERATIVO] Asignar significados estables a los colores y no cambiarlos: verde = éxito/positivo, rojo = error/destrucción, amarillo = advertencia/aviso, cian = información/neutral técnico, morado = creatividad/misterio. Documentar el mapa semántico del proyecto y respetarlo en todas las vistas.

### V-013: Color de fondo ≠ color funcional
[IMPERATIVO] Los colores vibrantes se reservan para elementos funcionales e iconos. El fondo nunca usa acentos vibrantes a saturación completa, solo tonos oscuros o pastel. Excepción: zonas de "escaparate" narrativo (banners, ilustraciones de cabecera) donde un fondo vibrante puntual es aceptable si el contenido sobre él se recorta en blanco/negro con contraste suficiente.

---

## 4. Profundidad y sombras

### V-014: Sombras planas (flat shadows)
[IMPERATIVO] La profundidad se representa con una **sombra dura, sólida, desplazada** (offset) del mismo color del elemento pero más oscuro —no difusa ni con degradado—. Es la "sombra tipo Kurzgesagt": un bloque de color desplazado bajo la forma.

### V-015: Desplazamiento de sombra
[IMPERATIVO] La sombra plana se desplaza hacia abajo-derecha o directamente hacia abajo. Regla práctica: offset vertical de 2–6 px (escala base) según elevación; el color de la sombra = oscurecer el color del elemento ~20–35 % (mantener tono). Nunca usar negro puro ni sombra difuminada.

### V-016: Sistema de elevación
[RECOMENDADO] Definir una escala de elevación (0, 1, 2) donde cada nivel sube el tono de superficie (un paso más claro del fondo) y aumenta el offset de sombra. Elevación 1 = elementos en reposo; elevación 2 = elementos flotantes/emergentes/modales. Los elementos elevados NO cambian su forma al elevarse, solo su sombra y tono.

### V-017: Sombra en interacción
[RECOMENDADO] Al pasar sobre un elemento (hover), la sombra se agranda y el offset crece (parece "flotar"); al presionar, la sombra se reduce o se anula y el elemento baja (parece hundirse). La dirección del "vuelo" debe ser coherente con la iluminación global del proyecto (ver `A-012`).

---

## 5. Bordes y líneas

### V-018: Sin contornos negros
[IMPERATIVO] Los elementos no llevan contorno negro. Cuando se necesita un borde para separar, se usa una línea fina (1–2 px) del **mismo color pero más oscuro**, o un tono neutro del fondo. El "contorno" suave que se ve en el estilo es en realidad la sombra plana, no un trazo.

### V-019: Separadores sutiles
[IMPERATIVO] Las líneas divisorias internas (entre secciones, celdas de lista) usan tonos del fondo, no acentos. Prohibido dibujar marcos completos alrededor de todo el contenido; enmarcar con tarjetas y elevación, no con recuadros.

### V-020: Líneas decorativas
[RECOMENDADO] Las líneas decorativas (subrayados, rayas de énfasis) pueden ser del color de acento dominante, con grosor 2–4 px y extremos redondeados. Una sola línea de acento suele bastar para dirigir la atención.

---

## 6. Tipografía

### V-021: Familia sans-serif geométrica
[IMPERATIVO] Tipografía **sans-serif geométrica, de trazo grueso y muy legible**, todas disponibles en Google Fonts. Prohibidas las serif de transición, las manuscritas y las condensadas finas para texto corriente.

Catálogo recomendado por función:

```
Títulos / display (700–900)          Cuerpo y UI (400–600)
  Montserrat       Montserrat        Poppins        Nunito Sans
  Outfit           Archivo Black     Jost           Quicksand
  Space Grotesk    Raleway           DM Sans        Plus Jakarta Sans
  Urbanist         Fredoka           Overpass       Barlow
```

- **Montserrat** — la referencia principal del estilo; trazo geométrico fuerte, excelente en 700–900 para títulos.
- **Poppins** — geométrica de círculo perfecto; cuerpo y UI amables.
- **Jost** — aire de Futura; alternativa geométrica elegante.
- **Nunito / Quicksand / Fredoka** — redondeadas y amables; ideales para el tono "In a Nutshell" y para texto junto a personajes.
- **Outfit / Space Grotesk / Urbanist / Archivo Black** — display contemporáneo con mucha presencia.
- **DM Sans / Plus Jakarta Sans / Overpass / Barlow** — cuerpos neutros de alta legibilidad.

Regla práctica: elegir una familia de títulos y una de cuerpo, o una sola familia variable con 2 pesos (ver `V-023`). Descargar desde la sección Tipografía con la API de Google Fonts (ver `V-102`).

### V-022: Sistema tipográfico
[IMPERATIVO] Definir una escala tipográfica cerrada (títulos, subtítulos, cuerpo, etiqueta) y usarla sin excepciones. Regla práctica: paso de escala ≈ 1.25 (escala mayor tercera). Títulos muy gruesos (700–900), cuerpo 400–600, etiquetas en mayúsculas con interletra ampliada.

### V-023: Dos pesos, una familia
[RECOMENDADO] Limitarse a 2 variantes de peso por contexto (p. ej. Bold para títulos, Regular/Medium para cuerpo). La jerarquía se marca por tamaño y peso, no por multiplicar familias.

### V-024: Legibilidad y contraste de texto
[IMPERATIVO] Sobre fondos oscuros, texto blanco (#FFFFFF) o acento claro; nunca un acento vibrante a saturación completa para párrafos largos. Sobre fondos claros, texto índigo oscuro (#242135) o un acento saturado solo para titulares cortos. Contraste mínimo AA (4.5:1) para texto normal (ver `U-014`).

### V-025: Cuerpo nunca vertical
[IMPERATIVO] Texto siempre horizontal (o rotado exactamente 90°/270° solo en etiquetas de ejes); prohibido texto diagonal, curvo o invertido. Esto mantiene la legibilidad que caracteriza al estilo.

### V-026: Título en caja/contorno de color
[RECOMENDADO] Los títulos pueden presentarse como texto en color vibrante plano, o como "píldoras de texto" (texto claro sobre fondo de acento redondeado). Evitar texto con contorno hueco salvo en ilustración narrativa.

### V-027: Números y datos protagonistas
[RECOMENDADO] Las cifras clave (estadísticas, contadores) se presentan grandes, gruesas y en acento vibrante, a menudo dentro de una forma (círculo o píldora) con sombra plana. El dato es el protagonista; el texto descriptivo es apoyo.

---

## 7. Iconografía

### V-028: Iconos vectoriales de trazo grueso
[IMPERATIVO] Los iconos se dibujan como **formas llenas (solid) de trazo grueso**, no como líneas finas. Contorno de trazo ≥ 2 px en escala base, o relleno completo. Prohibidos iconos de línea fina 1 px tipo "outline minimal".

### V-029: Módulo y retícula de icono
[IMPERATIVO] Todos los iconos viven en la misma cuadrícula (p. ej. 24×24) y se alinean a la misma retícula interna. Geometría cerrada: círculos y rectángulos redondeados dentro del canvas del icono, con separación generosa.

### V-030: Color de icono = significado
[IMPERATIVO] El color del icono sigue la semántica de `V-012` (éxito verde, error rojo, etc.) o el color de acento de su contexto. Un icono nunca cambia de color sin cambiar de significado, y nunca lleva contorno negro.

### V-031: Icono con sombra plana
[RECOMENDADO] En superficies, los iconos pueden apoyarse en la sombra plana del elemento padre; si flotan solos (por ejemplo como punto de interés), llevan su propia sombra plana desplazada (ver `V-014`).

### V-032: Iconografía de marca (estilo In a Nutshell)
[CONTEXTO] Motivos icónicos del estilo para usar con moderación: estrellas/asteriscos de 4 puntas, partículas puntuales (círculos pequeños), órbitas/elipses punteadas, planetas simples (círculo + órbita), engranajes geométricos simples, corazones redondeados, burbujas de diálogo píldora. Usarlos como apoyo narrativo, no como relleno decorativo constante (ver `G-009`).

### V-033: Pobreza de iconos ≠ claridad
[RECOMENDADO] Un icono ambiguo es peor que ninguno: si un concepto no admite un icono geométrico simple, usar una etiqueta de texto en píldora en su lugar. Los iconos siempre llevan etiqueta o tooltip en interfaces funcionales (ver `U-013`).

---

## 8. Personajes e ilustración

### V-034: Personaje = forma redondeada
[IMPERATIVO] Los personajes/mascotas se construyen como **masas redondeadas** (blobs, círculos, elipses, gotas) sin ángulos agudos. Cuerpo sin trazo negro; el contorno del personaje se percibe por la sombra plana y el contraste de color.

### V-035: Rostro mínimo
[IMPERATIVO] El rostro se reduce a: dos **ojos** (círculos u óvalos, preferentemente un mismo tamaño, con brillo pequeño si se desea) y una **boca** (línea corta o pequeña forma). Sin cejas, nariz o detalles realistas. La emoción se transmite con la forma de los ojos y la boca, y con la postura.

### V-036: Mejillas como acento
[RECOMENDADO] Mejillas en tono rosado o un círculo de acento bajo los ojos para ternura. Son un detalle de marca: incluirlas en personajes y en estados "contento/sorprendido".

### V-037: Extremidades y accesorios geométricos
[RECOMENDADO] Brazos/piernas como formas redondeadas sencillas (rectángulos píldora, óvalos), o solo manos/patitas circulares adheridas al cuerpo. Accesorios (gafas, gorros, signos de interrogación) como formas simples superpuestas en acento vibrante.

### V-038: Escala de personaje
[RECOMENDADO] El personaje nunca compite con el contenido: máximo un 25–35 % de la altura útil de la pantalla, y nunca tapando texto ni acciones. Es acompañamiento narrativo (estados vacíos, onboarding, errores amables, encabezados temáticos).

### V-039: Personaje interactivo
[RECOMENDADO] Si el personaje reacciona a la interacción (parpadea, saluda, señala), la reacción debe ser discreta, de un solo gesto y con la animación definida por el sistema de duraciones (`A-002`). Un personaje que se mueve constantemente distrae (ver `A-016`).

### V-040: Ilustración de fondo (escenario)
[RECOMENDADO] Cuando hay ilustración de fondo narrativa, mantenerla desaturada o en tonos del fondo respecto a los elementos funcionales, para que el primer plano (saturado) resalte. La ilustración puede incluir el motivo de puntos y partículas del estilo (ver `V-043`).

---

## 9. Texturas

### V-041: Textura de puntos (dotted field)
[RECOMENDADO] El fondo típico del estilo puede incluir una cuadrícula de **puntos pequeños** (círculos de 2–4 px separados ~20–40 px) en un tono ligeramente más claro que el fondo. Es la textura de marca más característica; usar en fondos y vacíos.

### V-042: Texturas prohibidas
[IMPERATIVO] Prohibidas en UI funcional: madera, metal, tela, ruido de película, goteo de pintura, grano fotográfico sobre superficies, texturas de "papel" rugoso. El estilo es de tinta plana, no de material.

### V-043: Partículas y brillos puntuales
[RECOMENDADO] Motivos puntuales pequeños (estrellas de 4 puntas, círculos, cruces finas) en acento vibrante se usan como énfasis sobre fondos, títulos o resultados. Máximo 3–5 partículas por zona y solo en momentos de celebración o foco (ver `G-009`, `A-018`).

---

## 10. Recursos y herramientas (dominio visual)

> Recursos de **estética estática**. Integración del antiguo documento de recursos en los archivos de reglas.

### V-101: Herramientas de diseño vectorial
- **Figma** (gratuito): estándar de la industria para UI, componentes y prototipos. Ideal para diseñar las tarjetas, botones y sistema de tokens.
- **Adobe Illustrator** (pago): ilustración vectorial pura; útil para personajes e iconos complejos.
- **Inkscape** (gratuito, código abierto): alternativa libre a Illustrator para SVG y vectores.
- **Figma Tokens / Tokens Studio**: gestión de la paleta y el sistema de diseño como tokens (ver `G-005`).

### V-102: Tipografía — fuentes y API de Google Fonts
- **Página oficial de catálogo**: `https://fonts.google.com` (buscar por nombre: Montserrat, Poppins, Jost, Nunito, Quicksand, Fredoka, Outfit, Space Grotesk, Urbanist, Archivo Black, DM Sans, Plus Jakarta Sans, Overpass, Barlow, Raleway).
- **API de Google Fonts (CSS2, sin clave)**: `https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700;900&family=Poppins:wght@400;600&display=swap` — devuelve las `@font-face` con los `woff2` listos para cargar en cualquier plataforma (web, escritorio vía CSS, etc.). Los pesos se indican como `wght@400;700;900`; se pueden concatenar varias familias con `&family=...`.
- **Catálogo completo (JSON, requiere clave API)**: `https://www.googleapis.com/webfonts/v1/webfonts?key=TU_API_KEY&sort=popularity` — devuelve todas las familias, sus pesos, categorías y subsets; útil para que un agente elija fuentes programáticamente. La clave se obtiene gratis en Google Cloud Console (activar "Web Fonts Developer API").
- **Fuentes sin API**: las mismas familias se autoalojan descargando los ficheros desde `https://fonts.google.com` → "Download family" (licencia libre, OFL/SIL).
- **Futura** (de pago) y su alternativa libre **Jost** (`https://fonts.google.com/specimen/Jost`).

### V-103: Generadores y recursos de color
- **Coolors** (`https://coolors.co`): generador de paletas para construir el esquema 60/30/10.
- **Palette generator** de Figma: derivar tonos oscuros del mismo color para sombras planas (ver `V-015`).
- **WebAIM Contrast Checker** (`https://webaim.org/resources/contrastchecker/`): validar contraste de texto (ver `V-024`).

### V-104: Iconos — API de Iconify y catálogos
- **Iconify** (`https://iconify.design`): catálogo unificado de 200 000+ iconos vectoriales (Material Design Icons, Tabler, Solar, Remix Icon, etc.) servido por API, sin instalar nada:
  - **SVG directo por URL**: `https://api.iconify.design/mdi:star-four-points.svg` (cualquier icono como SVG escalable; parámetro `?height=24` para tamaño). Formato: `https://api.iconify.design/<prefijo>:<nombre>.svg`.
  - **Búsqueda (JSON)**: `https://api.iconify.design/search?query=star&limit=32` — devuelve los nombres de iconos y sus colecciones.
  - **Metadatos**: `https://api.iconify.design/collections.json` (colecciones) y `https://api.iconify.design/collection?prefix=mdi` (iconos de una colección).
  - **Web component** (HTML/CSS): `<script src="https://code.iconify.design/iconify-icon/1.0.8/iconify-icon.min.js"></script>` y luego `<iconify-icon icon="mdi:star-four-points"></iconify-icon>`; hereda `color` y `font-size` del CSS, ideal para recolor a la paleta.
- **Colecciones recomendadas para el estilo**: `mdi` (Material Design Icons, formas llenas), `solar` (estilos bold/duotone muy "pop"), `tabler` (trazo grueso descargable) y `mingcute` (iconos llenos).
- **Otros catálogos**: **Iconoir** (`https://iconoir.com`), **Lucide** (`https://lucide.dev`), **The Noun Project** (`https://thenounproject.com`; filtrar por estilo "filled").

### V-105: Ilustración y motivos de marca
- **freepik / Flaticon** (gratuito con atribución): packs de ilustraciones planas; re-colorear a la paleta del proyecto.
- **unDraw** (`https://undraw.co`): ilustraciones planas cuyo color principal se puede cambiar.
- **LottieFiles** (`https://lottiefiles.com`): además de animaciones, cuenta con ilustraciones estáticas de estilo plano (ver `A-101`).

### V-106: Motivos de puntos y partículas
- **CSS Doodle / SVG dot generators**: generar la cuadrícula de puntos (V-041) como patrón SVG o CSS repeat.
- **Figma "Fill → Dot grid"**: el patrón de puntos se define una vez como componente y se reutiliza.

---

## 11. Checklist de diseño visual

- [ ] Todas las formas son círculos, píldoras/rectángulos redondeados o líneas limpias (V-004).
- [ ] Sin esquinas rectas ni formas orgánicas en la UI funcional (V-004, V-005).
- [ ] Paleta elegida: una de las 6 listas en V-009 o personalizada según V-009a; registrada como tokens (G-005).
- [ ] Proporción ~60 % fondo / 30 % superficies / 10 % acentos (V-010).
- [ ] Un solo acento dominante por pantalla (V-011).
- [ ] Las sombras son planas, desplazadas, del mismo color oscurecido (V-014, V-015).
- [ ] Sin contornos negros; separadores en tonos del fondo (V-018, V-019).
- [ ] Tipografía sans-serif geométrica; escala cerrada y ≤ 2 pesos por contexto (V-021, V-022, V-023).
- [ ] Contraste de texto AA verificado (V-024).
- [ ] Iconos de trazo grueso o rellenos, en retícula común, sin contorno negro (V-028, V-029, V-030).
- [ ] Personajes (si hay) con rostro mínimo, sin trazo negro y sin competir con el contenido (V-035, V-038).
- [ ] Texturas: solo puntos y partículas puntuales (V-041, V-042, V-043).
