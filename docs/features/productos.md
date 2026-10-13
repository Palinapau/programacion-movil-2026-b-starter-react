# Feature — Catálogo de productos

- **Owner:** Equipo de desarrollo
- **Status:** Planned
- **Related stories:** N/A (no se han proporcionado identificadores de historias de usuario)

---

## Purpose

Permitir consultar y administrar un catálogo de productos, mostrando su información y ofreciendo opciones para crear, actualizar y eliminar productos. La información se obtiene de una API REST desarrollada con Express.

---

## Screens

| Screen | Route | Purpose |
|--------|-------|---------|
| Lista de productos | `/products` | Consultar, buscar y filtrar productos. |
| Detalle de producto | `/products/:id` | Consultar la información de un producto seleccionado. |
| Formulario de producto | `/products/new` | Crear un producto. |
| Formulario de edición | `/products/:id/edit` | Actualizar un producto existente. |

---

## State

- **Pattern:** Por definir según la implementación de Ionic React.
- **State object(s):** Por definir según la implementación; debe contemplar los productos, la carga, los errores y los datos del formulario.
- **Key transitions:** Loading → Loaded; Loading → Error; Error → Loading al reintentar; formulario → Saving → Saved o Error.

---

## Data

- **Use cases:** Listar productos, consultar detalle, crear producto, actualizar producto y eliminar producto.
- **Repositories:** Por definir según la implementación.
- **Remote sources / endpoints:**
  - `GET /api/products`: listar y filtrar productos.
  - `GET /api/products/:id`: consultar un producto.
  - `POST /api/products`: crear un producto.
  - `PUT /api/products/:id`: actualizar un producto.
  - `DELETE /api/products/:id`: eliminar un producto.
- **Local persistence:** La API utiliza almacenamiento en memoria inicializado a partir de los datos semilla. Los cambios se pierden cuando se reinicia el servidor. La persistencia local en la app está por definir.

---

## Edge cases & states

- [ ] Loading
- [ ] Empty
- [ ] Error / retry
- [ ] Offline
- [ ] Permission denied (no aplica al alcance conocido de esta funcionalidad)

---

## Decisions

- [ADR-001 — Estado de la aplicación](../decisions/ADR-001-estado.md)
- [ADR-002 — Consumo de la API](../decisions/ADR-002-consumo-api.md)

---

## Tests

- **Unit:** Validación de productos, filtros y transiciones de estado.
- **Widget/UI:** Lista, detalle y formularios de creación y edición; estados de carga, vacío y error.
- **Integration/E2E:** Consultar el catálogo, crear un producto, editarlo y eliminarlo mediante la API.
