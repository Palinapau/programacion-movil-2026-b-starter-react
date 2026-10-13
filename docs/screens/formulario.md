# Screen — Formulario de producto

- **Route:** `/products/new` para crear; `/products/:id/edit` para editar.
- **Feature:** Catálogo de productos
- **Design reference:** N/A (no se ha proporcionado una maqueta)

---

## Purpose

Permitir crear un producto o modificar los datos de un producto existente, validando la información antes de enviarla a la API.

---

## UI regions

| Region | Component | Notes |
|--------|-----------|-------|
| Header | Ionic header y toolbar | Título «Nuevo producto» o «Editar producto», según el modo. |
| Body | Formulario | Campos para nombre, precio, categoría y stock. |
| Footer / CTA | Botones de acción | Guardar y cancelar. |

---

## States

| State | Trigger | UI |
|-------|---------|-----|
| Loading | Carga del producto en modo edición | Indicador de carga mientras se obtiene el producto. |
| Loaded | Formulario listo | Campos vacíos al crear o precargados al editar. |
| Empty | No aplica como estado de pantalla | En modo creación, los campos comienzan vacíos. |
| Error | Validación fallida o solicitud rechazada | Mensajes que permiten identificar y corregir los errores. |
| Offline | Sin conexión con la API | Mensaje de conexión no disponible y opción para reintentar. No se garantiza guardado sin conexión. |

---

## Actions

| User action | Result | Use case / event |
|-------------|--------|------------------|
| Completar campos | Introduce los datos del producto. | Editar datos del formulario. |
| Pulsar «Guardar» | Valida los datos y crea o actualiza el producto. | Crear o actualizar producto. |
| Pulsar «Cancelar» | Regresa sin guardar cambios. | Cancelar formulario. |
| Corregir errores | Permite volver a enviar el formulario. | Validar producto. |

---

## Accessibility

- [ ] All interactive elements have accessible labels.
- [ ] Touch targets ≥ 44×44 pt / 48×48 dp.
- [ ] Text scales with OS font-size setting.
- [ ] Contrast meets WCAG AA.
