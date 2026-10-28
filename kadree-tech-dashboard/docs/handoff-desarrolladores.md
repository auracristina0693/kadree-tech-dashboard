# Handoff para desarrolladores

Guía para implementar el dashboard a partir del prototipo. **Fuente de verdad:** `prototype/index.html` (HTML/CSS/JS sin dependencias, salvo la fuente Poppins de Google Fonts). Los tokens están en `tokens/tokens.json`.

## 1. Alcance

| Pantalla | Ruta (hash) | Prioridad |
|---|---|---|
| Dashboard — Resumen de proyectos | `#` (inicio) | Entregable de la prueba |
| Detalle del proyecto | `#proyecto-<id>` | Entregable de la prueba |
| Tareas | `#tareas` | Extra |
| Equipo | `#equipo` | Extra |
| Perfil | `#perfil` | Extra |

IDs de proyecto en el prototipo: `app`, `portal`, `migracion`, `rediseno`, `sitio`, `automatizacion`, `plataforma`.

## 2. Tokens de diseño

Definidos como variables CSS en `:root` y exportados a `tokens/tokens.json`.

- **Tipografía:** Poppins (300–700). Base 14 px / 1.43. Títulos de página 30 px/700 en móvil, detalle 24 px/700, secciones 18 px/600.
- **Color:** paleta base (`brand`, `cyan`, `neutral`, `red`, `green`, `amber`, `blue`, `purple`) y capa **semántica** (`--primary`, `--danger`, `--success`, `--warning-*`, `--surface`, `--fg`, `--muted`, `--border`). **Los componentes usan solo tokens semánticos**, nunca hex directos.
- **Modo oscuro:** soportado con `prefers-color-scheme` y `data-theme="dark|light"`; solo se sobrescriben los tokens semánticos.
- **Radios:** `sm .375rem`, `md .75rem`, `lg 1rem`, `xl 1.5rem`. Tarjetas: `lg`. Botones y campos: `md`. Chips y píldoras: `999px`.
- **Movimiento:** curva `cubic-bezier(.2,.8,.2,1)`; entrada de pantalla 380 ms, salida 160 ms, barras de progreso 1 s. Se respeta `prefers-reduced-motion`.

## 3. Layout y responsive

- **Móvil:** columna de máximo 430 px, navegación inferior fija de 5 ítems (Inicio, Proyectos, Tareas, Equipo, Perfil), encabezado fijo de 56 px.
- **Desktop (≥ 1024 px):** el prototipo cambia a vista de escritorio, con la lista de proyectos en tabla (Proyecto, Estado, % de avance, Fecha de entrega, Equipo, Riesgo, Acción), paginación y bloques de apoyo adicionales. Diseñado sobre 1280 px; entre 1024 y 1280 px aplica una variante `narrow`.
- **Áreas seguras:** se usan `env(safe-area-inset-*)` en encabezado, navegación y gutters.
- **Preferencia de vista:** el conmutador Móvil/Desktop guarda `kview` en `localStorage` (`auto` | `mobile` | `desktop`).

## 4. Componentes

| Componente | Variantes / estados | Notas |
|---|---|---|
| **Chip de estado** | `curso`, `riesgo`, `retraso`, `ok`, `info` | Punto de color + texto. Nunca solo color. |
| **Barra de progreso** | `primary`, `danger`, `warn`, `ok` | 8 px (6 px `thin`); animación de relleno al entrar. |
| **Tarjeta KPI** | normal, alerta | Valor 36 px/700, delta y pie. |
| **Tarjeta "Requieren atención"** | borde lateral rojo (`riesgo`) o ámbar (`retraso`) | Título, cliente · tipo, motivo en una línea, barra y enlace "Ver detalle". |
| **Dona de distribución** | 4 segmentos + leyenda con conteo y % | Centro: total de proyectos. |
| **Tarjeta de proyecto** | por estado; `press` (feedback táctil) | Cliente en mayúsculas, avance, fecha, riesgo, avatares apilados. |
| **Filtros (píldoras)** | `aria-pressed` | Todos, En curso, En riesgo, Retrasado, Completado, con conteo. |
| **Búsqueda** | cerrada, abierta con sugerencias, sin resultados | Teclado: ↑ ↓ Enter Esc. |
| **Selector de período** | listbox | Últimos 30 días, Este Q4, Histórico 2026. |
| **Pestañas del detalle** | `aria-selected` + indicador animado | Hacen scroll a la sección (`data-t`). |
| **Ruta de hitos** | completado / actual / pendiente | 5 nodos y 4 etiquetas por proyecto. |
| **Miembro del equipo** | carga < 85 % primary, 85–89 % ámbar, ≥ 90 % rojo | Barra y etiqueta "% carga". |
| **Feed de actividad** | punto de color por tipo | Texto con `<em>` para nombres de tarea. |
| **Panel de notificaciones** | abierto / cerrado | Se posiciona bajo la campana; se cierra con clic fuera. |

## 5. Reglas de negocio visibles en el diseño

- **Color por estado:** `En curso` → primary, `En riesgo` → rojo, `Retrasado` → ámbar, `Completado` → verde.
- **Carga de equipo (vista Equipo):** `sobre` ≥ 90 %, `alta` 75–89 %, `óptima` < 75 %.
- **Atención requerida:** se listan los proyectos en riesgo o retrasados, cada uno con su motivo concreto (avance vs. proyectado, tareas bloqueadas, presupuesto vs. avance validado).
- **Porcentaje "Operativo":** en el prototipo equivale a los proyectos que no están retrasados sobre el total (6 de 7 = 85.7 %). **Definición a confirmar con producto**, porque un proyecto "en riesgo" cuenta como operativo.
- **Totales coherentes:** KPI, lista, filtros y dona deben salir de la misma fuente de datos. Hoy todos dicen 7.

## 6. Comportamientos

- Filtros y búsqueda se combinan y actualizan lista, tabla (desktop) y contador "Mostrando X de Y proyectos".
- Navegación por hash; el detalle abre desde `#proyecto-<id>` y puede abrir una pestaña concreta.
- Transiciones horizontales entre pantallas; se recuerda la posición de scroll del Dashboard al volver.
- Las barras y la dona se animan al entrar a la pantalla.

## 7. Accesibilidad

- Roles y atributos ARIA en pestañas (`tablist`/`tab`), listbox del selector, grupos de filtros y tarjetas navegables (`role="link"`, `tabindex="0"`, `aria-label`).
- Foco visible con anillo `--ring`; estado nunca comunicado solo por color.
- Alturas mínimas de 40 px en botones, 44 px en controles táctiles y 48 px en campos y acciones primarias del detalle. Los botones de ícono del encabezado miden 36 px (por debajo de los 44 px recomendados; revisar).
- **Pendiente de auditar:** contraste del texto ámbar sobre fondo ámbar claro, y prueba con lector de pantalla.

## 8. Datos: modelo sugerido

El prototipo usa un objeto `DATA` por proyecto. Un contrato de API equivalente:

```json
{
  "id": "portal",
  "name": "Portal de Clientes",
  "client": "Seguros Delta",
  "status": "at_risk",
  "progress": 45,
  "planned_progress": 70,
  "risk": "high",
  "start_date": "2026-06-15",
  "due_date": "2026-11-03",
  "budget": { "spent_pct": 68, "spent": 35360, "cap": 52000, "currency": "USD" },
  "milestones": { "labels": ["..."], "completed": 2 },
  "tasks": { "total": 34, "todo": 9, "in_progress": 8, "done": 17 },
  "team": [{ "user_id": "...", "role": "Tech Lead", "load_pct": 95 }],
  "activity": [{ "user_id": "...", "text": "...", "at": "2026-10-28T14:00:00Z" }]
}
```

Estados: `in_progress`, `at_risk`, `delayed`, `done`. Riesgo: `low`, `medium`, `high`.

## 9. Fuera de alcance / por definir

Estos elementos existen en la interfaz pero **no tienen flujo ni pantalla** en el prototipo:

- **Nuevo** (crear proyecto), **Editar**, **+ Agregar** (miembro), **Ver todas** (tareas).
- **Revisar matriz** (matriz de riesgos) y **Reasignar recursos**.
- Estados de **carga** y **error**.
- Descarga/exportación (botón "Descargar" visible solo en desktop, sin comportamiento).

Los datos de ejemplo (clientes, personas, cifras) son ficticios.
