# Bitácora de entrevista — Podium

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

# Ficha de dominio contestada con base en el perfil entrevistado

## Quién eres

No eres una persona extremadamente aficionada a los juegos de mesa, pero disfrutas jugar Catan con un grupo habitual de amigos.

Normalmente juegas con prácticamente las mismas personas y se reúnen aproximadamente una vez cada una o dos semanas, dependiendo de la disponibilidad del grupo.

Tienen un grupo de WhatsApp dedicado principalmente a registrar cómo terminaron sus partidas. Ahí suelen enviar quién ganó, los puntos obtenidos y, algunas veces, fotografías.

No utilizas actualmente una aplicación especializada para llevar estadísticas o un historial organizado de las partidas.

---

## Cómo es tu día o contexto de juego

Cuando el grupo decide reunirse, normalmente se ponen de acuerdo mediante WhatsApp.

La organización de la reunión no representa un problema importante, porque el grupo ya está acostumbrado a utilizar ese medio para coordinarse.

Cuando termina una partida de Catan, normalmente alguien envía al grupo de WhatsApp quién ganó y cuántos puntos obtuvo cada persona.

En algunas ocasiones también comparten fotografías de la reunión.

Si después quieren recordar una partida antigua o saber quién ha ganado más veces, tienen que buscar entre los mensajes anteriores y revisar los resultados manualmente.

No cuentan con estadísticas automáticas ni con un historial organizado por jugador o por partida.

---

## Reglas que conoces y no vas a decir si no te preguntan

- Una persona puede pertenecer a más de un grupo de juegos.
- Formar parte del mismo grupo no significa necesariamente que todos sean amigos dentro de una aplicación.
- Algunas veces puede participar una persona invitada que no tenga cuenta.
- El resultado de una persona invitada también debe poder registrarse.
- No tendría sentido obligar a un invitado ocasional a crear una cuenta solamente para aparecer en una partida.
- Una partida que se cancela o no puede terminar normalmente no debería contarse en las estadísticas.
- Si alguien se retira y la partida ya no puede continuar, normalmente el grupo decide no contar ese resultado.
- Puede existir un empate y no siempre debería obligarse a registrar un único ganador.
- Si alguien registra mal una puntuación, el resultado debería poder corregirse posteriormente.
- Los resultados y puntuaciones pueden compartirse dentro del grupo.
- Las fotografías deberían tener mayor control de privacidad y no necesariamente ser públicas.
- Las estadísticas más útiles son partidas jugadas, victorias, porcentaje de victorias, puntos y promedio de puntos.
- Saber contra quién se jugó puede ser útil, pero no es tan importante como conocer los resultados y estadísticas generales.
- El feed social puede resultar interesante, pero no es la razón principal por la que utilizarías Podium.
- El historial de partidas, los grupos y las estadísticas son más importantes que las funciones sociales.
- No necesitas que Podium sustituya a WhatsApp para organizar las reuniones.

---

## Una excepción que ocurre a veces

En algunas reuniones puede jugar una persona que normalmente no pertenece al grupo.

En ese caso, su resultado sí debería poder registrarse, aunque solamente participe una vez y no tenga una cuenta en Podium.

Otra situación que puede ocurrir es que una partida no termine correctamente porque una persona tenga que retirarse antes de tiempo. Si debido a esto la partida no puede continuar, normalmente ese resultado no se considera válido.

También puede ocurrir que haya un empate o que después de terminar descubran que una puntuación fue registrada incorrectamente. En ese caso debería existir una forma de corregir el resultado sin perder el historial de la partida.

---

## Lo que te molesta de cómo lo hacen hoy

El principal problema no es registrar el resultado inmediatamente después de jugar, porque el grupo ya utiliza WhatsApp para hacerlo.

El problema aparece después, cuando se acumulan muchas partidas.

Para saber quién ha ganado más veces es necesario revisar mensajes anteriores y contar resultados manualmente.

También puede ser difícil encontrar una partida específica, recordar las puntuaciones exactas o localizar una fotografía relacionada con determinada reunión.

En ocasiones algún resultado puede quedar incompleto y después nadie recuerda exactamente cuál era la puntuación.

Te gustaría poder consultar fácilmente:

- cuántas partidas ha jugado cada persona;
- cuántas veces ha ganado;
- su porcentaje de victorias;
- cuántos puntos ha obtenido;
- su promedio de puntos en Catan;
- los resultados de partidas anteriores.

---

## Cómo responder

Contesta solamente lo que te pregunten.

Tus respuestas deben ser breves y naturales.

No propongas funciones para Podium por iniciativa propia; explica primero cómo haces actualmente las cosas.

Si te preguntan qué cambiarías o qué función te sería útil, puedes mencionar que te interesan principalmente el historial de partidas y las estadísticas.

Si te preguntan por funciones sociales, puedes decir que te parecen interesantes, pero que probablemente utilizarías más los grupos, el registro de partidas y las estadísticas.

Si te preguntan sobre organización de reuniones, explica que actualmente WhatsApp funciona suficientemente bien para eso.

Si te preguntan algo que no se haya definido, responde de forma coherente con el resto del perfil.

---

## Relación entre la ficha de dominio y los hallazgos de la entrevista

La ficha de dominio representa el mismo perfil utilizado durante la entrevista. El participante juega Catan con regularidad con prácticamente el mismo grupo de amigos y utiliza WhatsApp para coordinarse y conservar resultados.

La entrevista confirmó que la organización de las reuniones no es un problema prioritario. La principal dificultad aparece después, cuando se necesita recuperar información histórica o calcular estadísticas.

Las excepciones incluidas en la ficha —participantes invitados, partidas incompletas o canceladas, empates y correcciones de resultados— se reflejan directamente en los cambios realizados a los requisitos y en los nuevos RF-015, RF-016 y RF-017.

---

## Conclusión breve de la entrevista

La entrevista permitió comprender que la necesidad principal de Podium no consiste en sustituir todas las herramientas que utiliza actualmente un grupo de amigos, sino en centralizar el historial de partidas y convertir los resultados almacenados en información fácil de consultar.

Uno de los hallazgos más importantes fue que el sistema debe contemplar situaciones que no estaban completamente definidas en el planteamiento inicial, como participantes invitados sin cuenta, correcciones de resultados y empates.

También se identificó que las funciones sociales, como el feed o la agenda de próximas partidas, tienen una prioridad menor para este perfil de usuario que el registro de partidas, el historial, la consulta de grupos y las estadísticas.
