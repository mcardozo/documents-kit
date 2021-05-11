Git
==================================================================

:sipsonis: Comando útiles de git

Git es un software de control de versiones diseñado por Linus Torvalds, pensado en la eficiencia y
la confiabilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran
número de archivos de código fuente.


Inicialización
-------------------------------------------------------------------
Iniciar un repositorio::

  $ git init

Clonar un repositorio::

  $ git clone <url_repositorio>

Configuraciones::

  $ git config --global user.name "<nombre>"

  $ git config --global user.email "<email>"

Agregar un origin remoto a un repositorio local::

  $ git remote add origin <url>

  $ git remote -v

Cambiar la URL remota::

  $ git remote set-url origin <url>


Conexión a GitHub con SSH
-------------------------------------------------------------------
Conectar repositorio a github::

  $ git remote set-url origin <url-ssh-github>

Fusionar historias(grupos de commits)::

  $ git pull origin master --allow-unrelated-histories


Información
-------------------------------------------------------------------
Estado del árbol de trabajo del área local::

  $ git status

Información de la rama de trabajo::

  $ git log

Mostrar detalles del último commit::

  $ git show


Interaciones con el remoto
-------------------------------------------------------------------
Actualizamos nuestro repositorio::

  $ git fetch

Ver las diferencias de un archivo al commit anterior::

  $ git diff HEAD~2 HEAD -- <archivo>

Ver las modificaciones efectuadas en un archivo local contra el remoto::

  $ git diff HEAD:path/to/file.py <brach_remote>:path/to/archivo

  $ git diff HEAD:path/to/file.py path/to/archivo

Agregar todos los archivos o un archivo al proximo commit::

  $ git add .

  $ git add <archivo>

Guardar nuestras modificaciones::

  $ git commit -m "<mensaje>"

Agregar y guardar modificaciones::

  $ git commit -am "<mensaje>"

Mover o cambiar nombre::

  $ git mv <archivo>

Actualizar nuestro repositorio y realiza el merge::

  $ git pull <rama>

Subir las modificación al repositorio remoto::

  $ git push <rama>

Borrar un commit remoto::

  $ git reset --soft HEAD~1

  $ git push -f origin <rama>

Listar todos los HEAD::

  $ git reflog


Guardar cambios en memoria y recuperarlos después
-------------------------------------------------------------------
Guardado provisional::

  $ git stash

Guardado provisional de un solo archivo::

  $ git stash push -m <mensaje> <archivo>

Guardado provisional con nombre::

  $ git stash save '<name>'

Listar guardados::

  $ git stash list

Aplicar cambios nuevamente::

  $ git stash pop

  $ git stash pop stash@{index}

Guardar los cambios en memoria a una rama::

  $ git stash pop

  $ git stash branch <nombre-rama>

Borrar un stash::

  $ git stash drop stash@{index}


Realizar cambios
-------------------------------------------------------------------
Cambia el mensaje del último commit::

  $ git commit -m "<mensaje_corregido>" --amend

Agregar una modificación al último cambio::

  $ git add <archivo>

  $ git commit --amend

  $ git push origin <rama> -f

Verificar si hay commits sin subir al remoto::

  $ git log origin/master..HEAD

Borrar un commit local sin destruir cambios::

  $ git reset --soft HEAD~1

Borrar un commit local y destruir cambios::

  $ git reset --hard HEAD~1

Borrar un commit local::

  $ git reset --hard <commit>

  $ git reset --hard HEAD~1

  $ git push -f origin HEAD


Reorganizando
-------------------------------------------------------------------
Tomar todos los cambios confirmados en una rama, y reaplicarlos sobre otra
[Fuente](https://git-scm.com/book/es/v1/Ramificaciones-en-Git-Reorganizando-el-trabajo-realizado)::

  $ git checkout experiment

  $ git rebase master


Traerse un commit específico
-------------------------------------------------------------------
Traerse un *commit* específico de otra rama al *HEAD*::

  $ git cherry-pick <id-commit>


Archivos ignorados
-------------------------------------------------------------------
Actualizar los archivos o carpetas que no se le van a dar seguimiento::

  $ git rm -r --cached .

  $ git add .

Archivos ignorados solo en el local::

  $ vi $GIT_DIR/info/exclude


Ramas
-------------------------------------------------------------------
Listar Ramas::

  $ git branch

Listar ramas y ver sus historias::

  $ git show-branch

  $ git show-branch --all

Listar ramas locales y remotas::

  $ git branch -a

Listar ramas remotas::

  $ git branch -r

  $ git branch -v

Crear Rama::

  $ git branch <nombre>

Posicionarnos sobre una rama::

  $ git checkout <nombre>

Crear una rama y posicionarnos sobre ella::

  $ git checkout -b <nombre>

Crear una rama desde una rama remota::

  $ git checkout -b <nombre> origin/<nombre>

Borrar rama local::

  $ git branch -d <nombre_rama>

Borrar un rama remota::

  $ git push origin --delete <nombre_rama>

Borrar ramas ya mergueadas::

  $ git branch -d `git branch --merged`

Cambiar nombre a una rama::

  $ git branch -m <viejo_nombre> <nuevo_nombre>

  $ git push origin <nuevo_nombre>

  $ git push origin <viejo_name>

Actulizar la lista de ramas remotas::

  $ git remote update origin --prune


Tags
-------------------------------------------------------------------
Listar tags::

  $ git tag

Listar tags con su correspondientes commits::

  $ git show-ref --tags

Crear tag, se incluye en dónde estemos parados::

  $ git tag -a <nombre>

Crear un tag a un commit específico::

  $ git tag -a <nombre-tag> -m <mensaje> <hash-commit>

Subir tags al servidor remoto::

  $ git push origin --tags

Modificar el commit al que apunta el tag::

  $ git tag --force <nombre> <commit>

  $ git push --force --tags

Borrar tag::

  $ git tag -d <nombre_tag>

Borrar tag remotamente::

  $ git push origin :refs/tags/v0.2


Shortcut
-------------------------------------------------------------------
Generar método abreviado para ver los registros de log::

  $ git config --global alias.log-graph "log --branches --remotes --tags --graph --oneline --decorate"

  $ git config --global alias.log-commit "log --stat --graph --decorate"

  $ git log-commit -1

Listar alias personalizados::

  $ git config --get-regexp alias


Shortcut de sistema
-------------------------------------------------------------------
Agregar un shortcut de sistema::

  $ vi ~/.bashrc

.. code:: bash(code)

  gitpush() {
      git add .
      git commit -m "$*"
      git push
  }

  alias gp=gitpush

Cargar la configuración creada::

  $ source ~/.bashrc


Historial
-------------------------------------------------------------------
Ver historial de commits::

        git --no-pager log \
        --date=iso \
        --since="1 weeks" \
        --date-order \
        --full-history \
        --all \
        --pretty=tformat:"%C(cyan)%ad%x08%x08%x08%x08%x08%x08%x08%x08%x08 %C(bold red)%h %C(bold blue)%<(22)%ae %C(reset)%s"

Elimina archivo del repositorio remoto, local y del historial::

  $ git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch <file_name>' --prune-empty --tag-name-filter cat -- --all

Subir los cambios::

  $ git push -f origin master


Forkeds
-------------------------------------------------------------------
Para forkeds: mantener el repositorio actualizado con respecto al original::

  $ git remote add upstream <url>

  $ git pull upstream master


Comandos y recursos colaborativos
-------------------------------------------------------------------
Buscar dentro de los archivos::

  $ git grep color

  $ git grep -n color

Buscar dentro de los log::

  $ git log -S "<texto-a-buscar>"

Ver la cantidad de commits por colaborador::

  $ git shortlog -sn

  $ git shortlog -sn --all

  $ git shortlog -sn --all --no-merges

Ver linea por línea quien hizo *commits*::

  $ git blame <nombre-archivo>

  $ git -c blame <nombre-archivo>

Ver quien modificó ciertas líneas::

  $ git blame <nombre-de-archivo> -L<linea-inicio>,<linea-final>

  $ git blame <nombre-de-archivo> -L<linea-inicio>,<linea-final> -c

`Más comandos <https://csswizardry.com/2017/05/little-things-i-like-to-do-with-git/>`_
