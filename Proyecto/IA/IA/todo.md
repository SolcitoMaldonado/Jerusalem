# Pendientes — Química Jerusalén

## Estado actual (15/08/2026)

- ✅ Sitio publicado en Netlify: **https://resplendent-gnome-9548f1.netlify.app/** (cuenta creada, sitio hecho público).
- ✅ Fondo en celeste claro `#eef4fb` (se probó dorado `#f8f3e7`, el cliente prefirió celeste).
- ✅ Header del mismo celeste, translúcido (opacidad .55), deja ver los dibujos del fondo.
- ✅ Logo circular (border-radius:50%), 230px escritorio / 170px tablet / 140px móvil, franja 240px.
- ✅ Enlaces del nav (Inicio/Categorías/Productos) recuadrados (píldoras sutiles).
- ✅ Header que se encoge al bajar: 240px → 120px; el logo se encoge con `transform:scale(.478)` (acelerado por GPU, sin tilde).
- ✅ Header en `position:fixed` con `body{padding-top:240px}` → al encogerse no empuja el contenido ni tiembla el deslizador.
- ✅ Botón "Ver todos los productos" renderiza el catálogo completo (ya no salta solo al buscador vacío).
- ✅ "Explorar categorías" oculta el catálogo y muestra solo las categorías.
- ✅ `index.html` y `Sol_final_corregido 1.html` idénticos (hash igual).
- ✅ MCP de Netlify configurado en `opencode.json`.

## Pendiente de despliegue (importante)

- [ ] **El logo da 404 en el sitio desplegado**: en el deploy actual se subió el HTML pero no `logo-original.jpg`. Hay que re-desplegar subiendo **juntos** `index.html` + `logo-original.jpg` (zona de drag & drop en la pestaña Deploys, o Netlify Drop). Ya está configurado el MCP de Netlify en `opencode.json` para poder hacerlo.
- [ ] Cuando esté re-desplegado, verificar que `https://.../logo-original.jpg` devuelva 200 (ya no 404).
- [ ] (Opcional) Conectar un dominio propio (ej. `quimicajerusalen.com.ar`).
- [ ] (Opcional) Autenticar el MCP de Netlify: al reiniciar opencode pedirá `netlify login`; si falla, usar PAT en `NETLIFY_PERSONAL_ACCESS_TOKEN`.

## Mejoras futuras opcionales (no acordadas)

- [ ] **Ziploc bags**: el cliente mencionó que faltaban en Bolsas, pero se decidió dejarlo como está.
- [ ] Categorías **"Baño"** y **"Aromatizantes"**: resueltas con "Baños y aromatizantes".
- [ ] Categoría **"Jardín insecticidas"**: cubierta con Jardín + Insecticidas.
- [ ] Mejorar `esc()` para que también escape `<` y `>` (sin impacto actual).

## Cómo reabrir el archivo

- Abrir `index.html` o `Sol_final_corregido 1.html` en el navegador.
- El logo es el archivo externo `logo-original.jpg` (debe estar junto al HTML).
- `index.html` es una copia del catálogo para desplegar en Netlify (Netlify usa `index.html` como página principal).
- Mantener ambos HTML sincronizados (copiar el editado sobre el otro).