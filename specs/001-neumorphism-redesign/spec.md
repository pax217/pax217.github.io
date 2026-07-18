# Feature Specification: Rediseño visual — Neumorphism moderno 2026

**Feature Branch**: `001-neumorphism-redesign`

**Created**: 2026-07-18

**Status**: Draft — Amended 2026-07-18 (paleta azul/gris + referencia estructural)

**Input**: User description: "El look and feel del portafolio debería ser Neumorphism moderno 2026 — reemplazando la dirección visual 'minimal oscuro' de la v1 ya publicada (fondo claro/neutro, superficies 'soft UI' con sombras duales suaves, esquinas muy redondeadas, elementos que parecen extruidos o presionados del mismo fondo, sin bordes duros ni alto contraste. Debe mantenerse profesional, legible, accesible (AA) y con buen rendimiento (solo CSS, sin librerías pesadas)."

**Amendment (2026-07-18)**: El usuario pidió usar `https://johnserrano.co/portafolio` como referencia estructural de secciones, con paleta neumorphism clara en tonos **azul y gris**. Esto amplía el alcance original (que era solo de lenguaje visual, FR-009) para incluir ajustes de arquitectura de información acordados explícitamente con el usuario — ver "Decisiones de contenido confirmadas" al final de este documento.

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Impresión profesional inmediata para reclutadores (Priority: P1)

Un reclutador técnico o hiring manager abre `pax217.github.io` por primera vez y, en los primeros segundos, percibe un sitio visualmente moderno, cuidado y "senior" — coherente con la audiencia y el posicionamiento de liderazgo técnico ya definidos en la spec base del proyecto — en vez del tratamiento oscuro tipo terminal de la v1.

**Why this priority**: El look and feel es lo primero que se evalúa antes de leer una sola línea de contenido; si no transmite seniority/calidad, el resto del contenido pierde peso.

**Independent Test**: Se puede validar por completo abriendo el sitio publicado y evaluando de forma aislada (sin leer el copy) si la primera impresión visual se percibe como "moderna y profesional" vs. "genérica o desactualizada".

**Acceptance Scenarios**:

1. **Given** el visitante abre el sitio en desktop, **When** la página carga, **Then** ve un fondo claro/neutro con tarjetas y elementos de superficie suave (sombras duales, esquinas redondeadas), sin bordes duros ni el esquema oscuro de alto contraste de la v1.
2. **Given** el visitante abre el sitio en un dispositivo móvil, **When** navega entre secciones, **Then** el mismo lenguaje visual neumórfico se mantiene consistente, sin elementos que rompan el estilo (p. ej. tarjetas con bordes duros remanentes).

---

### User Story 2 - Interacción reconocible sin perder accesibilidad (Priority: P1)

Un visitante interactúa con los elementos clickeables (nav, botones de contacto, links de proyectos) y puede distinguir claramente estados de hover/foco/presionado, y cualquier persona que navegue por teclado o use un lector de pantalla puede seguir usando el sitio sin pérdida de funcionalidad respecto a la v1.

**Why this priority**: El neumorphism es un estilo con riesgo de accesibilidad conocido (bajo contraste entre superficie y fondo); si esto no se resuelve deliberadamente, el rediseño puede violar el requisito de accesibilidad ya establecido en la spec base (AA, Lighthouse Accessibility ≥95).

**Independent Test**: Se puede probar de forma aislada navegando el sitio solo con teclado (Tab/Enter) y corriendo una auditoría de accesibilidad automatizada, sin depender de las demás historias.

**Acceptance Scenarios**:

1. **Given** un usuario navega con teclado, **When** pasa el foco sobre un elemento interactivo, **Then** existe un indicador de foco claramente visible (no eliminado por el estilo de superficie suave).
2. **Given** un usuario hace hover/click sobre un botón o link, **When** ocurre la interacción, **Then** el elemento cambia visualmente (p. ej. de "extruido" a "presionado") de forma perceptible.
3. **Given** una auditoría de contraste de texto sobre las superficies neumórficas, **When** se mide el contraste texto/fondo, **Then** cumple el mínimo AA (4.5:1 para texto normal) en todas las secciones.

---

### User Story 3 - Diferenciación frente a la v1 y a portafolios genéricos de desarrollador (Priority: P2)

Carlos quiere que el sitio se perciba distinto a la plantilla "dark mode + acentos monoespaciados" típica de portafolios de desarrollador (incluyendo la v1 ya publicada), reforzando una identidad visual propia de cara a 2026.

**Why this priority**: Es una motivación de diferenciación/branding personal, valiosa pero no bloqueante para que el sitio funcione o sea evaluado favorablemente — depende de que P1 y P2 (arriba) ya estén resueltos.

**Independent Test**: Comparación lado a lado entre un screenshot de la v1 (dark, minimal, mono) y la nueva versión, confirmando que el lenguaje visual cambió de forma evidente y no es una variación menor de paleta.

**Acceptance Scenarios**:

1. **Given** se comparan capturas de la v1 y la nueva versión, **When** se revisan fondo, sombras, radios de borde y tipografía de acento, **Then** el cambio es inmediatamente reconocible como un sistema visual distinto (no solo un cambio de color).

---

### Edge Cases

- ¿Qué pasa en pantallas muy pequeñas (< 360px) donde sombras duales grandes pueden verse pesadas o recortadas? El tratamiento neumórfico debe reducirse/simplificarse en esos anchos sin perder la identidad visual.
- ¿Cómo se comportan los estados de foco de teclado sobre superficies de bajo contraste? Deben seguir siendo perceptibles aunque el resto de la superficie sea "suave".
- ¿Qué pasa si el usuario tiene activada la preferencia de sistema `prefers-contrast: more` o `prefers-reduced-motion`? El sitio no debe depender de sombras/transiciones que rompan la legibilidad bajo esas preferencias.
- ¿Cómo se ve el sitio impreso o exportado a PDF (un reclutador podría imprimirlo)? Las sombras suaves no deben desaparecer dejando bloques sin separación visual.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: El sitio DEBE reemplazar el lenguaje visual oscuro/alto-contraste de la v1 por un lenguaje neumórfico ("soft UI"): fondo claro y neutro, superficies con sombras duales suaves que simulan elementos extruidos o presionados del mismo fondo, y esquinas con radio de borde consistentemente grande.
- **FR-002**: Todos los elementos interactivos (nav, botones, links de contacto, anclas de sección) DEBEN tener un estado de hover/activo/presionado visualmente distinguible, coherente con el idioma neumórfico (p. ej. transición de sombra extruida a sombra interna).
- **FR-003**: Todo el texto y elementos interactivos DEBEN mantener contraste AA (mínimo 4.5:1 para texto normal, 3:1 para texto grande/UI) sobre las superficies neumórficas, sin excepción por el estilo visual.
- **FR-004**: Los indicadores de foco de teclado DEBEN permanecer visibles y perceptibles sobre las superficies de bajo contraste (no se elimina el outline de foco por estética).
- **FR-005**: El nuevo lenguaje visual DEBE aplicarse de forma consistente en las 7 secciones existentes (Hero, Sobre mí, Experiencia, Proyectos, Stack técnico, Educación, Contacto) sin dejar remanentes visuales del esquema oscuro anterior.
- **FR-006**: El tono visual DEBE seguir leyéndose profesional y orientado a seniority (no lúdico/casual), consistente con la audiencia definida en la spec base del proyecto.
- **FR-007**: El rediseño NO DEBE introducir regresiones sobre los requisitos no funcionales ya establecidos: responsive mobile-first, Lighthouse Performance ≥95, Lighthouse Accessibility ≥95.
- **FR-008**: El rediseño DEBE lograrse únicamente con CSS (sombras, radios, variables de color) sin agregar librerías de UI, frameworks nuevos, imágenes adicionales o dependencias de red (fuentes externas, iconos vía CDN).
- **FR-009**: La regla de confidencialidad (no mencionar al empleador actual) ya definida en la spec base del proyecto DEBE mantenerse sin excepción, incluyendo en cualquier archivo descargable (p. ej. CV en PDF) que el sitio ofrezca — ver FR-011.
- **FR-010**: La paleta visual DEBE construirse sobre azul y gris: fondo base gris muy claro/neutro, superficies neumórficas en un gris ligeramente distinto al fondo (para permitir el efecto de sombra dual), acentos y estados interactivos en azul, texto en tonos de gris oscuro con contraste AA.
- **FR-011**: El sitio DEBE ofrecer un botón de descarga de CV en PDF en el footer. Ese PDF DEBE ser una versión redactada/anonimizada equivalente al contenido ya aprobado del sitio (sin nombrar al empleador actual ni fechas que lo delaten), nunca el CV original sin editar.

### Decisiones de contenido confirmadas (2026-07-18)

Estructura de secciones final, adaptada de `johnserrano.co/portafolio` al perfil de Carlos (no freelance con proyectos públicos):

1. **Hero** — foto, nombre, rol, tagline, botones CTA "Ver experiencia" y "Contactar" (en vez de "Mis Trabajos"/"Conóceme" del ejemplo, porque no hay sección de proyectos con links en vivo).
2. **Sobre mí** — sin cambios respecto a la spec base.
3. **Stack técnico** — se mantiene **agrupado por categoría** (no la grilla plana de 30+ logos del ejemplo); más legible y coherente con el posicionamiento de liderazgo técnico.
4. **Experiencia laboral** — timeline, tono sobrio (sin emojis ✅/🚀 como el ejemplo, para mantener el tono "no casual" ya definido en la spec base).
5. **Proyectos destacados** — se mantienen los 2 casos de estudio ya redactados (Conekta, Harmon Hall), en formato problema→solución→resultado, sin links en vivo (no existen).
6. **Educación** — sin cambios.
7. **Contacto** — sin cambios (email, LinkedIn, GitHub).
8. **Footer** — botón de descarga de CV en PDF (versión redactada, ver FR-011), links a LinkedIn/GitHub, copyright.

**Explícitamente excluido** (a diferencia del sitio de referencia):
- **Testimonios** — no hay recomendaciones reales disponibles todavía; se puede agregar después si se consiguen.
- **Blog / artículos** — el usuario no tiene contenido escrito que destacar.
- **Grilla de "otros proyectos"** — no hay proyectos personales/open source públicos que mostrar.
- Redes sociales adicionales (X/Twitter, Facebook, YouTube) — el usuario confirmó mantener solo email, LinkedIn y GitHub.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Al comparar capturas de la v1 y la nueva versión, un observador identifica el cambio de estilo visual (fondo, sombras, radios) en menos de 5 segundos sin necesidad de explicación.
- **SC-002**: El sitio mantiene un score de Lighthouse Accessibility ≥95 después del rediseño.
- **SC-003**: El sitio mantiene un score de Lighthouse Performance ≥95 después del rediseño, sin nuevas peticiones de red respecto a la v1.
- **SC-004**: El 100% de los elementos interactivos (nav, botones, links) muestra un cambio de estado visualmente distinguible al probarse manualmente en desktop y en un viewport móvil.
- **SC-005**: El 100% de las combinaciones texto/superficie del sitio cumple contraste AA al medirse con una herramienta de auditoría de contraste.

## Assumptions

- El neumorphism se aplica como variante de superficie clara/neutra (la forma clásica y más legible del estilo); una variante neumórfica en modo oscuro queda fuera de alcance de esta iteración y puede evaluarse como mejora futura, sin bloquear esta entrega.
- "Moderno 2026" se interpreta como: colores base de baja saturación, sombras duales sutiles y conservadoras (no el neumorphism "plástico" de baja legibilidad criticado en versiones tempranas del estilo), radios de esquina grandes, y acentos de color discretos — priorizando siempre el contraste de texto por encima de la pureza estética del efecto de sombra.
- La estructura de contenido de la v1 cambia únicamente en lo acordado explícitamente con el usuario el 2026-07-18 (ver "Decisiones de contenido confirmadas"): CTAs del hero, footer con descarga de CV, y exclusión de Testimonios/Blog/grilla de otros proyectos. El copy de las secciones que sí se mantienen (Sobre mí, Experiencia, Proyectos, Stack técnico, Educación, Contacto) no cambia respecto a la spec base.
- No se introducen nuevas imágenes, íconos de librerías externas ni fuentes vía CDN; se mantiene la política de "sin frameworks/dependencias pesadas" ya establecida.
- La regla de confidencialidad (no mencionar al empleador actual) definida en la spec base permanece vigente y no se ve afectada por este cambio visual.
