# Norte, sin apuro

Sitio del itinerario Hohenau–Salta–Jujuy: 14 días en un solo scroll, con mapa, paradas, fichas de actividades y preparativos.

## Archivos

- `index.html`: sitio completo en un único archivo. Las imágenes van embebidas y la página no hace llamadas de red.
- `.nojekyll`: hace que GitHub Pages publique los archivos tal cual, sin procesarlos con Jekyll.
- `.gitignore`: excluye archivos locales y variables de entorno.
- `README.md`: instrucciones para abrirlo y publicarlo.

## Abrir el sitio

Abrí `index.html` en tu navegador. No necesita compilación ni servidor.

El botón con el ícono de mapa, arriba a la izquierda, abre el mapa a pantalla completa: se puede mover, acercar y tocar cada lugar para ver sus actividades. Para compartirlo abierto, agregá `#mapa` al final del enlace.

El botón de reproducir, primero en la tarjeta de pasos de abajo, recorre el viaje solo: se queda en cada momento el tiempo justo para leerlo y pasa al siguiente. Arranca en pausa y se detiene al llegar al final, al tocar pausa o al desplazarse a mano.

## Publicar con GitHub Pages

1. En el repositorio, entrá a **Settings → Pages**.
2. En **Build and deployment**, elegí **Deploy from a branch**, la rama `main` y la carpeta `/ (root)`.
3. Guardá. En uno o dos minutos el sitio queda en `https://diegobugs.github.io/norte-argentino-2026/`.

Lo mismo desde la terminal, con GitHub CLI:

```bash
gh api -X POST repos/diegobugs/norte-argentino-2026/pages -f "source[branch]=main" -f "source[path]=/"
```

Con el plan gratuito de GitHub, Pages solo funciona en repositorios públicos. Con GitHub Pro el repositorio puede seguir privado, pero el sitio publicado es público igual: cualquiera con el enlace puede verlo.

Cada `git push` a `main` vuelve a publicar el sitio.

## Privacidad y alcance

El itinerario no muestra fechas: los días se nombran de "Día 1" a "Día 14" y el margen para el regreso es un "día extra". Sí incluye el punto de partida, el alojamiento confirmado y los horarios propuestos. Revisá el contenido antes de compartir el enlace.

La página les pide a los buscadores que no la indexen (`noindex`), pero eso no la vuelve privada.

Las imágenes son ilustraciones generadas con IA, no fotografías documentales. La cartografía es orientativa, no navegación ni un track de senderismo. Los horarios y las actividades propuestos no equivalen a reservas confirmadas.

## Documentación

- Configurar la publicación de GitHub Pages: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- `gh api`: https://cli.github.com/manual/gh_api
