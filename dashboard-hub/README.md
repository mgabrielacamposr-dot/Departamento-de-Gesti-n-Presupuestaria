# Hub de Dashboards del Equipo

Página única que enlaza a todos los dashboards HTML del equipo. El link final
no cambia nunca, aunque actualicen el contenido todo el tiempo.

## Estructura

```
dashboard-hub/
├── index.html          → página portal (no la toques salvo que quieras cambiar el diseño)
├── dashboards.js        → lista de dashboards (ESTE es el archivo que editan seguido)
└── dashboards/
    ├── ventas.html
    ├── marketing.html
    └── operaciones.html
```

## Publicarlo en GitHub Pages (una sola vez)

1. Creen un repositorio nuevo en GitHub (puede ser privado si es solo para el equipo,
   pero si es privado necesitan plan Pro/Team/Enterprise de GitHub para que Pages
   sea accesible sin login; si no, háganlo público).
2. Suban todo el contenido de esta carpeta a la raíz del repo:
   ```
   git init
   git add .
   git commit -m "Hub de dashboards"
   git branch -M main
   git remote add origin https://github.com/SU-ORG/dashboard-hub.git
   git push -u origin main
   ```
3. En GitHub: **Settings → Pages → Source** → elijan la rama `main` y carpeta `/root`.
4. Guarden. GitHub les da un link fijo, algo como:
   ```
   https://SU-ORG.github.io/dashboard-hub/
   ```
   Ese es el link único que comparten con todo el equipo. **No vuelve a cambiar.**

## Actualizar dashboards (día a día)

- **Actualizar un dashboard existente:** reemplacen el archivo correspondiente
  en `/dashboards` (por ejemplo `dashboards/ventas.html`) por el HTML nuevo que
  exportó el compañero, con el mismo nombre de archivo.
- **Agregar un dashboard nuevo:**
  1. Copien el `.html` a la carpeta `/dashboards`.
  2. Agreguen una entrada en `dashboards.js`:
     ```js
     {
       title: "Finanzas",
       category: "Finanzas",
       description: "Cashflow y presupuesto mensual.",
       file: "dashboards/finanzas.html"
     }
     ```
- Después de cualquier cambio:
  ```
  git add .
  git commit -m "actualiza dashboard de ventas"
  git push
  ```
  GitHub Pages se actualiza solo en 30-60 segundos. El link del hub sigue siendo
  el mismo.

## Alternativa sin usar terminal/git

Si nadie del equipo quiere usar git, pueden subir/editar archivos directamente
desde la web de GitHub (botón "Add file" / lápiz de editar en cada archivo), o
usar **Netlify Drop** (netlify.com/drop): arrastran la carpeta completa y les da
un link al instante; para actualizar, vuelven a arrastrar la carpeta.
