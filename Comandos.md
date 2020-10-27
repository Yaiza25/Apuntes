# Comandos de consola

Los comandos mas simples y necesarios que debemos saber del "Simbolo del sistema" son:

- mkdir [nombre] -> Crea un directorio.
- cd [nombre del directorio] -> Cambiamos el directorio activo.
- rm /s /q [nombre del directorio o archivo] -> Borra un directorio/archivo.
- dir [nombre del directorio] -> Muestra una lista de archivos y subdirectorios en un directorio.
- echo [mensaje] -> Muestra un mensaje en pantalla.
- echo [mensaje] >> [nombre.txt] -> Se crea una nota con un texto.
- type [nombre del archivo] -> Permite visualizar en pantalla el contenido de un archivo de texto.
- [nombre.txt] -> Abre el archivo.
- copy [archivo original] [nombre del nuevo archivo] -> Copiamos un archivo.
- move [origen] [destino] -> Mueve un archivo o directorio a otro lugar.
- ren [nombre viejo] [nombre nuevo] -> Cambia el nombre a un directorio o archivo.
- tree [nombre del directorio] -> Muestra una estructura de archivos de forma grafica. 

Alguno de los comandos mas basicos y usados de GIT son:

- git version -> Muestra la version de git instalada.
- git init -> Inicia un nuevo repositorio o crea la carpeta oculta.
- git status -> Muestra los archivos.
    - git status -s -> Muestra los archivos modificados.
- git add . -> Agrega todos los archivos.
    - git add * .[extension del documento] -> Agrega los documentos con la extension especificada.
    - git add [nombre del documento] -> Agrega el documento especificado.
- git commit -m "[mensaje]" -> Crea una fotografia del proyecto en ese momento.
    - git commit -a -m "[mensaje]" -> Añade todos los documentos y crea una fotografia del proyecto en ese momento.
- git log --oneline -> Muestra los commit realizados.
- git resert --hard -> Viajamos al commit especifico o elimina los cambios futuros o restaura los documentos.
- git clone [URL] -> Descarga un repositorio completo.
- git push -> Sube todos los cambios locales al servidor remoto.
- git branch [nombre] -> Creamos una nueva rama.
- git checkout [nombre de la rama] -> Sirve para cambiar de rama.
- git merge [nombre de la rama] -> Juntamos la rama en la que estamos con la que hemos nombrado.