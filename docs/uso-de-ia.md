# Uso de IA en este proyecto

Trabajé con **Claude** como apoyo para la ejecución. La IA permitió llegar mucho más rápido de dos pantallas a un prototipo navegable con documentación. Las decisiones de diseño y el criterio fueron míos.

## Qué hice yo

- Definir el problema del usuario y qué debía ver un Project Manager primero.
- Decidir la jerarquía de la información y el uso del color (rojo y ámbar solo para riesgo y retraso).
- Elegir qué pantallas entregar y qué mostrar en cada una.
- Revisar y corregir el resultado: por ejemplo, detectar que los totales de proyectos no coincidían entre el KPI, la lista y la dona, y unificarlos.
- Decidir qué es un extra y qué queda fuera de la entrega.

## Qué aceleró la IA

- **Prototipo funcional en HTML/CSS/JS** de las pantallas, con filtros, búsqueda, navegación, vista móvil y desktop.
- **Sistema de tokens** (colores, tipografía, radios) y su exportación a `tokens.json`.
- **Pantallas adicionales** (Tareas, Equipo, Perfil) y datos de ejemplo coherentes.
- **Documentación:** handoff para desarrolladores, registro de decisiones y este repositorio.
- **Revisión de consistencia:** comprobar números y detectar elementos sin flujo definido.

## Qué no delegué

- La priorización de la información y la definición del problema.
- La validación con usuarios reales: **no se hizo**; está listada como mejora.
- La decisión final sobre qué entregar.

## Cómo lo reviso

La IA puede equivocarse o inventar detalles. Por eso contrasté la documentación con el prototipo (variables CSS, componentes, comportamientos) y dejé marcado en el handoff lo que está pendiente o sin flujo.
