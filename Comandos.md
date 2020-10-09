# Comandos de consola

Alguno de los comandos mas basicos y usados de git son:

- git version -> Muestra la version de git instalada.
- git init -> Inicia un nuevo repositorio o crea la carpeta oculta.
- git status -> Muestra los archivos.
    - git status -s -> Muestra los archivos modificados.
- git add . -> Agrega todos los archivos.
    - git add *.[extension del documento] -> Agrega los documentos con la extension especificada.
    - git add [nombre del documento] -> Agrega el documento especificado.
- git commit -m "[mensaje]" -> Crea una fotografia del proyecto en ese momento.
    - git commit -a -m "[mensaje]" -> Añade todos los documentos y crea una fotografia del proyecto en ese momento.
- git log --oneline -> Muestra los commit realizados.
- git resert --hard -> Viajamos al commit especifico o elimina los cambios futuros o restaura los documentos.
- git clone [URL] -> Descarga un repositorio completo.
- git push -> Sube todos los cambios locales al servidor remoto.