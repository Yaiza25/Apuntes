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

## 5.- ¿Qué es la rama master en git?

### ¿Tiene algo de especial la rama master?

Es la que se crea por defecto, y como verás en el resto de mis respuestas no tiene nada más de especial.

NOTA: Hay que tener en cuenta que algunas aplicaciones podrían presuponer que esa rama debería existir. Además, tal y como expongo en los comentarios, si borras la rama master deberías borrar cualquier referencia (incluso un HEAD) que apunte a un commit de éste.

### ¿Es diferente de las ramas que creo con git branch?

No.

### ¿Es obligatoria?

No.

### ¿Pasará algo malo si la borro?

No, se borrará como cualquier otra rama, pero previamente tendrás que hacer un checkout a una rama diferente (o crearla si no tienes otras ramas):

    git branch -D master
        error: Cannot delete the branch 'master' which you are currently on.

    git checkout todo

        Branch todo set up to track remote branch todo from origin.
        Switched to a new branch 'todo'

    git branch -D master
        Eliminada la rama master (era b14f27f)

## 6.- Quitar archivos añadidos antes de un commit

Debes removerlos del index con:

    git reset <paths>

Para que entiendas mejor que sucede, lo que el comando git add hace, es agregar una entrada al "index" con el contenido actual del archivo en el "working tree" (tu directorio de trabajo).

Cuando digo agregar una entrada al "index", me refiero a que git add hace una copia de tu archivo de trabajo a una zona conocida como de staging o pre producción, desde donde luego tomara los archivos el comando git commit.

Esto son archivos nuevos así que están únicamente el working tree y en el index, pero no en el branch actual, por lo que no tienen HEAD así que no podrás obtenerlos de ahí.

git reset elimina el/los archivos del "index" y solo quedara el original en tu working tree. Que es lo que querías.

## 7.- ¿Por qué no debería reescribir commits publicados?

No se recomienda hacer ni git reset en repositorios públicos por la sencilla razón de que los commits nuevos reemplazan a los viejos y en la historia de tu repositorio se va a ver como si un pedazo de ella simplemente hubiera desaparecido.

Sin embargo, estas herramientas existen por una razón y dicha razón es que son útiles para pulir o mejorar la historia de nuestros repositorios. Por ejemplo, si tuvieras un repositorio con un montón de commits inútiles u obsoletos entonces tienes la oportunidades de juntarlos con los commits que sí son significantes y al final la historia de tu repositorio se verá ordenada y limpia.

La nota de precaución es para que los demás desarrolladores que pudieron haber clonado tu repositorio no tengan problemas navegando en la historia de commits. Si eso pasa y se hacen varios amends simultáneos podría causar una confusión bastante grande en el repositorio aunque la probabilidad es muy reducida.