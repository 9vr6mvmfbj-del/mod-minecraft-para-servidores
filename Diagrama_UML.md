```mermaid
classDiagram
    %% INTERFAZ DE PERSISTENCIA
    class IPersistencia {
        <<interface>>
        +guardarJugadores(List~Jugador~ jugadores) void
        +cargarJugadores() List~Jugador~
        +guardarSanciones(List~Sancion~ sanciones) void
        +cargarSanciones() List~Sancion~
    }

    %% CLASE ABSTRACTA Y HERENCIA (POLIMORFISMO)
    class Sancion {
        <<abstract>>
        #int idSancion
        #String nickNameJugador
        #String motivo
        #String adminResponsable
        #boolean activa
        -int contadorSanciones$+getSiguienteId()$ int
        +aplicarEfecto()* boolean
        +revocar(String motivoPerdon) void
        +gettersAndSetters()
    }

    class Baneo {
        -int duracionDias
        -boolean esPermanente
        +aplicarEfecto() boolean
    }

    class Mute {
        -int duracionMinutos
        -String canalRestringido
        +aplicarEfecto() boolean
    }

    %% ENTIDADES DEL DOMINIO
    class Jugador {
        -String nickName
        -Rango rango
        -boolean sancionado
        -ArrayList~Sancion~ historialSanciones
        +agregarSancion(Sancion s) void
        +esReincidente() boolean
        +gettersAndSetters()
    }

    class Rango {
        -String nombre
        -int nivelPermiso
        +gettersAndSetters()
    }

    class Reporte {
        -int idReporte
        -String reportado
        -String denunciante
        -String motivo
        -String estado
        +gettersAndSetters()
    }

    %% GESTORES Y CLASE ANIDADA (NESTED CLASS)
    class GestorReportes {
        -ArrayList~Reporte~ listaReportes
        +agregarReporte(Reporte r) void
        +procesarReporte(int id, String estado) void
        +filtrarReportes(CriterioFiltro criterio) List~Reporte~
    }

    class CriterioFiltro {
        <<nested>>
        -String estadoBuscado
        -String fechaInicio
        +coincide(Reporte r) boolean
    }

    class GestorJugadores {
        -ArrayList~Jugador~ listaJugadores
        +registrarJugador(Jugador j) void
        +buscarJugador(String nick) Jugador
    }

    %% CLASE DE PERSISTENCIA
    class PersistenciaArchivo {
        -String rutaCarpeta
        +guardarJugadores(List~Jugador~ jugadores) void
        +cargarJugadores() List~Jugador~
        +guardarSanciones(List~Sancion~ sanciones) void
        +cargarSanciones() List~Sancion~
    }

    %% EXCEPCIONES PERSONALIZADAS
    class JugadorNoEncontradoException {
        +JugadorNoEncontradoException(String msg)
    }

    class SancionInvalidaException {
        +SancionInvalidaException(String msg)
    }

    %% RELACIONES Y JERARQUÍAS
    Sancion <|-- Baneo : extends
    Sancion <|-- Mute : extends
    IPersistencia <|.. PersistenciaArchivo : implements
    Jugador "1" *-- "0..*" Sancion : contiene en historial
    Jugador "1" --> "1" Rango : tiene
    GestorJugadores "1" o-- "0..*" Jugador : administra
    GestorReportes "1" o-- "0..*" Reporte : administra
    GestorReportes *-- CriterioFiltro : contiene (nested)
    GestorJugadores ..> JugadorNoEncontradoException : lanza
    Sancion ..> SancionInvalidaException : lanza
