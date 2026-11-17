# Análisis de impacto de SC-001: Avisos de nuevas partidas y correcciones

**Sistema:** Podium  
**Autor del análisis (dueño del sistema):** Josué Tiburcio Cruz  
**Fecha:** 16 de noviembre de 2026  
**Referencia:** [sc-001-avisos-de-partidas.md](sc-001-avisos-de-partidas.md)  
**Estado de este análisis:** Propuesta para evaluación; no implica implementación ni aprobación automática.

## Solicitud que se analiza

Se analiza **SC-001: Avisos de nuevas partidas y correcciones dentro de Podium**, propuesta el **16 de noviembre de 2026** por **Marco Villegas**, con el papel de dupla de revisión en el escenario documentado. La petición busca que los integrantes de un grupo se enteren, desde la aplicación, de partidas registradas o corregidas, conservando la privacidad del grupo.


## Traducción a términos del sistema

Podium ya contempla **RF-006 Registrar partida**, **RF-016 Corregir partida registrada**, **RF-007 Consultar estadísticas** y **RF-014 Configurar privacidad**, con el **CU-01 Registrar una partida** y el **CU-04 Corregir una partida**. Su arquitectura está descrita en **ADR-001 Monolito modular**, con los módulos **Identidad y participantes**, **Grupos y contenido**, **Partidas** y **Estadísticas**.

La solicitud se traduce en una nueva capacidad, propuesta como **RF-019 Consultar avisos de actividad del grupo**, que se relaciona con los requisitos existentes. Se propone incorporarla a **Grupos y contenido**, sin crear por ahora un microservicio ni integrar mensajería externa. La solución utilizaría los eventos internos **`PartidaRegistrada`** y **`PartidaCorregida`**, ya contemplados como mecanismo del diseño para actualizar los módulos interesados.

La entidad propuesta **`Notificacion`** contendría como mínimo: identificador, tipo de evento, destinatario registrado, grupo, partida relacionada, fecha y estado de lectura. El backend identificaría a los integrantes autorizados del grupo en el momento del evento, excluiría a quien hizo la operación y conservaría un aviso por destinatario. Al consultarlo volvería a validar permisos para no revelar datos de grupos a los que una cuenta ya no tiene acceso. Los participantes invitados sin cuenta no recibirían avisos dentro de la aplicación.

El nuevo flujo no debe bloquear el registro de la partida ni el cálculo de las estadísticas si falla la creación de un aviso; ese caso debe registrarse y permitir su recuperación. Se trata de **una propuesta de diseño**, no de una implementación existente.

## Impacto directo

Son las modificaciones necesarias para que la funcionalidad solicitada exista.

| Artefacto | Unidad | Qué hay que cambiar |
|---|---|---|
| **Nuevo RF-019** y criterios de aceptación | 2 | Añadir el requisito de avisos para registros y correcciones, destinatarios autorizados, conservación de avisos y ausencia de avisos por operaciones fallidas. |
| **RF-006, RF-016 y RF-014** | 2 | Agregar referencias a RF-019 y precisar que la notificación ocurre tras una operación confirmada y respeta la privacidad del grupo. No alterar la validación original de la partida. |
| **CU-01 Registrar una partida** | 2 | Añadir al resultado posterior al guardado correcto la generación del evento que permite crear los avisos; no avisar en el flujo alterno de datos incompletos. |
| **CU-04 Corregir una partida** | 2 | Añadir avisos cuando la corrección se confirme; describir el resultado si falla el aviso sin revertir una corrección válida. |
| **Trazabilidad de requisitos y casos de uso** | 2 | Relacionar RF-019 con CU-01, CU-04 y la nueva capacidad de consulta de avisos. Decidir si se añade un caso de uso específico al catálogo al revisar su límite anterior de ocho. |
| **Diagrama de clases** | 4 | Incorporar `Notificacion` con su identificador, tipo, fecha y leído; asociarla con un usuario destinatario, un grupo y una partida, con multiplicidades en ambos extremos. |
| **Diagrama de secuencia** | 4 | Crear o actualizar el flujo de registro y corrección para mostrar el evento, la generación del aviso y su posterior consulta. Si no existe un diagrama previo, generar el correspondiente para documentar este cambio. |
| **C4 nivel 3: componentes** | 3 | Representar la responsabilidad de avisos en **Grupos y contenido** y su reacción a eventos de **Partidas**, sin inventar otro servicio desplegable. |
| **Interfaz y prototipo Figma** | 2/4 | Agregar una sección para consultar avisos, mostrar la partida o corrección asociada y un estado vacío si no existen novedades. |
| **Persistencia y pruebas de funcionalidad** | Diseño/implementación | Diseñar el almacenamiento de avisos, lectura por usuario, deduplicación y pruebas para los cinco criterios de aceptación de la solicitud. |

## Impacto indirecto

Se revisan también los artefactos que pueden quedar inconsistentes como consecuencia del cambio. **Sin impacto** significa que se revisó y no necesita modificarse; no se dejan renglones vacíos.

| Artefacto | Unidad | Por qué se ve afectado / resultado de la revisión |
|---|---|---|
| **ADR-001 — Monolito modular** | 3 | **Sin cambio de decisión.** Los avisos pueden incorporarse a un módulo existente y aprovechar eventos internos. Conviene añadir una referencia a RF-019 como consecuencia documentada, sin reemplazar el ADR. |
| **C4 nivel 1: contexto** | 3 | **Sin impacto.** Siguen existiendo los mismos actores y no aparece un sistema externo; los avisos son internos. |
| **C4 nivel 2: contenedores** | 3 | **Sin impacto en contenedores.** Se mantienen aplicación web, API única, base de datos y almacenamiento de fotografías. No se crea un contenedor nuevo. |
| **Máquina de estados de Partida** | 4 | **Sin impacto en el ciclo de vida de Partida.** Se notifica después de guardar; el aviso no cambia los estados de una partida. Si se modela el estado leído/no leído de Notificacion, sería un diagrama adicional, no una alteración del de Partida. |
| **RNF-PRI-001 Privacidad** | 2 | Requiere pruebas adicionales: nadie ajeno al grupo puede ver sus avisos; la autorización debe revisarse al consultar, incluso después de abandonar el grupo. |
| **RNF-SEG-001 Seguridad** | 2 | Revisar que un usuario no pueda consultar, marcar como leído o manipular avisos ajenos mediante identificadores. |
| **RNF-REN-001 Rendimiento** | 2 | Verificar que cargar los avisos no incumpla la meta de **3 segundos** de las pantallas principales ni retrase el registro de partidas. |
| **RNF-CON-001 Consistencia** | 2 | Estadísticas e historial deben seguir coincidiendo con partidas válidas, aun si falla temporalmente la creación del aviso. |
| **RF-007 Estadísticas** | 2 | **Sin cambio funcional.** Debe continuar reaccionando a `PartidaRegistrada` y `PartidaCorregida` de manera independiente del nuevo consumidor. |
| **Pruebas de regresión** | 2/4 | Repetir pruebas de registro, corrección, invitados, empates, grupos privados y estadísticas para detectar efectos secundarios. |

## Lo que queda sin tocar

- **RF-015 Registrar participante invitado:** los invitados siguen pudiendo aparecer en una partida sin cuenta. Por definición no reciben avisos internos destinados a cuentas activas.
- **RF-017 Registrar empate:** las reglas de puntuación, empate y validación de resultados no cambian.
- **RF-003 y RF-004 Crear/unirse a grupos:** las reglas de membresía permanecen; se **consultan** para decidir quién puede ver cada aviso.
- **RF-012 Consultar información de grupo:** sigue mostrando la información e historial actual sin cambios en su definición central.
- **Fotografías y almacenamiento de objetos:** no se requiere modificar archivos, permisos de fotografías ni añadir contenido multimedia a los avisos.
- **Integraciones externas:** no se añade WhatsApp, correo, notificaciones push de terceros ni una pasarela de pagos.
- **Despliegue del backend:** sigue siendo una sola unidad, conforme a ADR-001.

## Riesgos

| Riesgo | Probabilidad estimada | Consecuencia | Medida de control |
|---|---|---|---|
| Avisos visibles a personas fuera del grupo o que ya salieron | Media | Exposición de actividad privada | Validar pertenencia en la generación y nuevamente al consultar; pruebas de acceso negativo. |
| Avisos duplicados por reintentos o eventos repetidos | Media | Confusión y pérdida de confianza | Identificador único del evento y combinación destinatario-evento; pruebas de idempotencia. |
| Retraso en el guardado de partidas si falla el módulo de avisos | Media | Incumplimiento del flujo principal | Desacoplar la creación del aviso del resultado funcional del registro; registrar y reintentar cuando proceda. |
| Muchos avisos en grupos activos | Baja inicialmente | Saturación visual y consultas lentas | Paginación, orden por fecha y medición del tiempo de respuesta. |
| No realizar el cambio | Baja | Los usuarios deberán revisar manualmente cada grupo para saber si hubo novedades | Mantener el historial y estadísticas consultables; reevaluar la prioridad si aumenta el uso. |

Las probabilidades son juicios iniciales, no mediciones obtenidas en producción, ya que Podium continúa en etapa de diseño.

## Alternativas consideradas

1. **Opción A — Avisos internos dentro del monolito modular (recomendada).** Añadir la entidad y consulta de avisos a **Grupos y contenido**, utilizando los eventos que publica **Partidas**. Aprovecha la API y la base de datos previstas, evita servicios externos y permite pruebas de privacidad con menor esfuerzo. Su costo es mantener esa nueva responsabilidad y un mecanismo de entrega confiable dentro del backend. **Estimación incremental:** unas **38 horas** bajo los supuestos que se indican abajo.
2. **Opción B — Servicio de notificaciones externas o un módulo independiente desplegable.** Separar el procesamiento de avisos y eventualmente enviarlos mediante un proveedor de correo o push. Facilita escalar el canal por separado y podría notificar fuera de la aplicación, pero añade credenciales, contratos con terceros, control de fallos, despliegue y monitoreo. Supera el alcance de la solicitud y obliga a revisar el C4 de contenedores y probablemente el ADR. **Estimación preliminar:** **55 a 75 horas incrementales**, sujeta a proveedor y requisitos todavía no definidos.

**Preferencia:** Opción A, porque responde al pedido sin comprometer la elección anterior de monolito modular ni introducir dependencias externas innecesarias.

## Estimación de esfuerzo

La estimación corresponde **únicamente al cambio adicional** sobre una versión de Podium que ya dispone de autenticación, membresías de grupos, registro/corrección de partidas y publicación confiable de eventos internos. No representa una promesa de implementación ni el tiempo necesario para desarrollar Podium desde cero.

| Concepto | Esfuerzo estimado |
|---|---:|
| Cambios de diseño y documentación (RF, casos de uso, clases, secuencia, C4 componentes y Figma) | **6 horas** |
| Implementación (modelo/persistencia de avisos, escucha de eventos, autorización y consulta en interfaz) | **22 horas** |
| Pruebas (criterios de aceptación, privacidad, reintentos, rendimiento básico y regresión) | **10 horas** |
| **Total incremental, opción A** | **38 horas** |

**De dónde sale este número.** Se comparó el trabajo con una función pequeña de seguimiento de registros dentro de los módulos ya proyectados: definición del dato, creación tras dos eventos existentes, consulta por usuario y validación de permisos. La estimación supone **una sola persona desarrollando**, sin diseño de notificaciones push y con la infraestructura principal ya operativa. Incluye mayor esfuerzo de pruebas por los riesgos de privacidad y duplicados. La incertidumbre es significativa: un rango razonable para planificación inicial sería **30 a 52 horas**.

**Qué no se incluyó.** Construcción inicial de autenticación, grupos, API, base de datos, interfaz completa o infraestructura si todavía no existen; servicio externo de mensajería; aplicaciones móviles nativas; auditoría de seguridad profesional; mantenimiento posterior a producción. Si el backend base o el sistema de eventos todavía no están implementados, estas dependencias deben presupuestarse por separado antes de comprometer una fecha.

## Recomendación

**Aceptar con prioridad media la Opción A**, condicionada a que las funciones principales de registro, corrección y privacidad ya estén estabilizadas. La mejora ayuda a que los integrantes sigan la actividad sin consultar manualmente cada grupo, y puede incorporarse manteniendo el **monolito modular**.

No recomiendo empezar por la Opción B porque no hay una necesidad demostrada de notificaciones fuera de la aplicación ni de un despliegue independiente. Antes de implementar se debe validar con el solicitante el alcance exacto de los avisos y confirmar los supuestos utilizados para estimar el esfuerzo.

**Decisión final pendiente:** el estado de **SC-001** sigue siendo *Propuesta* hasta que el responsable del proyecto documente formalmente su aceptación, rechazo o aplazamiento y el motivo. El presente texto es una **recomendación técnica**, no una decisión ejecutada.
