# Podium

**Proyecto académico · Ingeniería de Software I (SIS3407)**  
**Autor:** Josué Tiburcio Cruz

## Descripción

Podium es una propuesta de red social para personas que disfrutan los juegos de mesa. Busca centralizar el registro de partidas, conservar resultados anteriores y facilitar la consulta de estadísticas de jugadores y grupos.

El proyecto surgió de la dificultad de encontrar partidas antiguas y calcular estadísticas cuando los resultados se guardan en mensajes y fotografías. La elicitación llevó a priorizar el **historial de partidas**, los **grupos** y las **estadísticas** por encima de algunas funciones sociales.

> **Estado actual:** proyecto en etapa académica de análisis y diseño. Los documentos describen funcionalidades previstas, modelos y decisiones arquitectónicas; no representan una aplicación completamente implementada.

## Alcance

Se contemplan perfiles, grupos, registro y corrección de partidas, participantes invitados, empates, historial, estadísticas y configuración de privacidad. El prototipo de Figma permite visualizar parte de estas interacciones.

## Documentación

### Unidades 1 y 2 · Visión, elicitación y requisitos

- [Visión del producto](docs/vision-del-producto.md)
- [Guion de entrevista y ficha de dominio](docs/guion-entrevista.md)
- [Bitácora de entrevista y hallazgos](docs/bitacora-entrevista.md)
- [Especificación de requisitos funcionales y no funcionales](docs/especificacion-requisitos.md)
- [Casos de uso — archivo editable (.drawio)](docs/diagramas/casos-de-uso.drawio)
- [Casos de uso — imagen (.png)](docs/diagramas/casos-de-uso.png)

### Unidad 3 · Arquitectura de software

- [Diagramas C4: contexto, contenedores y componentes](doc/arch/diagramas.md)
- [ADR-001: decisión de arquitectura — monolito modular](doc/arch/adr-001-monolito-modular.md)
- [Ejemplos de Mermaid utilizados en clase](doc/arch/ejemplos-guia-mermaid.md)

Se propone una arquitectura de **monolito modular** con cuatro módulos: **Identidad y participantes**, **Grupos y contenido**, **Partidas** y **Estadísticas**. La separación es interna; no implica cuatro servicios desplegados por separado.

### Unidad 4 · Diseño orientado a objetos y comportamiento

- [Diagramas de la Unidad 4 y revisión de consistencia](doc/arch/diagramas-unidad4.md)

Este documento reúne el diagrama de secuencia de **CU-01 Registrar una partida**, la máquina de estados de `Partida`, un diagrama de actividad complementario, una propuesta de ajuste del diagrama de clases y su revisión de consistencia con los requisitos y la arquitectura.

**Nota de revisión:** este archivo todavía identifica ajustes pendientes por validar (incluyendo el renderizado en Mermaid y la coherencia de algunas transiciones con los requisitos). No se consideran cambios implementados automáticamente.

### Unidad 5 · Mantenimiento y evolución

- [SC-001: solicitud de cambio — avisos de partidas](doc/cambios/sc-001-avisos-de-partidas.md)
- [AI-001: análisis de impacto — avisos de partidas](doc/cambios/ai-001-avisos-de-partidas.md)

La solicitud plantea avisos dentro de Podium al registrar o corregir partidas. El análisis documenta impactos directos e indirectos, riesgos, alternativas, estimación de esfuerzo y recomendación. **La solicitud se encuentra en estado Propuesta**, y el análisis no equivale a una implementación ni a una aceptación definitiva.

## Prototipo navegable

[**Abrir prototipo de Podium en Figma**](https://www.figma.com/proto/TqQjTMT8wNM2V1mNhswcAF/Podium---Prototipo?node-id=1-125&scaling=min-zoom&content-scaling=fixed)

El prototipo muestra Inicio, Descubrir, Perfil, un grupo de ejemplo y una pantalla de flujo alterno para datos incompletos al registrar una partida. Su finalidad es apoyar la validación visual de los requisitos.

## Organización del repositorio

```text
Podium/
├── README.md
├── docs/
│   ├── vision-del-producto.md
│   ├── guion-entrevista.md
│   ├── bitacora-entrevista.md
│   ├── especificacion-requisitos.md
│   └── diagramas/
│       ├── casos-de-uso.drawio
│       └── casos-de-uso.png
└── doc/
    ├── arch/
    │   ├── diagramas.md
    │   ├── adr-001-monolito-modular.md
    │   ├── ejemplos-guia-mermaid.md
    │   └── diagramas-unidad4.md
    └── cambios/
        ├── sc-001-avisos-de-partidas.md
        └── ai-001-avisos-de-partidas.md
```

## Estado y próximos pasos

La estructura documental está reunida en este repositorio. Los siguientes trabajos son validar y ajustar los diagramas de la Unidad 4, revisar la correspondencia con requisitos y casos de uso, cerrar las decisiones de cambio pendientes y continuar la evolución del prototipo.
