# Explicación de la entrega

## Cómo prioricé la información

Diseñé pensando en un Project Manager que abre la app varias veces al día y necesita saber en segundos dónde intervenir. Por eso ordené las dos pantallas de lo general a lo específico:

- **Dashboard:** primero los KPIs (proyectos activos, capacidad, avance promedio vs. meta, en riesgo, entregas de la semana). Después "Requieren atención", con los proyectos críticos y el motivo en una línea (por ejemplo, "Avance 45% vs 70% proyectado"). Más abajo, la distribución global por estado y la lista completa con filtros.
- **Detalle:** primero "Avance y Estado", con porcentaje, mensaje de estado y ruta de hitos. Luego información general (cliente, fecha de entrega, riesgo, presupuesto), tareas, equipo con su carga y actividad reciente. Las pestañas permiten saltar a cada bloque sin hacer scroll largo.
- **Jerarquía visual:** el rojo y el ámbar se reservan para riesgo y retraso, y siempre van con texto e ícono, no solo con color. Así lo crítico destaca y el resto se mantiene sobrio.

## Qué problema principal del usuario resuelve

Un PM con varios proyectos digitales pierde tiempo abriendo uno por uno para saber cuál se está desviando. El diseño convierte esa revisión en un escaneo de segundos: el Dashboard responde "¿dónde tengo que actuar hoy?" y el Detalle responde "¿por qué está así y qué lo bloquea?". Con eso puede anticipar riesgos antes de que se vuelvan retrasos.

## Qué mejoraría con más tiempo

1. **Validar con PMs reales:** probar si el orden de la información coincide con cómo toman decisiones.
2. **Tendencias:** agregar sparklines o un burndown para ver si un proyecto mejora o empeora, no solo su estado actual.
3. **Matriz de riesgos:** construir la pantalla completa que hoy solo se enlaza como "Revisar matriz".
4. **Estados faltantes:** carga y error (hoy solo existe el estado vacío de la búsqueda) y flujos para acciones como Nuevo o Editar.
5. **Accesibilidad:** auditar contraste (sobre todo en ámbar) y probar con lector de pantalla.

---

## Extra: fui un paso más allá

Trabajar con Figma es genial, pero usar **Claude y Claude Code** lleva todo a otro nivel. Por eso decidí ir un poco más allá y construí **un prototipo mucho más completo con el que pueden interactuar**: filtros, búsqueda, navegación entre pantallas, vista móvil y desktop, y pantallas adicionales de Tareas, Equipo y Perfil. Además incluyo handoff para desarrolladores y documentación organizada en GitHub.

La IA aceleró la ejecución; las decisiones de diseño son mías (ver [`uso-de-ia.md`](uso-de-ia.md)).

**Prototipo interactivo:** https://claude.ai/artifact/1cKUS8E3moiF6sBRX9YRaH  
**Repositorio con handoff y documentación:** https://github.com/auracristina0693/kadree-tech-dashboard
