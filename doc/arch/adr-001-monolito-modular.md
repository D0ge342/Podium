# ADR-001 — Elegir monolito modular para Podium

**Estado:** Aceptado como decisión de diseño; implementación pendiente  
**Fecha:** 29 de octubre de 2026  
**Proyecto:** Podium  
**Autor:** Josué Tiburcio Cruz  
**Diagramas relacionados:** [diagramas.md](diagramas.md)

## 1. Contexto

Podium es una aplicación web SaaS que busca organizar partidas de juegos de mesa y ofrecer grupos, historial, contenido y estadísticas. El proyecto se trabaja inicialmente de forma individual, con un alcance académico y sin necesidad actual de desplegar equipos independientes por cada función.

En la Actividad 2 se identificaron cuatro módulos de negocio con fronteras relativamente claras: **Identidad y participantes**, **Grupos y contenido**, **Partidas** y **Estadísticas**. Partidas necesita validar participantes y pertenencia a grupos; cuando un resultado se registra o corrige, Estadísticas debe reaccionar al cambio. También debe respetarse la privacidad de los grupos y del contenido compartido. Se adoptó la idea de grupos como inquilinos lógicos con infraestructura compartida, por lo que las reglas de autorización y aislamiento de datos deben aplicarse dentro de los módulos.

## 2. Alternativas consideradas

- **Monolito tradicional:** ofrece un despliegue sencillo, pero puede mezclar responsabilidades y dificultar la evolución de reglas distintas.
- **Monolito modular:** conserva un único despliegue de backend, manteniendo el código y las reglas separados en módulos con interfaces bien definidas.
- **Microservicios:** permiten desplegar y escalar cada servicio por separado, pero introducen comunicación por red, mayor operación, monitoreo distribuido, coordinación entre servicios y desafíos de consistencia que el proyecto todavía no necesita.

## 3. Decisión

Se eligió un **monolito modular**. Se propone una aplicación web que consuma una API backend desplegada como **una sola unidad**, con estos cuatro módulos internos:

1. **Identidad y participantes:** usuarios registrados, roles y participantes invitados.
2. **Grupos y contenido:** grupos, membresías, fotografías, privacidad y moderación.
3. **Partidas:** juegos, participantes, resultados, validaciones, empates y correcciones.
4. **Estadísticas:** partidas jugadas, victorias, porcentajes, puntos y promedios.

Cada módulo concentra sus reglas y expone operaciones internas a los otros. Se propone usar eventos internos como `PartidaRegistrada` y `PartidaCorregida` para que Estadísticas se actualice sin crear dependencias innecesarias con Partidas. Como propuesta para los contenedores se consideran React, Node.js/TypeScript, PostgreSQL y almacenamiento de objetos para fotografías; **estas tecnologías aún no se consideran implementadas**.

## 4. Consecuencias

**Ventajas.** Hay menos infraestructura y despliegues que administrar, lo que se ajusta al desarrollo individual. Los límites de negocio ayudan a localizar cada regla y facilitan las pruebas y la evolución del código. Mantener interfaces entre módulos disminuye el acoplamiento.

**Costos y riesgos.** Todos los módulos del backend comparten el despliegue y parte de los recursos. Un cambio en uno de ellos requiere publicar nuevamente el backend. La modularidad debe respetarse en el código y no solo en los diagramas: un módulo no debe modificar directamente las tablas privadas de otro ni duplicar sus reglas.

**Impacto en requisitos.** La privacidad de grupos y contenido debe comprobarse en cada operación relevante (RNF-PRI-001). El cálculo de estadísticas debe mantenerse consistente con partidas válidas y correcciones (RNF-CON-001). Se deberá medir el tiempo de respuesta de las pantallas principales frente al objetivo de 3 segundos (RNF-REN-001).

## 5. Cuándo revisar la decisión

Se reconsiderará extraer **Estadísticas** como servicio independiente si aparece una necesidad medida y sostenida que no pueda resolverse razonablemente optimizando consultas, usando tareas asíncronas o aumentando los recursos del monolito. Por ejemplo: si el cálculo de resultados y promedios provoca que las pantallas principales superen reiteradamente el objetivo de **3 segundos**, aun después de optimizaciones, y se demuestra que ese módulo concentra la carga.

Antes de cambiar la arquitectura se revisarán tiempos, volumen de partidas y correcciones, consumo de recursos y necesidad real de despliegues independientes. No se separarán los cuatro módulos por anticipado.
