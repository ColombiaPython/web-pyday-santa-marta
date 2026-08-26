# web-pyday-santa-marta

Página web del evento **PyDay Santa Marta 2027 & Humble Data** — 12 y 13 de febrero de 2027,
Santa Marta, Magdalena, Colombia.

Sitio estático de un solo archivo (`index.html`), sin build ni dependencias.
Pensado para publicarse con **GitHub Pages** en `https://santamarta.pyday.co`.

## Por qué existe este repo

La PSF (Marie Nordin, 26 de agosto de 2026) pidió dos cosas para poder evaluar la solicitud de grant:

1. **Una página web dedicada al evento.** `https://www.pyday.co/` corresponde al PyDay Boyacá
   del 12 de septiembre de 2026, no a este evento. Esta página resuelve eso.
2. **Código de conducta enlazado directamente en esa página, con un método de reporte presencial.**
   Textualmente: *"an on site reporting method should be in place. The code of conduct should also
   be directly linked on the web page dedicated to the event."*

La sección [`#codigo-de-conducta`](index.html) cubre lo segundo: enlace directo al CoC de PyLadies
y a las políticas de la PSF, el canal de reporte en sitio (equipo identificado con escarapela,
mesa de registro, línea telefónica / WhatsApp), los correos de reporte y los nombres del comité.
No hace falta copiar el texto completo del CoC en la página — basta el enlace directo.

## Estructura

```
index.html      La página completa (HTML + CSS + JS en línea)
CNAME           Dominio personalizado para GitHub Pages: santamarta.pyday.co
.nojekyll       Evita el procesamiento de Jekyll en GitHub Pages
img/
  favicon.svg   Ícono del sitio
  *.jpg         Fotos de Santa Marta (ver abajo)
  *.png         Logos de las organizaciones (faltan)
```

### Fotos

Optimizadas desde la carpeta original `Santa_Marta/` (4,4 MB → 1,25 MB): reescaladas y
convertidas a JPEG progresivo de calidad 82.

| Archivo | Origen | Dónde se usa |
|---|---|---|
| `morro.jpg` | `morro-santa-marta.png` | Retrato circular del hero |
| `hero-costa.jpg` | `bg-beach-1.jpg` | Fondo del hero + galería |
| `amanecer.jpg` | `bg-beach-6.jpg` | Cabecera de la tarjeta Humble Data |
| `centro-historico.jpg` | `sm-city-2.png` | Cabecera de la tarjeta PyDay |
| `marina.jpg` | `sm-city-1.png` | Galería (foto grande) |
| `bahia.jpg` | `sm-city-3.png` | Galería |
| `playa-aerea.jpg` | `bg-beach-3.jpg` | Galería |
| `calle-noche.jpg` | `bg-beach-4.jpg` | Galería |
| `palmeras.jpg` | `bg-beach-7.jpg` | Galería |
| `atardecer.jpg` | `bg-beach-2.jpg` | Fondo de la banda de sponsors |

`bg-beach-5.jpg` **no se usó**: es un cañón rojo tipo Utah/Sedona, no tiene nada que ver con
el Caribe colombiano.

> **Ojo con los pies de foto.** Las cuatro que sí son reconociblemente Santa Marta
> (`morro`, `marina`, `bahia`, `centro-historico`) llevan pie de foto específico.
> Las demás vienen de banco de imágenes y podrían no ser Santa Marta, así que llevan
> pies genéricos (*Mar Caribe*, *Trópico*). Si alguna no es de la ciudad y prefieren no
> usarla, se puede reemplazar sin tocar el CSS: basta con dejar el mismo nombre de archivo.
> Conviene también confirmar la licencia de cada imagen antes de publicar.

### Movimiento

- Ken Burns lento sobre el fondo del hero.
- Revelado progresivo de cada bloque al entrar en pantalla (`IntersectionObserver`).
- Nav transparente que se vuelve sólida al bajar.
- Zoom suave al pasar el mouse sobre las fotos de la galería y las tarjetas del programa.
- Parallax en la banda de sponsors (solo en escritorio con mouse).

Todo respeta `prefers-reduced-motion: reduce`: con esa preferencia activa, nada se anima
y el contenido aparece de una vez.

## Publicar con GitHub Pages

1. Sube estos archivos a la raíz de la rama `main` del repo.
2. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*,
   Branch = `main`, carpeta = `/ (root)`.
3. En **Custom domain** escribe `santamarta.pyday.co` y guarda. El archivo `CNAME` ya está
   en el repo, así que el campo debería aparecer lleno.
4. En el DNS de `pyday.co`, crea un registro **CNAME**:

   | Tipo  | Nombre       | Valor                        |
   |-------|--------------|------------------------------|
   | CNAME | `santamarta` | `<usuario-u-org>.github.io.` |

5. Espera a que GitHub valide el dominio y marca **Enforce HTTPS**.

## Qué falta por completar

- [ ] **Logos** en `img/`: `pyladies-santa-marta.png`, `pyladies-colombia.png`,
      `python-colombia.png`, `humble-data.png`, `psf.png`.
      Si un archivo no existe, la página muestra el nombre de la organización como respaldo,
      así que se puede publicar sin ellos.
- [ ] **Enlace de registro.** El botón del hero dice "Registro próximamente" y está inerte.
      Cuando exista el evento en Luma, reemplázalo por el enlace real.
      > Ojo: el enlace `https://luma.com/clrwws8a` que quedó en la solicitud del grant es el del
      > PyDay Boyacá, no el de Santa Marta. Hay que crear uno nuevo.
- [ ] **Sede.** Cuando se confirme la universidad, agregar dirección y mapa en la sección Programa.
- [ ] **Línea de reporte del evento.** Ahora aparece `+57 301 631 2961` (el número que quedó en la
      solicitud del grant). Si prefieren no publicar un número personal, cámbienlo por una línea
      del evento antes de publicar — pero **debe quedar algún canal de reporte presencial**,
      que es justo lo que pidió la PSF.
- [ ] **Convocatoria de charlas (CFP)** para el sábado.

## Ajustes pendientes en la solicitud del grant

Cuando la página esté publicada:

- Actualizar *Event's/project's website* y *Link to Conference Schedule* a la URL nueva.
- *Link to Code of Conduct*: cambiar `https://kit.pyladies.com/en/latest/policies/` (índice de
  políticas) por `https://kit.pyladies.com/en/latest/policies/coc.html` (el CoC en sí).
- *Code of Conduct Enforcement Policy*: en la solicitud quedó como `include here` — un
  marcador de posición sin llenar. Debería apuntar a
  `https://policies.python.org/python.org/code-of-conduct/Enforcement-Procedures/`.
- Responderle a Marie con la URL nueva.

## Editar

Todo el contenido, los estilos y el script están en `index.html`. Los colores viven en las
variables CSS de `:root` (paleta Caribe: turquesa `--sea`, dorado `--gold`, coral `--coral`,
arena `--sand`), así que se pueden cambiar en un solo sitio.

Para verlo en local:

```bash
python -m http.server 8000
```
