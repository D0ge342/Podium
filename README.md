# Podium

**Proyecto académico · Ingeniería de Software I (SIS3407)**  
**Autor:** Josué Tiburcio Cruz

## Descripción

Podium es una propuesta de red social para personas que disfrutan los juegos de mesa. Su objetivo es centralizar el registro de partidas, conservar el historial de juego y facilitar la consulta de estadísticas de jugadores y grupos.

La idea surgió al identificar que muchos grupos conservan resultados en conversaciones y fotografías, lo que dificulta recuperar partidas anteriores y calcular estadísticas. El proyecto se encuentra en **etapa de análisis y diseño**, con documentación, modelos y un prototipo navegable; las funciones descritas son requisitos del sistema propuesto, no características ya implementadas.

## Alcance del sistema

La propuesta contempla perfiles de usuario, grupos, registro y corrección de partidas, participantes invitados, empates, historial, estadísticas y controles de privacidad. Las funciones sociales complementan estas capacidades, pero el registro de partidas y la consulta del historial son las prioridades principales identificadas en la elicitación.

## Documentación del proyecto

### Análisis y requisitos — Unidad 2

- [Visión del producto](docs/vision-del-producto.md)
- [Guion de entrevista y ficha de dominio](docs/guion-entrevista.md)
- [Bitácora de entrevista](docs/bitacora-entrevista.md)
- [Especificación de requisitos funcionales y no funcionales](docs/especificacion-requisitos.md)
- [Diagrama de casos de uso (editable)](docs/diagramas/casos-de-uso.drawio)
- [Diagrama de casos de uso (imagen)](docs/diagramas/casos-de-uso.png)

### Arquitectura y decisiones — Unidad 3

- [Diagramas C4 en Mermaid: contexto, contenedores y componentes](doc/arch/diagramas.md)
- [ADR-001: decisión de monolito modular](doc/arch/adr-001-monolito-modular.md)

La arquitectura propuesta es un **monolito modular**, organizado internamente en cuatro módulos: **Identidad y participantes**, **Grupos y contenido**, **Partidas** y **Estadísticas**. Se eligió para mantener separadas las responsabilidades sin introducir desde el inicio la complejidad operativa de los microservicios.

### Modelado orientado a objetos — Unidad 4

Se elaboró un diagrama de clases en Mermaid con entidades como `Usuario`, `Grupo`, `Partida`, `JuegoMesa`, `Participante`, `Resultado`, `Estadistica` y `Fotografia`. El modelo distingue entre participantes registrados e invitados y contempla reglas sobre resultados y partidas.

### Mantenimiento y evolución — Unidad 5

Las solicitudes de cambio y sus análisis de impacto se documentan en la carpeta `doc/cambios/`, siguiendo las plantillas **SC-001** y **AI-001** del curso. Cada análisis debe considerar efectos directos e indirectos sobre requisitos, casos de uso, arquitectura, diagramas y pruebas.

> **Nota:** los ejemplos de cambio utilizados para practicar no sustituyen una solicitud real recibida de la dupla de revisión. Cuando exista una solicitud real, debe identificarse al solicitante y documentarse su análisis correspondiente.

## Prototipo

[**Ver prototipo navegable de Podium en Figma**](https://www.figma.com/proto/TqQjTMT8wNM2V1mNhswcAF/Podium---Prototipo?node-id=1-125&scaling=min-zoom&content-scaling=fixed)

El prototipo presenta pantallas de inicio, descubrimiento de grupos, perfil, detalle de grupo y un ejemplo de flujo alterno de registro con información incompleta. Es una representación visual de las interacciones previstas, no una aplicación funcional.

## Estado del proyecto

**Análisis y diseño académico.** La documentación describe el sistema propuesto y las decisiones tomadas durante el semestre. La implementación, pruebas de software y despliegue quedan como etapas posteriores.
