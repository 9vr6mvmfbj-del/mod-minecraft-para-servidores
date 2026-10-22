classDiagram
%% INTERFAZ DE PERSISTENCIA
class IPersistencia {
  <<interface>>
  + guardarJugadores(List~Jugador~ jugadores) void
  + cargarJugadores() List~Jugador~
  + guardarSanciones(List~Sancion~ sanciones) void
  + cargarSanciones() List~Sancion~
}
