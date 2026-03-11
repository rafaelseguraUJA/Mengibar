# Arquitectura UX/UI — Aplicación Móvil AR Mengíbar

## Fase 2: Arquitectura y Diseño UX/UI

---

## 1. Arquitectura de Información

### 1.1 Mapa de Contenidos

```
Aplicación Móvil AR Mengíbar
│
├── Pantalla de Bienvenida (Splash)
│   ├── → Acceder como Invitado
│   └── → Iniciar Sesión / Registrarse
│
├── Acceso y Autenticación
│   ├── Iniciar Sesión
│   │   ├── Email + Contraseña
│   │   └── → Recuperar contraseña
│   ├── Registro
│   │   ├── Usuario general
│   │   └── Perfil docente
│   └── Modo Invitado (sin registro)
│
├── Pantalla Principal (Home)
│   ├── Barra de búsqueda
│   ├── Accesos rápidos
│   │   ├── Explorar (Mapa)
│   │   ├── Recorridos
│   │   ├── Vista AR
│   │   └── Novedades
│   └── POI Destacados
│
├── Mapa del Yacimiento
│   ├── Vista mapa interactivo
│   ├── Posición GPS del usuario
│   ├── Marcadores de POI
│   ├── Filtros por categoría
│   ├── Notificaciones de POI cercanos
│   └── → Detalle de POI
│
├── Vista de Realidad Aumentada (RA)
│   ├── Cámara en tiempo real
│   ├── Modelos 3D superpuestos
│   ├── Selector de época histórica
│   ├── Vista brújula-RA (dirección a POIs)
│   ├── Activar/Desactivar capa RA
│   └── Alternativa texto/mapa estático (accesibilidad)
│
├── Detalle de Punto de Interés (POI)
│   ├── Título y descripción breve
│   ├── Descripción extendida
│   ├── Galería de imágenes
│   ├── Audio narrativo + transcripción
│   ├── Modelo 3D interactivo (si aplica)
│   ├── Vídeo documental (si aplica)
│   ├── Vista RA desde este POI
│   └── Añadir a favoritos
│
├── Recorridos e Itinerarios
│   ├── Recorridos predefinidos
│   │   ├── Recorrido Corto (≈30 min)
│   │   ├── Recorrido Medio (≈60 min)
│   │   └── Recorrido Largo (≈90 min)
│   ├── Recorrido Personalizado
│   │   ├── Selección de POI
│   │   └── Cálculo de ruta y tiempo
│   ├── Progreso del recorrido activo
│   └── Resumen y exportación al finalizar
│
├── Perfil de Usuario
│   ├── Datos de usuario
│   ├── Historial de visitas
│   ├── Favoritos guardados
│   ├── Insignias obtenidas
│   ├── [Docente] Gestión de grupos
│   └── Sincronización
│
└── Ajustes
    ├── Idioma (ES / EN)
    ├── Modo alto contraste
    ├── Tamaño de fuente
    ├── Descargas para uso sin conexión
    ├── Privacidad y consentimiento GPS
    └── Información legal (RGPD)
```

---

## 2. Flujos de Usuario Principales

### 2.1 Flujo de Acceso

```
[Inicio App]
     │
     ▼
[Pantalla Bienvenida]
     │
     ├──────────────────────┬──────────────────────┐
     ▼                      ▼                      ▼
[Invitado]          [Iniciar Sesión]         [Registrarse]
     │                      │                      │
     │                      ▼                      ▼
     │              [Formulario Login]    [Formulario Registro]
     │                      │                      │
     └──────────────────────┴──────────────────────┘
                            │
                            ▼
                    [Pantalla Principal]
```

### 2.2 Flujo de Exploración con RA

```
[Pantalla Principal]
     │
     ▼
[Mapa del Yacimiento]
     │
     ├── [Seleccionar POI en mapa]
     │         │
     │         ▼
     │   [Detalle POI]
     │         │
     │         ▼
     │   [Activar Vista RA]
     │         │
     │         ▼
     │   [Modelo 3D en cámara] ←→ [Selector de época]
     │
     └── [Botón Vista RA directa]
               │
               ▼
         [Vista AR + brújula]
               │
               ▼
         [POI detectado]
               │
               ▼
         [Detalle POI]
```

### 2.3 Flujo de Recorrido

```
[Recorridos]
     │
     ├── [Seleccionar recorrido predefinido]
     │         │
     │         ▼
     │   [Detalle del recorrido]
     │   (mapa, hitos, duración estimada)
     │         │
     │         ▼
     │   [Iniciar recorrido]
     │         │
     │         ▼
     │   [Navegación hito a hito]
     │   (mapa + notificaciones proximidad)
     │         │
     │         ├── [Hito visitado → Contenido POI]
     │         │         │
     │         │         └── [Cuestionario/Actividad]
     │         │
     │         └── [Pausa / Reanudación]
     │                   │
     │                   ▼
     │           [Último hito completado]
     │                   │
     │                   ▼
     │           [Resumen del recorrido]
     │           (exportar imagen/PDF)
     │
     └── [Crear recorrido personalizado]
               │
               ▼
         [Selección de POI]
               │
               ▼
         [Cálculo de ruta]
               │
               ▼
         [Iniciar recorrido]
```

---

## 3. Pantallas Principales — Esquemas de Interfaz

### 3.1 Convenciones de Diseño

| Elemento | Descripción |
|----------|-------------|
| **Paleta cromática** | Ocre/tierra (#C4973B), blanco (#FFFFFF), gris oscuro (#2D2D2D), azul accesible (#1565C0) |
| **Tipografía** | Familia sans-serif de sistema; tamaño mínimo 16sp cuerpo, 14sp auxiliar |
| **Área táctil mínima** | 44×44 píxeles lógicos (ACC-07) |
| **Contraste mínimo** | 4.5:1 para texto normal, 3:1 para texto grande (WCAG 2.1 AA) |
| **Iconografía** | Iconos del sistema + etiqueta textual para todos los controles de navegación |

### 3.2 Índice de Wireframes

| Pantalla | Archivo |
|----------|---------|
| 01 — Bienvenida (Splash) | [wireframes/01-bienvenida.html](wireframes/01-bienvenida.html) |
| 02 — Acceso (Login / Registro / Invitado) | [wireframes/02-acceso.html](wireframes/02-acceso.html) |
| 03 — Pantalla Principal (Home) | [wireframes/03-home.html](wireframes/03-home.html) |
| 04 — Mapa del Yacimiento | [wireframes/04-mapa.html](wireframes/04-mapa.html) |
| 05 — Vista de Realidad Aumentada | [wireframes/05-vista-ra.html](wireframes/05-vista-ra.html) |
| 06 — Detalle de Punto de Interés | [wireframes/06-detalle-poi.html](wireframes/06-detalle-poi.html) |
| 07 — Recorridos e Itinerarios | [wireframes/07-recorridos.html](wireframes/07-recorridos.html) |
| 08 — Perfil de Usuario | [wireframes/08-perfil.html](wireframes/08-perfil.html) |
| 09 — Ajustes | [wireframes/09-ajustes.html](wireframes/09-ajustes.html) |
| Índice completo | [wireframes/index.html](wireframes/index.html) |

---

## 4. Especificaciones de Accesibilidad (WCAG 2.1 AA)

| ID | Requisito | Implementación en diseño |
|----|-----------|--------------------------|
| ACC-01 | Nivel AA en componentes no-RA | Contraste, tamaños tipográficos y áreas táctiles definidos según WCAG 2.1 |
| ACC-02 | Subtítulos en audios | Área de transcripción visible en la ficha de POI y durante la reproducción |
| ACC-03 | Audiodescripción en modelos 3D | Botón de audiodescripción en la vista de modelo 3D |
| ACC-04 | Soporte VoiceOver / TalkBack | Todos los elementos etiquetados con texto accesible; orden de foco lógico |
| ACC-05 | Alto contraste y tamaño de fuente | Opciones en Ajustes; interfaz reactiva al tamaño de fuente del sistema |
| ACC-06 | Alternativa texto/mapa estático para RA | Botón "Ver sin RA" en todas las vistas AR |
| ACC-07 | Área táctil ≥ 44×44 píxeles lógicos | Aplicado a todos los botones e iconos interactivos |

---

## 5. Sistema de Navegación

### 5.1 Barra de Navegación Inferior (Tab Bar)

Presente en todas las pantallas principales después del acceso:

| Posición | Icono | Etiqueta | Pantalla destino |
|----------|-------|----------|-----------------|
| 1 | 🏠 | Inicio | Pantalla Principal |
| 2 | 🗺️ | Mapa | Mapa del Yacimiento |
| 3 | 📷 | RA | Vista de RA |
| 4 | 🚶 | Recorridos | Recorridos e Itinerarios |
| 5 | 👤 | Perfil | Perfil de Usuario |

### 5.2 Barra de Navegación Superior (App Bar)

- Logo / Nombre de la app (izquierda)
- Buscador (centro, en Home y Mapa)
- Botón de ajustes (derecha)
- Botón de retroceso (izquierda, en pantallas secundarias)

---

## 6. Estados de Conectividad

| Estado | Indicador visual | Comportamiento |
|--------|-----------------|----------------|
| Conexión activa | Sin indicador especial | Todas las funciones disponibles |
| Sin conexión | Banner informativo en App Bar | Solo contenidos descargados disponibles |
| GPS disponible | Icono GPS activo en Mapa | RA basada en posición habilitada |
| GPS no disponible | Icono GPS con advertencia | Activar RA por marcador QR/fiducial |
| BLE activo (interior) | Icono de baliza en Mapa | Posicionamiento interior por beacons |

---

## 7. Consideraciones para el Equipo Científico

- Los recorridos y los hitos obligatorios/opcionales (RF-23) deben ser **validados por el equipo de arqueología y pedagogía** (CA-04) antes de la implementación.
- El selector de época histórica (RF-07, RF-21) requerirá coordinación con el equipo científico para definir los periodos (ibérico, romano, medieval, etc.) y los modelos 3D asociados.
- Los textos interpretativos y audios narrativos (RD-02, RD-03) se integrarán a través del CMS (RF-36), permitiendo actualizaciones sin lanzar nuevas versiones de la app.
- Los criterios de gamificación (RF-33 a RF-35) deberán ser validados con el equipo pedagógico para asegurar coherencia con los objetivos de aprendizaje.
