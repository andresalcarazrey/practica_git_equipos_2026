# practica_git_equipos_2026
# Ejercicio: La web del equipo, publicada en GitHub Pages

**Módulo:** Entornos de Desarrollo (1.º CFGS Desarrollo de Aplicaciones Web)
**Modalidad:** Grupos de 4 personas
**Duración:** 2 horas
**Herramientas:** Git instalado, cuenta de GitHub, terminal o Git Bash

En este ejercicio los cuatro integrantes del grupo van a construir juntos una pequeña web de presentación del equipo, cada uno desde su propio ordenador, usando Git y GitHub como herramienta de trabajo colaborativo. Y al final la publicaréis en Internet con GitHub Pages, para que cualquiera pueda visitarla con un enlace.

## 1. Objetivos

1. Crear un repositorio local con `git init` y conectarlo a GitHub con `git remote`.
2. Guardar cambios con `git status`, `git add` y `git commit`, y consultarlos con `git log`.
3. Crear y cambiar de ramas con `git branch` y `git checkout`.
4. Fusionar ramas con `git merge`.
5. Compartir el trabajo en equipo con `git push` y `git pull`.
6. Publicar la web del equipo con GitHub Pages.

## 2. Preparación (5 minutos)

- Comprueba que Git funciona: `git --version`.
- Configura tu identidad, si no lo has hecho ya:

```bash
git config --global user.name "Tu Nombre y Apellidos"
git config --global user.email "tu.correo@ejemplo.com"
```

- El grupo elige a una persona **coordinadora**. El resto serán las personas **desarrolladoras 2, 3 y 4**.
- **Coordinadora** crea un repositorio en GitHub llamado `portal-equipoXX` (sustituye XX por vuestro número de grupo), **sin** marcar "Add a README file".
- **Coordinadora** invita a sus tres compañeros como colaboradores: *Settings → Collaborators → Add people*.

## 3. Parte 1: El repositorio del equipo (15 minutos)

Trabajan **todos a la vez**, cada uno en su propio ordenador. La coordinadora ejecuta primero a pantalla completa; así todos ven cada comando.

**Coordinadora:**

1. Crea la carpeta del proyecto y conviértela en repositorio:

```bash
mkdir portal-equipoXX
cd portal-equipoXX
git init
```

2. Comprueba el estado con `git status`.
3. Crea un archivo `index.html`:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="utf-8">
    <title>Portal del equipo XX</title>
  </head>
  <body>
    <h1>Portal del equipo XX</h1>
    <p>Web hecha a cuatro manos (bueno, a ocho manos) con Git.</p>
  </body>
</html>
```

4. Prepara y confirma el archivo:

```bash
git add index.html
git commit -m "Primer commit: estructura de index.html"
```

5. Conecta el repositorio con GitHub y sube el trabajo (la primera vez hay que indicar la rama):

```bash
git remote add origin https://github.com/USUARIO-COORDINADORA/portal-equipoXX.git
git push -u origin main
```

    (Si tu rama principal se llama `master`, usa ese nombre en todos los comandos.)

**Desarrolladoras 2, 3 y 4:**

6. Clonad el repositorio que acaba de subir la coordinadora, cada uno en su equipo:

```bash
git clone https://github.com/USUARIO-COORDINADORA/portal-equipoXX.git
cd portal-equipoXX
```

7. Ejecutad `git log` y comprobad que veis el primer commit y su autor.

> **Anotad en el apartado 7:** ¿qué diferencia hay entre los comandos que ha usado la coordinadora (`init`, `remote`, `push`) y los que habéis usado el resto (`clone`)? ¿Qué se copia exactamente al clonar un repositorio?

## 4. Parte 2: Una rama por persona (25 minutos)

Cada integrante del grupo (las 4 personas) va a crear **su propia rama** para trabajar sin molestar al resto, y en ella hará **dos commits distintos**. Sustituye `tu-nombre` por tu nombre o iniciales, sin espacios (por ejemplo: `rama-ana`).

1. Crea tu rama y cámbiate a ella:

```bash
git branch rama-tu-nombre
git checkout rama-tu-nombre
```

2. Comprueba con `git branch` que estás en tu rama.
3. Añade en `index.html`, **debajo** del párrafo, una tarjeta con tu presentación:

```html
<section>
  <h2>Tu Nombre</h2>
  <p>Mi papel en el equipo: estudiante de DAW</p>
</section>
```

4. Comprueba con `git status` que Git ve la modificación y guarda tu trabajo:

```bash
git add index.html
git commit -m "Añade presentación de Tu Nombre"
```

5. Ahora, **sin cambiar de rama**, haz un segundo commit en tu tarjeta: añade debajo del párrafo de tu sección una línea `<p>` con tu película, serie, videojuego o grupo de música favorito y confirma con:

```bash
git add index.html
git commit -m "Añade favorito de Tu Nombre"
```

6. Ejecuta `git log` para confirmar que tus dos commits están en tu rama.

> **Anotad en el apartado 7:** mientras estás en tu rama, ¿qué pasaría si tu compañero edita `index.html` en su rama `main`? ¿Vosotros veríais su cambio? ¿Por qué?

## 5. Parte 3: Fusión, subida y sincronización (30 minutos)

Ahora cada uno integrará su tarjeta en la rama principal y la subirá a GitHub. **Es importantísimo seguir el orden y el turno acordados por el grupo** (por ejemplo: coordinadora, luego 2, 3 y 4). Después de cada turno, el siguiente debe bajar los cambios antes de seguir.

Para cada persona, **en su turno**, ejecuta:

1. Cámbiate a la rama principal y asegúrate de tenerla al día:

```bash
git checkout main
git pull
```

2. Ejecuta `git log --oneline` y comprueba que ves los commits de tus compañeros que ya se han fusionado.

3. Fusiona tu rama con la principal:

```bash
git merge rama-tu-nombre
```

4. Sube el resultado al repositorio remoto:

```bash
git push
```

El resto del grupo, mientras espera su turno, puede ver en GitHub cómo crece el historial del repositorio en la pestaña **Commits**.

5. Cuando hayan terminado los cuatro turnos, cada uno ejecuta una última vez:

```bash
git pull
```

y comprueba que su `index.html` local tiene **las cuatro tarjetas**. Compruébalo también todos juntos en la página del repositorio de GitHub.

6. Para terminar, cualquiera del grupo ejecuta `git log --oneline` y el grupo cuenta cuántos commits tiene el proyecto y cuántos autores distintos aparecen (en GitHub, en *Insights → Contributors*).

> **Anotad en el apartado 7:** ¿por qué hay que hacer `git pull` justo antes de fusionar y hacer `push` en tu turno? ¿Qué podría pasar si dos personas fusionan y suben a la vez sin bajar los cambios primero?

## 6. Parte 4: Publicar la web en GitHub Pages (30 minutos)

Vuestra web solo se ve desde el repositorio, en formato de código. Vamos a publicarla para que se pueda visitar como página normal.

1. Uno del grupo (por ejemplo, la coordinadora) va al repositorio en GitHub y entra en *Settings → Pages*.
2. En **"Build and deployment"**, en *Source*, elegid **"Deploy from a branch"** y en *Branch* seleccionad `main` y la carpeta `/ (root)`. Pulsad **Save**.
3. Esperad uno o dos minutos y recargad **Settings → Pages**: arriba aparecerá la URL pública de vuestra web, con el formato:

```
https://USUARIO-COORDINADORA.github.io/portal-equipoXX/
```

4. Abrid esa URL en el navegador y comprobad que se ve la web con las cuatro tarjetas. 🎉
5. Ahora haremos un último cambio **todos juntos, con turno**: cada persona añadirá en su propia rama una línea nueva a su sección (por ejemplo, un `<p>` con "Publicado con GitHub Pages"). El flujo completo, en vuestro turno, es:

```bash
git checkout rama-tu-nombre
# ...edita index.html...
git add index.html
git commit -m "Tu Nombre celebra la publicación"
git checkout main
git pull
git merge rama-tu-nombre
git push
```

6. Tras cada `push`, recargad la URL de GitHub Pages. ¿Cuánto tarda el cambio en aparecer? Anotadlo; es una buena lección sobre por qué los cambios se confirman y suben siempre, y no "al final".

> **Anotad en el apartado 7:** ¿en qué rama debe estar el contenido para que GitHub Pages lo publique? ¿Por qué un `commit` que está solo en tu rama local no se ve en la web publicada?

## 7. Respuestas y conclusiones (10 minutos)

Escribid como grupo las respuestas a las cuatro preguntas marcadas con *Anotad* en las partes 1, 2, 3 y 4:

1. ...
2. ...
3. ...
4. ...

## 8. Entrega

- Las cuatro personas deben aparecer como autores de commits (compruébalo con `git log` o en *Insights → Contributors*).
- Entregad en la tarea de la plataforma del centro **la URL del repositorio**, **la URL de la web publicada en GitHub.io** y los nombres de los cuatro integrantes.
- Cada integrante debe poder explicar qué comandos ha usado en **su turno de fusión**.

## 9. Rúbrica de evaluación (10 puntos)

| Criterio | Puntos |
| --- | --- |
| Repositorio local creado con `init`, commits correctos con `add`/`commit` y conexión con `remote` | 2 |
| Cada integrante crea su rama, hace dos commits y las fusiona con `merge` | 2 |
| Trabajo sincronizado: `push`/`pull` usados correctamente, cuatro tarjetas presentes | 2 |
| Web publicada en GitHub Pages y accesible desde la URL pública | 2 |
| Al menos un commit de cada uno de los cuatro integrantes en el remoto | 1 |
| Respuestas del apartado 7 correctas y entrega completa | 1 |

## 10. Ayuda rápida

| Comando | Para qué sirve |
| --- | --- |
| `git init` | Crea un repositorio en la carpeta actual |
| `git status` | Muestra el estado de los archivos |
| `git add archivo` | Prepara un archivo para el commit |
| `git commit -m "mensaje"` | Guarda los cambios preparados |
| `git log` / `git log --oneline` | Muestra el historial de commits |
| `git branch nombre` | Crea una rama |
| `git checkout nombre` | Cambia de rama |
| `git merge nombre` | Fusiona la rama indicada en la actual |
| `git remote add origin URL` | Conecta con un repositorio remoto |
| `git push` | Sube los commits al remoto |
| `git pull` | Baja los cambios del remoto |
| `git clone URL` | Descarga un repositorio remoto completo |

**Si te atascas:** el mensaje de error de Git casi siempre indica el comando exacto que te falta. Léelo con calma antes de pedir ayuda.

**Si la web no aparece en Pages:** revisad que el archivo se llama exactamente `index.html` (en minúsculas), que está en la raíz del repositorio y que en *Settings → Pages* está seleccionada la rama `main`. El primer despliegue puede tardar un par de minutos.
