# Dashboard de Gestión de Proyectos — Prueba técnica Kadree Tech

Dashboard para un Project Manager que gestiona varios proyectos digitales y necesita ver, en segundos, **avances, estados y riesgos**.

Diseño y prototipo por **Cristina Salazar** (UX/UI Designer), con apoyo de IA en la ejecución. Ver [`docs/uso-de-ia.md`](docs/uso-de-ia.md).

**[▶ Ver el prototipo en línea](https://claude.ai/artifact/1cKUS8E3moiF6sBRX9YRaH)**

## Qué entrego

| Entregable pedido | Dónde está |
|---|---|
| 2 pantallas en alta fidelidad | Dashboard (Resumen de proyectos) y Detalle del proyecto, dentro de [`prototype/index.html`](prototype/index.html) |
| Explicación (máx. 1 página) | [`docs/explicacion-entrega.md`](docs/explicacion-entrega.md) |

**Extras (no pedidos):** handoff para desarrolladores, tokens de diseño, decisiones de diseño y nota sobre el uso de IA.

## Cómo ver el prototipo

1. Abre el [prototipo en línea](https://claude.ai/artifact/1cKUS8E3moiF6sBRX9YRaH), o `prototype/index.html` en tu navegador (no necesita instalación ni servidor).
2. Usa el conmutador **Móvil / Desktop** del pie de página para cambiar de vista. En pantallas de 1024 px o más se ajusta solo.
3. Desde el Dashboard, toca **Ver detalle** en cualquier proyecto para abrir la segunda pantalla.

> Los datos son **ficticios**: clientes, proyectos, personas y cifras se inventaron para la prueba.

## Estructura del repositorio

```
.
├── README.md
├── docs/
│   ├── explicacion-entrega.md       # La explicación de 1 página (entregable)
│   ├── explicacion-entrega.pdf      # La misma explicación en PDF
│   ├── handoff-desarrolladores.md   # Guía para implementar el diseño
│   ├── decisiones-de-diseno.md      # Por qué se diseñó así
│   └── uso-de-ia.md                 # Qué hizo la IA y qué decidí yo
├── tokens/
│   └── tokens.json                  # Colores, tipografía, radios y sombras
└── prototype/
    └── index.html                   # Prototipo HTML/CSS/JS autocontenido
```

## Por dónde empezar

- **Evaluador de diseño:** `docs/explicacion-entrega.md`, luego el prototipo.
- **Desarrollador:** `docs/handoff-desarrolladores.md` y `tokens/tokens.json`.
