# Especificación de requisitos

**Sistema:** Podium  
**Autor:** Josué Tiburcio Cruz 
**Versión:** 1.0  
**Fecha de la última actualización:** 19 de septiembre de 2026

---

## 1. Propósito y alcance

**Propósito del documento:**

Este documento tiene como propósito definir los requisitos funcionales y no funcionales de Podium, estableciendo de manera clara qué debe hacer el sistema, qué características de calidad debe cumplir y cuáles son los límites de su primera versión.

La especificación está dirigida al equipo encargado del análisis, diseño, desarrollo y pruebas del sistema, y servirá como referencia para validar posteriormente que el producto desarrollado cumpla con las necesidades identificadas.

**Alcance del sistema:**

Podium será una red social enfocada en personas que juegan juegos de mesa. Permitirá a los usuarios crear un perfil, agregar amigos, pertenecer a grupos, registrar partidas, conservar fotografías y recuerdos de las sesiones de juego, consultar estadísticas generales y por juego, y visualizar publicaciones relacionadas con sus amigos y grupos.

El sistema también permitirá crear grupos, unirse a grupos mediante invitación o código, buscar grupos públicos, consultar actividad dentro de estos y visualizar estadísticas generadas a partir de las partidas registradas.

**Fuera del alcance:**

- Compra, venta o renta de juegos de mesa dentro de Podium.
- Sistema de chat o mensajería privada en tiempo real entre usuarios.
- Organización de torneos profesionales con premios, pagos, inscripciones o llaves de eliminación.
- Transmisión de partidas mediante video o streaming en tiempo real.
- Recomendaciones automáticas mediante inteligencia artificial.

---

## 2. Usuarios y su contexto

| Usuario | Qué hace hoy sin el sistema | Qué espera del sistema |
|---|---|---|
| **Usuario general** | Recuerda los resultados de manera informal o utiliza notas, fotografías o archivos como Excel para registrar partidas y victorias. | Registrar sus partidas, conservar fotografías y recuerdos, consultar su historial y visualizar estadísticas generales y por juego. |
| **Administrador de grupo** | Organiza sus grupos mediante aplicaciones de mensajería y lleva los resultados de forma manual o separada. | Crear y administrar grupos, controlar quién pertenece a ellos y consultar la actividad y estadísticas del grupo. |
| **Usuario que busca jugadores o grupos** | Encuentra nuevos jugadores principalmente mediante conocidos, redes sociales generales o invitaciones externas. | Buscar usuarios, agregar amigos, encontrar grupos públicos y unirse a comunidades relacionadas con juegos de mesa. |

**Conflictos identificados entre usuarios:**

Un usuario puede querer compartir una partida, fotografía o resultado con todos sus amigos, mientras que otro participante de la misma partida puede preferir que su información no sea visible fuera del grupo.

Por esta razón, el sistema deberá respetar la privacidad de los usuarios y la visibilidad definida para el grupo o publicación correspondiente.

---

## 3. Requisitos funcionales

### 3.1 Resumen

| ID | Nombre | Prioridad | Origen |
|---|---|---|---|
| RF-001 | Gestión del perfil | Imprescindible | Visión del producto |
| RF-002 | Gestión de amistades | Imprescindible | Visión del producto |
| RF-003 | Creación de grupos | Imprescindible | Visión del producto |
| RF-004 | Unión a grupos | Imprescindible | Visión del producto |
| RF-005 | Búsqueda de grupos públicos | Importante | Prototipo actual |
| RF-006 | Registro de partidas | Imprescindible | Visión del producto |
| RF-007 | Consulta de estadísticas | Imprescindible | Visión del producto |
| RF-008 | Visualización del feed | Imprescindible | Prototipo actual |
| RF-009 | Reacciones a publicaciones | Importante | Prototipo actual |
| RF-010 | Comentarios en publicaciones | Importante | Prototipo actual |

### 3.2 Fichas

#### RF-001 · Gestión del perfil

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite al usuario crear y consultar un perfil con fotografía, nombre, nombre de usuario, descripción e información básica. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al guardar un perfil con los datos obligatorios completos, la información actualizada aparece en la pantalla de perfil del usuario. |
| **Relacionado con** | RF-002, RF-007, RNF-SEG-001 |

#### RF-002 · Gestión de amistades

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite buscar otros usuarios y enviar, aceptar o rechazar solicitudes de amistad. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al enviar una solicitud de amistad, el usuario receptor puede visualizarla y aceptar o rechazarla. Si la acepta, ambos usuarios aparecen como amigos. |
| **Relacionado con** | RF-001, RF-008, RNF-PRI-001 |

#### RF-003 · Creación de grupos

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite a un usuario crear un grupo y establecer su nombre, descripción y nivel de privacidad. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al proporcionar los datos obligatorios y confirmar la creación, el grupo aparece dentro de los grupos del usuario creador. |
| **Relacionado con** | RF-004, RF-005, RNF-SEG-001 |

#### RF-004 · Unión a grupos

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite a un usuario unirse a un grupo cuando cumple con las condiciones de acceso establecidas para dicho grupo. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Cuando el usuario utiliza un código válido o una invitación autorizada, el grupo aparece dentro de sus grupos y puede consultar su contenido permitido. |
| **Relacionado con** | RF-003, RF-005, RNF-SEG-001 |

#### RF-005 · Búsqueda de grupos públicos

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite buscar y consultar grupos configurados como públicos. |
| **Origen** | Prototipo actual. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al realizar una búsqueda utilizando el nombre de un grupo público existente, el sistema lo muestra entre los resultados. |
| **Relacionado con** | RF-003, RF-004 |

#### RF-006 · Registro de partidas

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite registrar una partida indicando el juego, los participantes, los resultados, la fecha y el contenido adicional asociado a la partida. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Cuando se proporciona el juego, los participantes y un resultado válido, la partida queda registrada y puede consultarse posteriormente en el historial correspondiente. Si faltan datos obligatorios, el sistema no permite finalizar el registro. |
| **Relacionado con** | RF-007, RF-008, RNF-CON-001 |

#### RF-007 · Consulta de estadísticas

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema calcula y muestra estadísticas del usuario utilizando las partidas registradas, incluyendo partidas jugadas, victorias y estadísticas específicas por juego. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Después de registrar una partida finalizada, las estadísticas de los participantes reflejan el nuevo resultado sin que el usuario tenga que modificar manualmente sus valores. |
| **Relacionado con** | RF-006, RNF-CON-001, RNF-REN-001 |

#### RF-008 · Visualización del feed

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema muestra al usuario un feed con publicaciones y partidas correspondientes a sus amigos y grupos autorizados. |
| **Origen** | Prototipo actual. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al ingresar a Inicio, el usuario puede visualizar publicaciones correspondientes a usuarios o grupos para los que tiene permiso de visualización. |
| **Relacionado con** | RF-002, RF-006, RF-009, RF-010, RNF-PRI-001 |

#### RF-009 · Reacciones a publicaciones

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite a los usuarios reaccionar a publicaciones visibles para ellos. |
| **Origen** | Prototipo actual. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al reaccionar a una publicación, la reacción queda asociada al usuario y se actualiza el conteo mostrado en la publicación. |
| **Relacionado con** | RF-008 |

#### RF-010 · Comentarios en publicaciones

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permite a los usuarios agregar comentarios a publicaciones para las que tengan permiso de visualización. |
| **Origen** | Prototipo actual. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al publicar un comentario válido, este aparece asociado a la publicación y al usuario que lo realizó. |
| **Relacionado con** | RF-008, RNF-SEG-001 |

---

## 4. Requisitos no funcionales

### 4.1 Resumen

| ID | Atributo | Nombre | Prioridad | Origen |
|---|---|---|---|---|
| RNF-REN-001 | Rendimiento | Tiempo de carga de pantallas principales | Importante | Derivado del tipo de sistema |
| RNF-SEG-001 | Seguridad | Control de acceso a información | Imprescindible | Derivado del tipo de sistema |
| RNF-USA-001 | Usabilidad | Facilidad para registrar partidas | Imprescindible | Visión del producto |
| RNF-PRI-001 | Privacidad | Visibilidad del contenido | Imprescindible | Conflicto entre usuarios |
| RNF-CON-001 | Consistencia | Coherencia de estadísticas | Imprescindible | Reglas de negocio |

### 4.2 Fichas

#### RNF-REN-001 · Tiempo de carga de pantallas principales

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Rendimiento |
| **Descripción** | Las pantallas principales de Inicio, Grupos, Descubrir y Perfil deben desplegar su contenido en un tiempo máximo de tres segundos bajo condiciones normales de operación. |
| **Métrica** | Tiempo transcurrido desde que el usuario solicita la pantalla hasta que se muestra su contenido principal: máximo 3 segundos. |
| **Origen** | Derivado del tipo de sistema Web y SaaS. |
| **Prioridad** | Importante |
| **Por qué importa** | Podium depende de una navegación frecuente entre diferentes secciones. Una respuesta lenta afecta directamente la experiencia de uso. |
| **Afecta a** | RF-001, RF-005, RF-007, RF-008 |

#### RNF-SEG-001 · Control de acceso a información

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Seguridad |
| **Descripción** | El sistema solo debe permitir que un usuario consulte o modifique información para la cual posee autorización. |
| **Métrica** | En las pruebas de autorización, el 100 % de los intentos realizados con usuarios sin permiso deben ser rechazados. |
| **Origen** | Derivado del tipo de sistema y de la existencia de cuentas y grupos privados. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | El sistema almacena perfiles, fotografías, grupos y publicaciones pertenecientes a diferentes usuarios. |
| **Afecta a** | RF-001, RF-003, RF-004, RF-010 |

#### RNF-USA-001 · Facilidad para registrar partidas

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Usabilidad |
| **Descripción** | Un usuario familiarizado con las funciones básicas de Podium debe poder registrar una partida sin asistencia externa. |
| **Métrica** | Al menos 4 de cada 5 usuarios de prueba deben completar correctamente el registro de una partida en su primer intento sin recibir instrucciones adicionales. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Registrar partidas es una de las funciones principales de Podium. Si resulta complicado, los usuarios pueden dejar de utilizar esta función. |
| **Afecta a** | RF-006 |

#### RNF-PRI-001 · Visibilidad del contenido

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Privacidad |
| **Descripción** | El contenido perteneciente a grupos privados solo debe ser visible para los integrantes autorizados de dichos grupos. |
| **Métrica** | En las pruebas de privacidad, el 100 % de los usuarios externos al grupo deben ser incapaces de visualizar publicaciones definidas como privadas. |
| **Origen** | Conflicto identificado entre usuarios. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Una partida puede contener nombres, fotografías y resultados de varios participantes que no necesariamente desean hacer pública esa información. |
| **Afecta a** | RF-002, RF-004, RF-008 |

#### RNF-CON-001 · Coherencia de estadísticas

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Consistencia |
| **Descripción** | Las estadísticas mostradas deben corresponder con los resultados almacenados de las partidas finalizadas. |
| **Métrica** | En una muestra de 100 partidas registradas, el 100 % de las estadísticas recalculadas debe coincidir con los resultados almacenados. |
| **Origen** | Regla de negocio de actualización automática de estadísticas. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Una misma partida modifica la información de varios participantes. Una inconsistencia afectaría la confiabilidad de las estadísticas mostradas. |
| **Afecta a** | RF-006, RF-007 |

---

## 5. Casos de uso


---

## 6. Trazabilidad

## 7. Registro de cambios

| Fecha | Requisito | Qué cambió | Por qué |
|---|---|---|---|
| 22/09/2026 | Documento inicial | Se creó la primera versión de la especificación de requisitos de Podium. | Inicio formal de la especificación del sistema. |

---

## Antes de entregar

- [x] Todos los requisitos tienen identificador único y ninguno está repetido
- [x] Cada requisito expresa una sola idea
- [x] Cada requisito funcional tiene criterio de aceptación comprobable
- [x] Cada requisito no funcional tiene una métrica, no solo un adjetivo
- [x] El campo Origen distingue lo confirmado de lo que todavía debe validarse
- [x] Hay al menos un requisito no funcional por cada atributo de calidad identificado
- [x] Ningún requisito impone una solución técnica específica
- [ ] Todos los requisitos caben dentro del alcance declarado
- [ ] La tabla de trazabilidad está completa
- [ ] Mi dupla revisó el documento y su revisión está registrada
- [x] Se eliminaron los ejemplos e instrucciones de la plantilla
