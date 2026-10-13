# ADR-001 — Gestión del estado de la aplicación

- **ID:** ADR-001
- **Date:** 2026-10-12
- **Status:** Proposed
- **Authors:** Equipo de desarrollo

---

## Context

La aplicación de catálogo debe mostrar productos obtenidos desde una API y gestionar los estados de carga, resultados vacíos y errores. También necesita manejar los datos introducidos en los formularios de creación y edición.

**Known constraints:**
- La aplicación utiliza Ionic React y React.
- La API Express y la aplicación se ejecutan por separado durante el desarrollo.
- El almacenamiento de productos en el servidor es en memoria.
- El tiempo disponible para desarrollar y probar la solución es limitado.

---

## Decision

**We decided:** Utilizar el estado de React para gestionar los datos y estados de interfaz de la funcionalidad de productos, manteniendo la lógica organizada por funcionalidad.

**Justification:**

El estado de React permite actualizar la interfaz cuando cambian los datos o el resultado de una petición. Es una solución compatible con Ionic React y evita incorporar una biblioteca adicional de gestión de estado. La organización definitiva de los hooks y componentes se confirmará durante la implementación.

---

## Evaluated alternatives

| Alternative | Pros | Cons | Reason for discarding |
|-------------|------|------|-----------------------|
| Estado de React (`useState` y `useEffect`) | Integrado, sencillo y sin dependencias adicionales. | Puede requerir coordinación entre componentes. | Elegida por su sencillez y adecuación al alcance. |
| Context API | Permite compartir estado entre componentes. | Añade configuración y complejidad si el estado es pequeño. | No se considera necesaria inicialmente. |
| Biblioteca externa de estado | Puede facilitar estados compartidos complejos. | Añade dependencias y aprendizaje. | No se justifica para el alcance actual. |

---

## Consequences

**Positive:**
- La solución utiliza herramientas ya disponibles en React.
- Los cambios de estado pueden reflejarse en la interfaz.
- Se reduce la complejidad inicial del proyecto.

**Negative / Trade-offs:**
- Los componentes deben coordinar correctamente las peticiones y los estados compartidos.
- El estado en memoria de la interfaz no garantiza persistencia después de recargar la aplicación.

**Impact on the system:**
- Affected features/screens: Catálogo de productos, lista, detalle y formulario.
- Documents to update: `docs/features/productos.md`, `docs/screens/lista.md`, `docs/screens/detalle.md`, `docs/screens/formulario.md`.

---

## References

- Documentación de React: https://react.dev/
- Related to: ADR-002 — Consumo de la API.
