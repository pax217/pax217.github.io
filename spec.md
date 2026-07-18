# Spec — Portafolio profesional de Carlos Maldonado (pax217.github.io)

Estado: **Borrador para revisión — Fase 1 (spec, sin implementación)**

## 1. Propósito y audiencia

**Propósito:** sitio personal que funcione como carta de presentación técnica para procesos de reclutamiento, mostrando trayectoria, criterio técnico y capacidad de liderazgo.

**Audiencia primaria:** reclutadores técnicos y hiring managers evaluando a Carlos para roles de **Backend Developer Lead / Lead Engineer** (Go, arquitectura, liderazgo de equipos).

**Audiencia secundaria:** pares técnicos (otros ingenieros/leads) que puedan validar profundidad técnica real detrás del branding.

**No es el objetivo:** un blog personal, un espacio creativo/casual, ni un CV en PDF replicado 1:1 — es una versión curada y navegable orientada a conversión (que el reclutador agende una llamada / escriba un correo).

## 2. Restricción de confidencialidad (importante)

El sitio **no debe revelar que Carlos trabaja actualmente en OCC**. La experiencia más reciente (2022–actualidad) se presenta:

- Sin mencionar el nombre de la empresa ("OCC", "OCC Mundial", "Redarbor") en ningún texto visible ni en metadata/alt-text.
- Con una descripción funcional del tipo de organización (p. ej. "empresa líder de reclutamiento online en LATAM") en vez del nombre propio.
- Sin fecha de fin explícita tipo "2022 – Actualidad" que delate que es el empleo vigente; se puede usar fraseo relativo ("Rol más reciente") en vez de rango de fechas exacto, o solo año de inicio.

Esta regla aplica a toda mención de esa etapa: Experiencia laboral, Sobre mí, y cualquier caso de estudio futuro derivado de ese rol (incluyendo AMP for Email, si se agrega más adelante).

## 3. Contenido extraído del CV

Fuente: `CV_Carlos_Maldonado_12.pdf`.

### 3.1 Datos de contacto
- Email: cmaldonadod.217@gmail.com
- LinkedIn: https://www.linkedin.com/in/carlos-alberto-maldonado-díaz-70542b214/
- GitHub: https://github.com/pax217
- Teléfono: **excluido** del sitio público (decisión del usuario, evitar spam/scraping).
- Ubicación: CDMX (opcional mostrar solo ciudad, sin dirección).

### 3.2 Hero / Intro
- Nombre: Carlos Alberto Maldonado Díaz
- Título profesional: Backend Developer Lead — Go
- Tagline corto (propuesta, sujeta a aprobación del usuario): algo que combine "7+ años construyendo backends en Go" + "4 años liderando equipos" + enfoque en arquitectura escalable. Redacción final se define en fase de contenido, no en esta spec.

### 3.3 Sobre mí (resumen ejecutivo)
Basado en el perfil profesional del CV: Backend Developer Lead con 7+ años de experiencia en desarrollo de software y 4 años liderando equipos técnicos. Especialista en Go — arquitecturas escalables en cloud, contenedores (Docker/Kubernetes), APIs REST y gRPC/Protocol Buffers. Combina liderazgo técnico y funcional (mentoring, code reviews, definición de estándares de calidad) con participación activa en diseño e implementación backend, patrones de diseño (Arquitectura Hexagonal, Clean Architecture, Microkernel, Factory, MVC) y metodologías ágiles (Scrum). Uso habitual de herramientas de IA (Claude, GitHub Copilot) bajo un enfoque de Spec-Driven Development (SDD).

Ángulo editorial: enfatizar **liderazgo técnico + criterio de arquitectura**, no solo ejecución individual.

### 3.4 Experiencia laboral

**Rol más reciente — Backend Developer Lead** *(sin nombrar empresa, ver §2)* — desde 2022
- Liderazgo técnico y funcional de un equipo de desarrollo backend, incluyendo mentoría de desarrolladores.
- Definición de arquitectura y diseño de soluciones escalables en entornos cloud.
- Coordinación con stakeholders y producto para definición y priorización de requerimientos.
- Code reviews y estándares de calidad (Clean Code, SOLID, Testing, CI/CD; Singleton como patrón estándar de inyección de dependencias en microservicios del equipo).
- Diseño y supervisión de despliegues containerizados (Docker/Kubernetes).
- Gestión técnica de incidencias en producción con observabilidad (Datadog, Grafana, Prometheus, Elasticsearch).
- Adopción diaria de Claude bajo Spec-Driven Development (SDD) para análisis, generación y revisión de código.

**Senior Software Engineer — Conekta** · 2019–2022
- Desarrollo backend en Go para productos de pagos.
- Diseño e implementación de un servicio en Go con gRPC + Protocol Buffers para procesamiento de transferencias bancarias, permitiendo a producto crear y aplicar reglas antifraude propias de forma dinámica.
- Diseño e implementación de APIs REST y definición de contratos entre servicios.
- Patrones de diseño (Factory, MVC, Arquitectura por Capas).
- Contenerización con Docker y soporte en adopción de Kubernetes.

**Software Developer Sr. (Full Stack) — Harmon Hall** · 2017–2019
- Desarrollo de skills para Alexa, integrando backend con asistentes de voz.
- Migración de servicios legacy a .NET Core y Angular.
- Desarrollo full stack: APIs REST + frontend.

> **Nota honesta:** el CV no incluye logros con métricas cuantificadas (%, tiempos, cifras de negocio). No se van a inventar números. Si Carlos tiene métricas reales (ej. "reduje incidentes en X%", "el servicio procesa Y tx/día"), agregarlas en fase de contenido; si no, los logros se presentan en términos cualitativos de alcance y responsabilidad, como está en el CV.

### 3.5 Proyectos destacados (casos de estudio)

Formato: problema → solución → resultado/impacto.

**Caso de estudio 1 — Servicio de transferencias bancarias antifraude (Conekta)**
- Problema: producto necesitaba poder definir y aplicar reglas antifraude propias de forma dinámica sobre transferencias bancarias.
- Solución: Carlos diseñó e implementó un servicio en Go con gRPC/Protocol Buffers dedicado a este flujo.
- Resultado: producto ganó capacidad de configurar reglas antifraude sin depender de releases de backend (impacto cualitativo, sin cifra en el CV).

**Caso de estudio 2 (secundario, opcional) — Skills de Alexa + migración legacy (Harmon Hall)**
- Problema: servicios legacy y necesidad de presencia en asistentes de voz.
- Solución: desarrollo de skills para Alexa integradas a backend existente; migración de servicios a .NET Core/Angular.
- Resultado: modernización de stack (cualitativo).

**AMP for Email — omitido en esta fase.** El usuario decidió no incluir este caso de estudio por ahora (no hay detalle de problema/solución/impacto disponible y, de estar ligado al rol actual, aplicaría la restricción de confidencialidad de §2). Puede agregarse después como una sección nueva si se define el contenido y cómo anonimizarlo.

### 3.6 Stack técnico (por categoría)

- **Backend / Lenguajes:** Go (7 años, avanzado) — goroutines, channels, worker pools, operaciones atómicas.
- **APIs e integración:** REST, gRPC, Protocol Buffers.
- **Mensajería:** Kafka, RabbitMQ.
- **Contenedores y orquestación:** Docker, Kubernetes.
- **Cloud y CI/CD:** AWS, Azure DevOps, Jenkins, Drone, Harness.
- **Bases de datos:** *no listadas explícitamente en el CV* — pendiente de confirmar con Carlos si hay motores específicos (Postgres, MySQL, Redis, etc.) para incluir en esta categoría.
- **Testing y calidad:** testing automatizado unitario/integración (10 años), pruebas de carga con k6.
- **Observabilidad:** Datadog, Grafana, Prometheus, Elasticsearch (métricas, tracing, logs).
- **Arquitectura y patrones:** Arquitectura Hexagonal, Clean Architecture, Microkernel, Singleton, Strategy, Factory, MVC, Arquitectura por Capas.
- **Metodologías:** Scrum, Agile.
- **Herramientas de IA para desarrollo:** Claude (Spec-Driven Development), GitHub Copilot.

### 3.7 Educación / certificaciones

- Ingeniería en Sistemas Computacionales — Universidad del Valle de México · 2007–2011 · Titulado, con cédula profesional.
- Certificaciones: *ninguna listada en el CV.* Si Carlos tiene certificaciones (AWS, Kubernetes, etc.) no incluidas en el CV, agregarlas en fase de contenido.

### 3.8 Contacto
- Email (mailto, sin exponer en texto plano sin protección básica anti-scraping simple).
- LinkedIn.
- GitHub.
- Sin teléfono, sin dirección física.

## 4. Tono y voz

- Profesional, orientado a **seniority y liderazgo técnico**. No junior, no creativo/casual, no informal.
- Primera persona, verbos de acción concretos ("diseñé", "lideré", "definí"), evitando adjetivos vacíos ("apasionado", "rockstar", "ninja").
- Prioriza claridad y precisión técnica sobre "storytelling" de marketing.
- Copy en español (idioma del CV y del usuario) salvo decisión explícita de bilingüe — **pendiente de confirmar** si el sitio es solo español, solo inglés, o con selector de idioma (afecta alcance de Fase 2).

## 5. Requisitos técnicos (no funcionales)

- Sitio 100% estático, desplegado en GitHub Pages en la raíz (`https://pax217.github.io`), rama `main` (o `/docs` si se decide así en plan.md).
- Mobile-first, responsive en breakpoints estándar (móvil, tablet, desktop).
- Performance: objetivo Lighthouse Performance ≥ 95, sin frameworks pesados innecesarios, sin JS bloqueante para contenido above-the-fold.
- Accesibilidad: objetivo Lighthouse Accessibility ≥ 95 — contraste AA, HTML semántico, navegación por teclado, `alt` en imágenes.
- SEO básico: metadata (title, description, OG tags), sitemap, favicon.
- Modo oscuro/claro: **nice to have**, no bloqueante para el lanzamiento inicial.
- Sin dependencia de backend/base de datos — todo el contenido vive en el repo (markdown/JSON/config, según stack elegido).

## 6. Stack técnico propuesto para el sitio

Comparativa para un sitio de este tamaño (portafolio de una página o pocas páginas, contenido mayormente estático, actualizado con poca frecuencia):

| Opción | Pros | Contras |
|---|---|---|
| **HTML/CSS/JS puro** | Cero build step, cero dependencias, control total, deploy trivial a GH Pages, carga instantánea. Ideal si el sitio es realmente 1 página. | Sin componentización → duplicación de markup si crecen las secciones/casos de estudio; agregar dark mode y estructura de datos (ej. lista de experiencias) a mano es más tedioso de mantener; sin optimización automática de assets. |
| **Astro** | Static-site generator pensado para contenido mayormente estático, output final es HTML/CSS con JS mínimo o cero ("islands"), soporta componentes reutilizables (cards de experiencia, skills), buen soporte oficial para deploy a GitHub Pages vía Actions, fácil de escalar a más páginas (ej. página dedicada por caso de estudio) sin duplicar código, dark mode con poco esfuerzo. | Requiere Node/build step y un poco de curva de aprendizaje si no se ha usado antes (aunque el usuario es backend lead, no debería ser fricción real); una dependencia más que mantener actualizada. |
| **Next.js (static export)** | Ecosistema grande, familiar para muchos reclutadores/equipos frontend, mismo resultado final estático que Astro si se usa `output: export`. | Sobra para este caso: trae runtime/tooling pensado para apps con rutas dinámicas, SSR, API routes — nada de eso aplica a un portafolio estático. Bundle de JS por defecto más pesado que Astro para el mismo contenido si no se es cuidadoso. Mayor complejidad de configuración para algo que no la necesita. |

**Recomendación:** **Astro**. Da el balance correcto entre "sitio realmente estático y rápido" (cumple el requisito de "sin frameworks pesados") y "mantenible a mediano plazo" (componentes reutilizables para experiencia/skills/proyectos, fácil agregar casos de estudio como páginas propias, dark mode de bajo esfuerzo). HTML/CSS/JS puro es válida si se prefiere cero tooling y el sitio se mantiene deliberadamente simple (una sola página, pocas secciones) — decisión final se confirma en `plan.md` / revisión del usuario antes de implementar.

## 7. Gaps de contenido pendientes (antes de pasar a implementación)

1. **Tagline del hero** — necesita redacción final aprobada por Carlos.
2. **Bases de datos / motores de datos** usados — no aparecen en el CV, confirmar si aplica agregarlos al stack técnico.
3. **Certificaciones** — no hay ninguna en el CV; confirmar si existen y no se incluyeron.
4. **Idioma del sitio** — español único vs. bilingüe.
5. **Caso de estudio AMP for Email** — omitido en esta fase; se puede retomar más adelante con detalle de problema/solución/impacto y respetando la regla de confidencialidad de §2.
6. **Métricas cuantificadas de logros** — el CV no las tiene; confirmar si existen datos reales que se puedan citar honestamente.

## 8. Fuera de alcance (Fase 1)

- Cualquier código de implementación (HTML/CSS/JS, configuración de Astro, GitHub Actions, etc.).
- Diseño visual final (paleta, tipografía, wireframes) — se define en fase de diseño/implementación, no en esta spec de contenido/estructura.
- Blog o sección de artículos técnicos.
- Formulario de contacto con backend (fuera de alcance para un sitio 100% estático sin backend).

---

**Siguiente paso:** revisión y aprobación de este `spec.md` y de `plan.md` por parte de Carlos antes de iniciar implementación.
