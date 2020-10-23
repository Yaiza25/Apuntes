# Preguntas y respuestas

## 1.- ¿Cómo ver qué archivos son diferentes entre 2 ramas con Git?

Básicamente el comando para ver las diferencias entre dos branches es:

    git diff branch1..branch2

Para listar qué archivos han cambiado entre dos branches puedes usar --name-status:

    git diff --name-status branch1..branch2

## 2.- ¿Cuál es la diferencia entre 'git rebase' y 'git merge'?

De forma menos visual pero más descriptiva, podemos referirnos a ello de la siguiente forma:

- git-rebase –> Genera una serie de commits secuencialmente, de modo que puedan aplicarse directamente sobre la cabeza del nodo.

Cuando haces un rebase en tu rama, le estás diciendo a Git que haga como si hubieras cambiado de rama (checkout) de una forma limpia y que luego empezaste a trabajar a partir de allí. Esto convierte los cambios en algo limpio y conceptualmente simple que otra persona podrá revisar. Puedes repetir este proceso otra vez cuando hay nuevos cambios en la otra rama: siempre terminarás con una serie de cambios limpios en la cabeza de la rama.

![rebase](https://i.stack.imgur.com/TvXuJ.png)

- git-merge –> Une dos o más historiales de desarrollo.

Cuando haces un merge de una rama en la tuya, juntas el historial de ambas. Si después haces esto otra vez, empezarás a crear una serie de historiales intercalados: algunos cambios de Daniel, algunos de Enrique, algunos de Daniel... lo que puede ser lioso.

![merge](https://i.stack.imgur.com/9Ul5w.png)

## 3.- ¿Cómo modificar el mensaje de un commit en particular?

Lo que tenés que hacer es un rebase interactivo (-i) usando el comando reword del mismo.

Primero ejecutá git rebase -i < hash del commit >~1 para pedir hacer rebase interactivo de la rama actual a partir del commit anterior (~1) al que estás queriendo modificar. Eso disparará tu $EDITOR con un listado de todos los commits que existen desde ese hasta el tope de tu rama, indicando pick, hash y mensaje de cada uno. Algo como:

    pick abcdef0 Mensaje del commit más nuevo
    pick bcdef01 Mensaje del commit anterior
    ...
    pick fde2152 Mensaje del commit a editar

Cambiá pick por r o reword en la línea del commit a editar. Algo así:

    pick abcdef0 Mensaje del commit más nuevo
    pick bcdef01 Mensaje del commit anterior
    ...
    r fde2152 Mensaje del commit a editar

Guardá el archivo y salí del editor, y git va a volver hasta ese commit y disparar el $EDITOR nuevamente, pero esta vez con el mensaje del commit ahí presente. Algo como:

    Mensaje del commit a editar

    Este mensaje es el que habías escrito en el primer
    git commit, y que ahora querés reemplazar por uno nuevo

Editá el mensaje para que quede como querés, grabá el archivo, salí del editor, y git aplicará todos los commits que faltaban para que tu rama quede igual, excepto por tener el mensaje actualizado.

No te olvides que estás modificando la historia de tu repositorio, por lo que si habías publicado el commit al que estás editando el mensaje o cualquiera de sus sucesores podés generar conflictos al resto de tu equipo.

## 4.- ¿Cómo revertir un commit, si ya subí los cambios al origen?

Podrías usar git rebase, para eliminar el ultimo commit.

    git rebase -i HEAD~1

Debes comentar la linea de código correspondiente al commit, guardar y salir del editor.

Posteriormente ejecutar.

    git push -f origin master