# Norte, sin apuro

Sitio del itinerario Hohenau–Salta–Jujuy: 10 días en un solo scroll, con mapa, paradas, fichas de actividades y preparativos.

## Distribución del viaje

10 días y 9 noches: Sáenz Peña, 2 noches (ida y vuelta); Salta, 1; Cafayate, 2; Cachi, 1; Tilcara, 3 en El Cielo en Tilcara. Regreso a Hohenau el día 10, con un día extra de margen.

- Días 1–2: Hohenau → Sáenz Peña → Salta.
- Días 3–4: Quebrada de las Conchas y Cafayate, sin Domos del Viento.
- Día 5: Ruta 40, Quebrada de las Flechas y Cachi.
- Día 6: Cachi → Los Cardones → Cuesta del Obispo → El Carril → Cerrillos → Circunvalación Sureste de Salta → General Güemes → Tilcara.
- Día 7: sendero largo de las Señoritas, Humahuaca y Hornocal desde Tilcara (07:30–19:00).
- Día 8: Salinas Grandes, Purmamarca, Paleta del Pintor en Maimará y Pucará de Tilcara. Salida a las 07:00; mirador a las 13:30, almuerzo a las 14:00 y Pucará de 15:30 a 17:00. Regreso a la base a las 17:30.
- Días 9–10: Tilcara → Sáenz Peña → Hohenau.

El día 4 combina La Yesera / Los Estratos por la mañana (09:00–11:15), pausa en el hotel de Cafayate y almuerzo en Piattelli a las 13:30, con la tarde completa en la bodega como última visita. Salida de Cafayate a las 08:15; prever 35–45 minutos de manejo por tramo a La Yesera y 15–20 minutos del hotel a Piattelli. Son estimaciones de planificación: confirmar el circuito corto, la mesa, el turno de visita y el cierre de la bodega. El traslado Cachi–Tilcara y el regreso Tilcara–Sáenz Peña requieren jornadas largas, con pausas.

El día 7 sale de Tilcara a las 07:30: encuentro con el guía en Uquía a las 08:15, sendero largo de las Señoritas de 08:30 a 12:30 (cuatro horas estimadas en total con ida, vuelta y pausas), más 30 minutos de margen hasta las 13:00, almuerzo en Humahuaca a las 13:30 y ascenso a Hornocal a las 14:30. Mirador de 15:45 a 16:30, descenso hasta las 17:45, pausa y salida de Humahuaca a las 18:00 para llegar a El Cielo en Tilcara alrededor de las 19:00. Es una jornada larga: la iglesia de Uquía depende de terminar antes la caminata y el paseo urbano de Humahuaca es breve y opcional. Confirmar el turno temprano del guía, el acceso a Hornocal y los horarios de temporada; sin mes definido no se garantiza volver con luz.

El día 8 aprovecha la tarde libre para el Pucará y reemplaza la merienda por la visita a la Paleta del Pintor y el almuerzo en Maimará. Cada atractivo tiene su ficha e imagen propia en el mapa. Según la UBA, el Pucará abre de martes a domingo, de 09:00 a 18:30, con último ingreso a las 17:15; los lunes cierra. Reconfirmar apertura, tarifa y turnos guiados cuando se definan las fechas. Los horarios de manejo y visita son estimaciones de planificación.

## Archivos

- `index.html`: el renderer. Tiene el HTML, los estilos y el código del mapa y del recorrido, pero ningún dato del viaje.
- `itinerario.json`: el viaje completo. Lugares, días, paradas, fichas por ciudad, pendientes, fuentes e imágenes.
- `public/attractions/<imagen>/image.webp`: las ilustraciones. Cada lugar del JSON elige la suya.
- `public/map/countries.json`: el contorno de los países para el mapa base (Natural Earth).
- `.nojekyll`: hace que GitHub Pages publique los archivos tal cual, sin procesarlos con Jekyll.
- `.gitignore`: excluye archivos locales y variables de entorno.
- `README.md`: instrucciones para abrirlo y publicarlo.

## Abrir el sitio

El sitio lee `itinerario.json` al cargar, así que necesita un servidor. Abrir `index.html` con doble clic no alcanza, porque el navegador no deja leer archivos locales desde `file://`. Desde la carpeta del proyecto:

```bash
python3 -m http.server
```

Después entrá a `http://localhost:8000`. No hace falta compilar nada. En GitHub Pages funciona tal cual.

El botón con el ícono de mapa, arriba a la izquierda, abre el mapa a pantalla completa: se puede mover, acercar y tocar cada lugar para ver sus actividades. Para compartirlo abierto, agregá `#mapa` al final del enlace.

El botón de reproducir, primero en la tarjeta de pasos de abajo, recorre el viaje solo: se queda en cada momento el tiempo justo para leerlo y pasa al siguiente. Arranca en pausa y se detiene al llegar al final, al tocar pausa o al desplazarse a mano.

## Editar el itinerario

Todo el contenido está en `itinerario.json`. Guardá el archivo y recargá la página para ver los cambios.

- `places`: cada lugar, con `name`, `lat`, `lon` e `image`. Los lugares de Paraguay llevan además `"country": "Paraguay"`.
  En el mapa, un lugar con paradas se muestra como parada. Con `"passThrough": true` se muestra como punto de paso aunque tenga paradas. El criterio:
  - **Parada:** lugares turísticos, miradores y vistas, hoteles y almuerzos en un lugar con atractivo.
  - **De paso:** ciudades y pueblos de ruta, lugares sin atractivos, almuerzos de ruta y lugares solo para desayunar o descansar. Por ejemplo, Hohenau, Posadas, Corrientes, Molinos o Chicoana.
- `days`: los 10 días en orden. Cada día tiene `route`, la lista de lugares que dibuja el trayecto, y `stops`, las paradas.
- Cada parada usa `time` (`"HH:MM"`, el reloj se calcula a partir de ahí), `place`, `title`, `body` y `kind` (el ícono: `car`, `border`, `food`, `coffee`, `walk`, `wine`, `camera`, `bed`, `moon`, `pin`, `home`, `domo`). `routeIndex` es la posición de la parada dentro de `route` y `uid` identifica su ficha: tiene que ser único.
- `accommodation`: alojamiento elegido para una jornada. Las noches de Tilcara comparten El Cielo en Tilcara, con entrada el día 6 y salida el día 9. El mapa usa el punto de la localidad; no representa el acceso del alojamiento.
- `activityGroups`: las secciones de "Actividades por ciudad" y qué lugares entran en cada una.
- `checklist`: la lista de "Por confirmar". Cada navegador guarda las tildes por posición y por `checklistVersion`. Al reordenar o reemplazar ítems, incrementar esa versión para evitar que una tilde vieja marque una tarea distinta.
- `sources`: las referencias que citan las paradas en `refs`.

El mapa conecta los puntos de `route` con segmentos rectos: es un esquema del recorrido, no navegación vial. En el día 6, los puntos de Cerrillos, Circunvalación Sur/Sureste, acceso este y empalme RN 9/RN 34 representan el corredor comprobado en OpenStreetMap/OSRM. Evita el centro de Salta, pero pasa por su periferia sur y este; los enlaces no son paradas ni atractivos.

### Imágenes

Cada lugar elige su ilustración con `image`. Por ejemplo, `"image": "salta"` usa `public/attractions/salta/image.webp`. Varios lugares pueden compartir una imagen, como los pueblos del corredor chaqueño con `chaco`. Una parada puede usar otra imagen que la de su lugar si también lleva `image`.

Para sumar una imagen, creá la carpeta `public/attractions/<nombre>/`, guardá adentro `image.webp` y escribí ese nombre en `image`. En `images` podés agregar opcionalmente el texto del crédito (`label`) y el encuadre (`position`, en el formato de `object-position` de CSS).

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

El itinerario no muestra fechas: los días se nombran de "Día 1" a "Día 10" y el margen para el regreso es un "día extra". Sí incluye el punto de partida, el alojamiento elegido en Tilcara y los horarios propuestos. Revisá el contenido antes de compartir el enlace.

La página les pide a los buscadores que no la indexen (`noindex`), pero eso no la vuelve privada.

Las imágenes son ilustraciones generadas con IA, no fotografías documentales. La cartografía es orientativa, no navegación ni un track de senderismo. Los horarios y las actividades propuestos no equivalen a reservas confirmadas.

## Documentación

- Configurar la publicación de GitHub Pages: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- `gh api`: https://cli.github.com/manual/gh_api
