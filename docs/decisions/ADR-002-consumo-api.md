# ADR-002 — Consumo de la API de productos

- **ID:** ADR-002
- **Date:** 2026-10-12
- **Status:** Proposed
- **Authors:** Equipo de desarrollo

---

## Context

La aplicación Ionic React necesita consultar y modificar productos mediante una API REST independiente desarrollada con Express. La comunicación puede fallar por problemas de red, respuestas HTTP de error o datos no válidos.

**Known constraints:**
- La aplicación web se ejecuta durante el desarrollo en `http://localhost:5173`.
- La API Express se ejecuta durante el desarrollo en `http://localhost:3000`.
- La API utiliza respuestas JSON y códigos HTTP para comunicar resultados y errores.
- La implementación actual de las funciones de la API debe verificarse antes de dar por terminado el flujo.

---

## Decision

**We decided:** Utilizar `fetch` para las peticiones HTTP, centralizar la dirección base en `API_URL` y representar los errores de las peticiones mediante `ApiError`, traduciendo los errores técnicos a mensajes comprensibles en la interfaz.

**Justification:**

`fetch` está disponible en el entorno web utilizado por Ionic React y permite realizar peticiones HTTP sin añadir una biblioteca externa. Centralizar la URL facilita cambiar el servidor de destino. Un tipo de error común permite manejar de forma consistente las respuestas fallidas y mostrar mensajes adecuados al usuario.

---

## Evaluated alternatives

| Alternative | Pros | Cons | Reason for discarding |
|-------------|------|------|-----------------------|
| `fetch` con una capa común de API | Disponible en la plataforma y sin dependencias adicionales. | Requiere gestionar manualmente las respuestas HTTP y el JSON. | Elegida por simplicidad y compatibilidad. |
| Biblioteca Axios | Ofrece utilidades para peticiones y respuestas. | Añade una dependencia al proyecto. | No es necesaria para el alcance previsto. |
| Peticiones directamente desde cada pantalla | Fácil de iniciar. | Duplica lógica y dificulta un manejo uniforme de errores. | Se prefiere centralizar el acceso a la API. |

---

## Consequences

**Positive:**
- La dirección de la API puede configurarse en un único lugar.
- Los errores HTTP pueden manejarse de manera consistente.
- Se separa el acceso a los datos de la presentación de las pantallas.

**Negative / Trade-offs:**
- Hay que implementar y probar la conversión de respuestas HTTP en errores de aplicación.
- La configuración de la dirección del servidor debe ser correcta para cada entorno.

**Impact on the system:**
- Affected features/screens: Catálogo de productos, lista, detalle y formulario.
- Documents to update: `docs/features/productos.md`, `docs/api/products-endpoints.md`, `docs/api/product-entity.md` y `README.md`.

---

## References

- Documentación de Fetch API: https://developer.mozilla.org/docs/Web/API/Fetch_API
- Related to: ADR-001 — Gestión del estado de la aplicación.
