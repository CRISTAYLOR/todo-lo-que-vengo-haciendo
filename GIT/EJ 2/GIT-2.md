Práctica: Introducción a Git - Ejercicios Nivel Medio
Objetivo General
El objetivo de esta práctica es que los estudiantes profundicen en el uso de Git, explorando conceptos intermedios y avanzados como la gestión de ramas remotas, resolución de conflictos, etiquetas (tags) y colaboración en repositorios remotos. A través de estos ejercicios, se familiarizarán con comandos más avanzados y técnicas clave para trabajar eficientemente en proyectos colaborativos.

Cada ejercicio incluye instrucciones detalladas para facilitar la comprensión y ejecución,

Ejercicio 1: Verificar la Configuración Global de Git
Antes de comenzar a trabajar en un proyecto colaborativo, es importante asegurarse de que tu configuración global está correctamente configurada.

Instrucciones Detalladas:

Abre una terminal o línea de comandos.
Inserta el comando adecuado para verificar tu nombre de usuario y dirección de correo electrónico configurados globalmente en Git.
Si no están configurados, configúralos usando los comandos apropiados.
Preguntas a responder:

1- ¿Qué comando debes usar para verificar tu configuración global?

    git config --global --list
    OPCION: configuración específica:
    git config --global user.name
    git config --global user.email


2- ¿Cómo puedes configurar tu nombre de usuario y dirección de correo electrónico globalmente?

    a- Si el nombre de usuario y el correo electrónico no están configurados, o deseas cambiarlos, usa los siguientes comandos:
    git config --global user.name "Tu Nombre"
    git config --global user.email "tuemail@example.com"

    b- Si solo deseas configurar estos valores para un repositorio específico (sin afectar otros), omite la opción --global y usa:
    git config user.name "Tu Nombre"
    git config user.email "tuemail@example.com"
    Esto establecerá la configuración solo para el repositorio en el que estés trabajando.



Ejercicio 2: Clonar un Repositorio Remoto
Para trabajar en un proyecto existente, necesitas clonar su repositorio desde una ubicación remota.

Instrucciones Detalladas:

Encuentra un repositorio público en GitHub o cualquier otro servicio de alojamiento de código.
Usa el comando adecuado para clonar el repositorio en tu máquina local.
Navega hasta la carpeta clonada y verifica que todos los archivos estén presentes.
Preguntas a responder:

1- ¿Qué comando usas para clonar un repositorio remoto?

    Se usa 
    git clone <URL-del-repositorio>

2- ¿Qué pasa si intentas clonar un repositorio que ya existe en tu máquina?

    Si intentas clonar un repositorio en una carpeta donde ya existe otro con el mismo nombre, Git mostrará un error similar a:
    fatal: destination path '<nombre-del-repositorio>' already exists and is not an empty directory.

    Soluciones:

    a- Eliminar o renombrar la carpeta existente antes de clonar de nuevo.

    b- Clonar el repositorio en una carpeta diferente usando:
    git clone <URL-del-repositorio> <nombre-diferente>
    Ejemplo:
    git clone https://github.com/torvalds/linux.git linux-copy



Ejercicio 3: Crear y Publicar una Rama Remota
Cuando trabajas en un proyecto colaborativo, es común crear ramas remotas para gestionar nuevas características o correcciones.

Instrucciones Detalladas:

Crea una nueva rama local llamada feature/new-ui.
Realiza algunos cambios en los archivos del proyecto.
Sube la rama al repositorio remoto para que otros colaboradores puedan acceder a ella.
Preguntas a responder:

1- ¿Qué comando usas para crear una rama local?

    Se usa git checkout -b feature/new-ui o git branch feature/new-ui seguido de git checkout feature/new-ui.

2- ¿Cómo subes una rama local al repositorio remoto?

    Usa git push -u origin feature/new-ui para subir la rama y establecer el seguimiento con la versión remota.

3- ¿Qué diferencia hay entre una rama local y una rama remota?

    La rama local está en tu PC la remota en tu repositorio online  

Ejercicio 4: Resolver Conflictos en Ramas
Los conflictos son inevitables cuando varios desarrolladores trabajan en el mismo archivo. Aprende a resolverlos.

Instrucciones Detalladas:

Crea dos ramas locales (branch-a y branch-b) a partir de la rama principal.
Modifica el mismo archivo en ambas ramas de manera diferente.
Intenta fusionar branch-a y branch-b con la rama principal.
Resuelve los conflictos manualmente y completa la fusión.
Preguntas a responder:

1- ¿Qué ocurre cuando Git detecta un conflicto durante una fusión?

    Cuando Git detecta un conflicto, no puede completar la fusión automáticamente. En su lugar:

    a- Git marcará los archivos en conflicto y los dejará sin cambios hasta que los edites manualmente.
    b- Te mostrará un mensaje de error indicando en qué archivos hay conflictos.

2- ¿Cómo identificas las secciones conflictivas en un archivo?

    Abre el archivo en conflicto (ejemplo.txt). Verás algo como esto:

    <<<<<<  HEAD
    cambio en branch-a
    =======
    Cambio en branch-b 
    >>>>>> branch-b

    Indicaciones:
    <<<<<<< HEAD: Muestra la versión actual en main.
    =======: Divide las dos versiones en conflicto.
    >>>>>>> branch-b: Muestra la versión de branch-b

3- ¿Qué pasos sigues para resolver un conflicto y completar la fusión?

    EDICIÓN:

    a- EDITAR ARCHIVO

    Edita manualmente el archivo para decidir qué cambios conservar. Puedes combinar ambos cambios o elegir uno.

    Esto veremos después de resolver el conflicto:
    Cambio en branch-a y branch-b combinados

    b- MARCAR ARCHIVO COMO RESUELTO

    Una vez editado, agrega el archivo a la zona de preparación:
    git add archivo.txt

    c- COMPLETAR LA FUSIÓN

    Finaliza la fusión con:
    git commit -m "Resuelto conflicto entre branch-a y branch-b"

    CHECKEO:

    Después de esto, la rama main tendrá la fusión completa de ambas ramas con los conflictos resueltos.

Ejercicio 5: Etiquetar Versiones Importantes
Las etiquetas (tags) son útiles para marcar versiones importantes de tu proyecto.

Instrucciones Detalladas:

Crea una etiqueta llamada v1.0.0 en el último commit de la rama principal.
Verifica que la etiqueta ha sido creada correctamente.
Sube la etiqueta al repositorio remoto.
Preguntas a responder:

1- ¿Qué comando usas para crear una etiqueta en Git?

    git tag <nombre-de-la-etiqueta> (Etiqueta ligera)
    git tag -a <nombre-de-la-etiqueta> -m "Mensaje" (Etiqueta anotada)


2- ¿Cómo puedes listar todas las etiquetas existentes en tu repositorio?

    Con git tag

3- ¿Por qué es útil utilizar etiquetas en tus proyectos?

    a- Permiten marcar versiones importantes del proyecto (como v1.0.0, v2.0.0).
    b- Facilitan el mantenimiento y el control de versiones.
    c- Ayudan a los equipos a identificar y distribuir versiones específicas del software.


Ejercicio 6: Revertir Cambios en un Commit
A veces es necesario revertir cambios realizados en un commit específico.

Instrucciones Detalladas:

Identifica el hash del commit que deseas revertir.
Usa el comando adecuado para revertir este commit sin eliminar la historia del repositorio.
Verifica que los cambios han sido revertidos correctamente.
Preguntas a responder:

1- ¿Qué comando usas para revertir un commit en Git?

    git revert <commit-hash>, lo que crea un nuevo commit que deshace los cambios del commit original.

2- ¿Cuál es la diferencia entre revertir un commit y eliminarlo completamente?

    Revertir (git revert): Crea un nuevo commit que deshace los cambios, manteniendo el historial del repositorio intacto.
    Eliminar (git reset --hard <commit-hash>): Borra commits de la historia, lo que puede causar problemas si los commits ya fueron empujados a un repositorio remoto.

3- ¿Por qué es importante mantener la historia del repositorio intacta?

    a- Transparencia: Permite ver qué cambios se hicieron y cuándo.
    b- Colaboración: Evita problemas para otros desarrolladores que trabajan en el mismo proyecto.
    c- Seguridad: Mantiene un registro claro de cambios, facilitando revertir problemas en el futuro.


Ejercicio 7: Trabajar con Ramas Origen/Destino
Cuando trabajas en ramas, es útil especificar explícitamente la rama origen y destino durante una fusión.

Instrucciones Detalladas:

Crea una rama llamada bugfix/login-issue.
Realiza algunos cambios en esta rama.
Fusiona los cambios de bugfix/login-issue a la rama principal utilizando el parámetro --no-ff para preservar la historia de la rama.
Verifica que la fusión se ha realizado correctamente.
Preguntas a responder:

1- ¿Qué significa el parámetro --no-ff en una fusión?

    El parámetro --no-ff (sin avance rápido) preserva la historia de la rama fusionada. En lugar de mover directamente el puntero de main al último commit de bugfix/login-issue, Git crea un nuevo commit de fusión, manteniendo el historial de la rama.

2- ¿Por qué es útil preservar la historia de una rama después de fusionarla?

    a- Claridad en el historial: Muestra que los cambios provinieron de una rama específica.
    b- Trazabilidad: Facilita rastrear qué cambios correspondían a una corrección o nueva funcionalidad.
    c- Mejor organización: En equipos grandes, ayuda a entender cómo se incorporaron las modificaciones.

3- ¿Qué ocurre si omites el parámetro --no-ff?

    Si omites --no-ff, Git usa una fusión con avance rápido (fast-forward), lo que significa que la rama main simplemente se moverá al último commit de bugfix/login-issue. Esto no creará un commit de fusión, haciendo que la historia de la rama desaparezca y parezca que los cambios se hicieron directamente en main.


Ejercicio 8: Actualizar y Sincronizar con el Repositorio Remoto
Mantener tu repositorio local sincronizado con el remoto es crucial para evitar problemas.

Instrucciones Detalladas:

Verifica si hay actualizaciones disponibles en el repositorio remoto.
Descarga las actualizaciones y fusiona los cambios con tu rama local.
Sube tus cambios locales al repositorio remoto.
Preguntas a responder:

1- ¿Qué comando usas para verificar si hay actualizaciones disponibles en el repositorio remoto?

git fetch (trae los cambios del remoto sin fusionarlos).
git remote show origin (muestra información detallada sobre el estado del remoto).

2- ¿Cómo descargas las actualizaciones y las fusionas con tu rama local?

    git pull origin <rama> (descarga y fusiona automáticamente los cambios).
    git pull --rebase origin <rama> (descarga los cambios y reordena los commits locales encima de los remotos).

3- ¿Qué ocurre si hay conflictos durante la sincronización? ¿Cómo los resuelves?

    Si Git detecta conflictos al hacer git pull, mostrará mensajes como:
    CONFLICT (content): Merge conflict in archivo.txt

    Para resolverlos:

    a- Abre el archivo con conflicto y edítalo manualmente, eligiendo qué cambios conservar.

    b- Marca el conflicto como resuelto añadiendo el archivo al área de preparación:
    git add archivo.txt

    c- Finaliza la fusión con:
    git commit -m "Resuelto conflicto en archivo.txt"

    d- Si aún no has subido los cambios, haz git push:
    git push origin main

Ejercicio 9: Usar Alias para Comandos Frecuentes
Crear alias para comandos frecuentes puede ahorrar tiempo y mejorar tu productividad.

Instrucciones Detalladas:

Crea un alias para el comando git status llamado gst.
Prueba tu nuevo alias para verificar que funciona correctamente.
Preguntas a responder:

1- ¿Cómo creas un alias para un comando Git?

    con el siguiente comando: git config --global alias.<nombre-del-alias> "<comando>"

2- ¿Qué otros comandos frecuentes podrías simplificar con alias?

    a- EJEMPLOS DE ALIAS:
    git config --global alias.co "checkout"
    git config --global alias.br "branch"
    git config --global alias.ci "commit"
    git config --global alias.st "status"

    b- ATAJOS Y FACILIDADES (algunos de ellos)

    git co → checkout
    git config --global alias.co "checkout"

    git br → branch
    git config --global alias.br "branch"

    git ci → commit
    git config --global alias.ci "commit -m"

    git lg → Ver historial de commits en formato gráfico
    git config --global alias.lg "log --oneline --graph --decorate --all"

3- ¿Cómo puedes hacer que tus alias sean persistentes entre sesiones?

    Los alias creados con git config --global se guardan en el archivo de configuración global de Git (~/.gitconfig en Linux/macOS o C:\Users\tu_usuario\.gitconfig en Windows).

    a- Puedes verificar tus alias con:
    git config --global --list

    b- Editar el archivo directamente con:
    nano ~/.gitconfig  # Linux/macOS
    notepad C:\Users\tu_usuario\.gitconfig  # Windows


Ejercicio 10: Colaborar en un Proyecto con Pull Requests
En proyectos colaborativos, los pull requests son una herramienta fundamental para revisar y discutir cambios antes de integrarlos.

Instrucciones Detalladas:

Crea una rama para una nueva funcionalidad o corrección.
Sube tus cambios al repositorio remoto.
Crea un pull request en GitHub u otra plataforma similar.
Solicita comentarios de otros colaboradores y realiza ajustes según sea necesario.
Preguntas a responder:

1- ¿Qué es un pull request y cuál es su propósito?

    Un pull request (PR) es una solicitud para fusionar los cambios de una rama a otra en un repositorio. El propósito de un PR es revisar el código antes de integrarlo a la rama principal o de desarrollo, proporcionando un espacio para discusión, comentarios y revisión de calidad de código.
    
2- ¿Cómo creas un pull request en GitHub?

    Para crear un pull request en GitHub:

    a- Empuja tus cambios a la rama remota.
    b- En GitHub, navega a tu repositorio y selecciona la opción "Compare & pull request".
    c- Rellena el título y la descripción del PR.
    d- Selecciona las ramas de origen y destino.
    e- Haz clic en "Create pull request".

3- ¿Qué pasa si recibes comentarios o sugerencias sobre tus cambios?

    Si recibes comentarios o sugerencias sobre tus cambios, puedes:

    a- Revisar el feedback y entender las mejoras propuestas.
    b- Modificar el código en tu rama local según los comentarios.
    c- Hacer nuevos commits con los ajustes y luego hacer un nuevo git push para actualizar el PR.
    d- GitHub mantendrá el pull request actualizado con los nuevos cambios.
