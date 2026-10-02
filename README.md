# Norte, sin apuro

Sitio del itinerario Hohenau–Salta–Jujuy. El archivo `index.html` es una copia exacta de la última versión del HTML de la conversación, renombrada para servir como entrada del sitio.

## Archivos

- `index.html`: sitio completo.
- `.gitignore`: excluye archivos locales y variables de entorno.
- `README.md`: instrucciones para abrirlo y subirlo.

## Abrir el sitio

Abrí `index.html` en tu navegador. Este paquete no necesita un paso de compilación.

## Crear un repositorio privado en GitHub

No se ha creado ningún repositorio ni subido ningún archivo desde ChatGPT. Los siguientes comandos se ejecutan en tu computadora, dentro de esta carpeta.

Requisitos: Git, GitHub CLI (`gh`) y una identidad de autor configurada en Git. Si `gh` no está instalado, seguí las instrucciones oficiales de https://cli.github.com/.

Autenticación, si todavía no iniciaste sesión en GitHub CLI:

```bash
gh auth login --hostname github.com --web --git-protocol https
```

Iniciá sesión como `diegobugs`. Después, desde esta carpeta:

```bash
git init -b main &&
git add index.html README.md .gitignore &&
git commit -m "Add interactive northern Argentina itinerary" &&
gh repo create diegobugs/norte-argentino-2026   --private   --source=.   --remote=origin   --push
```

Si el nombre ya existe, elegí otro nombre para el nuevo repositorio. No uses opciones de sobrescritura ni `--force` para resolver un conflicto.

Si Git pide nombre y correo de autor, configurá tu identidad en este repositorio con `git config user.name` y `git config user.email`, usando tus propios datos; después volvé a ejecutar el commit y el comando de creación del repositorio.

Esta secuencia sube el código a un repositorio privado; no activa GitHub Pages ni publica una web abierta.

## Privacidad y alcance

El itinerario contiene fechas de viaje y alojamientos. La configuración propuesta es privada. Revisá el contenido antes de hacerlo público.

Las imágenes son ilustraciones generadas con IA, no fotografías documentales. La cartografía es orientativa, no navegación ni un track de senderismo. Los horarios y las actividades propuestos no equivalen a reservas confirmadas.

## Documentación de los comandos

- Creación del repositorio y subida del commit: https://cli.github.com/manual/gh_repo_create
- Inicio de sesión: https://cli.github.com/manual/gh_auth_login
