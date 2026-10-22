```mermaid
classDiagram
    %% INTERFAZ DE PERSISTENCIA
    class IPersistencia {
        <<interface>>
        +guardarJugadores(List~Jugador~ jugadores) void
        +cargarJugadores() List~Jugador~
        +guardarSanciones(List~Sancion~ sanciones) void
        +cargarSanciones() List~Sancion~
        +guardarReportes(List~Reporte~ reportes) void
        +cargarReportes() List~Reporte~
    }

    %% CLASE ABSTRACTA Y HERENCIA (POLIMORFISMO)
    class Sancion {
        <<abstract>>
        #int idSancion
        #String fechaInicio
        #String fechaFin
        #String nickNameJugador
        #String motivo
        #String adminResponsable
        #boolean activa
        -int contadorSanciones$
        +getSiguienteId()$ int
        +aplicarEfecto()* boolean
        +revocar(String motivoPerdon) void
        +gettersAndSetters()
    }

    class Advertido {
        -int nivelSeveridad
        -String advertenciaPrevia
        +aplicarEfecto() boolean
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
        -ArrayList~String~ permisos
        +tienePermiso(String permiso) boolean
        +gettersAndSetters()
    }

    class Reporte {
        -int idReporte
        -String fechaCreacion
        -String adminResponsable
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

    class GestorSanciones {
        -ArrayList~Sancion~ sancionesActivas
        +aplicarSancion(Jugador j, Sancion s) void
        +revocarSancion(int idSancion, String motivo) void
        +consultarHistorial(Jugador j) List~Sancion~
        +calcularReincidencia(Jugador j) boolean
    }

    %% CLASE DE PERSISTENCIA
    class PersistenciaArchivo {
        -String rutaCarpeta
        +guardarJugadores(List~Jugador~ jugadores) void
        +cargarJugadores() List~Jugador~
        +guardarSanciones(List~Sancion~ sanciones) void
        +cargarSanciones() List~Sancion~
        +guardarReportes(List~Reporte~ reportes) void
        +cargarReportes() List~Reporte~
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
    Sancion <|-- Advertido : extends
    IPersistencia <|.. PersistenciaArchivo : implements
    Jugador "1" *-- "0..*" Sancion : contiene historial
    Jugador "1" --> "1" Rango : tiene
    GestorJugadores "1" o-- "0..*" Jugador : administra
    GestorReportes "1" o-- "0..*" Reporte : administra
    GestorReportes *-- CriterioFiltro : contiene (nested)
    GestorSanciones --> Jugador : procesa
    GestorSanciones --> Sancion : administra
    GestorJugadores ..> JugadorNoEncontradoException : lanza
    Sancion ..> SancionInvalidaException : lanza
