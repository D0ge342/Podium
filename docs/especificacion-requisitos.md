
## 1. Propósito y alcance

**Propósito del documento:**

Este documento define los requisitos funcionales y no funcionales de Podium, estableciendo qué debe hacer el sistema, qué características de calidad debe cumplir y cuáles son los límites de su primera versión.

La especificación está dirigida al análisis, diseño, desarrollo y pruebas del sistema, y servirá como referencia para comprobar que el producto responde a las necesidades identificadas.

**Alcance del sistema:**

Podium será una red social enfocada en personas que juegan juegos de mesa. Permitirá a los usuarios mantener un perfil, buscar y agregar amigos, pertenecer a grupos, registrar partidas, conservar fotografías y recuerdos, consultar estadísticas generales y por juego, y visualizar contenido relacionado con sus amigos y grupos.

El sistema también permitirá crear grupos, unirse a grupos mediante invitación o código, buscar grupos públicos, consultar información y actividad de cada grupo y visualizar estadísticas generadas a partir de las partidas registradas.

La entrevista confirmó que el valor principal de Podium está en centralizar el historial de partidas, facilitar la consulta de resultados antiguos y generar estadísticas automáticamente. También se identificó la necesidad de contemplar participantes invitados sin cuenta, empates y correcciones posteriores de resultados.

**Fuera del alcance:**

- Compra, venta o renta de juegos de mesa dentro de Podium.
- Sistema de chat o mensajería privada en tiempo real entre usuarios.
- Organización de torneos profesionales con premios, pagos, inscripciones o llaves de eliminación.
- Transmisión de partidas mediante video o streaming en tiempo real.
- Recomendaciones automáticas mediante inteligencia artificial.
- Sustituir las aplicaciones de mensajería utilizadas para coordinar reuniones.

---

## 2. Usuarios y su contexto

| Usuario / rol | Qué hace hoy sin el sistema | Qué espera del sistema |
|---|---|---|
| **Usuario** | Registra resultados mediante mensajes, fotografías o archivos separados y debe buscar manualmente partidas antiguas. | Registrar partidas, consultar historial y estadísticas, conservar recuerdos y participar en grupos. |
| **Administrador de grupo** | Organiza integrantes y resultados mediante aplicaciones externas. | Administrar su grupo, integrantes, partidas y actividad. |
| **Participante invitado** | Puede participar ocasionalmente sin pertenecer al grupo habitual ni tener cuenta. | Aparecer correctamente en una partida sin crear una cuenta. |
| **Administrador de Podium** | No existe una figura equivalente en el proceso actual. | Revisar contenido reportado y tomar acciones de moderación cuando incumpla las reglas de la plataforma. |

**Conflictos identificados:**

Un usuario puede querer compartir una partida, fotografía o resultado, mientras que otro participante puede preferir que su información permanezca dentro del grupo. Por ello, el sistema deberá respetar la configuración de privacidad correspondiente.

**Hallazgos relevantes de la entrevista:**

- Los resultados pueden almacenarse en un grupo de WhatsApp, pero consultarlos posteriormente es poco práctico.
- Las estadísticas automáticas tienen mayor valor que un feed social.
- Las fotografías no deberían hacerse públicas automáticamente.
- Un invitado ocasional no debería estar obligado a crear una cuenta.
- Una partida puede terminar en empate o requerir una corrección posterior.
- Agendar próximas partidas tiene menor prioridad porque la coordinación ya se resuelve mediante WhatsApp.

---

## 3. Requisitos funcionales

### 3.1 Resumen

| ID | Nombre | Prioridad | Origen |
|---|---|---|---|
| RF-001 | Actualizar perfil | Imprescindible | Visión del producto |
| RF-002 | Gestionar solicitudes de amistad | Importante | Visión del producto |
| RF-003 | Crear grupo | Imprescindible | Entrevista — confirmado |
| RF-004 | Unirse a grupo | Imprescindible | Entrevista — confirmado |
| RF-005 | Buscar grupos públicos | Importante | Prototipo actual |
| RF-006 | Registrar partida | Imprescindible | Entrevista — confirmado y ampliado |
| RF-007 | Consultar estadísticas | Imprescindible | Entrevista — confirmado |
| RF-008 | Consultar feed | Importante | Entrevista — menor prioridad |
| RF-009 | Reaccionar a publicación | Deseable | Prototipo actual |
| RF-010 | Comentar publicación | Deseable | Prototipo actual |
| RF-011 | Buscar usuarios | Importante | Visión del producto |
| RF-012 | Consultar información de grupo | Imprescindible | Entrevista — confirmado |
| RF-013 | Agendar partida de grupo | Deseable | Entrevista — menor prioridad |
| RF-014 | Configurar privacidad del perfil y contenido | Importante | Entrevista — confirmado parcialmente |
| RF-015 | Registrar participante invitado | Imprescindible | Entrevista — nuevo hallazgo |
| RF-016 | Corregir partida registrada | Imprescindible | Entrevista — nuevo hallazgo |
| RF-017 | Registrar empate | Imprescindible | Entrevista — nuevo hallazgo |
| RF-018 | Moderar contenido reportado | Importante | Necesidad de moderación del sistema social |

### 3.2 Fichas

#### RF-001 · Actualizar perfil

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir al usuario modificar la fotografía, nombre, nombre de usuario, descripción e información básica de su perfil. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al modificar un dato con un valor válido y guardar los cambios, el sistema muestra el nuevo valor en el perfil. Si un dato obligatorio es inválido, el sistema no guarda el cambio y señala el campo correspondiente. |
| **Relacionado con** | RF-011, RF-014, RNF-SEG-001, RNF-PRI-001 |

#### RF-002 · Gestionar solicitudes de amistad

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir enviar, aceptar o rechazar solicitudes de amistad entre usuarios registrados. |
| **Origen** | Visión del producto. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al enviar una solicitud a otro usuario, el receptor puede verla y aceptarla o rechazarla. Si la acepta, ambos usuarios aparecen como amigos. |
| **Relacionado con** | RF-008, RF-011, RNF-PRI-001 |

#### RF-003 · Crear grupo

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir a un usuario crear un grupo indicando al menos un nombre y su nivel de privacidad. |
| **Origen** | Entrevista — confirmado. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al proporcionar los datos obligatorios y confirmar la creación, el grupo aparece entre los grupos del usuario creador y este queda registrado como administrador. |
| **Relacionado con** | RF-004, RF-005, RF-012, RNF-SEG-001 |

#### RF-004 · Unirse a grupo

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir a un usuario unirse a un grupo cuando cumpla con las condiciones de acceso definidas para ese grupo. |
| **Origen** | Entrevista — confirmado. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al utilizar un código válido, una invitación autorizada o el mecanismo permitido por un grupo público, el grupo aparece entre los grupos del usuario. |
| **Relacionado con** | RF-003, RF-005, RF-012, RNF-SEG-001 |

#### RF-005 · Buscar grupos públicos

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir buscar y consultar grupos configurados como públicos. |
| **Origen** | Prototipo actual. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al realizar una búsqueda con el nombre total o parcial de un grupo público existente, el sistema lo incluye entre los resultados. |
| **Relacionado con** | RF-003, RF-004, RF-012 |

#### RF-006 · Registrar partida

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir registrar una partida indicando juego, participantes, fecha y resultado. El registro deberá contemplar participantes invitados y empates cuando corresponda. |
| **Origen** | Entrevista — confirmado y ampliado. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al proporcionar un juego, una fecha, al menos dos participantes y un resultado válido, el sistema guarda la partida. Si falta un dato obligatorio, no finaliza el registro e indica qué información falta. |
| **Relacionado con** | RF-007, RF-012, RF-015, RF-016, RF-017, RNF-USA-001, RNF-CON-001 |

#### RF-007 · Consultar estadísticas

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá calcular y mostrar estadísticas a partir de las partidas registradas, incluyendo partidas jugadas, victorias, porcentaje de victorias y, cuando aplique, puntos y promedio de puntos. |
| **Origen** | Entrevista — confirmado. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Después de registrar o corregir una partida contabilizable, las estadísticas relacionadas reflejan el resultado sin modificación manual de los valores calculados. |
| **Relacionado con** | RF-006, RF-012, RF-016, RF-017, RNF-CON-001, RNF-REN-001 |

#### RF-008 · Consultar feed

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá mostrar al usuario un feed con publicaciones y partidas para las que tenga permiso de visualización. |
| **Origen** | Entrevista — función útil, pero secundaria frente a grupos, historial y estadísticas. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al ingresar a Inicio, el usuario visualiza el contenido disponible para su cuenta. Si no existe contenido, el sistema muestra un estado vacío. |
| **Relacionado con** | RF-002, RF-006, RF-009, RF-010, RNF-PRI-001, RNF-REN-001 |

#### RF-009 · Reaccionar a publicación

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir que un usuario registre una reacción en una publicación que puede visualizar. |
| **Origen** | Prototipo actual. |
| **Prioridad** | Deseable |
| **Criterio de aceptación** | Al seleccionar una reacción disponible, esta queda asociada al usuario y la publicación refleja el cambio. |
| **Relacionado con** | RF-008, RNF-SEG-001 |

#### RF-010 · Comentar publicación

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir que un usuario agregue un comentario a una publicación que puede visualizar. |
| **Origen** | Prototipo actual. |
| **Prioridad** | Deseable |
| **Criterio de aceptación** | Al enviar un comentario con contenido válido, este aparece asociado a la publicación y al usuario. |
| **Relacionado con** | RF-008, RF-018, RNF-SEG-001 |

#### RF-011 · Buscar usuarios

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir buscar usuarios registrados mediante su nombre o nombre de usuario. |
| **Origen** | Visión del producto. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al introducir un nombre o nombre de usuario que coincida total o parcialmente con una cuenta existente, el sistema muestra la cuenta entre los resultados. |
| **Relacionado con** | RF-001, RF-002 |

#### RF-012 · Consultar información de grupo

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir a un miembro autorizado consultar la información de un grupo, sus integrantes, partidas, juegos y estadísticas disponibles. |
| **Origen** | Entrevista — confirmado. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al abrir un grupo al que tiene acceso, el usuario puede visualizar la información, integrantes, partidas y estadísticas disponibles. |
| **Relacionado con** | RF-003, RF-004, RF-006, RF-007, RF-015, RNF-PRI-001 |

#### RF-013 · Agendar partida de grupo

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema podrá permitir a un miembro autorizado proponer una fecha para una próxima partida dentro de un grupo. |
| **Origen** | Entrevista — función considerada de baja prioridad porque la coordinación actual se realiza por WhatsApp. |
| **Prioridad** | Deseable |
| **Criterio de aceptación** | Al seleccionar una fecha válida y confirmar la acción, la partida propuesta aparece dentro del grupo con la fecha indicada. |
| **Relacionado con** | RF-012 |

#### RF-014 · Configurar privacidad del perfil y contenido

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir al usuario controlar la visibilidad de su perfil y deberá respetar la privacidad aplicable a fotografías y contenido de grupos privados. |
| **Origen** | Entrevista — confirmado parcialmente. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al modificar una configuración de privacidad, las consultas posteriores respetan la nueva visibilidad. Una fotografía restringida a un grupo privado no puede ser visualizada por una cuenta externa. |
| **Relacionado con** | RF-001, RF-008, RF-012, RNF-PRI-001, RNF-SEG-001 |

#### RF-015 · Registrar participante invitado

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir registrar en una partida a una persona que no posea una cuenta de Podium. |
| **Origen** | Entrevista — nuevo hallazgo. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Durante el registro de una partida, el usuario puede agregar un participante invitado proporcionando al menos un nombre identificador. |
| **Relacionado con** | RF-006, RF-012 |

#### RF-016 · Corregir partida registrada

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir que un usuario autorizado corrija los resultados de una partida previamente registrada. |
| **Origen** | Entrevista — nuevo hallazgo. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al modificar un resultado con datos válidos y guardar la corrección, la partida refleja los nuevos valores y las estadísticas relacionadas se recalculan. |
| **Relacionado con** | RF-006, RF-007, RNF-CON-001 |

#### RF-017 · Registrar empate

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir registrar más de un participante en la primera posición cuando las reglas del juego permitan un empate. |
| **Origen** | Entrevista — nuevo hallazgo. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Si el juego permite empate, el usuario puede seleccionar a dos o más participantes como empatados en la primera posición sin que el sistema exija un único ganador. |
| **Relacionado con** | RF-006, RF-007, RNF-CON-001 |

#### RF-018 · Moderar contenido reportado

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema deberá permitir a un Administrador de Podium revisar contenido reportado y mantenerlo visible u ocultarlo cuando incumpla las reglas de la plataforma. |
| **Origen** | Necesidad de moderación derivada del carácter social de Podium. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al revisar una publicación, comentario o fotografía reportada, el administrador puede mantenerla disponible u ocultarla. Si la oculta, deja de ser visible para los usuarios y queda registrada la acción administrativa. |
| **Relacionado con** | RF-008, RF-010, RNF-SEG-001 |

---

## 4. Requisitos no funcionales

### 4.1 Resumen

| ID | Atributo | Nombre | Prioridad | Origen |
|---|---|---|---|---|
| RNF-REN-001 | Rendimiento | Tiempo de carga de pantallas principales | Importante | Derivado del tipo de sistema Web y SaaS |
| RNF-SEG-001 | Seguridad | Control de acceso a información | Imprescindible | Derivado del tipo de sistema Web y SaaS |
| RNF-USA-001 | Usabilidad | Facilidad para registrar partidas | Imprescindible | Entrevista |
| RNF-PRI-001 | Privacidad | Visibilidad del contenido | Imprescindible | Entrevista |
| RNF-CON-001 | Consistencia | Coherencia de estadísticas | Imprescindible | Entrevista |
| RNF-DIS-001 | Disponibilidad | Disponibilidad mensual del servicio | Importante | Derivado del tipo de sistema Web y SaaS |
| RNF-ESC-001 | Escalabilidad | Respuesta bajo usuarios concurrentes | Importante | Derivado del tipo de sistema Web y SaaS |

### 4.2 Fichas

#### RNF-REN-001 · Tiempo de carga de pantallas principales

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Rendimiento |
| **Descripción** | Las pantallas principales de Inicio, Descubrir, Perfil y Grupo deberán desplegar su contenido principal en un tiempo máximo de tres segundos bajo condiciones normales de operación. |
| **Métrica** | Tiempo entre la solicitud de la pantalla y el despliegue de su contenido principal: máximo 3 segundos. |
| **Origen** | Derivado del tipo de sistema Web y SaaS. |
| **Prioridad** | Importante |
| **Por qué importa** | Podium depende de una navegación frecuente entre distintas secciones y una espera prolongada afectaría la experiencia de uso. |
| **Afecta a** | RF-001, RF-005, RF-007, RF-008, RF-011, RF-012 |

#### RNF-SEG-001 · Control de acceso a información

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Seguridad |
| **Descripción** | El sistema solo deberá permitir que un usuario consulte o modifique información para la cual posee autorización. |
| **Métrica** | En las pruebas de autorización, el 100 % de los intentos realizados con cuentas sin permiso deberán ser rechazados. |
| **Origen** | Derivado del tipo de sistema y de la existencia de cuentas, perfiles, grupos y funciones de administración. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Podium almacena perfiles, fotografías, grupos, partidas y publicaciones de diferentes usuarios. |
| **Afecta a** | RF-001, RF-002, RF-003, RF-004, RF-009, RF-010, RF-012, RF-014, RF-016, RF-018 |

#### RNF-USA-001 · Facilidad para registrar partidas

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Usabilidad |
| **Descripción** | Un usuario familiarizado con las funciones básicas de Podium deberá poder registrar una partida sin asistencia externa. |
| **Métrica** | Al menos 4 de cada 5 usuarios de prueba deberán completar correctamente el registro de una partida en su primer intento sin recibir instrucciones adicionales. |
| **Origen** | Entrevista. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Registrar partidas es una de las funciones centrales de Podium. |
| **Afecta a** | RF-006, RF-015, RF-017 |

#### RNF-PRI-001 · Visibilidad del contenido

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Privacidad |
| **Descripción** | El sistema deberá respetar la configuración de visibilidad antes de mostrar perfiles, grupos, fotografías o publicaciones. |
| **Métrica** | En las pruebas de privacidad, el 100 % de los usuarios sin autorización deberán ser incapaces de visualizar contenido marcado como privado. |
| **Origen** | Entrevista. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Una partida puede contener información que sus participantes no desean hacer pública. |
| **Afecta a** | RF-004, RF-008, RF-012, RF-014 |

#### RNF-CON-001 · Coherencia de estadísticas

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Consistencia |
| **Descripción** | Las estadísticas mostradas deberán corresponder con los resultados almacenados y actualizarse después de una corrección. |
| **Métrica** | En una muestra de 100 partidas registradas o corregidas, el 100 % de las estadísticas recalculadas deberá coincidir con los resultados almacenados. |
| **Origen** | Entrevista. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Una misma partida modifica información relacionada con varios participantes y una inconsistencia reduciría la confiabilidad del sistema. |
| **Afecta a** | RF-006, RF-007, RF-016, RF-017 |

#### RNF-DIS-001 · Disponibilidad mensual del servicio

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Disponibilidad |
| **Descripción** | El servicio deberá permanecer disponible durante la mayor parte del periodo de operación mensual. |
| **Métrica** | Disponibilidad mensual mínima de 99 %, sin considerar ventanas de mantenimiento previamente anunciadas. |
| **Origen** | Derivado del tipo de sistema Web y SaaS. |
| **Prioridad** | Importante |
| **Por qué importa** | Los usuarios pueden necesitar consultar o registrar una partida durante una reunión. |
| **Afecta a** | RF-001 a RF-018 |

#### RNF-ESC-001 · Respuesta bajo usuarios concurrentes

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Escalabilidad |
| **Descripción** | El sistema deberá conservar un tiempo de respuesta aceptable cuando varios usuarios utilicen las funciones principales simultáneamente. |
| **Métrica** | Con al menos 100 sesiones activas concurrentes en un entorno de prueba, el 95 % de las solicitudes de las pantallas principales deberá responder en máximo 3 segundos. |
| **Origen** | Derivado del tipo de sistema Web y SaaS. |
| **Prioridad** | Importante |
| **Por qué importa** | La cantidad de usuarios, partidas, publicaciones y grupos puede aumentar con el uso de la plataforma. |
| **Afecta a** | RF-005, RF-007, RF-008, RF-011, RF-012 |

---

## 5. Casos de uso

### 5.1 Resumen

| ID | Caso de uso | Actor principal | Requisitos funcionales relacionados |
|---|---|---|---|
| CU-01 | Registrar una partida | Usuario | RF-006, RF-007, RF-015, RF-017 |
| CU-02 | Consultar estadísticas | Usuario | RF-007 |
| CU-03 | Consultar un grupo | Usuario / Administrador de grupo | RF-005, RF-012, RF-014 |
| CU-04 | Corregir una partida | Usuario autorizado / Administrador de grupo | RF-016, RF-007 |
| CU-05 | Crear un grupo | Usuario | RF-003 |
| CU-06 | Unirse a un grupo | Usuario | RF-004, RF-005 |
| CU-07 | Administrar un grupo | Administrador de grupo | RF-012, RF-013, RF-014 |
| CU-08 | Moderar contenido reportado | Administrador de Podium | RF-018 |

**Nota:** Los requisitos RF-001, RF-002, RF-008, RF-009, RF-010 y RF-011 corresponden a funciones secundarias o transversales de Podium que se conservan en la especificación, pero no se representan como casos de uso independientes en el diagrama para mantener el límite de cinco a ocho casos solicitado para la entrega.

### 5.2 Descripción breve de los casos de uso

**CU-01 · Registrar una partida:** El usuario registra una partida terminada indicando juego, participantes, fecha y resultado. El sistema valida los datos, almacena la partida y actualiza las estadísticas correspondientes.

**CU-02 · Consultar estadísticas:** El usuario consulta sus estadísticas generales o por juego calculadas a partir de las partidas registradas.

**CU-03 · Consultar un grupo:** El usuario o administrador accede a un grupo para consultar integrantes, juegos, partidas, actividad y estadísticas disponibles.

**CU-04 · Corregir una partida:** Un usuario autorizado modifica un resultado previamente registrado y el sistema recalcula las estadísticas afectadas.

**CU-05 · Crear un grupo:** El usuario crea un nuevo grupo indicando la información obligatoria y queda registrado como administrador.

**CU-06 · Unirse a un grupo:** El usuario se incorpora a un grupo mediante un código, invitación o mecanismo permitido para grupos públicos.

**CU-07 · Administrar un grupo:** El administrador gestiona información y funciones propias del grupo, incluyendo integrantes, privacidad y funciones de organización disponibles.

**CU-08 · Moderar contenido reportado:** El Administrador de Podium revisa contenido reportado y decide si permanece visible o debe ocultarse.

### 5.3 Caso de uso detallado

#### CU-01 · Registrar una partida

**Actor principal:** Usuario.

**Objetivo:** Registrar el resultado de una partida para conservarla en el historial y actualizar las estadísticas correspondientes.

**Precondiciones:**

- El usuario ha iniciado sesión en Podium.
- El usuario tiene acceso al grupo donde desea registrar la partida.
- El juego que se utilizará en el registro está disponible para seleccionarse.

**Escenario principal:**

1. El usuario ingresa al grupo donde se realizó la partida.
2. El usuario selecciona la opción para registrar una partida.
3. El sistema solicita el juego, la fecha, los participantes y el resultado.
4. El usuario selecciona el juego correspondiente.
5. El usuario selecciona a los participantes de la partida.
6. El usuario captura el resultado de cada participante, incluyendo puntos o posición cuando corresponda.
7. El usuario puede agregar de manera opcional una fotografía o comentario relacionado con la partida.
8. El usuario confirma el registro.
9. El sistema verifica que los datos obligatorios sean válidos.
10. El sistema almacena la partida.
11. El sistema actualiza automáticamente las estadísticas de los participantes registrados.
12. El sistema muestra la confirmación del registro y la partida queda disponible en el historial del grupo.

**Flujo alterno A — Participante invitado:**

A1. Durante el paso 5, el usuario indica que uno de los participantes no tiene cuenta de Podium.  
A2. El sistema ofrece la opción de agregar un participante invitado.  
A3. El usuario introduce al menos un nombre identificador para el invitado.  
A4. El sistema incluye al invitado en la partida sin crearle una cuenta.  
A5. El flujo continúa en el paso 6 del escenario principal.

**Flujo alterno B — Empate:**

B1. Durante el paso 6, el usuario indica que la partida terminó con dos o más participantes empatados.  
B2. Si el juego permite empate, el sistema permite marcar a varios participantes en la misma posición.  
B3. El usuario continúa capturando el resultado.  
B4. El flujo continúa en el paso 7 del escenario principal.

**Flujo alterno C — Datos obligatorios incompletos o inválidos:**

C1. En el paso 9, el sistema detecta que falta información obligatoria o existe un resultado inválido.  
C2. El sistema no guarda la partida.  
C3. El sistema identifica los campos que deben corregirse.  
C4. El usuario corrige la información.  
C5. El flujo regresa al paso 8 del escenario principal.

**Postcondiciones:**

- La partida queda almacenada en el historial correspondiente.
- Los resultados quedan asociados a los participantes registrados.
- Las estadísticas se actualizan a partir del resultado almacenado.
- Si se utilizó un participante invitado, este queda asociado únicamente mediante el identificador capturado y no se crea una cuenta nueva.

**Requisitos que realiza:** RF-006, RF-007, RF-015 y RF-017.

**Requisitos no funcionales relacionados:** RNF-USA-001 y RNF-CON-001.

---

## 6. Trazabilidad

### 6.1 Trazabilidad de los casos de uso principales

| Caso de uso | Requisitos que realiza | Actor | Elemento del prototipo |
|---|---|---|---|
| CU-01 Registrar una partida | RF-006, RF-007, RF-015, RF-017 | Usuario | Flujo Registrar partida — pendiente de completar en Figma |
| CU-02 Consultar estadísticas | RF-007 | Usuario | Grupo · estadísticas / Perfil |
| CU-03 Consultar un grupo | RF-005, RF-012, RF-014 | Usuario / Administrador de grupo | Grupo · prueba |
| CU-04 Corregir una partida | RF-016, RF-007 | Usuario autorizado / Administrador de grupo | Pantalla de corrección — pendiente |
| CU-05 Crear un grupo | RF-003 | Usuario | Descubrir · Crear o unirme a un grupo |
| CU-06 Unirse a un grupo | RF-004, RF-005 | Usuario | Descubrir · Crear o unirme a un grupo |
| CU-07 Administrar un grupo | RF-012, RF-013, RF-014 | Administrador de grupo | Grupo · prueba / configuración |
| CU-08 Moderar contenido reportado | RF-018 | Administrador de Podium | Pendiente de representar |

### 6.2 Trazabilidad completa de requisitos funcionales

| Requisito | Origen | Caso de uso relacionado | Evidencia / prototipo |
|---|---|---|---|
| RF-001 Actualizar perfil | Visión del producto | Función transversal | Pantalla Perfil |
| RF-002 Gestionar solicitudes de amistad | Visión del producto | Función secundaria | Pendiente de representar |
| RF-003 Crear grupo | Entrevista | CU-05 Crear un grupo | Descubrir · Crear o unirme a un grupo |
| RF-004 Unirse a grupo | Entrevista | CU-06 Unirse a un grupo | Descubrir · Crear o unirme a un grupo |
| RF-005 Buscar grupos públicos | Prototipo actual | CU-03 / CU-06 | Descubrir · Grupos públicos |
| RF-006 Registrar partida | Entrevista | CU-01 Registrar una partida | Pendiente de completar en Figma |
| RF-007 Consultar estadísticas | Entrevista | CU-01, CU-02 y CU-04 | Grupo · estadísticas / Perfil |
| RF-008 Consultar feed | Entrevista | Función secundaria | Pantalla Inicio |
| RF-009 Reaccionar a publicación | Prototipo actual | Función secundaria del feed | Pendiente en prototipo final |
| RF-010 Comentar publicación | Prototipo actual | Función secundaria del feed | Pendiente en prototipo final |
| RF-011 Buscar usuarios | Visión del producto | Función secundaria | Pendiente de representar |
| RF-012 Consultar información de grupo | Entrevista | CU-03 y CU-07 | Grupo · prueba |
| RF-013 Agendar partida de grupo | Entrevista | CU-07 Administrar un grupo | Grupo · Agendar una partida |
| RF-014 Configurar privacidad | Entrevista | CU-03 y CU-07 | Perfil · Privacidad / Grupo |
| RF-015 Registrar participante invitado | Entrevista | CU-01 Registrar una partida | Pendiente de completar en Figma |
| RF-016 Corregir partida registrada | Entrevista | CU-04 Corregir una partida | Pendiente de representar |
| RF-017 Registrar empate | Entrevista | CU-01 Registrar una partida | Pendiente de completar en Figma |
| RF-018 Moderar contenido reportado | Necesidad de moderación | CU-08 Moderar contenido reportado | Pendiente de representar |

---

## 7. Registro de cambios

| Fecha | Requisito / sección | Qué cambió | Por qué |
|---|---|---|---|
| 22/09/2026 | Documento inicial | Se creó la primera versión de la especificación. | Inicio formal del documento. |
| 28/09/2026 | Requisitos funcionales | Se actualizaron prioridades y orígenes utilizando los hallazgos de la entrevista. | Incorporar evidencia obtenida durante la elicitación. |
| 28/09/2026 | RF-015 a RF-017 | Se agregaron participante invitado, corrección de partida y empate. | Nuevos hallazgos de la entrevista. |
| 28/09/2026 | RF-018 | Se agregó moderación de contenido reportado. | Justificar el rol de Administrador de Podium y controlar contenido inapropiado. |
| 29/09/2026 | Sección 5 | Se definieron ocho casos de uso y se desarrolló CU-01 Registrar una partida. | Completar el análisis de comportamiento solicitado en la entrega. |
| 01/10/2026 | Sección 6 | Se completó la trazabilidad entre requisitos, casos de uso y prototipo. | Mostrar la relación entre alcance, requisitos, comportamiento y evidencia visual. |

---

