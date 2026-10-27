

Este archivo reproduce los ocho ejemplos de diagramas de la guía de clase. Los primeros tres corresponden a los niveles 1, 2 y 3 del modelo C4; los cinco restantes son ejemplos para practicar.

## 1. Nivel 1 · Diagrama de contexto

El sistema completo, quién lo usa y con quién habla.

```mermaid
flowchart TD
    rec([Recepcionista])
    vet([Veterinario])
    sis[Sistema de la clinica]
    lab[Laboratorio externo]
    pago[Pasarela de pagos]

    rec -->|agenda y cobra| sis
    vet -->|consulta expedientes| sis
    sis -->|envia estudios| lab
    sis -->|cobra consultas| pago

    style sis fill:#ff5d00,color:#fff
```

En este nivel no se especifican tecnologías: solamente el sistema, sus usuarios y las relaciones externas.

## 2. Nivel 2 · Diagrama de contenedores

Las piezas que se despliegan y se ejecutan por separado.

```mermaid
flowchart TD
    rec([Recepcionista])

    subgraph sistema[Sistema de la clinica]
        web[App web<br/>React]
        api[API<br/>Node.js]
        db[(Base de datos<br/>PostgreSQL)]
    end

    lab[Laboratorio externo]

    rec -->|usa| web
    web -->|HTTPS/JSON| api
    api -->|lee y escribe| db
    api -->|SFTP| lab

    style api fill:#ff5d00,color:#fff
```

En este nivel sí se muestran tecnologías y el límite del sistema mediante `subgraph`.

## 3. Nivel 3 · Diagrama de componentes

Lo que hay dentro de un contenedor.

```mermaid
flowchart TD
    web[App web]

    subgraph api[API del sistema]
        agenda[Agenda<br/>citas y horarios]
        cobros[Cobros<br/>cuentas y pagos]
        exp[Expedientes<br/>historial clinico]
        notif[Notificador<br/>interfaz de envio]
    end

    db[(Base de datos)]
    correo[Servicio de correo]

    web --> agenda
    web --> cobros
    web --> exp
    cobros -->|pregunta que se atendio| agenda
    cobros -->|enviarRecibo| notif
    notif --> correo
    agenda --> db
    cobros --> db
    exp --> db

    style cobros fill:#ff5d00,color:#fff
```

Este ejemplo representa la comunicación entre los componentes de la API del sistema.

## 4. Diagrama de flujo con decisiones

Los rombos y las flechas etiquetadas con Sí y No.

```mermaid
flowchart TD
    ini([Inicio])
    val{Monto mayor a cero?}
    exc{Excede el saldo?}
    apl[Aplicar el abono]
    err1[Monto invalido]
    err2[Excede el saldo]
    fin([Fin])

    ini --> val
    val -->|No| err1
    val -->|Si| exc
    exc -->|Si| err2
    exc -->|No| apl
    err1 --> fin
    err2 --> fin
    apl --> fin

    style apl fill:#ff5d00,color:#fff
```

Representa las validaciones del monto de un abono.

## 5. Diagrama de secuencia

Cómo se pasan mensajes entre componentes, en orden temporal.

```mermaid
sequenceDiagram
    actor Rec as Recepcionista
    participant Web as App web
    participant Cob as Cobros
    participant Age as Agenda
    participant BD as Base de datos

    Rec->>Web: Registra un abono de 500
    Web->>Cob: abonar(cuenta, 500)
    Cob->>Age: Que servicio se atendio?
    Age-->>Cob: Consulta general
    Cob->>BD: Guarda el pago
    BD-->>Cob: Listo
    Cob-->>Web: Pago registrado
    Web-->>Rec: Muestra el nuevo saldo
```

Muestra las llamadas y respuestas del registro de un abono.

## 6. Diagrama de clases

Atributos, métodos, visibilidad y multiplicidad.

```mermaid
classDiagram
    class CuentaDePaciente {
        -saldo: double
        -pagos: List~Pago~
        +abonar(monto) string
        +consultarSaldo() double
    }

    class Pago {
        -monto: double
        -fecha: Date
    }

    class Paciente {
        -nombre: string
        -especie: string
    }

    Paciente "1" --> "1" CuentaDePaciente : tiene
    CuentaDePaciente "1" --> "*" Pago : registra
```

El signo `-` indica un miembro privado, el `+` uno público y las multiplicidades indican cuántos elementos se relacionan.

## 7. Diagrama de estados

Por qué estados pasa una cita y qué evento produce cada cambio.

```mermaid
stateDiagram-v2
    [*] --> Agendada
    Agendada --> Confirmada: el dueno confirma
    Agendada --> Cancelada: se cancela a tiempo
    Confirmada --> Atendida: llega a consulta
    Confirmada --> NoAsistio: no se presenta
    Atendida --> [*]
    Cancelada --> [*]
    NoAsistio --> [*]
```

Los símbolos `[*]` indican inicio y fin del ciclo de vida.

## 8. Diagrama entidad-relación

Las tablas de la base de datos y sus relaciones.

```mermaid
erDiagram
    PACIENTE ||--o{ CITA : tiene
    PACIENTE ||--|| CUENTA : tiene
    CITA ||--o| EXPEDIENTE : genera
    CUENTA ||--o{ PAGO : registra

    PACIENTE {
        int id
        string nombre
        string especie
    }
    CITA {
        int id
        date fecha
        string motivo
    }
    PAGO {
        int id
        decimal monto
        date fecha
    }
```

Los símbolos de los extremos indican cardinalidad. Se mantiene el ejemplo y la estructura presentada en la guía.

---

**Nota:** Los ocho códigos anteriores corresponden al ejemplo académico de la clínica veterinaria mostrado en la guía. La adaptación al sistema Podium se realizará posteriormente.
