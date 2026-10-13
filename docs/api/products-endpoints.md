# Endpoint Integration — API de productos

- **Feature:** Catálogo de productos
- **Method + path:** `GET`, `GET /:id`, `POST`, `PUT /:id` y `DELETE /:id` bajo `/api/products`
- **Auth required:** No

---

## Request

### 1. Listar productos

**Method + path:** `GET /api/products`

| Param | In | Type | Required | Notes |
|-------|----|------|----------|-------|
| `search` | query | string | No | Busca coincidencias en el nombre sin distinguir mayúsculas y minúsculas. |
| `category` | query | string | No | Filtra por coincidencia exacta de categoría. |

**Body:** N/A.

### 2. Consultar detalle

**Method + path:** `GET /api/products/:id`

| Param | In | Type | Required | Notes |
|-------|----|------|----------|-------|
| `id` | path | number | Yes | Identificador numérico del producto. |

**Body:** N/A.

### 3. Crear producto

**Method + path:** `POST /api/products`

**Body:**

```json
{
  "name": "Agua",
  "price": 2500,
  "category": "Bebidas",
  "stock": 10
}
```

### 4. Actualizar producto

**Method + path:** `PUT /api/products/:id`

| Param | In | Type | Required | Notes |
|-------|----|------|----------|-------|
| `id` | path | number | Yes | Identificador numérico del producto. |

**Body:**

```json
{
  "name": "Agua",
  "price": 3000,
  "category": "Bebidas",
  "stock": 15
}
```

### 5. Eliminar producto

**Method + path:** `DELETE /api/products/:id`

| Param | In | Type | Required | Notes |
|-------|----|------|----------|-------|
| `id` | path | number | Yes | Identificador numérico del producto. |

**Body:** N/A.

---

## Response

**Success (2xx):**

| Endpoint | Status | Response |
|----------|--------|----------|
| `GET /api/products` | 200 | Arreglo de productos. |
| `GET /api/products/:id` | 200 | Objeto del producto encontrado. |
| `POST /api/products` | 201 | Objeto del producto creado, con `id` asignado por el servidor. |
| `PUT /api/products/:id` | 200 | Objeto del producto actualizado. |
| `DELETE /api/products/:id` | 204 | Sin cuerpo de respuesta. |

**DTO → domain mapping:**

| DTO field | Domain field | Transform |
|-----------|--------------|-----------|
| `id` | `id` | Identificador numérico. |
| `name` | `name` | Texto no vacío, máximo 60 caracteres. |
| `price` | `price` | Número mayor que 0. |
| `category` | `category` | Una de las categorías permitidas: `Bebidas`, `Snacks`, `Aseo` o `Hogar`. |
| `stock` | `stock` | Entero mayor o igual que 0. |

---

## Errors

| Status | Meaning | App behavior |
|--------|---------|--------------|
| 400 | Identificador no numérico o cuerpo inválido. | Mostrar el error y los detalles para corregir la solicitud. |
| 404 | Producto inexistente o ruta no encontrada. | Mostrar mensaje de producto no encontrado o regresar a la lista. |
| 500 | Error interno del servidor. | Mostrar mensaje de error y permitir reintentar. |

Los errores de validación tienen el formato `{ "error": "mensaje", "details": ["..."] }`.

---

## Caching / offline

- **Strategy:** Online-only; no se garantiza caché local.
- **Cached entity:** N/A (almacenamiento en memoria).
- **TTL / invalidation:** N/A; los datos se consultan al servidor y el almacenamiento se reinicia cuando se reinicia la API.

