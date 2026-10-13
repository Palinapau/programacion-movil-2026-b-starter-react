# Screen — Lista de productos

- **Route:** `/products`
- **Feature:** Catálogo de productos
- **Design reference:** N/A (no se ha proporcionado una maqueta)

---

## Purpose

Permitir consultar el catálogo, buscar productos por nombre, filtrar por categoría y acceder al detalle o al formulario para crear un producto.

---

## UI regions

| Region | Component | Notes |
|--------|-----------|-------|
| Header | Ionic header y toolbar | Título «Productos». |
| Body | Lista de productos | Muestra nombre, precio, categoría y stock de cada producto. |
| Search | Campo de búsqueda | Permite buscar por nombre. |
| Filter | Selector de categoría | Filtra por Bebidas, Snacks, Aseo y Hogar. |
| Footer / CTA | Botón «Nuevo producto» | Navega al formulario de creación. |

---

## States

| State | Trigger | UI |
|-------|---------|-----|
| Loading | Solicitud de productos en curso | Indicador de carga. |
| Loaded | Respuesta exitosa con productos | Lista con los productos obtenidos. |
| Empty | Respuesta exitosa sin resultados | Mensaje indicando que no hay productos y opción para crear uno. |
| Error | Solicitud fallida | Mensaje de error y botón para reintentar. |
| Offline | Sin conexión con la API | Mensaje de conexión no disponible y opción para reintentar. No se garantiza contenido en caché. |

---

## Actions

| User action | Result | Use case / event |
|-------------|--------|------------------|
| Buscar por nombre | Actualiza los resultados según el texto ingresado. | Listar productos con búsqueda. |
| Seleccionar categoría | Muestra productos de la categoría elegida. | Filtrar productos. |
| Seleccionar producto | Abre el detalle del producto. | Consultar detalle. |
| Pulsar «Nuevo producto» | Abre el formulario de creación. | Crear producto. |
| Pulsar «Reintentar» | Vuelve a solicitar los productos. | Recargar catálogo. |

---

## Accessibility

- [ ] All interactive elements have accessible labels.
- [ ] Touch targets ≥ 44×44 pt / 48×48 dp.
- [ ] Text scales with OS font-size setting.
- [ ] Contrast meets WCAG AA.
