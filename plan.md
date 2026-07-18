# Plan — Implementación del portafolio (pax217.github.io)

Estado: **Borrador para revisión — depende de la aprobación de `spec.md`**

Este plan asume que `spec.md` fue aprobado tal cual, o con los ajustes que resulten de resolver los gaps de la sección 7. Ningún paso de este plan se ejecuta hasta que Carlos apruebe ambos documentos.

Cada tarea es chica y verificable: tiene un criterio claro de "terminado" que se puede comprobar sin ambigüedad.

## Fase 0 — Resolver gaps de la spec (bloqueante)

- [ ] 0.1 Confirmar tagline del hero (texto final).
- [ ] 0.2 Confirmar si se incluyen bases de datos/motores en el stack técnico (cuáles, si aplica).
- [ ] 0.3 Confirmar certificaciones a incluir (si existen).
- [ ] 0.4 Confirmar idioma del sitio (español único vs. bilingüe).
- [ ] 0.5 Confirmar decisión de stack técnico del sitio (Astro recomendado vs. HTML/CSS/JS puro vs. otra).
- [ ] 0.6 Confirmar si hay métricas reales de logros para citar (o se mantiene todo cualitativo).

**Criterio de éxito de la fase:** `spec.md` actualizado sin secciones marcadas como "pendiente".

## Fase 1 — Setup del proyecto

- [ ] 1.1 Inicializar el proyecto con el stack elegido (ej. `npm create astro@latest` si es Astro, o estructura de carpetas simple si es HTML/CSS/JS puro).
  - Verificación: el proyecto corre localmente (`npm run dev` o abrir `index.html`) y muestra una página en blanco/placeholder sin errores en consola.
- [ ] 1.2 Configurar linting/formato básico (ej. Prettier) si el stack lo soporta.
  - Verificación: `npm run format` (o equivalente) corre sin errores sobre el proyecto inicial.
- [ ] 1.3 Configurar GitHub Actions (o config nativa de Pages) para build + deploy a `pax217.github.io` en push a `main`.
  - Verificación: push de un commit trivial (ej. cambio en README) dispara el workflow y el deploy termina en verde, aunque el sitio siga siendo un placeholder.
- [ ] 1.4 Confirmar que `https://pax217.github.io` sirve el placeholder tras el primer deploy.
  - Verificación: la URL pública carga el contenido esperado (no un 404 de GitHub Pages).

## Fase 2 — Estructura base y navegación

- [ ] 2.1 Crear el layout base (head con metadata/SEO básico, estructura semántica: header, main, footer).
  - Verificación: `view-source` muestra `<title>`, `<meta description>`, favicon enlazado.
- [ ] 2.2 Crear el esqueleto de las 6 secciones definidas en la spec (Hero, Sobre mí, Experiencia, Proyectos, Stack técnico, Educación, Contacto) con contenido placeholder.
  - Verificación: todas las secciones son visibles y accesibles por ancla (`#experiencia`, etc.) navegando desde un índice/nav simple.
- [ ] 2.3 Implementar estilos base mobile-first (tipografía, espaciado, grid/flex de layout) sin contenido final todavía.
  - Verificación: la página se ve correctamente estructurada en 3 anchos de viewport (375px, 768px, 1440px) sin overflow horizontal ni elementos rotos.

## Fase 3 — Contenido real por sección

Cada tarea reemplaza el placeholder de su sección con el contenido aprobado en `spec.md`.

- [ ] 3.1 Hero: nombre, título profesional, tagline final.
  - Verificación: coincide textualmente con lo aprobado en spec §3.2/0.1.
- [ ] 3.2 Sobre mí: resumen ejecutivo con enfoque en liderazgo.
  - Verificación: coincide con spec §3.3, sin mención de la empresa actual (regla de confidencialidad §2).
- [ ] 3.3 Experiencia laboral: las 3 posiciones del CV, respetando la regla de anonimización del rol más reciente.
  - Verificación: revisión manual confirmando que "OCC"/"Redarbor" no aparecen en ningún texto ni metadata del HTML renderizado (`grep -i "occ\|redarbor"` sobre el output final debe devolver 0 resultados).
- [ ] 3.4 Proyectos destacados: caso de estudio de Conekta (problema → solución → resultado) y, si se aprueba, el caso de Harmon Hall.
  - Verificación: cada caso de estudio sigue la estructura de 3 partes definida en la spec.
- [ ] 3.5 Stack técnico: categorías aprobadas (backend, APIs, mensajería, contenedores, cloud/CI-CD, testing, observabilidad, patrones, metodologías, IA).
  - Verificación: cada ítem del CV relevante aparece clasificado en exactamente una categoría, sin duplicados.
- [ ] 3.6 Educación: universidad, carrera, año, estatus.
  - Verificación: coincide con spec §3.7.
- [ ] 3.7 Contacto: email, LinkedIn, GitHub (sin teléfono), con protección básica anti-scraping en el email si aplica.
  - Verificación: los 3 links abren/apuntan a los destinos correctos (email compone un `mailto:` válido, LinkedIn y GitHub apuntan a las URLs confirmadas).

## Fase 4 — Calidad y no-funcionales

- [ ] 4.1 Auditoría de accesibilidad (Lighthouse o axe).
  - Verificación: score de Accessibility ≥ 95.
- [ ] 4.2 Auditoría de performance.
  - Verificación: score de Performance ≥ 95 en Lighthouse (móvil).
- [ ] 4.3 Revisión responsive final en los 3 breakpoints de la fase 2.
  - Verificación: sin overflow, sin texto cortado, botones/links con área táctil adecuada en móvil.
- [ ] 4.4 (Opcional / nice-to-have) Implementar modo oscuro/claro con toggle.
  - Verificación: el toggle cambia el tema y persiste la preferencia (ej. `localStorage`) entre recargas.
- [ ] 4.5 Revisión final de la regla de confidencialidad (§2 de la spec) sobre el sitio ya desplegado en producción, no solo en local.
  - Verificación: `curl -s https://pax217.github.io | grep -i "occ\|redarbor"` devuelve 0 resultados.

## Fase 5 — Lanzamiento

- [ ] 5.1 Revisión de contenido completa por Carlos (lectura de punta a punta del sitio desplegado).
  - Verificación: aprobación explícita.
- [ ] 5.2 Merge final a `main` / confirmación de que el deploy de producción refleja el último contenido aprobado.
  - Verificación: hash del último commit visible coincide con lo desplegado en `https://pax217.github.io`.

---

## Fuera de alcance de este plan

- Caso de estudio de AMP for Email (ver spec §3.5 y §7.5) — se retoma como iteración futura si se define su contenido.
- Selector de idioma / bilingüe, salvo que se resuelva en la Fase 0 como requerido desde el inicio.
- Formulario de contacto con backend.

**Siguiente paso:** Carlos revisa `spec.md` y este `plan.md`. Tras su aprobación (y resolución de la Fase 0), se inicia la Fase 1 de implementación.
