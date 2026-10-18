# Primera Entrega del Proyecto

# LINK DEL REPOSITORIO
*https://github.com/yhosy77/mod-minecraft-para-servidores*
---

# Skill Issue Admin - Plugin de Gestión para Servidores de Minecraft
**Grupo:** POO-Error Capa 8

# Nuevo nombre definitivo:
Skill Issue Admin
- La frase "Skill Issue", lo propusimos por su definición como una muletilla humorística de la comunidad para referirse a la "falta de habilidad", en este caso, por la falta de habilidad de un admin al tratar de controlar el caos de los baneos, rangos y reportes.

---

## Conformación del Equipo y Roles inciales:
| Nombre Completo | Rol Inicial | Responsabilidades Principales |
| :--- | :--- | :--- |
| **David Santiago Díaz** | Responsable de Producto (PO) | Cuidar el problema y validar que los RF respondan a las necesidades del proyecto. |
| **Samuel Gacharna** | Responsable de Producto (PO) | Apoyo en la definición de requerimientos y criterios de aceptación. |
| **Samuel Zona** | Responsable de Diseño (AR) | Liderar el diagrama de clases UML y el registro de decisiones de POO. |
| **Juan Bello** | Responsable de Diseño (AR) | Garantizar que la arquitectura y clases respeten el diseño estructurado. |
| **Miguel** | Responsable de Calidad (QA) | Definir criterios de aceptación, casos límite, pruebas y manejo de errores. |
| **Juan Felipe Camacho Landazábal** | Responsable de Integración (GI) | Administrar el repositorio de GitHub, ramas, PRs y frecuencia de commits. |

## PASO 1: Descripción del Problema y Contexto de Automatización

### 1. Contexto (Dominio)
El proyecto se ubica en el dominio de la administración de **servidores multijugador del Minecraft (Java obviamente)**. En estos entornos virtuales coinciden simultáneamente decenas o cientos de jugadores en tiempo real. Para garantizar una convivencia armónica y un juego justo, las comunidades requieren moderar comportamientos tóxicos, gestionar rangos/permisos y controlar sanciones de forma ordenada.

### 2. Actores del Sistema
* **Jugador (Player / User):** Usuario convencional del servidor. Puede jugar, interactuar y enviar reportes sobre infracciones cometidas por otros usuarios.
* **Administrador / Moderador (Admin / Staff):** Encargado de mantener el orden, revisar la cola de reportes, aplicar/revocar sanciones (bans, mutes, advertencias) y asignar rangos.
* **Sistema (Skill Issue Admin):** El plugin en Java que procesa los comandos, valida las reglas de negocio, administra la persistencia de datos y ejecuta las restricciones automáticas.

### 3. Proceso Actual (Cómo se hace hoy)
Actualmente, en muchos servidores medianos y pequeños, la moderación se realiza mediante un parche de métodos manuales e ineficientes:
1. Un jugador nota una infracción y debe avisar por chat general o abrir un ticket manual en un canal de Discord externo.
2. Los administradores anotan las sanciones en hojas de texto plano local, blocs de notas o mensajes dispersos.
3. Las sanciones como baneos o mutes temporales se gestionan manualmente o con comandos nativos aislados (`/ban`, `/mute`), sin guardar un historial unificado vinculante.

### 4. El Dolor
* **Las faltas se olvidan:** Si un jugador rompe las reglas varias veces pero lo atienden administradores distintos, nadie sabe que es reincidente y termina recibiendo castigos leves una y otra vez.
* **Mucho trabajo manual y desorden:** Anotar los baneos en notas sueltas, calcular a mano cuántos días dura un castigo y acordarse de quitarlo a tiempo quita mucho tiempo y da espacio a errores o injusticias.
* **Los reportes se pierden:** Los usuarios reportan un problema pero no saben si se atendió, y los dueños del servidor no tienen forma de revisar si los administradores están haciendo bien su trabajo.

### 5. Impacto de la Solución
* **Técnico:** Reemplaza las notas sueltas por un sistema ordenado que guarda toda la información automáticamente y la mantiene a salvo sin perder datos si la aplicación se cierra.
* **Económico:** Lleva un control claro de las compras de rangos y donaciones de los jugadores, evitando cobros duplicados o que se entreguen beneficios a la persona equivocada.
* **Social:** Hace que el juego sea más justo para todos, ya que las sanciones se aplican con reglas claras y automáticas para evitar favoritismos, dando además segundas oportunidades con periodos de prueba a quienes apelan.

---

## PASO 2: Requerimientos del Sistema

### Matriz de Requerimientos Funcionales (RF) y No Funcionales (RNF)
`**Esto va en el otro archivo**`

# Plan Hacia La Entrega 2

## Tabla de Trazabilidad Inicial

| Requerimiento | Clases Involucradas (Previstas) | Temas del Curso Aplicados | Estado Inicial |
| :---: | :--- | :--- | :---: |
| **RF-01 / RF-06** | `Reporte`, `GestorReportes` | Clases y Objetos, Encapsulamiento | Pendiente |
| **RF-02 / RF-05** | `Jugador`, `Rango` | Encapsulamiento, Atributos Privados | Pendiente |
| **RF-03 / RF-07** | `Sancion` (Abstracta), `Baneo`, `Mute` | Herencia, Clases Abstractas | Pendiente |
| **RF-04 / RF-08** | `HistorialSanciones`, `GestorJugadores` | Comunicación entre objetos | Pendiente |

##  Conformación del Equipo y Roles (Entrega 2)
| Nombre Completo | Rol Entrega 2 | Responsabilidades Principales |
| :--- | :---: | :--- |
| **David Santiago Díaz** | **Responsable de Diseño (AR)** | Liderar la arquitectura de clases, jerarquías de herencia, interfaces y el Registro de Decisiones v2. |
| **Juan Felipe Camacho Landazábal** | **Responsable de Diseño (AR)** | Diseñar el diagrama de clases UML actualizado y asegurar la correcta estructuración del código en Java. |
| **Samuel Zona** | **Responsable de Producto (PO)** | Validar que la implementación de la Entrega 2 cumpla los 10 Requerimientos Funcionales planteados. |
| **Juan Bello** | **Responsable de Producto (PO)** | Mantener la trazabilidad entre el problema, los requerimientos y los casos de uso del mod. |
| **Samuel Gacharna** | **Responsable de Calidad (QA)** | Diseñar las excepciones personalizadas, probar casos límite y verificar la persistencia sin errores. |
| **Miguel** | **Responsable de Integración (GI)** | Controlar la estructura del repositorio en GitHub, verificar commits de cada integrante y gestionar ramas. |
