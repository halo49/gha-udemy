# Curso - Domina Github Actions

### ejemplos y ejercicios
Repositorio para ejercicios de github actions

[gha-udemy](https://github.com/BrainsDevOps/gha-udemy)

Repositorios de acciones reutilizables

1- [gha-dockerpy-dice](https://github.com/BrainsDevOps/gha-dockerpy-dice)

2- [gha-dockerpy-hola](https://github.com/BrainsDevOps/gha-dockerpy-hola)

3- [gha-javascript-hola](https://github.com/BrainsDevOps/gha-javascript-hola)

4- [gha-javascript-dice](https://github.com/BrainsDevOps/gha-javascript-dice)

5- [gha-composite-action](https://github.com/BrainsDevOps/gha-composite-action)

6- [gha-npm-composite-action](https://github.com/BrainsDevOps/gha-npm-composite-action)

./LosBloques.png

1. __WORKFLOWS__
Estos estan en un repositorio, se pueden tener varios workflows en un solo repositorio

2. __EVENTOS__
Los workflows los disparan los eventos

3. **JOBS**
En un workflow hay uno o mas jobs, se pueden ejecutar en secuencia o en paralelo

4. **RUNNER**
Los jobs se ejecutan en un runner (maquina virtual de github, maquina virtual propia, contenedor docker)

5. __STEPS__
Cada job tiene uno o mas steps, ejecutan scripts, o llaman una accion o workflow externo

Todos estos bloques se ejecutan con un lenguaje declarativo yaml

./LosBloquesYaml.png

Ejercicios
Se crea un repositorio en github llamado gha-udemy que sera para hacer los ejercicios de github actions, este sera publico y con un archivo README.md por default, despues en la pestaña de Actions se muestran varias plantillas para trabajar y en el input de busqueda se pone manual, lo que nos devolvera un Simple Workflow y nos metemos a configurarla con el boton configure

Lo anterior abrira un archivo de configuracion yaml que esta ubicado en ```gha-udemy/.github/workflows```

y hay un input al final de la ruta anterior que nos deja cambiarle el nombre de ```manual.yml``` a ```01a-hola-mundo.yml``` 

del lado derecho de la pantalla hay opciones del marketplace y de documentacion que se veran mas adelante

este es el codigo que se dejara

```
name: 01a Hola mundo
on:
  workflow_dispatch:

jobs:
  hola-mundo:
    runs-on: ubuntu-latest
    steps:
    - name: Hola mundo
      run: echo "Hola mundo"
```

Ahora se le da al boton Commit changes y se deja el mensaje por default y que se va a mandar a la rama main

se da click en el apartado de ```Actions``` y en Actions ya se puede ver el workflow que hemos creado con el nombre que le pusimos ```01a Hola mundo``` y del lado derecho podemos ejecutar manualmente con la opcion de ```Run workflow``` y se va a ejecutar en la rama main

una vez que le dimos que lo corriera, le damos refresh a la pagina y se puede ver que esta en pendiente y despues de unos segundos se vera que ya fue ejecutado y le damos click encima del nombre en el apartado de ```All workflows``` y se vera una cajita con ```hola-mundo``` y los segundos qque se tardo que en este caso fueron como 4 segundos y al darle click a esta caja se veran 3 pasos como listas de despliegue

1. Setup job
2. Hola mundo
3. Complete job

Al expandir la lista de ```Hola mundo``` se vera que se ejecutó el ```>Run echo "Hola mundo"``` y la ejecucion de este que seria ```"Hola mundo"```

#### Eventos que desencaden flujos de trabajo
[Eventos para flujos de trabajo - workflows](https://docs.github.com/es/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows#push)

Eventos, Tipos de actividad y filtros
- manual / workflow_dispatch
- cron / scheduled - '* * 1 * *' - El dia primero de cada mes / [ver mas patrones](https://crontab.guru/)
- filtros / branches: -main - sobre que rama se ejecutara , se pueden poner patrones [patrones para filtros](https://docs.github.com/es/actions/writing-workflows/workflow-syntax-for-github-actions#filter-pattern-cheat-sheet)
- tipos de actividad / types: - opened
- eventos externos / repository_dispatch: types: [mievento]

./eventosactividadesyfiltros.png

#### Github CLI [github-cli](https://cli.github.com/)

Este es el [manual](https://cli.github.com/manual/)

este es el comando para loguearse a github mediante cli
```gh auth login```
Se pusieron las siguientes opciones

./ghclilogin.png

Esto redirecciona a la pagina de github y ahi se pone el codigo que se puso en la terminal, despues se pone el codigo del authenticator y eso es todo

Para probar que todo esta bien se pueden listar los repositorios
```gh repo list```

Los comandos son contextuales, quiere decir que dentro de un repositorio de git se puede dar lo siguiente
```gh repo view```

El cli se puede utilizar en los workflows y ya viene preinstalado en los distintos runners

