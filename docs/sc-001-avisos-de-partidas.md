# SC-001: Avisos de nuevas partidas y correcciones dentro de Podium

**Proyecto revisado:** Podium  
**Fecha de elaboración:** 16 de noviembre de 2026  
**Elaborado para:** Ingeniería de Software I · SIS3407 · Unidad 5

## Estado

**Propuesta · 16 de noviembre de 2026.**

La solicitud permanece en este estado hasta que el dueño de Podium decida aceptarla, rechazarla o aplazarla. Si cambia su estado, deberá añadirse la decisión y su justificación, sin eliminar el historial.

## Quién la pide

**Marco Villegas**, en el papel de **dupla de revisión**.

## Qué se pide

Quiero que Podium me avise dentro de la aplicación cuando alguien de uno de mis grupos registre una partida nueva. También quisiera recibir un aviso si más adelante corrigen un resultado, para enterarme de lo que cambió sin tener que entrar a revisar cada grupo.

Los avisos deben poder consultarse cuando vuelva a abrir Podium y no deberían mostrarse a personas que no formen parte de ese grupo.

## Por qué

La utilidad principal de Podium es conservar y consultar resultados de juegos de mesa. Si un grupo registra varias partidas o corrige una puntuación, los demás integrantes pueden tardar en enterarse. Un aviso dentro de la aplicación facilitaría seguir la actividad y detectar cambios relevantes en el historial del grupo.

## Qué pasa si no se hace

Podium seguiría permitiendo registrar partidas y consultar estadísticas, pero cada integrante tendría que entrar a sus grupos para comprobar si existen resultados nuevos o corregidos. No es una falla que impida usar el sistema; es una oportunidad de mejorar la experiencia de seguimiento.

## Tipo de mantenimiento

- [ ] **Correctivo** · algo está mal y hay que repararlo
- [ ] **Adaptativo** · el entorno cambió y hay que ajustarse
- [x] **Perfectivo** · funciona, pero puede ser mejor
- [ ] **Preventivo** · todavía no falla, pero va a fallar

**Justificación:** se propone una funcionalidad adicional para mejorar la experiencia de consulta; no corrige un error existente ni responde a un cambio obligatorio del entorno.

## Criterio de aceptación

Se considerará atendida la solicitud si se comprueba que:

1. Al registrarse correctamente una partida en un grupo, cada integrante con cuenta activa de ese grupo, salvo quien la registró, dispone de un aviso dentro de Podium.
2. Cuando se corrige y guarda correctamente el resultado de una partida, los mismos destinatarios pueden consultar un nuevo aviso que indica que hubo una corrección.
3. Los avisos se conservan para consultarlos al volver a entrar a la aplicación.
4. Una persona que no pertenece al grupo no puede consultar sus avisos ni la información privada de sus partidas.
5. Si el registro o la corrección no se completa por datos inválidos, no se genera un aviso.

## Prioridad que sugiere el solicitante

**Media.** Ayuda a enterarse de los resultados y correcciones, pero la funcionalidad básica de registrar partidas, consultar el historial y calcular estadísticas debe seguir teniendo prioridad.

---

**Fin de la solicitud.** Este documento describe qué necesita el solicitante y por qué. No determina la tecnología ni los cambios internos del sistema; eso corresponde al análisis de impacto del dueño de Podium.
