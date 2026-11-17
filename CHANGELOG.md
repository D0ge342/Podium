# Historial de cambios — Podium

**Proyecto:** Podium · Ingeniería de Software I (SIS3407)  
**Tipo de registro:** evolución de la documentación y del diseño del sistema.  
**Última actualización de este historial:** 16 de noviembre de 2026.

Este archivo resume los cambios relevantes realizados durante el semestre, así como las razones que llevaron a ajustar el proyecto. **Podium se encuentra documentado como una propuesta de análisis y diseño**: las decisiones descritas no implican que la aplicación ya esté implementada.

> **Sobre las fechas:** las entradas de septiembre y octubre proceden de las fechas indicadas en los documentos. Los ajustes del 16 de noviembre corresponden a la revisión reciente del repositorio y sus documentos. Este registro no sustituye el historial de commits de GitHub; las fechas exactas de publicación se consultan en la pestaña **History** de GitHub Desktop.

## 16 de noviembre de 2026 — Revisión final de documentación y diseño

### Unidad 4 · Consistencia de diagramas

- Se revisó [`doc/arch/diagramas-unidad4.md`](doc/arch/diagramas-unidad4.md), que contiene los diagramas de **clases, secuencia, estados y actividad** del caso de uso **CU-01 — Registrar una partida**.
- Se incorporó `ServicioPartidas` como coordinador del registro, y se distinguieron las responsabilidades de `RepositorioPartidas` y `BusEventos`.
- Se alinearon las operaciones de las clases con los mensajes del diagrama de secuencia, se ajustaron las activaciones y se definió `EstadoPartida` como enumeración.
- Se retiró la anulación de partidas **ya guardadas**, por no estar respaldada por un requisito funcional explícito.
- **Motivo:** mantener la coherencia entre requisitos, comportamiento, clases y arquitectura. La visualización de los diagramas Mermaid en GitHub fue revisada por el responsable del proyecto.

### Unidad 5 · Solicitud de cambio y análisis de impacto

- Se documentó la [**SC-001 — Avisos de nuevas partidas y correcciones**](doc/cambios/sc-001-avisos-de-partidas.md), presentada como una **propuesta** de mejora.
- Se elaboró el [**AI-001 — Análisis de impacto**](doc/cambios/ai-001-avisos-de-partidas.md) para identificar efectos sobre requisitos, casos de uso, diagramas, privacidad, pruebas y módulos.
- El análisis estimó **38 horas adicionales** bajo los supuestos indicados en el propio documento y recomendó aceptar la alternativa de avisos **dentro de la aplicación**, con prioridad media y condicionada a estabilizar las funciones principales.
- **Motivo:** evaluar el costo técnico de evolucionar Podium antes de aprobar o implementar el cambio. **SC-001 continúa en estado «Propuesta»**; la recomendación no es una aceptación formal.

### Organización y consistencia documental

- Se reorganizó el repositorio: los requisitos y la elicitación quedaron en `docs/`, los documentos de arquitectura y UML en `doc/arch/`, y los de mantenimiento en `doc/cambios/`.
- Se normalizaron nombres de archivos y se actualizaron los enlaces del [`README.md`](README.md).
- Se corrigió la discrepancia entre [`guion-entrevista.md`](docs/guion-entrevista.md) y [`bitacora-entrevista.md`](docs/bitacora-entrevista.md): ambos describen reuniones **cada una o dos semanas**, según la disponibilidad del grupo.
- **Motivo:** mejorar la navegación del repositorio y evitar contradicciones en la evidencia de la entrevista.

## 29 de octubre de 2026 — Unidad 3: arquitectura

- Se documentaron los [diagramas C4 de contexto, contenedores y componentes](doc/arch/diagramas.md).
- Se registró el [**ADR-001 — Elegir monolito modular**](doc/arch/adr-001-monolito-modular.md), con contexto, alternativas, decisión, consecuencias y criterios para reconsiderarla.
- Se delimitaron cuatro módulos: **Identidad y participantes**, **Grupos y contenido**, **Partidas** y **Estadísticas**.
- **Motivo:** separar responsabilidades del sistema sin asumir el costo operativo de microservicios para un proyecto académico desarrollado inicialmente por una persona.

## 1 de octubre de 2026 — Unidad 2: trazabilidad

- Se completó la correspondencia entre **requisitos funcionales, casos de uso y pantallas o evidencias del prototipo** en la [especificación de requisitos](docs/especificacion-requisitos.md).
- **Motivo:** demostrar de dónde surge cada comportamiento y reconocer las partes del prototipo que aún no están representadas.

## 30 de septiembre de 2026 — Revisión de la dupla

- Se registraron observaciones sobre invitados sin cuenta, prioridad del feed, corrección de resultados y flujos alternos de **CU-01**.
- Se documentaron las respuestas a esas observaciones en la [sección de revisión de la dupla](docs/especificacion-requisitos.md#revisión-de-la-dupla).
- **Motivo:** comprobar y mejorar la especificación a partir de una revisión externa registrada en el documento.

## 29 de septiembre de 2026 — Casos de uso

- Se documentaron **ocho casos de uso** y se desarrolló **CU-01 — Registrar una partida**, con escenario principal y alternativas de invitado, empate y datos incompletos.
- **Motivo:** describir el comportamiento principal de Podium y sus excepciones reales.

## 28 de septiembre de 2026 — Ajustes después de la entrevista

- Se ajustaron prioridades: el **historial, los grupos y las estadísticas** se consideraron más importantes que el feed y la agenda de partidas.
- Se incorporaron **RF-015 (participante invitado), RF-016 (corrección de partida), RF-017 (empate)** y **RF-018 (moderación de contenido reportado)**.
- **Motivo:** reflejar las necesidades y excepciones identificadas durante la elicitación.

## 22 de septiembre de 2026 — Primera especificación

- Se creó la primera versión de [`docs/especificacion-requisitos.md`](docs/especificacion-requisitos.md).
- **Motivo:** documentar formalmente los requisitos, el alcance y las condiciones de calidad del sistema.

## Artefactos existentes sin fecha de creación verificada

También forman parte del proyecto la [visión del producto](docs/vision-del-producto.md), el [guion de entrevista](docs/guion-entrevista.md), la [bitácora](docs/bitacora-entrevista.md), el [diagrama editable de casos de uso](docs/diagramas/casos-de-uso.drawio), su [imagen](docs/diagramas/casos-de-uso.png) y el prototipo de Figma enlazado en el [`README.md`](README.md). **No se asigna una fecha de creación exacta a estos artefactos** porque los archivos examinados no permiten comprobarla por sí solos.

---

**Criterio de mantenimiento:** al realizar un cambio futuro, agregar una entrada con **fecha, documento afectado, modificación y motivo**. Si se implementa la SC-001, registrar por separado la fecha de aprobación y la de implementación; no confundir una propuesta de diseño con una función terminada.
