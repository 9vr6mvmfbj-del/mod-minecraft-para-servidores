Bitacora de IA del proyecto "Skill Issue Admin"

La idea de hacer un mod de minecraft fue propuesta por Felipe, pero tras su previa experiencia programando mods, y las complicaciones que le conllevó animar, un asistente de IA (claude) mandó algunas propuestas para darle un nuevo enfoque al proyecto sin la necesidad de agregar mobs (animales y mounstros), y fue discutida con el equipo hasta definir Esta idea del proyecto.

# Primer integrante
### Yo, David Santiago Díaz Lozano (Responsable de producto), hago reporte sobre mi uso de IA.
`Inteligencia Artificial Usada`: Gemini.

`Prompt`: *Una pregunta Gemini, si existen varios "Git hub", en qué se diferencian y por qué nunca había escuchado de Git lab y los otros, pero si he escuchado solo de Github? acaso los otros son tan malos que nunca se usan?*

**Respuesta:** La razón por la cual casi solo se escucha hablar de GitHub es porque se convirtió en el estándar de la comunidad global de desarrollo, los proyectos de código abierto (open source) y la formación académica.¿En qué se diferencian si todos usan Git?Todos estos servicios tienen el mismo motor técnico por debajo: Git. Los comandos de Git que ejecutas en la consola de tu computadora funcionan exactamente igual en todos ellos.   La diferencia no está en cómo guardas tu código, sino en la interfaz web, las herramientas adicionales que ofrecen y el público al que están dirigidos:   GitHub: Es el estándar para proyectos públicos, educación y la comunidad de desarrolladores. Funciona como una "red social" para programadores donde la gente comparte proyectos y arma su portafolio.GitLab: Es una de las alternativas más usadas en empresas medianas y grandes. Destaca por tener herramientas avanzadas de CI/CD (Integración y Despliegue Continuo) nativas y por permitir instalar la plataforma en servidores propios (self-hosted), algo crucial para la privacidad corporativa. En lugar de llamar a los cambios Pull Requests como en GitHub, los llama Merge Requests.   Bitbucket: Pertenece a la empresa Atlassian. Es extremadamente popular en empresas porque se integra de forma directa con herramientas de gestión de proyectos como Jira y Confluence.Azure DevOps: Es la plataforma de Microsoft integrada con su ecosistema de la nube para entornos corporativos.Codeberg: Una alternativa sin fines de lucro, alojada en Europa, pensada para quienes buscan una opción verdaderamente libre y centrada en la privacidad.   ¿Por qué casi solo se conoce GitHub si no estás en la industria?Efecto de red: Al concentrar la gran mayoría de bibliotecas y proyectos de código abierto del mundo, la comunidad de programadores converge naturalmente en GitHub.Uso académico y tutoriales: Como es la plataforma pública más grande, casi todos los cursos universitarios, bootcamps y guías de programación la eligen como plataforma predeterminada para enseñar.Portafolio profesional: En los procesos de contratación de programadores junior, es común mostrar la cuenta de GitHub como prueba de código enviado o proyectos realizados.

`Siguiente prompt`: *ok ok, yo estoy haciendo un proyecto junto con mis amigos para Programación Orientada a Objetos, y pues quería preguntarte si algunas de estas plataformas nos podrían dar una ventaja en nuestro proyecto que estamos haciendo en Github, sin perder el foco  obviamente. Es decir, que si me recomiendas hacer o utilizar una de estas herramientas para alguna cosa de nuestro proyecto, sin perder de vista que tenemos que finalizar nuestro proyecto.*

**Respuesta:** Para un proyecto universitario de Programación Orientada a Objetos (POO) donde la prioridad es la entrega y la calidad del código, la recomendación definitiva es no cambiar de plataforma y quedarse en GitHub.Migrar el repositorio a GitLab o Bitbucket en este momento no les dará una ventaja técnica directa sobre su proyecto, pero sí les sumaría una curva de aprendizaje y tiempo de configuración que podría restarles atención a lo realmente importante: la arquitectura de clases, el diseño y la entrega a tiempo.Sin embargo, sí pueden sacarle una ventaja gigantesca a GitHub utilizando herramientas que ya vienen integradas en la plataforma y que la mayoría de los estudiantes no aprovechan. Esto mejorará la coordinación de tu equipo y le dará una presentación impecable al proyecto frente a tu profesor:1. Organización del trabajo con GitHub Projects (Tablero Kanban)En proyectos de POO es muy común repartir el desarrollo por módulos, diagramas de clases o componentes.Ventaja: En lugar de coordinar por chat qué hace cada uno, usen la pestaña Projects dentro de su repositorio en GitHub.Cómo usarlo: Creen un tablero tipo Kanban sencillo con tres columnas: Por hacer, En progreso y Hecho. Asignen cada clase o requerimiento (ej. "Crear clase Usuario", "Implementar interfaz de la base de datos") a un integrante del grupo.2. Flujo de trabajo con Ramas (Branches) y Pull Requests (PR)Una de las mayores pérdidas de tiempo en proyectos grupales son los conflictos al fusionar el código (merge conflicts) o cuando alguien sobrescribe por error el trabajo de otro.Ventaja: Nadie debe subir código directamente a la rama principal (main).Cómo usarlo: Cada integrante crea una rama secundaria para su tarea (ej. feature/clase-estudiante), trabaja ahí, y al terminar abre un Pull Request para que otro compañero revise el código antes de unirlo a main. (Recordatorio: en GitLab esto se conoce como Merge Request, pero la lógica en GitHub es exactamente la misma).   3. Registro de errores con GitHub IssuesVentaja: Les permite rastrear errores (bugs) o pendientes sin olvidar nada.Cómo usarlo: Si durante la prueba del programa encuentran un fallo (ej. "El método calcularPromedio() arroja una excepción NullPointer"), abran un Issue, etiquétenlo como bug y asígnesenlo a quien escribió esa parte del código.4. Integración Continua con GitHub Actions (Opcional)Si en su curso de POO están realizando pruebas unitarias (como JUnit en Java o pytest en Python):Ventaja: Pueden configurar una GitHub Action muy básica (toma menos de 5 minutos usando las plantillas predeterminadas de GitHub).Cómo usarlo: Cada vez que alguien suba código o cree un Pull Request, GitHub ejecutará automáticamente las pruebas unitarias y les avisará si el nuevo código rompió alguna funcionalidad existente.


### Reporte de IA: Felipe Camacho

`Inteligencia Artificial Usada`: ChatGPT.

## 1. ¿El proyecto debería desarrollarse como un mod de Minecraft o como un plugin de servidor?

**Respuesta:**  
Las funcionalidades principales de *Skill Issue Admin* —reportes, sanciones, rangos, historial y persistencia— corresponden principalmente a lógica del servidor, por lo que un **plugin de Paper/Spigot** resulta más adecuado. Un mod sería necesario principalmente si se requirieran modificaciones del cliente o nuevas mecánicas, bloques, ítems o interfaces.

## 2. ¿Ha cambiado significativamente la forma de desarrollar plugins en versiones recientes de Minecraft?

**Respuesta:**  
Sí. Un cambio importante ocurrió en **Paper 1.20.5**, especialmente en el uso de mappings y acceso a internals/NMS. Sin embargo, la estructura tradicional basada en `JavaPlugin` y `plugin.yml` continúa siendo válida. Paper recomienda utilizar su API en lugar de depender directamente de NMS por problemas de compatibilidad entre versiones. 

## 3. ¿Es obligatorio utilizar Java 25 para el proyecto?

**Respuesta:**  
Solo si se utiliza **Minecraft 26.1 o superior**. Estas versiones requieren Java 25. Para mantener Java 21, que es la versión utilizada en clase, se puede trabajar con **Minecraft 1.21.11 + Paper**, que continúa utilizando Java 21. 

## 4. ¿Es obligatorio utilizar Kotlin para desarrollar el plugin?

**Respuesta:**  
No. Paper permite desarrollar plugins en Java, Kotlin, Groovy y Scala. El uso de `build.gradle.kts` corresponde al sistema de configuración de Gradle y **no significa que el código del plugin deba estar escrito en Kotlin**. El proyecto puede desarrollarse completamente en Java.

## 5. ¿Podemos hacer el proyecto como un mod utilizando únicamente Java?

**Respuesta:**  
Sí. Fabric permite desarrollar mods utilizando Java y, técnicamente, *Skill Issue Admin* podría implementarse como un mod server-side. Sin embargo, dado que los requerimientos principales corresponden a administración y lógica del servidor, un plugin de Paper sigue siendo una alternativa más directa para este proyecto.

Bitacora de IA de la entrega dos del proyecto "Skill Issue Admin":

## 

`Inteligencia Artificial Usada`: ChatGPT.

### 6. Propuesta para la gestión de reportes mediante interfaces gráficas

### Reporte de IA: Felipe Camacho

`Inteligencia Artificial Usada`: ChatGPT.

`Prompt`: *Dame una idea para este requerimiento que planteamos para que el server siga siendo "jugable" para los mods y que no les salgan chorrocientos reportes en pantalla a la vez: El sistema debe permitir al administrador atender los reportes recibidos, cambiando su estado hasta resolverlos o descartarlos. Tengo la idea de que se pueda abrir como un inventario y que se ordenen los jugadores por cantidad de reportes para que puedan ser atendidos por "prioridad"... qué tan viable es esa idea? Y que propondrías tu?*

**Respuesta:** La idea de utilizar un inventario gráfico para gestionar los reportes es viable y encaja con el objetivo del plugin: administrar la moderación sin interrumpir la experiencia de juego. Se propuso implementar un centro de reportes accesible mediante el comando `/reportes`, desde el cual los moderadores puedan consultar y gestionar los casos pendientes.

La interfaz principal podría representar a cada jugador reportado mediante su cabeza de Minecraft. La descripción del objeto mostraría la cantidad de reportes recibidos, los motivos y la hora del reporte más reciente. Los casos se organizarían por prioridad y se incluirían botones para navegar entre páginas.

Se propuso clasificar los reportes en tres niveles de prioridad:

- **Alta:** reportes urgentes o múltiples reportes recientes.
- **Media:** jugadores con varios reportes pendientes.
- **Baja:** reportes aislados sin indicios de urgencia.

Sin embargo, la cantidad de reportes no debe considerarse una prueba de culpabilidad. Por ejemplo, varios reportes coordinados contra un jugador inocente no deberían desplazar automáticamente un caso potencialmente más grave.

Al seleccionar un jugador, se abriría una segunda interfaz que permitiría consultar sus reportes individuales, incluyendo el motivo, el reportante, la hora y las evidencias disponibles. Desde esta interfaz, el moderador podría cambiar el estado del reporte a `EN_REVISION`, resolverlo o descartarlo si no procede.

Para evitar interrupciones durante el juego, también se propusieron las siguientes medidas:

1. **Notificaciones agrupadas:** evitar que aparezca un mensaje por cada reporte recibido; en su lugar, acumularlos en la interfaz.
2. **Notificaciones discretas:** mostrar mensajes breves, como «Hay 3 reportes pendientes», con la posibilidad de desactivarlos.
3. **Actualización de datos:** consultar los reportes más recientes al abrir la interfaz, evitando que el moderador tenga que reiniciar el menú para ver los cambios.

Para la primera versión se recomendó priorizar la creación del inventario de reportes pendientes, el ordenamiento por antigüedad y cantidad de reportes recientes, la interfaz de detalle, las acciones para revisar, resolver y descartar casos, y la persistencia de los reportes y sus estados después de reiniciar el servidor.

**Conclusión:** La propuesta es técnicamente viable mediante Paper/Bukkit y permite relacionar los requerimientos del plugin con los conceptos de la segunda entrega académica: entidades de negocio, colecciones, operaciones CRUD y persistencia. Se recomienda conservar la idea del inventario gráfico, complementándola con un sistema de prioridades y una interfaz para gestionar los reportes individuales. Los criterios definitivos deberán validarse con los requerimientos del proyecto antes de su implementación.

