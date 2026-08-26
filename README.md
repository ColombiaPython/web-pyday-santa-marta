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
   La sección [`#codigo-de-conducta`](index.html) enlaza el CoC de PyLadies y describe el canal de
   reporte en sitio (equipo identificado con escarapela, mesa de registro, línea telefónica /
   WhatsApp), además de los correos de reporte y los nombres del comité.

Cuando la página esté publicada, hay que responderle a Marie con la URL nueva y actualizar en la
solicitud los campos *Event's/project's website* y *Link to Conference Schedule*.

## Estructura

```
index.html      La página completa (HTML + CSS en línea, ilustración SVG en línea)
CNAME           Dominio personalizado para GitHub Pages: santamarta.pyday.co
.nojekyll       Evita el procesamiento de Jekyll en GitHub Pages
img/
  favicon.svg   Ícono del sitio
  *.png         Logos de las organizaciones (ver abajo)
```

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

## Editar

Todo el contenido y los estilos están en `index.html`. Los colores viven en las variables CSS
de `:root` (paleta Caribe: turquesa `--sea`, dorado `--gold`, coral `--coral`, arena `--sand`),
así que se pueden cambiar en un solo sitio.

Para verlo en local basta con abrir `index.html` en el navegador, o:

```bash
python -m http.server 8000
```
