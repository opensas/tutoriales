Introducción a git y github
===========================

tl;dr (está bien, ya conozco la teoría, quiero el resumen ayuda-memoria)

Sistemas de control de versiones
--------------------------------

A la hora de desarrollar una aplicación, un sitio web o una visualización, vamos generando distintos archivos (archivos de código fuente, html, documentación, planillas, hojas de estilo, gráficos, etc) que son los que conformarán nuestro proyecto.

A medida que estos proyectos se vuelven más complejos se torna indispensable poder llevar el control de los cambios que efectuamos, en especial cuando trabajamos en equipo y debemos recibir y gestionar contribuciones de terceros.

Para eso surgieron los <a href='http://es.wikipedia.org/wiki/Control_de_versiones'>sistemas de control de versiones</a>, que nos permiten almacenar los archivos que queremos gestionar, actualizarlos y llevar el registro histórico de las acciones efectuadas sobre cada elemento.

Git
---

Uno de los sistemas de control de versiones que últimamente ha cobrado gran popularidad es <a href='http://es.wikipedia.org/wiki/Git'>Git</a>. Fue creado por <a href='http://es.wikipedia.org/wiki/Linus_Torvalds'>Linus Torvalds</a> en 2005, para gestionar el código fuente del <a href='http://es.wikipedia.org/wiki/Linux_(núcleo)'>núcleo del sistema operativo Linux</a>. Git es además <a href='http://es.wikipedia.org/wiki/Software_libre'>software libre</a> publicado bajo la licencia <a href='https://gnu.org/licenses/old-licenses/lgpl-2.0.html'>GPL v2</a>.

A diferencia de otros sistemas de control de versiones que cuentan con un repositorio central al cual hay que conectarse para obtener o enviar nuevas versiones, git es un sistema distribuido. Esto significa que cada repositorio de git contiene todo el historial del proyecto y es completamente autónomo e independiente de cualquier otro repositorio central o acceso a la red.

Para más información acerca de Git puedes consultar <a href='http://git-scm.com/'>su sitio web</a>, en el cual encontrarás también el libreo <a href='http://git-scm.com/book'>Pro Git</a> completo en castellano.

Github
------

Github es un servicio web que te permite alojar el código fuente de tus proyectos, y utiliza git como sistema de control de versiones. Pero la principal característica de Github es que provee una plataforma social para el desarrollo de aplicaciones, permitiéndote publicar tus proyectos, seguir aquéllos que te interesan, colaborar con proyectos existentes y toda una serie de servicios sumamente útiles para trabajar de manera colaborativa.

Muchos lo describen como 'el Facebook de los desarrolladores', pero últimamente su uso alcanza a otras profesiones, y hacia principios de 2013 ya contaba con más de tres millones de usuarios alojando más de cinco millones de repositorios (<a href='https://en.wikipedia.org/wiki/GitHub#cite_ref-27'>ver cita</a>).

Manos a la obra
===============

Instalando git
--------------

Lo primero que debemos hacer es <a href='http://git-scm.com/book/es/Empezando-Instalando-Git#Instalando-en-Linux'>instalar git</a> en nuestras estaciones de trabajo.

Si estás utilizando Ubuntu (o cualquier otra distribución basada en Debian) sólo tienes que abrir una ventana de comandos, y ejecutar la siguiente orden:

```
$ sudo apt-get install git
```

Si estás usando Fedora (o cualquier otra distribución que usa paquetes rpm) deberás abrir una ventana de comandos e ingresar:

```
$ yum install git-core
```

Para probar que git se instaló correctamente ingresa el siguiente comando:

```
$ git --version
git version 1.8.1.2
```

Luego deberás [configurar git](http://git-scm.com/book/es/Empezando-Configurando-Git-por-primera-vez). Ingresa los siguientes comandos para configurar tu nombre de usuario y dirección de correo electrónico.

```
$ git config --global user.name "mi nombre de usuario"
$ git config --global user.email mi_mail@ejemplo.com
```

Esto es importante ya que cada vez que confirmes un cambio (commit) esta información será almacenada por git para tener registro de qué persona hizo cada cambio. A su vez, github utiliza esta cuenta de correo para asociar cada cambio con tu cuenta de github, así que tenés que configurar la misma cuenta de correo que vayas a utilizar para registrar tu cuenta en github.

Para este tutorial utilizaremos el usuario 'hackatoner' y la cuenta de mail 'hackatoner.programar@gmail.com'

![configurando git](images/github/github_config.png "Configurando git")

Nota: También incluiremos esta configuración evitar un mensaje bastante molesto que git emite y para que tenga un comportamiento más conservador a la hora de actualizar ramas remotas. Para más información podés consultar <a href='http://stackoverflow.com/a/13148313/47633'>esta respuesta</a> en stackoverflow.

```
$ git config --global push.default simple
```

Registrar una cuenta en github
------------------------------

Ahora deberás registrar una cuenta en github. Para ello, navegá a https://github.com, ingresá tu nombre de usuario, dirección de correo y una clave, y luego hacé click en 'Sign up for GitHub'.

picture github-signin.com

En nuestro caso elegimos como nombre hackatoner, y nuestra dirección de correo es hackatoner.programar@gmail.com.

Luego de registrar nuestra cuenta veremos la pantalla principal de github.

picture github homepage

Creando nuestro primer proyecto
-------------------------------

Abajo a la derecha, veremos que todavía no contamos con ningún repositorio. Vamos a crear nuestro primer proyecto.

github - your repositories

Hacemos click en 'New repository' y completamos la información de nuestro proyecto.

github - create a new repo

Deberemos elegir un nombre, ingresar una descripcióny elegir una licencia. También es buena idea inicializar nuestro repositorio con un archivo README (Léame) en el cual expliquemos de qué se trata el proyecto.

Luego hacemos click en 'Create repository'. Veremos que github ha creado el proyecto con la licencia que le especificamos y un archivo leame con el comentario que ingresamos

github - mi primer proyecto

También github ha creado para nosotros un url: https://github.com/hackatoner/mi_primer_proyecto. Esta es la dirección de nuestro proyecto en github, y a través de esa dirección el resto del mundo puede ver nuestro proyecto, seguirlo, controlar nuestros avances, copiárselo localmente para mejorarlo, y colaborar con nosotros.

Clonando localmente nuestro repositorio

Sin embargo, no podemos hacer todo en la web. Para poder trabajar en nuestro proyecto, debemos disponer de los archivos localmente en nuestra estación de trabajo. Por eso lo que haremos será copiarnos el repositorio entero (con su historial de cambios) en nuestra estación de trabajo.

Recuerda que git es un sistema de control de versiones distribuido, por eso cada copia del repositorio es totalmente autónoma. En la jerga de git, hablamos de 'clonar' un repositorio cuando queremos hacer una copia. El nuevo respositorio mantiene una referencia al repositorio original, lo que nos permite luego enviar y scinronizar los cambios.

Para clonar localmente nuestro repositorio debemos copiar la dirección que se encuentra en la parte inferior derecha de la página de nuestro proyecto:

github clone repo

En nuestro caso el url para clonar nuestro flamante repositorio es: https://github.com/hackatoner/mi_primer_proyecto.git

Nota: Hay otros métodos para comunicarte con repositorios de github. En <a href='https://help.github.com/articles/generating-ssh-keys'>este artículo</a> puedes ver cómo establecer una conexion segura con github utilizando SSH, para ello deberás crear un par de claves pública-privada, agregar tu clave pública a github y luego podrás usar el url de la forma git@github.com:hackatoner/mi_primer_proyecto.git.


Ahora tendremos que abrir una consola, y decirle a git que clone este repositorio:

$ git clone https://github.com/hackatoner/mi_primer_proyecto.git

En nuestro caso creamos un directorio 'proyectos' en nuestro directorio de usuario. Vemos como git creó a su vez un directorio 'mi_primer_proyecto' y trajo además los archivos del mismo.

github local clone

Flujo de trabajo con git

http://git-scm.com/book/es/Fundamentos-de-Git-Guardando-cambios-en-el-repositorio

Es importante entender el flujo de trabajo con git. Los arhivos en un repositorio pueden estar bajo seguimiento (tracked) o sin seguimiento (untracked). Cuando nos clonamos un repositorio todos los archivos estarán inicialmente bajo seguimiento de control (tracked).

Los archivos bajo seguimiento (tracked) pueden estar sin modificaciones (unmodified), con modificaciones (modified), o preparados para ser grabados (staged).

Cada vez que querramos confirmar algún cambio en el repositorio, deberemos preparar el archivo (pasarlo a stage), luego de lo cual grabaremos los cambios (commit) de todos los archivos que estaban preparados. En ese momento, los cambios se grabarán en el repositorio como un nuevo commit, y los archivos pasaran a estado sin modificaciones.

Este flujo de trabajo se ve reflejado en el siguiente cuadro:

http://git-scm.com/figures/18333fig0201-tn.png

Vamos a verlo con un ejemplo práctico. Mediante el comando git status podemos ver el estado de los archivos en nuestro directorio de trabajo.

$ git status
# En la rama master
nothing to commit, working directory clean

Lo que haremos a continuación es editar localmente el archivo README.md. Podés utilizar cualquier editor de texto, en nuestro caso utilizaremos gedit.

$ cd mi_primer_proyecto
$ gedit README.md

mi_primer_proyecto
==================

Este es un proyecto de prueba para aprender a utilizar git y github.

También agregaremos un archivo html.

$ gedit index.html

<html>
  <body>
    <h1>Bienvenido a mi primer proyecto</h1>
  </body>
</html>

Veamos ahora qué nos retorna el comando git status:

$ git status
# En la rama master
# Cambios no preparados para el commit:
#   (use «git add <archivo>...» para actualizar lo que se ejecutará)
#   (use «git checkout -- <archivo>...« para descartar cambios en le directorio de trabajo)
#
# modificado:   README.md
#
# Archivos sin seguimiento:
#   (use «git add <archivo>...» para incluir lo que se ha de ejecutar)
#
# index.html
no hay cambios agregados al commit (use «git add» o «git commit -a»)

Nos indica que el archivo README.md está modificado (modified) pero que no está preparado (staged) para ser confirmado. También nos indica que el archivo index.html está sin seguimiento. Por última nos indica que no hay ningún cambio para ser grabado (staged).

Mediante el comando 'git add' indicaremos qué archivos queremos preparar (stage) para ser grabados en el próximo commit.

$ git add README.md
$ git status
# En la rama master
# Cambios para hacer commit:
#   (use «git reset HEAD <archivo>...«para eliminar stage)
#
# modificado:   README.md
#
# Archivos sin seguimiento:
#   (use «git add <archivo>...» para incluir lo que se ha de ejecutar)
#
# index.html

Ahora vemos como el archivo README.md está listo para ser confirmado. Entonces lo vamos a confirmar con el comando 'git commit'. Cada vez que hagamos un commit debemos incluir un mensaje mediante el parámetro -m, e la siguiente manera:

$ git commit -m 'completamos el archivo README.md'
[master 981d17b] completamos el archivo README.md
 1 file changed, 1 insertion(+), 1 deletion(-)

$ git status
# En la rama master
# Su rama está delante de «origin/master« para 1 commit.
#   (use "git push" to publish your local commits)
#
# Archivos sin seguimiento:
#   (use «git add <archivo>...» para incluir lo que se ha de ejecutar)
#
# index.html
no se ha agregado nada al commit pero existen archivos sin seguimiento (use «git add» para darle seguimiento)

De la misma manera, preparamos (stage) y confirmamos (commit) el archivo index.html:

$ git add index.html

$ git commit -m 'creamos pagina html de bienvenida'
[master d6d9019] creamos pagina html de bienvenida
 1 file changed, 5 insertions(+)
 create mode 100644 index.html
hackatoner@station:~/proyectos/mi_primer_proyecto$ git status
# En la rama master
# Su rama está delante de «origin/master« para 2 commits.
#   (use "git push" to publish your local commits)
#
nothing to commit, working directory clean

Vemos que git nos indica que nuestra rama de trabajo está dos commits por delante de origin/master. Como habíamos dicho, nuestro repositorio mantiene una referencia al repositorio original. Esto lo podemos ver mediante el siguiente comando:

$ git remote -v
origin  https://github.com/hackatoner/mi_primer_proyecto.git (fetch)
origin  https://github.com/hackatoner/mi_primer_proyecto.git (push)

Lo que tenemos que hacer ahora es enviar los cambios que acabamos de confirmar (commit) en nuestro repositorio local a nuestro repositorio remoto en github. Haremos esto mediante el comando 'git push'.

Nota: debido a que estamos utilizando el url https, git nos pedirá nuestro nombre de usuario y password de github.

$ git push
Username for 'https://github.com': hackatoner
Password for 'https://hackatoner@github.com': xxxxxx

Counting objects: 8, done.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 670 bytes, done.
Total 6 (delta 1), reused 0 (delta 0)
To https://github.com/hackatoner/mi_primer_proyecto.git
   194a26c..d6d9019  master -> master

Si volvemos a nuestro sitio en github, veremos que que se ha agregado el archivo index.html, y que el archivo README.md fue modificado

picture github post push

Además, si hacemos clicks en 'commits' podemos ver la lista de commits:

picture github - commit list

Y haciendo click en cada uno de ellos podemos ver el detalle de los cambios efectuados, y quién los hizo:

picture github - review a commit

Manteniendo nuestro repositorio local actualizado

A veces pasará que nuestro repositorio remoto de github está más actualizado que nuestro repositorio local. Esto puede ocurrir cuando utilizamos otra máquina para desarrollar, o cuando hay más de una persona trabajando sobre el mismo repositorio.

Para ello utilizamos el comando 'git pull' para traernos los últimos cambios del repositorio remoto en github a nuestro repositorio local en nuestra estación de trabajo.

$ git pull
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
De https://github.com/hackatoner/mi_primer_proyecto
   d6d9019..8f9e950  master     -> origin/master
Updating d6d9019..8f9e950
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)

En este caso, git nos dice que el archivo README.md fue actualizado.

Nota: en este artículo hemos trabajado exclusivamente desde la línea de comandos, sin embargo existen varias herramientas visuales que nos facilitan la tarea (una herramienta muy recomendable es <a href='http://www.syntevo.com/smartgithg/'>SmartGit</a>). Sin embargo, es recomendable trabajar un buen tiempo desde la línea de comandos para aprender bien los conceptos básicos antes de adoptar una herramienta visual.

Conclusión

La combinación de git más github nos brinda herramientas sumamente poderosas para gestionar archivos y trabajar colaborativamente.

En este artículo apenas hemos visto lo mínimo indispensable como para poder iniciar un proyecto en github. Git es un tema muy vasto como para ver en un solo artículo, y github provee muchos servicios más de suma utilidad.

Para más información no dejen de leer el libro <a href='http://git-scm.com/book/es/'>Pro Git</a> que se encuentra disponible en castellano, en el sitio de git. Además, cualquier duda que tengan acerca de git seguramente estará preguntada y contestada en <a href='http://stackoverflow.com/'>stackoverflow</a>.

Por último, les dejamos un resumen ayuda-memoria para los más ansiosos:

--

Instalar git

debian:

sudo apt-get install git

rpm:

yum install git-core


Configurar git

$ git config --global user.name "mi nombre de usuario"
$ git config --global user.email mi_mail@ejemplo.com
$ git config --global push.default simple

Registrar una cuenta en github

Navegá a navegá a <a href='https://github.com/'>https://github.com</a> y completá la información

Crear un nuevo repositorio

Ingresá a github con tu cuenta, hacé click en 'Repositories' y luego 'New', o simplemente navegá a <a href='https://github.com/new'>https://github.com/new</a>.

Clonarte el repositorio localmente

git clone https://github.com/mi_usuario/mi_proyecto.git

Consultar el estado de los archivos

git status

Agregar archivos para ser confirmados (stage)

git add <archivo>

Confirmar (commit) archivos

git commit -m 'mensaje del commit'

Enviar los cambios de mi repositorio local al repositorio remoto en github

git push

Actualizar mi repositorio local con los cambios del repositorio de github

git pull
