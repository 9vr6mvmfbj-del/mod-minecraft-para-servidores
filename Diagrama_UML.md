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
        -int contadorSanciones$
        +int getSiguienteId()$
        +boolean aplicarEfecto()*
        +revocar(String motivoPerdon) void
        +gettersAndSetters()
    }
