# Decisiones de diseño

Registro corto de las decisiones principales, con su motivo y lo que se descartó o dejó pendiente.

## 1. El Dashboard responde "¿dónde actúo hoy?"

- **Decisión:** "Requieren atención" va justo después de los KPIs, antes de la lista completa.
- **Por qué:** el PM no necesita recorrer 7 proyectos para encontrar los 3 que se desvían. Cada tarjeta explica el motivo concreto (avance vs. proyectado, tareas bloqueadas, presupuesto vs. avance validado), así sabe qué hacer sin abrir el detalle.
- **Descartado:** ordenar la pantalla solo como lista de proyectos. Obliga a escanear todo para detectar problemas.

## 2. El estado nunca depende solo del color

- **Decisión:** chips con punto, texto e ícono; rojo y ámbar reservados para riesgo y retraso; borde lateral de color en las tarjetas críticas.
- **Por qué:** accesibilidad (daltonismo) y claridad. Si todo tiene color, nada destaca.

## 3. Cuatro estados, un lenguaje

- **Decisión:** `En curso`, `En riesgo`, `Retrasado`, `Completado`, con el mismo color y etiqueta en chips, barras, dona, filtros y tabla.
- **Por qué:** coherencia entre vistas. Los conteos del KPI, la dona, los filtros y la lista salen de los mismos datos.

## 4. El Detalle va de la conclusión a la evidencia

- **Decisión:** "Avance y Estado" primero (porcentaje, mensaje y ruta de hitos), luego información general, tareas, equipo y actividad.
- **Por qué:** lo primero que el PM quiere saber es si el proyecto va bien. El resto es evidencia para entender por qué y qué hacer.
- **Pestañas con scroll:** en móvil evitan una página larga sin perder el contexto de que todo pertenece al mismo proyecto.

## 5. La carga del equipo se ve como alerta temprana

- **Decisión:** barra de carga por persona, que cambia de color al acercarse a la saturación (ámbar desde 85 %, rojo desde 90 % en el detalle).
- **Por qué:** muchos retrasos empiezan por sobrecarga. Mostrarla junto al proyecto permite actuar antes.

## 6. Móvil primero, desktop como extensión

- **Decisión:** diseño base en columna de 430 px con navegación inferior. En desktop, la lista pasa a tabla con paginación y se agregan bloques de apoyo.
- **Por qué:** el PM consulta en movimiento, pero también trabaja en escritorio. El conmutador de vista permite revisar ambos.

## 7. Sistema de tokens con capa semántica

- **Decisión:** paleta base + tokens semánticos (`--primary`, `--danger`, `--surface`…). Los componentes solo usan los semánticos.
- **Por qué:** facilita el modo oscuro y cambiar la marca sin tocar componentes. Ver `tokens/tokens.json`.

## Pendiente por decidir

- Definición de "Operativo" (hoy cuenta proyectos en riesgo como operativos).
- Matriz de riesgos y reasignación de recursos: se enlazan, pero no están diseñadas.
- Estados de carga y error.
- Auditoría de contraste del texto ámbar.
- Validación con Project Managers reales.
