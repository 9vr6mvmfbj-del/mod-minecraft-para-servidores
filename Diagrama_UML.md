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
        +guardarDonaciones(List~Donacion~ donaciones) void
        +cargarDonaciones() List~Donacion~
        +guardarComprasRango(List~CompraRango~ compras) void
        +cargarComprasRango() List~CompraRango~
    }

    %% CLASE ABSTRACTA Y HERENCIA
    class Sancion {
        <<abstract>>
        #int idSancion
        #Date fechaInicio
        #Date fechaFin
        #String nickNameJugador
        #String motivo
        #String adminResponsable
        #boolean activa
        -int contadorSanciones$+getSiguienteId() int$
        +aplicarEfecto() boolean*
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
        -Date fechaCreacion
        -String adminResponsable
        -String reportado
        -String denunciante
        -String motivo
        -String estado
        +gettersAndSetters()
    }

    %% NUEVA CLASE: DONACIONES
    class Donacion {
        -int idDonacion
        -double monto
        -Date fecha
        -String estado
        -Jugador jugador
        +registrar() void
        +gettersAndSetters()
    }

    %% NUEVA CLASE: COMPRA DE RANGOS
    class CompraRango {
        -int idCompra
        -double precio
        -Date fecha
        -String estado
        -Jugador jugador
        -Rango rangoComprado
        +confirmarCompra() boolean
        +gettersAndSetters()
    }

    %% GESTORES Y CLASE ANIDADA
    class GestorReportes {
        -ArrayList~Reporte~ listaReportes
        +agregarReporte(Reporte r) void
        +procesarReporte(int id, String estado) void
        +filtrarReportes(CriterioFiltro criterio) List~Reporte~
    }

    class CriterioFiltro {
        <<nested>>
        -String estadoBuscado
        -Date fechaInicio
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

    %% PERSISTENCIA EN ARCHIVOS
    class PersistenciaArchivo {
        -String rutaCarpeta
        +guardarJugadores(List~Jugador~ jugadores) void
        +cargarJugadores() List~Jugador~
        +guardarSanciones(List~Sancion~ sanciones) void
        +cargarSanciones() List~Sancion~
        +guardarReportes(List~Reporte~ reportes) void
        +cargarReportes() List~Reporte~
        +guardarDonaciones(List~Donacion~ donaciones) void
        +cargarDonaciones() List~Donacion~
        +guardarComprasRango(List~CompraRango~ compras) void
        +cargarComprasRango() List~CompraRango~
    }

    %% EXCEPCIONES PERSONALIZADAS
    class JugadorNoEncontradoException {
        +JugadorNoEncontradoException(String msg)
    }

    class SancionInvalidaException {
        +SancionInvalidaException(String msg)
    }

    %% HERENCIA
    Sancion <|-- Baneo : extends
    Sancion <|-- Mute : extends
    Sancion <|-- Advertido : extends

    %% IMPLEMENTACION DE INTERFAZ
    IPersistencia <|.. PersistenciaArchivo : implements

    %% RELACIONES DEL JUGADOR
    Jugador "1" --> "1" Rango : tiene
    Jugador "1" *-- "0..*" Sancion : historial

    %% RELACIONES DE REPORTES
    GestorReportes "1" o-- "0..*" Reporte : administra
    GestorReportes *-- CriterioFiltro : contiene
    GestorJugadores "1" o-- "0..*" Jugador : administra

    %% RELACIONES DE SANCIONES
    GestorSanciones --> Jugador : procesa
    GestorSanciones --> Sancion : administra

    %% NUEVAS RELACIONES: DONACIONES
    Jugador "1" --> "0..*" Donacion : realiza

    %% NUEVAS RELACIONES: COMPRAS DE RANGO
    Jugador "1" --> "0..*" CompraRango : realiza
    CompraRango "0..*" --> "1" Rango : adquiere

    %% EXCEPCIONES
    GestorJugadores ..> JugadorNoEncontradoException : lanza
    Sancion ..> SancionInvalidaException : lanza
