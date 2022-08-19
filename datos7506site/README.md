# Acerca de

Este repositorio contiene el código necesario para generar el sitio web de la materia, cuya dirección es:
https://datos7506-fiuba.github.io

El sitio estático que tiene el código del sitio per se se halla en el otro repositori: https://github.com/datos7506-fiuba/datos7506-fiuba.github.io

El código de dicho repositorio se halla incluido en éste como un submódulo, en la carpeta `/public`. Como veremos, cada vez que se hacen cambios en el sitio de la materia y se genera el contenido del mismo mediante hugo, la carpeta public se actualiza con los contenidos nuevos, tras lo cual hay que generar un nuevo commit dentro de ese submódulo y actualizar la rama main de ese repositorio.

El sitio está construido con [Hugo](https://gohugo.io/), usando el tema [DocDock](https://docdock.vjeantet.fr/).

# Instalación

## 1. Instalar Hugo
Como mencionamos, este sitio hace uso del framework web [Hugo](https://gohugo.io/). Es necesario instalarlo para poder editar el sitio. La instalación es muy sencilla, tal y como se indica en la página, dependiendo el sistema operativo se instala de la siguiente manera:
* Mac: `$ brew install hugo`
* Windows: `$ choco install hugo -confirm`
* Linux: `$ snap install hugo`

## 2. Descargar el repositorio

El link a este repositorio es `git@github.com:datos7506-fiuba/course_site.git`, no obstante hace uso de referencias a dos otros repositorios (submódulos) que deben ser instalados para poder levantar el sitio en un entorno local y poder efectuar cambios en él. Por eso es que es necesario instalar el repositorio con el flag `--recurse-submodules`, que se encarga de traer los repositorios referenciados en los lugares apropiados:

``` git clone --recurse-submodules git@github.com:datos7506-fiuba/course_site.git ```

El repositorio del tema [DocDock](https://docdock.vjeantet.fr/) se instalará en la carpeta `/themes`, mientras que el otro repositorio nuestro con el sitio estático se instalará en la carpeta `/public`. 

# Editar el sitio

## Levantar un entorno local

Para ver los cambios efectuados en el sitio, correr 

```$ hugo server```

para levantar el sitio en un entorno local, antes de deployar los cambios al sitio publico. Se puede acceder al sitio mediante el link que te especifica hugo, generalmente algo por el estilo de `https://localhost:1313`. Cada cambio que se efectúa en el código se ve automáticamente reflejado en ese entorno.

## Estructura 

Las páginas se ubican bajo la carpeta `/content`. Se pueden subdividir en carpetas, cada una de las cuales debe contener un archivo `_index.md` conteniendo los contenidos de la página principal de dicha sección, luego cada una de las páginas en markdown en esas carpetas constituirán subpáginas de dicha sección.

En el archivo `config.toml` se ubican metadatos importantes para el sitio. Conviene editarlos con cautela, ya que pueden hacer que el sitio público deje de funcionar bien.

Si van a la carpeta `/themes/hugo-theme-docdock/exampleSite` pueden ver una página de prueba que viene con el tema. Pueden levantarla mediante `$ hugo server` y jugar con ella; dicha página de ejemplo contiene un montón de documentación acerca de cómo usar el tema. 

## Deployar cambios

Una vez realizados nuestros cambios, se debe modificar el sitio público. Hugo nos genera el sitio web con los cambios incorporados cuando ejecutamos

```
$ hugo -t hugo-theme-docdock
```

Este comando va a modificar la carpeta `/public` y agregar nuestros cambios.

Debemos pushear estos cambios al main del submódulo (recordemos que los contenidos de `/public` son un submódulo) para ver los cambios en el sitio públic (https://datos7506-fiuba.github.io).

Hacemos:
```
$ git add *
$ git commit -m "Mensaje de commit"
$ git push origin main
``` 

y listo, al cabo de un minuto aprox, los cambios en el sitio se verán reflejados.