# Documentación del Proyecto: MotorDesk

## 1. Visión General
**MotorDesk** es una interfaz web moderna diseñada para la gestión operativa de un taller mecánico. El proyecto se centra en ofrecer una experiencia de usuario fluida y visualmente atractiva, utilizando tecnologías web estándar (HTML5 y CSS3) sin dependencia de frameworks pesados de JavaScript para la lógica visual.

## 2. Sistema de Diseño (Design System)

El proyecto utiliza un lenguaje de diseño consistente basado en el concepto de **"Dark Glassmorphism"** (Vidrio Oscuro).

### Paleta de Colores
Las variables principales se encuentran en `css/variables.css`.
-   **Fondo Principal:** Gradiente radial oscuro (`#0f172a` a `#020617`).
-   **Superficies (Tarjetas/Paneles):** Fondos semitransparentes con desenfoque (`backdrop-filter: blur`).
-   **Acentos:**
    -   **Primario (Azul):** `#3b82f6` (Botones de acción, enlaces).
    -   **Secundario (Cian):** `#06b6d4` (Bordes, efectos de brillo).
    -   **Terciario (Violeta):** `#8b5cf6` (Identificadores, detalles).
    -   **Éxito (Verde):** `#10b981` (Estado "Entregado", Botón "Imprimir").
    -   **Alerta (Ámbar):** `#f59e0b` (Estado "En Espera").

### Tipografía
-   **Fuente:** 'Nunito', sans-serif (Google Fonts).
-   Se prioriza la legibilidad con altos contrastes de color blanco/gris sobre fondos oscuros.

## 3. Estructura del Proyecto

```
PROYECTO_DISE-O/
├── component-layout/       # Estilos de componentes reutilizables
│   ├── Navbar.css          # Barra de navegación superior
│   └── Sub-cars.css        # Tarjetas de sub-servicios
├── css/                    # Hojas de estilo principales
│   ├── orden-en-curso.css  # Módulo de órdenes activas
│   ├── historial.css       # Módulo de historial
│   ├── repuestos.css       # Módulo de selección de repuestos
│   ├── panel.css           # Estilos del dashboard principal
│   ├── estilos.css         # Estilos base y de login
│   ├── variables.css       # Definición de colores y fuentes
│   └── tipo-orden/         # Estilos específicos para modales de servicio
├── pages/                  # Vistas HTML de la aplicación
│   ├── historial.html      # Página de historial
│   ├── orden-en-curso.html # Tablero de órdenes
│   ├── panel.html          # Dashboard principal
│   ├── seleccion-repuestos.html # Catálogo de repuestos
│   └── tipo-orden/         # Páginas individuales para cada servicio (12 archivos)
├── LogoI_mg/               # Recursos de imágenes y logotipos
└── index.html              # Landing page / Login
```

## 4. Módulos Principales

### Panel de Control (Dashboard)
-   **Archivo:** `pages/panel.html`
-   **Función:** Centro de mando con accesos directos a las categorías de servicio principales (Mecánica, Eléctrico, etc.) y vista rápida de inventario bajo.

### Selección de Servicios
-   **Archivos:** `pages/tipo-orden/*.html`
-   **Función:** Al seleccionar una categoría en el panel, el usuario navega a una página específica (ej. "Mantenimiento Preventivo") donde elige un sub-servicio.
-   **Flujo:** Servicio -> Sub-servicio -> Selección de Repuestos.

### Selección de Repuestos
-   **Archivo:** `pages/seleccion-repuestos.html`
-   **Función:** Catálogo visual de piezas dividido por tipo de vehículo (Motos, Autos, Camiones).
-   **Características:**
    -   Barra de búsqueda en el encabezado.
    -   Opción "Continuar sin repuestos".
    -   Modal de confirmación de registro.

### Órdenes en Curso
-   **Archivo:** `pages/orden-en-curso.html`
-   **Función:** Tablero visual tipo Kanban (lista) de los vehículos que están siendo atendidos.
-   **Interacción:** Al hacer clic en una tarjeta, se abre un modal con detalles.
-   **Acciones:** Editar (Visual), Imprimir Factura (Visual), Cerrar.

### Historial
-   **Archivo:** `pages/historial.html`
-   **Función:** Lista tabular de servicios finalizados.
-   **Características:** Buscador integrado y etiquetas de estado (Entregado/Cancelado).

## 5. Aspectos Técnicos Destacados

### Modales CSS-Only
Se implementaron ventanas modales sin usar JavaScript, utilizando la pseudo-clase `:target`.
-   **Funcionamiento:** Los enlaces apuntan a un ID (ej. `#modal-exito`). Al cambiar el hash de la URL, el elemento con ese ID cambia su propiedad `display` o `opacity` para hacerse visible.

### Efectos Visuales
-   **Glassmorphism:** Uso extensivo de `background: rgba(...)` y `backdrop-filter: blur()` para crear profundidad.
-   **Grid Layout:** Uso de CSS Grid para las cuadrículas de tarjetas, asegurando que sean responsivas (se adaptan al ancho de la pantalla automáticamente).
-   **Animaciones:** Transiciones suaves (`transition: all 0.3s`) en botones y tarjetas al pasar el cursor (hover).
