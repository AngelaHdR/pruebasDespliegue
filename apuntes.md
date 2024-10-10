#Apuntes Despliegue Angela y Sole

##Verbos que se pueden usar en los issue y commits
feat
fix
doc

##Forma de nombrar las ramas
nombre_usuario/num_issue

##Como mantener una historia lineal
Realizar microcommits en la rama para completar la tarea, al acabar switch a develop.
Ejecutar comando "git merge --squash nombreRama"
Nuevo commit final del issue: verbo(#num_issue): nombre_issue

##Borrar rama finalizada
Desde la rama ejecutar el comando "git push origin --delete nombreRama"
Desde develop ejecutar el comando "git branch -d -f nombreRama"

##Bajar los cambios de origin
Ejecutar el comando "git fetch --prune" (Para que no se vuelvan a bajar las ramas eliminadas)
Ejecutar el comando "git merge --ff-only origin/nombreRama"

Si las ramas develop y origin/develop han divergido, desde develop hacer "git rebase origin/develop"

##Mantener la rama actualizada y resolver conflictos
Desde la rama feature hacer "git merge develop" para resolver los conflictos que van surgiendo
Antes de hacer "git merge --squash" resolver los conflictos en la rama

##Combinaciones de comandos

###Bajarse las tres ramas
git fetch --prune && git switch develop && git merge --ff-only origin/develop && git switch release && git merge --ff-only origin/release && git switch main && git merge --ff-only origin/main && git switch develop

###Combinar los cambios de la rama en develop y subirlo
git switch develop && git fetch --prune && git merge --ff-only origin/develop && git merge --squash nombreRama

git commit -m nombreCommit && git push

###Combinar los cambios en release y subirlo
git switch release & git fetch --prune && git merge --ff-only origin/release && git merge --ff-only develop && git push

###Combinar los cambios en main y subirlo
git switch main & git fetch --prune && git merge --ff-only origin/main && git merge --ff-only release && git push

###Actualizar la rama develop una vez el commit hecho
git fetch --prune && git rebase origin/develop


git commit -m nombreCommit && git push

