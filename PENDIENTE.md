# Catalogo Forza WorkGear: estado y siguientes pasos

Ultima actualizacion: 2026-09-16
Objetivo: publicar el catalogo en Facebook, Instagram, WhatsApp Business y TikTok,
sin subir producto por producto en cada plataforma.
Modelo de venta decidido: **el cliente pide por WhatsApp**. No hay checkout ni TikTok Shop.

**Alcance contractual: 20 articulos** (con sus variantes de color/talla), no los 34 del CSV
completo. Es el acuerdo por el precio cobrado. Lista confirmada en la seccion 9.

---

## 1. Estado actual

### Hecho

- **Precios completos.** Se extrajeron del PDF `F:\Fotos Victor\catalogo_productos.xlsx - Catálogo.pdf`
  y se cargaron en `catalogo_productos_completo.csv`. 67 de 67 filas con precio, formato `37.00 USD`.
- **Herramienta HTML corregida.** `copy-forza-workgear.html` mostraba "43 sin precio" porque lee de
  `localStorage`, no del CSV. Se le agrego el mapa `PRECIOS_BASE` para que el precio por defecto salga
  de ahi. Recargar con Ctrl+F5 para verlo.
- **20 paginas de producto**, estaticas, listas para GitHub Pages, en `p/<id>.html`
  (ej. `p/001.html`, `p/008.html`). Cada una tiene foto principal + galeria, titulo, precio,
  descripcion y boton **"Pedir por WhatsApp"** que abre el chat con el mensaje ya escrito.
  Los productos con variantes (color o talla) muestran un selector que actualiza el mensaje
  de WhatsApp antes de enviarlo.
- **`index.html`** en la raiz del repo: catalogo con las 20 tarjetas de producto, enlaza a
  cada pagina.
- **`assets/style.css`**: estilos compartidos por `index.html` y las paginas de producto.
- **`link` lleno** en el CSV para los 52 renglones de los 20 productos en alcance (las otras
  14 filas de productos fuera de alcance se dejaron vacias a proposito, no tienen pagina).
- **`feed_meta.csv`**: el feed listo para Commerce Manager, ya filtrado a los 20 productos /
  52 filas, con las columnas que pide Meta (ver seccion 4).
- **Numero de WhatsApp confirmado:** +1 210 794 4086, ya integrado en las 20 paginas.
- **Respaldos:** `catalogo_productos_completo.csv.bak` y `copy-forza-workgear.html.bak`
  (de antes de esta sesion; no incluyen los cambios de hoy).

### Pendiente

- **Activar GitHub Pages.** Ver seccion 4a, instrucciones de 3 clics. Sin esto las URLs de
  `link` en el feed no cargan (dan 404).
- **Subir estos cambios al repo remoto** (commit + push). Se hace en esta misma sesion salvo
  que digas lo contrario.

### Verificado en linea

| Cosa | Resultado |
|---|---|
| Repo `partnerpathai-TX/catalogo-productos-forza-workgear` | publico, responde 200 |
| Fotos en `raw.githubusercontent.com/.../productos/` | cargan, 200 |
| GitHub Pages | **no activado todavia** (404) — ver seccion 4a |

### Campos del feed (solo los 20 productos en alcance, 52 filas)

| Campo | Lleno |
|---|---|
| id, title, description, image_link, price, brand, availability, condition | 52 / 52 |
| **link** | **52 / 52** — apunta a `p/<id>.html`, activo en cuanto se prenda GitHub Pages |
| item_group_id / color / size | solo en las filas que son variantes (13, 14, 28, 37, 46, 81) |

---

## 2. Datos que faltan (para las cuentas, no para el catalogo)

Lo que bloqueaba generar el catalogo ya se resolvio:

- [x] **Numero de WhatsApp:** +1 210 794 4086.
- [x] **Como subimos al repo:** se autorizo `git config --global --add safe.directory` sobre
      esta carpeta. Se sube con `git` directamente, sin `gh`.
- [x] **Nombre comercial exacto:** Forza WorkGear.
- [x] **Ciudad / zona de cobertura:** San Antonio, TX.
- [x] **Correo del negocio** para las altas: Forzaworkgear@gmail.com.
- [x] **Confirmar 2 precios** de tarps: sin cambios (ver seccion 6).
- [x] **Confirmar los 20 articulos del alcance:** ver seccion 9.

Lo que sigue pendiente es de las cuentas (seccion 3), no del catalogo:

- [x] Verificacion del negocio ante Meta: Meta dijo que **no es necesaria por ahora**
      para este portafolio (puede pedirla mas adelante si escala anuncios o mas gente
      en el portafolio). No bloqueo.
- [x] Portafolio comercial "Forza WorkGear" creado, con la Pagina de Facebook y el
      Instagram (@forzaworkgear, cuenta profesional Empresa) conectados adentro.
- [x] Cover photo de la Pagina de Facebook: `assets/facebook-cover-forza-workgear.jpg`
      (generada con IA, flat-lay de herramienta con los colores de marca).
- [x] Catalogo de Commerce Manager creado (tipo E-commerce, dentro del portafolio),
      productos cargados via "Subir un archivo de datos" con la URL de `feed_meta.csv`
      en GitHub. Confirmado: los 20 productos aparecen con foto y precio.
      Se omitio "Conectar datos" (Meta Pixel) a proposito: no hay carrito/checkout que
      trackear con el modelo de venta por WhatsApp; solo hace falta si mas adelante
      corren anuncios dinamicos de catalogo.
- [ ] WhatsApp Business: **pausado a proposito (2026-09-17)**. Instalar app con el
      numero +1 210 794 4086, vincular a la Pagina/portafolio, cuando se retome.
- [x] **Decidido NO publicar la "Tienda" con checkout de Meta (2026-09-17).** El asistente
      de Commerce Manager -> Tiendas exige "Perfil de envio" y "URL de pago" para poder
      publicar, y no hay checkout real en el sitio (se vende por WhatsApp). Inventar una
      URL de pago falsa generaria pedidos rotos y problemas con las politicas de Meta, asi
      que se dejo esa Tienda sin publicar (queda como borrador, sin efecto). Los 20
      productos ya son visibles y administrables desde Commerce Manager de todas formas.
- [x] **Los 20 productos ya estan publicados en Facebook e Instagram (2026-09-17).**
      6 publicaciones agrupadas por categoria, con foto(s) + precio + CTA de WhatsApp,
      textos en `posts-facebook-instagram.md`, publicadas via Meta Business Suite en
      ambas cuentas a la vez.
- [x] **Los 20 productos ya estan publicados en TikTok (2026-09-17).** Cuenta
      `@forzaworkgear` creada (personal/creador, sin verificacion de empresa -- ese
      "Verificacion de la empresa" es opcional, no se activo, no bloquea nada). Bio con
      `wa.me/12107944086`. 6 publicaciones con las mismas fotos y textos adaptados de
      `posts-tiktok.md`.

**Entrega cumplida (2026-09-17): los 20 productos del acuerdo estan publicados en
Facebook, Instagram y TikTok**, cada uno con foto, precio y forma de pedir por WhatsApp.

---

## 3. Cuentas a crear, en orden

El orden importa. Si creas el catalogo antes del portafolio comercial, queda colgado de tu
cuenta personal y moverlo despues es un problema.

- [x] **1. Cuenta personal de Facebook.** Ya la tenia (Eduardo Rodriguez).
- [x] **2. Pagina de Facebook** del negocio. Creada, con foto de portada.
- [x] **3. Meta Business** en `business.facebook.com` -> portafolio comercial "Forza WorkGear" creado.
- [x] **4. Instagram** -> `@forzaworkgear`, cuenta profesional tipo Empresa, creada y vinculada.
- [x] **5. Agregar Pagina + Instagram dentro del portafolio comercial.** Confirmado en Configuracion -> Personas.
- [x] **6. Verificacion del negocio**: Meta indico que no es necesaria por ahora. Ver seccion 2.
- [x] **7. Commerce Manager** -> catalogo tipo *E-commerce* creado dentro del portafolio,
      fuente de datos = la URL de `feed_meta.csv` en GitHub (confirmado, no fue subida
      manual). Confirmados 20 productos con foto y precio. Se actualiza solo cuando el
      CSV cambia y se sube a GitHub.
- [ ] **8. WhatsApp Business** -> **pausado a proposito (2026-09-17)**, el cliente decidio
      saltarselo por ahora. No bloquea nada de lo demas: las 20 paginas de producto y el
      boton "Pedir por WhatsApp" ya estan listos con el numero +1 210 794 4086 en cuanto
      se retome. Instalar con el numero dedicado -> vincular a la Pagina / portafolio.
- [x] **9. TikTok** -> cuenta `@forzaworkgear` creada (2026-09-17). Se quedo como
      personal/creador: el toggle "Verificacion de la empresa" pide documento legal del
      negocio que no se tenia a la mano, pero es opcional (solo desbloquea herramientas
      de marketing extra) y no bloquea publicar. El dueno del negocio puede activarlo
      despues con su documentacion si quiere.
      **No se abrio TikTok Shop.** Con venta por WhatsApp no se necesita, y pide documentos y cobra comision.

Recordatorio: Facebook, Instagram y WhatsApp comparten **un solo catalogo** de Meta.
Se crea una vez, no tres. TikTok si es aparte.

---

## 4. Lo que ya se genero esta sesion

1. ~~43 paginas de producto~~ **20 paginas de producto + `index.html`**, estaticas, para
   GitHub Pages. Cada una con foto, titulo, descripcion, precio y boton "Pedir por WhatsApp"
   que abre el chat con el mensaje ya escrito (incluye color/talla si aplica).
   URL resultante: `https://partnerpathai-tx.github.io/catalogo-productos-forza-workgear/p/001.html`
2. **`link` lleno** en los 52 renglones (de 67) que corresponden a los 20 productos en alcance.
3. **`feed_meta.csv`**, filtrado a los 20 productos / 52 filas, columnas:
   `id, title, description, availability, condition, price, link, image_link,
   additional_image_link, brand, item_group_id, color, size, identifier_exists`.
   `identifier_exists = no` en todas las filas porque no manejamos GTIN/MPN.
4. **Feed de TikTok**: no generado. Solo hace falta si mas adelante quieren anuncios de
   catalogo en TikTok (no es necesario para publicar organico ni para Shop, que no se va a usar).

### 4a. Activar GitHub Pages (3 clics, lo tienes que hacer tu)

1. Entra a `https://github.com/partnerpathai-TX/catalogo-productos-forza-workgear/settings/pages`.
2. En "Build and deployment" -> "Source", elige **"Deploy from a branch"**.
3. En "Branch", elige **`main`** y la carpeta **`/ (root)`** -> Save.

GitHub tarda uno o dos minutos en publicar. Despues, `index.html` queda en
`https://partnerpathai-tx.github.io/catalogo-productos-forza-workgear/` y cada producto en
`.../p/<id>.html`.

Despues de eso el flujo queda: tu editas el CSV -> se sube a GitHub -> Facebook e Instagram
se actualizan solos con el feed programado. Nunca subes producto por producto.

---

## 5. Pendiente por verificar

- **Catalogo en WhatsApp.** La app gratis de WhatsApp Business tiene catalogo manual.
  Que el catalogo del feed aparezca dentro de WhatsApp esta documentado para cuentas conectadas
  via WhatsApp Business Platform (la API); la documentacion de Meta no aclara si la app gratis
  lo soporta igual. Se verifica en el paso 8, ya con las cuentas creadas.
  Plan B si no jala: cargar los 20 productos a mano una sola vez en la app, o poner el link
  del catalogo web en el perfil. No bloquea el lanzamiento.
  Referencia: https://developers.facebook.com/documentation/business-messaging/whatsapp/catalogs/catalogs-overview/

---

## 6. Precios por confirmar

Los precios salieron del PDF. Dos quedaron por inferencia porque el PDF imprimio los nombres
truncados (solo la ultima linea de cada celda). Ya se confirmaron con el cliente (2026-09-16),
sin cambios:

| base | producto | precio puesto | por que |
|---|---|---|---|
| 5 | poly tarp 20' x 30' | 150.00 | fila "(20' x 30')" del PDF |
| 9 | mesh tarp 20' x 30' | 145.00 | fila "Malla 20 X 30" del PDF |
| 6 | poly tarp 20' x 20' | 135.00 | una de las dos filas "(20' x 20')" |
| 4 | mesh tarp 20' x 20' | 130.00 | la otra fila "(20' x 20')" |

Nota aparte: el PDF trae "Pala para roofing 2ft" a 55.00 y "4ft" a 75.00 que no existen en el CSV.
La unica pala del catalogo (base 92) quedo en 65.00, que es la de 3ft. Base 92 SI esta en los
20 del alcance (seccion 9); si tambien venden las de 2ft y 4ft, hay que darlas de alta como
productos nuevos y ver si entran en el mismo acuerdo de 20 o son adicionales.

---

## 7. Notas tecnicas para retomar

- **La numeracion de fotos NO coincide entre carpetas.** Las fotos originales en `F:\Fotos Victor\`
  usan una numeracion y las de `productos/` usan otra. Ejemplo comprobado: `F:\Fotos Victor\21.jpg`
  es el morral cafe, mientras que `productos/21.jpg` es el marro de 16 lb.
  La columna ID del PDF usa la numeracion **original**, no la de `productos/`.
  Por eso los precios se emparejaron por identidad de producto, no por numero.
- **El CSV completo tiene 34 productos distintos (`producto_base`) = 67 filas.** Los items
  `008` (botas Rhino) y `018` (botines) generan 13 filas cada uno por talla; otros 5 productos
  generan 2 a 4 filas por color. El "43" de versiones viejas de este documento no aplicaba al
  CSV final. El alcance real a publicar son 20 de esos 34 (seccion 9).
- **Los precios de la herramienta HTML viven en `localStorage`**, llave
  `forza-workgear-catalogo-v2`. No lee el CSV. Por eso se parcho el archivo.
- **Formato de precio:** `37.00 USD`. Es el que exporta la herramienta HTML.
- **El generador de paginas** (script de una sola vez usado en esta sesion, no se guardo en el
  repo) agrupa filas por `producto_base`, usa `item_group_id` como nombre de archivo cuando
  existe (ej. `007`, `008`) y si no, el `id` propio de la fila (ej. `001`). Si se agregan o
  quitan productos del alcance, hay que volver a correr algo equivalente — avisame y lo regenero.

### Archivos

| Archivo | Que es |
|---|---|
| `catalogo_productos_completo.csv` | el bueno, 67 filas, `link` lleno en las 52 de los 20 productos en alcance |
| `catalogo_productos_completo.csv.bak` | respaldo previo a esta sesion (antes de precios) |
| `feed_meta.csv` | feed para Commerce Manager, 20 productos / 52 filas |
| `index.html` | catalogo web, portada |
| `p/<id>.html` | 20 paginas de producto |
| `assets/style.css` | estilos del sitio |
| `copy-forza-workgear.html` | herramienta de captura, ya parchada |
| `copy-forza-workgear.html.bak` | respaldo antes del parche |
| `verificacion_productos.csv` | archivo viejo, 13 columnas, sin titulos. No se uso |
| `productos/` | las fotos que consume el sitio y el feed |
| `F:\Fotos Victor\catalogo_productos.xlsx - Catálogo.pdf` | fuente de los precios |

---

## 8. Como retomar

Si ya se activo GitHub Pages y las cuentas de Meta/TikTok siguen su curso (seccion 3), lo
siguiente es avisar cuando llegues al paso 7 (Commerce Manager) para conectar `feed_meta.csv`
como fuente de datos, o si necesitas agregar/quitar productos del alcance de 20.

---

## 9. Alcance confirmado: 20 articulos

Confirmado por el cliente el 2026-09-16. `base` = `producto_base` en el CSV.

| base | producto |
|---|---|
| 1 | Funda de cuero gamuza Zeluga de 10 bolsillos con porta-martillo |
| 4 | Malla de seguridad naranja Zeluga de uso rudo 12 mil 220 GSM |
| 12 | Funda de cuero cafe Zeluga con porta cinta metrica |
| 13 | Rodilleras de cuero Zeluga forradas en borrega (3 colores: vino, negro, natural) |
| 14 | Bota de trabajo Rhino 90M07 de cuero curtido al aceite (13 tallas, 5 a 11) |
| 15 | Barredor magnetico de mano Zeluga recoge clavos |
| 19 | Cinturon portaherramientas camuflaje Zeluga con tirantes |
| 28 | Tirantes acolchados Zeluga para cinturon (4 colores: azul, rojo, naranja, negro) |
| 32 | Manguera de aire Zeluga Z-Lite 1/4 x 100 pies, naranja |
| 36 | Set de cinturon portaherramientas Zeluga en lona verde y cuero |
| 37 | Bota de trabajo Rhino de agujetas con punta de mocasin (13 tallas, 5 a 11) |
| 42 | Clavadora neumatica de rollo para techo Zeluga 15 grados 28-145 |
| 43 | Clavadora neumatica estructural Zeluga 28-512 |
| 46 | Manguera de aire Coilhose Flexeel (3 colores: azul, rojo, amarillo) |
| 61 | Set de cinturon portaherramientas Zeluga en lona negra y cuero |
| 68 | Cinturon portaherramientas Zeluga de poliester con tirantes |
| 79 | Arnes de cuerpo completo Zeluga para trabajo en altura |
| 81 | Funda de cuero para electricista Zeluga 20-169 (2 colores: natural, cafe) |
| 91 | Set de cinturon portaherramientas de cuero cafe Zeluga |
| 92 | Pala quita tejas dentada con mango tipo D |

Los 14 productos que quedaron fuera (5, 6, 9, 21, 25, 30, 35, 38, 45, 47, 55, 59, 87, 90) no
tienen `link` ni pagina — siguen en el CSV completo por si mas adelante entran a un acuerdo
distinto, pero no se promocionan.
