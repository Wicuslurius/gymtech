# gymtech
hola mundo . Somos German y miguel 

#Objectivo
Instalar el entorno de desarrollo necesario para desplegar aplicaciones con Ruby on Rails incluyendo librerías, consola de comandos, 
base de datos y editor de texto en ambientes de escritorio compatibles con linux, usando Ubuntu 20.04 LTS.

#Recomendaciones
No copies y pegues los comandos de la guía dado que en algunas ocasiones podrían tener caracteres especiales de formato que podrían dañar la ejecución de los mismos, 
por otro lado, la instalación se realiza sobre un sistema operativo recién instalado, 
si tienes una instalación previa puedes encontrar que algunas respuestas de tus comandos sean diferentes.

#Convenciones
$ (consola de comandos) debes traspasar el comando sin el símbolo $

#=> (salida de comando)

[] (Opcional)

<consola cursiva> (texto que hay que añadir o quitar acorde a la explicación del paso)

#Nota importante
No debes usar el usuario superusuario (root) a menos que de forma explícita se especifique que este debe ser usado a través del comando “sudo”, 
de otra forma no debes usarlo así como tampoco sus variaciones como “$ sudo su”

El programa “sudo” pronunciado “SUDU” /suːduː/ es normalmente interpretado como “superuser do…” y permite al comando inmediatamente siguiente, 
correr con los permisos de otro usuario que tiene condiciones especiales de seguridad o permisos, 
comúnmente sudo se usa para invocar los permisos del superusuario del sistema operativo, sin embargo, 
en las últimas versiones de sistemas compatibles con Linux no sólo puede ejecutar como superusuario sino también es posible usar otros tipos especiales de usuario. 
Sin embargo, nosotros usaremos “sudo” para usar los permisos de superusuario.

#Adecuacion del sistema operativo
#instalacion de librerias base
Usando sudo y y el comando apt-get (como gestor de paquetes) vas a actualizar los enlaces a los repositorios de las librerías que se pueden instalar en el sistema operativo así como sus dependencias.

$ sudo apt-get update

Deberás obtener una respuesta de varias líneas al comando con la actualización de la lista de paquetes y una línea final mencionado que la lectura de las listas de paquetes ha sido finalizada similar a lo siguiente:

Reading package lists... Done

Ahora vamos a instalar las librerias necesarias usando sudo y el comando apt install

$ sudo apt install build-essential curl wget openssl libssl-dev libreadline-dev dirmngr zlib1g-dev libmagickwand-dev imagemagick-6.q16 libffi-dev libpq-dev cmake libwebp-dev

Para autorizar la instalación deberás aceptar la continuación del proceso digitando la letra Y y dando enter

Do you want to continue? [Y/n]

Las librerías instaladas cumplirán con los siguientes propósitos:

    build-essentials: contiene herramientas para compilar y construir software desde sus fuentes usando generalmente lenguaje C y sus derivados

    curl: es una herramienta para transferir información de un servidor a otro usando diversos tipos de protocolos, entre esos: HTTP, FTP, IMAP entre otros

    wget: es una herramienta para recibir contenido desde la web usando los protocolos más comunes como HTTP y FTP

    openssl: es un robusto conjunto de librerías que te permitirán manipular y leer contenido de los protocolos TLS y SSL, que son usados para garantizar la seguridad y encriptación de las comunicaciones entre servidores y clientes.

    libssl-dev: es una librería que forma parte de OpenSSL usada para lidiar con procesos de encriptación, este paquete, contiene librerías de desarrollo, cabeceras de compilación entre otro tipos de archivos.

    libreadline-dev: aporta la librerías de desarrollo para el paquete readline que ayuda a la consistencia de interfaces de usuario que están asociadas a líneas interactivas de comandos.

    dirmngr: es un pequeño servidor para gestionar y descargar certificados de tipo X.509 y la lista de revocación de los mismos.

    zlib1g-dev: aporta librerías de desarrollo para soportar mecanismos de compresión y descompresión compatibles con GZIP y PKZIP, tecnologías de compresión comunes en paquetes de herramientas para nuestro entorno.

    imagemagick-6.q16: es un programa que permite editar, crear y componer mapas de bits en imágenes.

    libmagickwand-dev: es un conjunto de librerías de desarrollo para compilar librerías necesarias para el uso de MagickWand, este último es la tecnología predilecta como interface del lenguaje de programación C a ImageMagick.

    libffi-dev: provee librerías de desarrollo para habilitar mecanismos de alto nivel para el uso de calling conventions sobre ciertos compiladores, de esta forma esta librería le permite al desarrollador invocar cualquier función específica por medio de una llamada en tiempo de ejecución.

    libpq-dev: esta librería contiene paquetes de desarrollo para habilitar el uso de conjuntos de binarios y cabeceras requeridas para construir componentes externos para PostgreSQL

    cmake: es usado para controlar el proceso de compilación de software usando un método independiente del compilador.

    libwebp-dev: habilita un conjunto de librerías de desarrollo para el manejo de formatos de imágenes de nueva generación compatibles con WebP

#Instalacion de GIT

A continuación instalaremos nuestro sistema para controlar versiones de nuestro código, para este caso usaremos GIT, y procederemos a su instalación usando el siguiente comando

$ sudo apt install git

Una vez instalado GIT configuraremos de forma global algunas variables

$ git config --global user.name "Miguel Aranguren"

$ git config --global user.email miguel@gymtech.com

$ git config --global color.ui true

Solo si tu conexión a internet está habilitada a través de un proxy (muy común en las instituciones públicas) debemos configurarlo de la siguiente manera

$ git config --global http.proxy http://proxy.alu.uma.es:3128

$ git config --global https.proxy https://proxy.alu.uma.es:3128

#Instalando RBENV
Imagina que estás trabajando en varios proyectos con Ruby y Ruby on Rails, y que todos tengan diferentes versiones… ¿cómo haces para garantizar que todas librerias, versiones y paquetes sean consistentes en cada uno de los proyectos?

Bien, para resolver esto debemos usar gestores de versiones, en este caso usaremos RBENV, no debes confundirte con controladores de versiones (como GIT), son dos tecnologías con propósitos distintos, pero que se complementan.

Para instalar RBENV debemos ejecutar el siguiente comando
###https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-ubuntu-20-04
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash

Next, add ~/.rbenv/bin to your $PATH so that you can use the rbenv command line utility. Do this by altering your ~/.bashrc file so that it affects future login sessions:

echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc

Next, apply the changes you made to your ~/.bashrc file to your current shell session:

source ~/.bashrc

Verify that rbenv is set up properly by running the type command, which will display more information about the rbenv command:

type rbenv

#Step 2 – Installing Ruby with ruby-build

With the ruby-build plugin now installed, you can install whatever versions of Ruby that you may need with a single command. First, list all the available versions of Ruby:

rbenv install -l

The output of that command will be a list of versions that you can choose to install:

Output
2.6.8
2.7.4
3.0.2
jruby-9.2.19.0
mruby-3.0.0
rbx-5.0
truffleruby-21.2.0.1
truffleruby+graalvm-21.2.0

Only latest stable releases for each Ruby implementation are shown.
Use 'rbenv install --list-all / -L' to show all local versions.

rbenv install 2.7.6

Installing Ruby can be a lengthy process, so be prepared for the installation to take some time to complete.

Once it’s done installing, set it as your default version of Ruby with the global sub-command:

rbenv global 2.7.6

Verify that Ruby was properly installed by checking its version number:

ruby -v

If you installed version 2.7.6 of Ruby, this command will return output like this:

Output
ruby 3.0.2p107 (2021-07-07 revision 0db68f0233) [x86_64-linux]

You now have at least one version of Ruby installed and have set your default Ruby version. Next, you will set up gems and Rails.


#bundler
Para poder mantener los espacios de librerías de forma consistente entre versiones y manifiestos usaremos BUNDLER, la cual es una librería que nos permitirá gestionar a su vez un conjunto de librerías de ruby agrupadas por entornos de trabajo y garantizando la consistencia de versiones y dependencias entre las mismas.

En Ruby, las librerías son llamadas gemas, y bundler usa un archivo manifiesto llamado Gemfile para listar todas las gemas que un proyecto tendrá, bundler puede usar varias fuentes para encontrar de forma pública estas librerías en la nube, sin embargo, nosotros vamos a usar dos fuentes rubygems y github.

Para instalar Bundler (que también es una gema) usaremos el comando gem que es proveído en este caso por RBENV. También habilitaremos el protocolo seguro de HTTP para que cuando se tome github como fuente este sea establecido por defecto.

➜ ~ gem install bundler

➜ ~ bundle config github.https true


Rails necesita de un motor de javascript para abordar ciertas funcionalidades de compilación, transformación y en sus últimas versiones, funcionalidades de integración con webpack, es por esta razón que vamos a usar nodejs como nuestro motor, sin embargo, NodeJS podría tener la misma situación de conflicto de versiones entre ambientes, por lo que que usaremos también un gestion de versiones de NodeJS para lidiar con estos escenarios.

NOTA si ya tienes instalado NodeJS u otro motor de javascript compatible con el interprete de javascript V8 o similar, no deberás hacer este paso, aunque es ampliamente recomendable usar un gestor de versiones, si lo quieres llegar a usar debes desinstalar el intérprete de javascript que tengas instalado para evitar conflictos futuros.

Para gestionar la versiones de NodeJS usaremos NODENV ejecutando la siguiente secuencia de comandos, que instalará el NODENV, añadirá sus binarios a la variable de entorno PATH, e instalará la versión 12.17.0 de NodeJS.

➜ ~ curl -fsSL https://raw.githubusercontent.com/nodenv/nodenv-installer/master/bin/nodenv-installer | bash

➜ ~ echo 'export PATH="$HOME/.nodenv/bin:$PATH"' >> ~/.bash

➜ ~ echo 'eval "$(nodenv init -)"' >> ~/.bash

➜ ~ source ~/.bash

➜ ~ nodenv install 12.17.0

➜ ~ nodenv global 12.17.0

#Instalando el ambiente de desarrollo con Rails y PostgreSQL

Habiendo instalado RBENV y BUNDLER ya podemos empezar a instalar todas las gemas, herramientas y servidores necesarios para poder seguir adelante con nuestros primeros pasos con Ruby on Rails

Vamos a instalar Ruby on Rails usando el siguiente comando (si, Rails es también una gema…)

gem install rails

Rails instalará con varias gemas como dependencias para su ejecución, así que obtendremos una instalación con una larga lista de librerías, al final podrás corroborar la versión de Rails usando el comando de abajo, que en nuestro caso será la versión 6.0.3.1

➜ ~ rails -v

#=> Rails 6.0.3.1

Las versiones de Rails superiores a la 6, requieren usar YARN como gestor de paquetes de javascript y habilitar el enlace de Webpack usando la tecnología Webpacker, para esto, vamos a usar la versión oficial de los repositorios de YARN a través de los siguientes comandos

➜ ~ sudo curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -

➜ ~ sudo sh -c "echo 'deb https://dl.yarnpkg.com/debian/ stable main' >> /etc/apt/sources.list"

➜ ~ sudo apt update
sudo apt list --upgradable

Para instalar YARN vamos a usar el comando de abajo, y usaremos nuestra versión de NodeJS instalada en el paso anterior usando la opción --no-install-recommends

sudo apt --no-install-recommends install yarn

Finalmente, vamos a instalar la base de datos de postgreSQL y configurar un usuario para poder gestionarla, lo primero que debes hacer es configurar las listas de los repositorios

➜ ~ wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

➜ ~ echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list

➜ ~ sudo apt update

Una vez actualizado la lista de paquetes de postgreSQL usaremos el siguiente comando para instalarlo

sudo apt -y install postgresql-12 postgresql-client-12

Una vez instalado postgreSQL, entraremos a la sesión del mismo y crearemos desde allí un nuevo usuario con capacidad de crear bases de datos (de usuario platzi, rol platzi y contraseña platzi), y que usaremos para nuestras futuras aplicaciones, para hacerlo debemos seguir el siguiente conjunto de instrucciones (No tener en cuenta el prefijo postgres@ubuntu:~$ para su ejecución):

➜ ~ sudo -i -u postgres

postgres@ubuntu:~$ createuser --pwprompt --interactive platzi


#=> Enter password for new role: ****** (platzi)

#=> Enter it again: ******

#=> Shall the new role be a superuser? (y/n) n

#=> Shall the new role be allowed to create databases? y

#=> Shall the new role be allowed to create more new roles? (y/n) n

Para salir de la sesión de postgreSQl debemos usar el comando exit

postgres@ubuntu:~$ exit















