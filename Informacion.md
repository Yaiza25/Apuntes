# Informacion sobre GIT

## 1.- ¿Qué es GIT?

Git, es un software de control de versiones diseñado por Linus Torvalds. La pregunta es ¿qué es control de versiones? Pues bien, se define como control de versiones a la gestión de los diversos cambios que se realizan sobre los elementos de algún producto o una configuración del mismo es decir a la gestión de los diversos cambios que se realizan sobre los elementos de algún producto o una configuración, y para los que aún no les queda claro del todo, control de versiones es lo que se hace al momento de estar desarrollando un software o una página web. Exactamente es eso que haces cuando subes y actualizas tu código en la nube, o le añades alguna parte o simplemente le editas cosas que no funcionan como deberían o al menos no como tú esperarías.

Y, entonces ¿a que le llamamos sistema de control de versiones? Muy sencillo, son todas las herramientas que nos permiten hacer todas esas modificaciones antes mencionadas en nuestro código y hacen que sea más fácil la administración de las distintas versiones de cada producto desarrollado; es decir Git.

## 2.- Características

El diseño de Git se basó en BitKeeper y en Monotone. Originalmente fue diseñado como un motor de sistema de control de versiones de bajo nivel sobre el cual otros podrían codificar interfaces frontales, tales como Cogito o StGIT. Desde ese entonces hasta ahora el núcleo del proyecto Git se ha vuelto un sistema de control de versiones completo, utilizable en forma directa.

El diseño de Git mantiene una enorme cantidad de código distribuida y gestionada por mucha gente, que incide en numerosos detalles de rendimiento, y de la necesidad de rapidez en una primera implementación.

Entre las características más relevantes se encuentran:

- Fuerte apoyo al desarrollo no lineal, por ende rapidez en la gestión de ramas y mezclado de diferentes versiones.
- Gestión distribuida. Git le da a cada programador una copia local del historial del desarrollo entero, y los cambios se propagan entre los repositorios locales. 
- Los almacenes de información pueden publicarse por HTTP, FTP, rsync o mediante un protocolo nativo, ya sea a través de una conexión TCP/IP simple o a través de cifrado SSH. 
- Los repositorios Subversion y svk se pueden usar directamente con git-svn.
- Gestión eficiente de proyectos grandes, dada la rapidez de gestión de diferencias entre archivos, entre otras mejoras de optimización de velocidad de ejecución.
- Todas las versiones previas a un cambio determinado, implican la notificación de un cambio posterior en cualquiera de ellas a ese cambio.
- Resulta algo más caro trabajar con ficheros concretos frente a proyectos, eso diferencia el trabajo frente a CVS, que trabaja con base en cambios de fichero, pero mejora el trabajo con afectaciones de código que concurren en operaciones similares en varios archivos.
- Los renombrados se trabajan basándose en similitudes entre ficheros.
- Realmacenamiento periódico en paquetes. Esto es relativamente eficiente para escritura de cambios y relativamente ineficiente para lectura si el reempaquetado no ocurre cada cierto tiempo.

## 3.- Nubes de GIT

Github, GitLab, Bitbucket son herramientas basadas en la nube para construir software usando GIT. Normalmente cuando creas un repositorio a menos que tu empresa tenga montada su propia infraestructura dependerás de herramientas en la nube que faciliten a ti y a tu equipo trabajar en conjunto. Estas herramientas ayudan al trabajo con GIT, control de tickets y hacen más fácil toda la experiencia visual del trabajo.

- GitHub alberga mas de 50 millones de proyectos de código abierto.
GitLab es similar a su principal competidor, GitHub, existen algunas peculiaridades importantes. 
- GitLab tiene versiones diferentes, como GitLab SAAS que es adecuada para las empresas y GitLab Community Edition, una solución individual para los usuarios.
- Bitbucket esta mejor orientado a los equipos de desarrollo profesional, ya que proporciona grandes beneficios para ellos, como repositorios privados gratuitos, integración con Jira.