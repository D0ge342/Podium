

## Supuestos que se confirmaron

| Supuesto | Evidencia obtenida en la entrevista |
|---|---|
| Los jugadores se organizan en grupos relativamente definidos. | El entrevistado juega regularmente Catan con prácticamente el mismo grupo de amigos. |
| Registrar partidas es una necesidad relevante. | Actualmente utilizan un grupo de WhatsApp específicamente para conservar resultados. |
| Las estadísticas automáticas aportarían valor. | Actualmente deben revisar y contar resultados manualmente para saber quién ha ganado más. |
| Una persona puede pertenecer a varios grupos. | El entrevistado considera normal que una persona pueda jugar con distintos grupos de amigos. |
| Ser amigo y pertenecer a un grupo son relaciones diferentes. | Indicó que compartir un grupo no implica necesariamente querer agregar a una persona como amigo. |
| La privacidad es importante. | Prefiere que las fotografías y cierta actividad permanezcan dentro del grupo. |

---

## Supuestos que resultaron falsos o menos importantes

| Supuesto anterior | Qué se descubrió realmente | Cambio sugerido |
|---|---|---|
| El feed social sería una de las funciones centrales. | Al entrevistado le parece útil, pero prioriza grupos, partidas y estadísticas. | Cambiar RF-008 de Imprescindible a Importante. |
| Agendar partidas dentro de Podium sería una función relevante. | El grupo ya se organiza mediante WhatsApp y el entrevistado no considera necesario reemplazarlo. | RF-013 puede pasar a Deseable o quedar fuera de la primera versión. |
| Todos los participantes necesitarían una cuenta. | A veces participan invitados que juegan una sola vez. | Permitir registrar un participante invitado sin cuenta. |
| Una partida siempre tiene un único ganador. | Pueden existir empates u otras condiciones dependiendo del juego. | El registro de resultados no debe obligar a tener un único ganador. |

---

## Información que apareció y no se esperaba

- El grupo ya utiliza un chat de WhatsApp dedicado casi exclusivamente a registrar resultados.
- El problema principal no es registrar el resultado, sino consultarlo después y obtener estadísticas de forma sencilla.
- Un participante invitado debería poder aparecer en una partida sin necesidad de crear una cuenta en Podium.
- El usuario considera importante poder corregir posteriormente un resultado registrado de forma incorrecta.
- La organización de próximas reuniones no representa un problema importante porque WhatsApp ya cubre esa necesidad.
- El usuario valora más el historial y las estadísticas que las funciones sociales del feed.

---

## Reglas de negocio identificadas

1. Las estadísticas de los usuarios deben calcularse a partir de las partidas registradas.
2. Una partida incompleta o cancelada no debe afectar las estadísticas si el grupo decide que no cuenta.
3. Un participante puede aparecer como invitado sin tener una cuenta de Podium.
4. Los resultados deben permitir representar empates cuando las reglas del juego lo permitan.
5. Una corrección realizada sobre una partida debe actualizar las estadísticas relacionadas.
6. La visibilidad de fotografías y contenido del grupo debe respetar la configuración de privacidad correspondiente.

---

## Excepciones identificadas

- Un participante puede ser invitado y no pertenecer al grupo.
- Un participante puede no tener cuenta de Podium.
- Una partida puede quedar incompleta.
- Una partida puede cancelarse y no contabilizarse.
- Puede existir un empate.
- Un resultado puede haber sido registrado incorrectamente y necesitar corrección.
- Una fotografía puede ser visible solo para integrantes del grupo.

---

## Requisitos confirmados durante la entrevista

| Requisito actual | Resultado |
|---|---|
| RF-003 · Crear grupo | Confirmado |
| RF-004 · Unirse a grupo | Confirmado |
| RF-006 · Registrar partida | Confirmado y ampliado |
| RF-007 · Consultar estadísticas | Confirmado |
| RF-012 · Consultar información de grupo | Confirmado |
| RF-014 · Configurar privacidad | Confirmado parcialmente |

---

## Requisitos que deben modificarse

| Requisito | Cambio necesario | Motivo |
|---|---|---|
| RF-006 · Registrar partida | Permitir participantes invitados y resultados con empate. | La entrevista mostró que no todos los participantes pertenecen al grupo ni tienen cuenta y que pueden existir empates. |
| RF-007 · Consultar estadísticas | Añadir porcentaje de victorias, puntos y promedio de puntos cuando aplique. | Son las estadísticas que el entrevistado considera más útiles. |
| RF-008 · Consultar feed | Cambiar prioridad de Imprescindible a Importante. | El entrevistado lo considera útil, pero menos relevante que grupos, historial y estadísticas. |
| RF-013 · Agendar partida de grupo | Reducir prioridad o dejarlo fuera de la primera versión. | El grupo ya se organiza mediante WhatsApp y no considera esta función prioritaria. |
| RF-014 · Configurar privacidad | Incluir explícitamente fotografías y contenido de grupos privados. | El entrevistado considera que las fotografías no deberían ser públicas automáticamente. |

---

## Nuevos requisitos identificados

### RF-015 · Registrar participante invitado

El sistema deberá permitir registrar en una partida a una persona que no posea una cuenta de Podium.

### RF-016 · Corregir partida registrada

El sistema deberá permitir que un usuario autorizado corrija los resultados de una partida previamente registrada.

### RF-017 · Registrar empate

El sistema deberá permitir registrar más de un participante en la primera posición cuando las reglas del juego admitan un empate.

---

## Conclusión breve de la entrevista

La entrevista permitió comprender que la necesidad principal de Podium no consiste en sustituir todas las herramientas que utiliza actualmente un grupo de amigos, sino en centralizar el historial de partidas y convertir los resultados almacenados en información fácil de consultar.

Uno de los hallazgos más importantes fue que el sistema debe contemplar situaciones que no estaban completamente definidas en el planteamiento inicial, como participantes invitados sin cuenta, correcciones de resultados y empates.

También se identificó que las funciones sociales, como el feed o la agenda de próximas partidas, tienen una prioridad menor para este perfil de usuario que el registro de partidas, el historial, la consulta de grupos y las estadísticas.

---

## Nota metodológica

Esta bitácora fue elaborada a partir de una entrevista simulada basada en un perfil de usuario definido previamente. Los resultados se utilizarán para actualizar la especificación de requisitos, los casos de uso y el prototipo de Podium.
