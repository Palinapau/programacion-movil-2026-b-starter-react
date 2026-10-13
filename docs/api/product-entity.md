# Local Entity — Product

- **Store:** N/A (almacenamiento en memoria).
- **Table/collection:** N/A (almacenamiento en memoria).
- **Schema version introduced:** N/A (almacenamiento en memoria).

---

## Fields

| Column | Type | Null | Notes |
|--------|------|------|-------|
| `id` | integer | No | Identificador único asignado incrementalmente por la API. |
| `name` | string | No | Nombre no vacío, máximo 60 caracteres. |
| `price` | number | No | Precio mayor que 0. |
| `category` | string | No | Debe ser una de las categorías permitidas: `Bebidas`, `Snacks`, `Aseo` o `Hogar`. |
| `stock` | integer | No | Existencias; debe ser un entero mayor o igual que 0. |

---

## Indexes

N/A (almacenamiento en memoria).

---

## Relationships

N/A (almacenamiento en memoria).

---

## Sync

- **Synced?** No.
- **Conflict policy:** N/A (almacenamiento en memoria).

---

## Migration notes

N/A (almacenamiento en memoria). La API carga los productos iniciales desde `server/data/products.json` al iniciar el servidor. Los cambios realizados durante la ejecución se conservan únicamente en memoria y se pierden al reiniciar el servidor.
