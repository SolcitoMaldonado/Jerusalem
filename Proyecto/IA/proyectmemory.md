# Proyecto: Química Jerusalén — Catálogo online

## Descripción

Tienda online de un solo archivo HTML para **Química Jerusalén** (artículos de limpieza, San Francisco Solano, Buenos Aires). Permite navegar un catálogo, elegir modalidad minorista/mayorista, armar un carrito y enviar el pedido por WhatsApp.

## Archivo principal

- **Ruta:** `C:\Users\Rodrigo\Desktop\Proyecto\Sol_final_corregido 1.html`
- Formato: un único HTML con CSS y JS embebidos (sin dependencias externas), ~60 KB.
- El logo es un **archivo externo** `logo-original.jpg` (1254×1254) en la misma carpeta. Antes era un base64 embebido (~1,5 MB) que se extrajo y reemplazó.

## Funcionalidades

- **Catálogo** con 306 productos organizados en **27 categorías**.
- **Botones de categoría generados automáticamente** en JS (`buildCategories()`): todas las categorías del array `products` aparecen como botones.
- **Categorías ocultas al inicio**: la sección `#categorias` arranca con `display:none` y se muestra al tocar "Ver categorías" (o el enlace "Categorías" del menú) mediante `openCategories(event)`.
- **Modalidad minorista / mayorista**: `setMode('minor' | 'may')`. Los precios cambian automáticamente.
- **Nota de unidad por categoría**: las categorías de líquidos muestran "Precio por litro"; Esencias muestra "Precio por litro · rinde 60 lt".
- **Mínimo mayorista**: $ 100.000 (`WHOLESALE_MIN`). Si el total no llega, el checkout se deshabilita y muestra cuánto falta.
- **Carrito** tipo chat de Facebook:
  - Botón `▾` minimiza el carrito a una burbuja "Mi carrito (n)"; al tocar la burbuja se vuelve a desplegar.
  - Lista de productos con scroll propio (max-height 320px).
  - No hay botón para "cerrar" con `←`/`×` (se quitó por pedido del cliente; quedó solo `▾`).
- **Buscador** en vivo (busca por nombre y por categoría). Ya no salta la página en cada tecla: solo hace `scrollIntoView` la primera vez que se empieza a buscar (`searchWasActive`).
- **Destacados**: 4 productos fijos definidos en `featuredNames`.
- **Checkout**: modal con nombre y apellido, elección envío / retiro. El campo de dirección solo aparece y se habilita si se elige "Envío".
- **Pedido por WhatsApp**: `https://wa.me/5491134430701?text=...` con el detalle del pedido.
- **Sección de contacto** con WhatsApp y mapa de Google embebido.

## Fondo de la página

- Color crema (`--cream:#f8fbff`) con un patrón SVG embebido (data URI) en `background-image` del `body`: dibujos muy sutiles de limpieza (burbujas, esponja, jabón, gota, rociador) en trazo azul `#2b75c9` con opacidad 0.12, repetido cada 260px. Por encima se mantienen los degradados sutiles previos (puntitos azul/oro y diagonales).
- Acompaña el scroll (no es fijo).

## Logo

- **Archivo:** `logo-original.jpg` (imagen cuadrada 1254×1254: círculo blanco con corona dorada arriba, "Química Jerusalén" al centro, tubo de ensayo, gotas y burbujas; textos curvos "Precios mayoristas y minoristas" y "Todo para la limpieza, en un solo lugar"). Colores: azul marino oscuro `#021744`, dorado suave.
- Tamaños mostrados: escritorio `244px`, tablet (≤700px) `204px`, móvil (≤520px) `168px`.
- El header creció para que entre el logo: 250px escritorio / 210px tablet; `scroll-padding-top` en 258px.
- Se intentó recrear como SVG (`logo.svg`) pero no convenció; se descartó y se eliminó el archivo.

## Modelo de datos

Cada producto en el array `products`:

```js
{ "cat": "Nombre de categoría", "name": "Nombre del producto", "minor": "precio minorista", "may": "precio mayorista" }
```

Los precios son strings numéricos (se formatean con `$` y separador de miles argentino `toLocaleString('es-AR')`).

Ayudantes clave:
- `num(s)` — convierte el string de precio a número.
- `priceOf(p)` — devuelve el precio según modalidad.
- `fmt(n)` — formatea con `$` y miles.
- `esc(s)` — escapa para atributos HTML.
- `unitNote(p)` — devuelve la nota "Por litro" / "Por litro · rinde 60 lt" / "".
- `LIQUID_CATS` — Set con las 10 categorías de líquidos.

## Estilo / tipografía

- **Fuente de la página:** Cambria (con fallback a Georgia y Times New Roman). Se probaron Segoe UI y Georgia antes; el cliente eligió Cambria (siente que Georgia era "estirada").
- **Hero:** título `clamp(34px,5vw,56px)`. El párrafo descriptivo va **debajo de los botones** "Ver categorías / Ver todos", en dos líneas separadas.

## Categorías (27) y cantidades

**Líquidos (precio por litro):**
1. Jabones (9)
2. Suavizantes (8)
3. Detergentes (6)
4. Desengrasantes, ceras y otro (21)
5. Esencias (20) — rinde 60 lt
6. Desodorante de piso preparado (16)
7. Perfuminas (11)
8. Jabón Manos (7)
9. Automotor (7)
10. Insumo Piletas (4)

**Por unidad:**
11. Envases (5)
12. Papeles (26) — incluye lo institucional
13. Bolsas (13)
14. Textil (13)
15. Cabos (4)
16. Cepillos (7)
17. Escobas (8)
18. Secadores (7)
19. Esponjas (9)
20. Limpieza hogar (13)
21. Lavado de ropa (4)
22. Accesorios (5)
23. Baños y aromatizantes (8)
24. Jardín (6)
25. Insecticidas (26)
26. Perfumeria (15)
27. Plasticos (28)

## Estado (15/08/2026)

- Catálogo reconstruido y validado: 306 productos, sin nombres duplicados, precios válidos.
- Sintaxis JS validada con `node --check`.
- HTML optimizado: el logo pasó de base64 embebido (~1,5 MB) a archivo externo (~61 KB).
- Logo en `logo-original.jpg`; `logo.svg` eliminado.
- Fuente de la página: Cambria.
- Hero: título más chico; párrafo debajo de los botones, en dos líneas; botones **EXPLORAR CATEGORÍAS** / **VER TODOS LOS PRODUCTOS** grandes, en mayúsculas y el principal con degradado + brillo pulsante.
- Buscador: ya no salta la página por tecla.
- Favicon agregado (usa `logo-original.jpg`).
- Fondo en **celeste claro** `--cream:#eef4fb` (el cliente eligió celeste tras probar crema y dorado).
- Header translúcido `rgba(224,236,250,.55)` + blur, muestra los dibujos del fondo.
- Logo **circular** (border-radius:50%): 230px escritorio / 170px ≤700px / 140px ≤520px; franja 240px.
- Enlaces del nav recuadrados (píldoras); color azul marino `#0e2a5a`.
- Header que se encoge al bajar: `body.header-shrunk` (240→120px), logo con `transform:scale(.478)` (GPU, sin tilde).
- Header en `position:fixed` con `body{padding-top:240px}` → el encogido no empuja el contenido ni tiembla el scroll.
- "Ver todos los productos" renderiza el catálogo completo; "Explorar categorías" oculta el catálogo y muestra solo categorías.
- `index.html` y `Sol_final_corregido 1.html` idénticos (se mantienen sincronizados).
- `opencode.json` en la raíz con MCP de Netlify.

## Despliegue (14/08/2026)

- **Sitio publicado en Netlify:** https://resplendent-gnome-9548f1.netlify.app/ (cuenta gratis, sitio hecho público).
- Se creó `index.html` (copia del catálogo) porque Netlify usa `index.html` como página principal.
- **Pendiente:** el logo da 404 en el sitio porque en el primer deploy se subió el HTML sin la imagen. Re-desplegar con `index.html` + `logo-original.jpg` juntos. Ya está disponible el MCP de Netlify (`opencode.json`).

## Notas

- La migración a React (Vite + react-motion, carpeta `app/`) se intentó el 15/08 y **se deshizo** por pedido del cliente; el proyecto sigue siendo HTML plano.

## Cómo modificar

- **Agregar/cambiar productos:** editar el array `products` (o reemplazarlo).
- **Cambiar destacados:** editar `featuredNames`.
- **Cambiar mínimo mayorista:** editar `WHOLESALE_MIN`.
- **Cambiar WhatsApp:** editar las URLs `wa.me/5491134430701`.
- **Categorías de líquidos:** editar `LIQUID_CATS`.
- **Fondo con dibujos:** editar la data URI SVG del `background-image` en el `body`.
- **Tamaño del logo:** editar las reglas `.logo img` (width/height, escritorio y media queries) y la altura del `.nav`.
- **Header que se encoge:** editar `body.header-shrunk` (CSS) y el umbral `scrollY>140` (JS `updateHeaderShrink`).
- **Fuente de la página:** editar `font-family` en el `body`.