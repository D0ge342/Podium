# Visión del producto

> **Plantilla del curso · Ingeniería de Software I · SIS3407**
> Este documento es el primer entregable del semestre y la base de todo lo que viene después.
> Se entrega completo en la **semana 4** y se presenta ante el grupo.
>
> **Cómo usarla:** copia este archivo a tu repositorio como `docs/vision-del-producto.md`, borra las instrucciones en gris de cada apartado y escribe tu contenido en su lugar. Conserva los títulos.

---

**Autor:**
Josué Tiburcio
**Fecha de la última versión:**
20/08/2026
**Repositorio:**

---

1. Descripción del sistema
Instrucción: nombre del sistema y qué hace, en un párrafo que cualquier persona entienda sin ser del área. Si necesitas usar una palabra técnica para explicarlo, todavía no está listo.
Nombre del sistema: Podium	
Descripción: Red social para los fanáticos de los juegos de mesa
________________________________________
2. Problema y usuarios
Instrucción: qué problema resuelve, a quién le sirve y, muy importante, qué hace esa gente hoy para arreglárselas sin el sistema. Esa última parte es la que revela el problema real.
El problema: las personas que tienen grupos de amigos donde juegan muchos juegos de mesas no tienen forma de registrar las victorias y ver estadísticas de cada uno
Cómo se resuelve hoy sin el sistema: algunas personas optan por usar una tabla de Excel para compensar la falta de una app o software que sea específico para esa tarea












Usuarios del sistema:
Tipo de usuario	Qué necesita del sistema	Qué le preocupa
Usuario general	Crear su perfil, agregar amigos, unirse a grupos, registrar partidas, subir fotografías, consultar su historial y ver sus estadísticas generales y por juego. También necesita interactuar con publicaciones mediante comentarios y reacciones.	Que registrar una partida sea complicado o tardado, que sus estadísticas sean incorrectas y que información privada, fotografías o resultados sean visibles para personas que no deberían verlos.


Usuario que busca nuevos jugadores o grupos	Utilizar la sección Descubrir para buscar personas, enviar solicitudes de amistad, encontrar grupos públicos y conocer usuarios con intereses similares en juegos de mesa.	No encontrar fácilmente personas o grupos relevantes y que se muestre demasiada información personal antes de establecer una amistad o pertenecer a un grupo.
		


Un conflicto entre usuarios:
Instrucción: describe algo que un usuario quiera y que a otro le estorbe. Ahí está tu primera decisión de diseño real.
Un usuario puede querer que las partidas que registra sean visibles para todos sus amigos o incluso para otros usuarios de Podium, mientras que otro jugador que participó en esa misma partida puede preferir que su nombre, puntuación o fotografía no aparezcan públicamente.
La decisión de diseño será permitir que cada usuario controle la privacidad de su perfil y que las publicaciones respeten la visibilidad del grupo o cuenta donde fueron creadas. Además, la información de otros jugadores no deberá hacerse pública fuera del grupo si sus configuraciones de privacidad no lo permiten.
________________________________________

				
3. Alcance
Instrucción: lo que escribes en "fuera del alcance" es lo que después evita que el proyecto crezca sin control. Sé específico: "reportes" no dice nada, "reportes de ventas mensuales exportables a PDF" sí.
Dentro del alcance
•	Registro de usuarios con perfil, fotografía, nombre de usuario, descripción e información básica.
•	Creación de grupos, unión mediante código de invitación y búsqueda de grupos públicos.
•	Registro de partidas de juegos de mesa incluyendo juego, participantes, resultados, fecha, fotografías y descripción de la partida.
•	Feed de inicio donde se muestran partidas y publicaciones realizadas por amigos y grupos a los que pertenece el usuario.


Explícitamente fuera del alcance
•	Compra, venta o renta de juegos de mesa dentro de la app.
•	Sistema de chat o mensajería privada en tiempo real entre usuarios.
•	Organización de torneos profesionales con premios, inscripciones, llaves de eliminación y pagos.
Por qué queda fuera:
Instrucción: para al menos una de las exclusiones, explica la razón. Puede ser tiempo, complejidad, o que no aporta al problema central.
El sistema de mensajería en tiempo real queda fuera de la primera versión porque aumenta considerablemente la complejidad técnica del proyecto porque requiere, comunicación en tiempo real, almacenamiento de conversaciones, notificaciones y medidas adicionales de seguridad. Que se traduce a mas tiempo y dinero para desarrollar. Aparte de que la app no está enfocado específicamente en esa clase de interacciones 
________________________________________
4. Tipo de sistema y restricciones
Instrucción: identifica de qué tipo es tu sistema y qué te obliga a garantizar ese tipo. Un sistema de información y un sistema crítico no se diseñan igual.
Tipo de sistema:
(De información · Embebido · Crítico · Web y SaaS · De datos y análisis)
Por qué es de ese tipo:
Atributos de calidad que impone:
Atributo	Por qué importa en mi caso	Qué pasa si no se cumple
		
		
		
Reglas de negocio que ya identifiqué:
Instrucción: reglas que no son obvias desde fuera y que alguien que conoce el dominio tendría que explicarte. Si no encuentras ninguna, tu caso puede ser demasiado simple.
1.	
2.	
3.	
________________________________________
5. Ciclo de vida elegido
Instrucción: este apartado se trabaja en la semana 3, después de ver los modelos de desarrollo. La justificación pesa más que la elección: no hay un modelo correcto, hay uno defendible para tu caso.
Modelo elegido:
Por qué le conviene a este proyecto:
Instrucción: argumenta con las características reales de tu caso. Estabilidad de los requisitos, disponibilidad del cliente, nivel de riesgo, tamaño del equipo, frecuencia de entregas esperada.
Alternativas descartadas
Alternativa 1:
Por qué la descarté:
Alternativa 2:
Por qué la descarté: 
________________________________________
Antes de entregar
Reviso que el documento cumpla lo siguiente:
•	[ ] La descripción del apartado 1 se entiende sin ser del área
•	[ ] Hay al menos dos tipos de usuario con necesidades distintas
•	[ ] Identifiqué un conflicto real entre usuarios
•	[ ] El alcance dice qué queda fuera, no solo qué queda dentro
•	[ ] Las exclusiones son específicas, no genéricas
•	[ ] Identifiqué el tipo de sistema y al menos dos atributos de calidad
•	[ ] Anoté al menos tres reglas de negocio no obvias
•	[ ] Justifiqué el ciclo de vida contra dos alternativas descartadas
•	[ ] El documento está en mi repositorio y se puede leer desde el navegador
•	[ ] Borré todas las instrucciones en cursiva de la plantilla

