**1. Descripción del sistema**

**Nombre del sistema:** Podium

**Descripción:** Red social para los fanáticos de los juegos de mesa

**2. Problema y usuarios**

**El problema:** las personas que tienen grupos de amigos donde juegan muchos juegos de mesas no tienen forma de registrar las victorias y ver estadísticas de cada uno

**Cómo se resuelve hoy sin el sistema:** algunas personas optan por usar una tabla de Excel para compensar la falta de una app o software que sea específico para esa tarea

**Usuarios del sistema:**

| **Tipo de usuario** | **Qué necesita del sistema** | **Qué le preocupa** |
| --- | --- | --- |
| Usuario general | Crear su perfil, agregar amigos, unirse a grupos, registrar partidas, subir fotografías, consultar su historial y ver sus estadísticas generales y por juego. También necesita interactuar con publicaciones mediante comentarios y reacciones. | Que registrar una partida sea complicado o tardado, que sus estadísticas sean incorrectas y que información privada, fotografías o resultados sean visibles para personas que no deberían verlos. |
| Usuario que busca nuevos jugadores o grupos | Utilizar la sección Descubrir para buscar personas, enviar solicitudes de amistad, encontrar grupos públicos y conocer usuarios con intereses similares en juegos de mesa | No encontrar fácilmente personas o grupos relevantes y que se muestre demasiada información personal antes de establecer una amistad o pertenecer a un grupo |

**Un conflicto entre usuarios:**

Un usuario puede querer que las partidas que registra sean visibles para todos sus amigos o incluso para otros usuarios de Podium, mientras que otro jugador que participó en esa misma partida puede preferir que su nombre, puntuación o fotografía no aparezcan públicamente.

La decisión de diseño será permitir que cada usuario controle la privacidad de su perfil y que las publicaciones respeten la visibilidad del grupo o cuenta donde fueron creadas. Además, la información de otros jugadores no deberá hacerse pública fuera del grupo si sus configuraciones de privacidad no lo permiten.

**Reflexion con la dupla**
Falta exploracion y ranking publico
Se podria agregar exploracion por juego de mesa

**3. Alcance**

**Dentro del alcance**

- Registro de usuarios con perfil, fotografía, nombre de usuario, descripción e información básica.
- Creación de grupos, unión mediante código de invitación y búsqueda de grupos públicos.
- Registro de partidas de juegos de mesa incluyendo juego, participantes, resultados, fecha, fotografías y descripción de la partida.
- Feed de inicio donde se muestran partidas y publicaciones realizadas por amigos y grupos a los que pertenece el usuario.

**Explícitamente fuera del alcance**

- Compra, venta o renta de juegos de mesa dentro de la app.
- Sistema de chat o mensajería privada en tiempo real entre usuarios.
- Organización de torneos profesionales con premios, inscripciones, llaves de eliminación y pagos.

**Por qué queda fuera:**

El sistema de mensajería en tiempo real queda fuera de la primera versión porque aumenta considerablemente la complejidad técnica del proyecto porque requiere, comunicación en tiempo real, almacenamiento de conversaciones, notificaciones y medidas adicionales de seguridad. Que se traduce a mas tiempo y dinero para desarrollar. Aparte de que la app no está enfocado específicamente en esa clase de interacciones

**4. Tipo de sistema y restricciones**


**Tipo de sistema: Web y Saas**

**Por qué es de ese tipo:**

Es una aplicación a la que los usuarios acceden por medio de Internet para utilizar un servicio centralizado. La información de perfiles, amigos, grupos, partidas, publicaciones y estadísticas se almacena en una base de datos y puede ser consultada desde la aplicación.

**Atributos de calidad que impone:**

| **Atributo** | **Por qué importa en mi caso** | **Qué pasa si no se cumple** |
| --- | --- | --- |
| Usabilidad | Los usuarios deben poder registrar una partida, buscar amigos o consultar sus estadísticas de manera sencilla y rápida. | Si la aplicación es confusa o requiere demasiados pasos, los usuarios pueden dejar de utilizarla. |
| Seguridad | Podium almacena cuentas, perfiles, fotografías, grupos y otra información de los usuarios. | Alguien podría acceder a cuentas o información que no le corresponde. |
| Consistencia de datos | Una partida afecta las estadísticas de varios jugadores y posiblemente las estadísticas de un grupo. | Podrían mostrarse resultados diferentes o estadísticas incorrectas dependiendo de la pantalla consultada. |

**Reglas de negocio que ya identifiqué:**

1. Las estadísticas de los usuarios se calculan automáticamente a partir de las partidas registradas. Un usuario no puede modificar manualmente su número de victorias, partidas jugadas o porcentaje de victorias.
2. Solo los miembros de un grupo privado pueden consultar las publicaciones y partidas pertenecientes a ese grupo. Para ingresar se necesita una invitación o código de acceso
3. Al registrar una partida, las estadísticas de todos los jugadores participantes deben actualizarse utilizando el mismo resultado, para evitar información diferente entre perfiles.

**5. Ciclo de vida elegido**

**Modelo elegido:** Prototipado Rápido

**Por qué le conviene a este proyecto:**

*El modelo de Prototipado Rápido es adecuado para Podium porque, aunque la idea principal de la aplicación ya está definida, todavía existen requisitos que pueden cambiar conforme los usuarios prueben las distintas pantallas y funciones.*

*En Podium es especialmente importante la experiencia de usuario, ya que funciones como registrar una partida, consultar estadísticas, navegar por el feed, buscar amigos o entrar a grupos deben ser fáciles de entender y utilizar. Por esta razón, crear prototipos permite probar estas funciones antes de desarrollar completamente el sistema.*

**Alternativas descartadas**

**Alternativa 1:** **Cascada**

*Por qué la descarté: Descarté el modelo de Cascada porque requiere definir los requisitos con mucha precisión desde el inicio y avanzar de una etapa a otra de manera secuencial. En Podium todavía pueden surgir cambios en las funciones o en la interfaz conforme los usuarios utilicen los prototipos.*

**Alternativa 2: Modelo V**

*Por qué la descarté: Descarté el Modelo V porque está muy enfocado en la verificación y validación de cada etapa del desarrollo y funciona mejor cuando los requisitos están claramente definidos desde el principio.*
