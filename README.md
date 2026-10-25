# GitWorktreePractice

Proyecto mínimo para aprender a usar `git worktree`: trabajar con las ramas
`main` y `develop` al mismo tiempo, cada una en su propia carpeta.

## Proyecto

Abre `index.html` en tu navegador. Es una página HTML sin dependencias,
instalación ni compilación.

## Práctica con dos ramas

Después de integrar estos archivos en `main`, ejecuta desde la carpeta del
repositorio (con los cambios locales guardados):

```sh
git switch main
git pull --ff-only origin main
git worktree add -b develop ../GitWorktreePractice-develop main
git worktree list
```

El último comando de creación crea la rama local `develop` a partir de `main`,
con el mismo contenido inicial, y la abre en la carpeta vecina
`../GitWorktreePractice-develop`. Si `develop` ya existe localmente, usa
`git worktree add ../GitWorktreePractice-develop develop` en su lugar.

Modifica el texto de `index.html` en la carpeta de `develop` y guarda el cambio:

```sh
cd ../GitWorktreePractice-develop
git add index.html
git commit -m "Practicar cambios en develop"
```

Abre el HTML de ambas carpetas para comprobar que `main` conserva el contenido
original y `develop` tiene tu cambio. No necesitas cambiar de rama en la carpeta
principal. Para publicar también la rama `develop`, ejecuta desde su carpeta:

```sh
git push -u origin develop
```

Cuando termines, vuelve a la carpeta de `main` y elimina únicamente el worktree
(la rama y sus commits se conservan):

```sh
cd ../GitWorktreePractice
git worktree remove ../GitWorktreePractice-develop
```