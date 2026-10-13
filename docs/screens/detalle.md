# Screen — Detalle de producto

- **Route:** `/products/:id`
- **Feature:** Catálogo de productos
- **Design reference:** N/A (no se ha proporcionado una maqueta)

---

## Purpose

Permitir consultar la información completa de un producto seleccionado y acceder a las opciones para editarlo o eliminarlo.

---

## UI regions

| Region | Component | Notes |
|--------|-----------|-------|
| Header | Ionic header y toolbar | Título «Detalle del producto» y navegación de regreso. |
| Body | Vista de detalle | Muestra nombre, precio, categoría y stock. |
| Footer / CTA | Botones de acción | Opciones para editar y eliminar el producto. |

---

## States

| State | Trigger | UI |
|-------|---------|-----|
| Loading | Solicitud del detalle en curso | Indicador de carga. |
| Loaded | Producto encontrado | Información del producto y acciones disponibles. |
| Empty | No aplica como lista vacía | No se muestra un estado vacío independiente. |
| Error | Error de red o respuesta 404 | Mensaje indicando que no se pudo cargar el producto y opción para regresar o reintentar. |
| Offline | Sin conexión con la API | Mensaje de conexión no disponible y opción para reintentar. No se garantiza contenido en caché. |

---

## Actions

| User action | Result | Use case / event |
|-------------|--------|------------------|
| Regresar | Vuelve a la pantalla anterior o a la lista. | Navegar atrás. |
| Pulsar «Editar» | Abre el formulario de edición del producto. | Actualizar producto. |
| Pulsar «Eliminar» | Solicita confirmación y, si se confirma, elimina el producto y vuelve a la lista. | Eliminar producto. |
| Pulsar «Reintentar» | Vuelve a solicitar el detalle. | Consultar detalle. |

---

## Accessibility

- [ ] All interactive elements have accessible labels.
- [ ] Touch targets ≥ 44×44 pt / 48×48 dp.
- [ ] Text scales with OS font-size setting.
- [ ] Contrast meets WCAG AA.
