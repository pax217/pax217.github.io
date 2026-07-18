# Feature Specification: Hero en dos columnas con foto grande

**Feature Branch**: `002-hero-split-layout`

**Created**: 2026-07-18

**Status**: Implemented (2026-07-18)

**Input**: User description: "Nuevo spec para la sección de introducción: que la foto se vea más grande, en dos columnas — del lado izquierdo la descripción, del lado derecho la foto más grande, del tamaño de la descripción."

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Primera impresión con foto prominente en desktop (Priority: P1)

Un reclutador abre el sitio en desktop/laptop y ve el hero organizado en dos columnas: a la izquierda el bloque de texto (saludo, nombre, rol, tagline, botones de acción, iconos sociales), a la derecha una foto de Carlos considerablemente más grande que en la v actual, cuya altura visual iguala la del bloque de texto de la izquierda — dando más peso y presencia a la foto sin que el layout se vea desbalanceado.

**Why this priority**: Es el cambio central solicitado — la foto pasa de ser un avatar circular pequeño a un elemento visual principal del hero, a la par del texto.

**Independent Test**: Se puede validar abriendo el sitio en un viewport de escritorio y confirmando visualmente que existen dos columnas alineadas en altura, con la foto claramente más grande que el avatar circular de la versión anterior.

**Acceptance Scenarios**:

1. **Given** un visitante abre el sitio en un viewport de escritorio (≥ el breakpoint de navegación actual, 720px), **When** la página carga, **Then** el hero muestra dos columnas lado a lado: texto a la izquierda, foto a la derecha.
2. **Given** las dos columnas están renderizadas, **When** se mide la altura de cada una, **Then** la columna de la foto ocupa una altura visualmente equivalente a la columna de texto (no una foto pequeña flotando junto a un bloque de texto mucho más alto).

---

### User Story 2 - Layout coherente en mobile (Priority: P1)

Un visitante en un dispositivo móvil ve el mismo contenido del hero, pero en una sola columna (no hay espacio horizontal para dos columnas), sin que la foto grande rompa el layout, genere scroll horizontal, o desplace el texto fuera de pantalla.

**Why this priority**: El sitio ya tiene un requisito no funcional de mobile-first (spec base del proyecto); un hero de dos columnas que no degrade correctamente en mobile sería una regresión.

**Independent Test**: Se puede probar de forma aislada abriendo el sitio en un viewport móvil y confirmando que el hero se apila verticalmente sin overflow horizontal ni elementos cortados.

**Acceptance Scenarios**:

1. **Given** un visitante abre el sitio en un viewport móvil (< 720px), **When** la página carga, **Then** el hero se muestra en una sola columna (foto y texto apilados), sin scroll horizontal.
2. **Given** el hero apilado en mobile, **When** se mide el ancho de cualquier elemento del hero, **Then** ninguno excede el ancho del viewport.

---

### Edge Cases

- ¿Qué pasa si el bloque de texto es más alto que un valor razonable para una foto (p. ej. si el tagline se hace más largo en el futuro)? La foto no debe deformarse (estirarse) para igualar la altura — debe recortarse (crop) manteniendo su proporción, no distorsionarse.
- ¿Qué pasa en anchos intermedios tipo tablet (720px–1024px)? Las dos columnas deben seguir siendo legibles sin que la foto opaque al texto ni quede demasiado angosta.
- ¿Qué pasa con el foco de teclado y el orden de lectura para lectores de pantalla? El orden en el DOM debe seguir siendo lógico (texto antes que la imagen, o al menos un orden que no confunda la navegación), independientemente del orden visual en pantalla.
- La foto fuente actual está recortada como cuadrado (480×480). Si la columna resultante no es cuadrada, la imagen debe recortarse visualmente (`object-fit: cover`) para llenar el espacio sin distorsión, no reemplazarse por una nueva foto.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: En viewports de escritorio (≥720px, el breakpoint ya definido en la spec base), el hero DEBE mostrarse en un layout de dos columnas: descripción (saludo, nombre, rol, tagline, CTAs, iconos sociales) a la izquierda, foto a la derecha.
- **FR-002**: La columna de la foto DEBE tener una altura visual equivalente a la columna de texto (misma altura de fila), no una foto pequeña de tamaño fijo independiente del contenido de texto.
- **FR-003**: La foto DEBE mostrarse significativamente más grande que el avatar circular actual (128px), ocupando el ancho completo de su columna.
- **FR-004**: La imagen DEBE recortarse para llenar su contenedor sin distorsionar la proporción original (equivalente a `object-fit: cover`), incluso si el contenedor resultante no es cuadrado.
- **FR-005**: En viewports móviles (<720px), el hero DEBE volver a un layout de una sola columna (apilado), sin scroll horizontal ni elementos cortados.
- **FR-006**: El cambio DEBE mantener el lenguaje visual neumórfico ya establecido (sombras suaves, esquinas redondeadas) definido en `specs/001-neumorphism-redesign/spec.md`.
- **FR-007**: El cambio NO DEBE modificar el copy del hero (saludo, nombre, rol, tagline, textos de los botones) ni los links de contacto/redes ya aprobados — es un cambio de layout únicamente.
- **FR-008**: El contraste de texto sobre fondo DEBE mantenerse AA, sin excepción por el nuevo layout.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: En un viewport de escritorio estándar (1280px), la foto ocupa al menos el doble del área visual que el avatar circular de 128px de la versión anterior.
- **SC-002**: La diferencia de altura entre la columna de texto y la columna de foto es visualmente imperceptible (alineadas dentro de un margen razonable, sin una quedando notablemente más corta o más alta que la otra).
- **SC-003**: En un viewport móvil (375–430px), el hero no genera scroll horizontal y todo el contenido es legible sin recorte.
- **SC-004**: El sitio mantiene los scores de Lighthouse Accessibility y Performance ≥95 ya establecidos como requisito no funcional del proyecto.

## Assumptions

- La foto deja de ser un avatar circular pequeño y pasa a mostrarse como un panel grande (esquinas redondeadas grandes, tratamiento neumórfico) que ocupa toda su columna — no un círculo, ya que un círculo "del tamaño de la descripción" dejaría espacio vacío a los lados dentro de la columna. Si Carlos prefiere mantenerla circular pero más grande (con espacio vacío alrededor), es un ajuste menor sobre esta spec.
- La proporción de columnas se asume aproximadamente equilibrada (cercana a 50/50), ligeramente a favor del texto si es necesario para mantener línea de lectura cómoda (p. ej. 55/45) — la proporción exacta se define en la fase de implementación dentro de ese rango.
- La imagen fuente (`img/profile.jpg`, recorte cuadrado 480×480 ya procesado) se reutiliza tal cual; no se vuelve a recortar desde el original. El recorte visual a la nueva forma de columna se logra en CSS (`object-fit: cover`), no reprocesando el archivo.
- El breakpoint mobile/desktop reutiliza el ya definido en el proyecto (720px) para mantener consistencia con el resto del sitio (nav, demás secciones).
- Los botones CTA e iconos sociales se alinean a la izquierda (no centrados) dentro de la columna de texto, ya que el layout deja de ser una columna centrada única — esto es un cambio visual respecto a la v actual, coherente con el propio ejemplo de referencia (`johnserrano.co/portafolio`) que usa alineación izquierda en su hero de dos columnas.
