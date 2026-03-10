# Requisitos Funcionales — Aplicación Móvil de Realidad Aumentada para Mengíbar

## 1. Introducción

Este documento recoge los requisitos funcionales detallados de la aplicación móvil de Realidad Aumentada (RA) orientada a la difusión del patrimonio arqueológico e histórico de Mengíbar. Surge del proceso de levantamiento de requisitos conjuntos entre los equipos de arqueología, pedagogía e informática, en el marco de la **Fase 1: Análisis y definición funcional**.

---

## 2. Objetivos Pedagógicos

| ID | Objetivo |
|----|---------|
| OP-01 | Facilitar la comprensión del contexto histórico y arqueológico del yacimiento a través de capas de información superpuestas sobre la realidad. |
| OP-02 | Ofrecer itinerarios temáticos adaptados a distintos niveles educativos (educación primaria, secundaria y público general). |
| OP-03 | Fomentar la exploración autónoma y el aprendizaje activo mediante recorridos autoguiados con hitos interpretativos. |
| OP-04 | Proporcionar contenidos en distintos formatos (texto, audio, vídeo, modelos 3D) para favorecer distintos estilos de aprendizaje. |
| OP-05 | Incluir actividades interactivas (cuestionarios, retos de exploración) que refuercen la retención del conocimiento. |

---

## 3. Públicos Objetivo

| ID | Perfil | Características principales |
|----|--------|-----------------------------|
| PU-01 | Visitantes generales | Adultos sin conocimientos previos; buscan una experiencia divulgativa amena. |
| PU-02 | Grupos escolares (6–12 años) | Necesitan contenidos simplificados, lúdicos y supervisión docente integrada. |
| PU-03 | Grupos escolares (13–18 años) | Pueden manejar contenidos más densos; se benefician de retos y gamificación. |
| PU-04 | Investigadores y académicos | Requieren acceso a datos técnicos, bibliografía y capas de información avanzadas. |
| PU-05 | Personas con diversidad funcional | Necesitan contenidos accesibles: subtítulos, audiodescripción, contraste alto y navegación simplificada. |

---

## 4. Inventario de Recursos Digitales

| ID | Tipo | Descripción |
|----|------|-------------|
| RD-01 | Modelos 3D | Reconstrucciones virtuales de estructuras arqueológicas, monumentos y objetos del yacimiento (formato glTF/GLB). |
| RD-02 | Textos interpretativos | Fichas descriptivas de cada punto de interés, disponibles en español e inglés. |
| RD-03 | Audios narrativos | Locuciones en español e inglés que describen cada punto de interés; versión adaptada para niños. |
| RD-04 | Fotografías históricas | Imágenes de archivo del yacimiento y su entorno, georreferenciadas. |
| RD-05 | Vídeos documentales | Clips cortos (< 3 min) sobre procesos de excavación y hallazgos relevantes. |
| RD-06 | Animaciones 3D | Secuencias que ilustran la evolución temporal del yacimiento. |
| RD-07 | Mapas históricos | Cartografía georeferenciada que permite comparar el paisaje actual con el histórico. |

---

## 5. Requisitos Funcionales

### 5.1 Gestión de Usuarios y Acceso

| ID | Requisito | Prioridad |
|----|-----------|-----------|
| RF-01 | La aplicación permitirá el uso sin registro previo (modo invitado). | Alta |
| RF-02 | Se ofrecerá registro opcional de usuario para guardar progreso, favoritos e historial de visitas. | Media |
| RF-03 | Existirá un perfil de usuario docente que permita crear grupos y asignar itinerarios a estudiantes. | Media |
| RF-04 | La aplicación funcionará en modo sin conexión para zonas del yacimiento con cobertura limitada, descargando previamente los contenidos del recorrido seleccionado. | Alta |

### 5.2 Realidad Aumentada

| ID | Requisito | Prioridad |
|----|-----------|-----------|
| RF-05 | La aplicación superpondrá modelos 3D sobre la vista de la cámara del dispositivo al detectar marcadores visuales o zonas georreferenciadas. | Alta |
| RF-06 | Los modelos 3D podrán ser explorados interactivamente: rotación, zoom y selección de partes etiquetadas. | Alta |
| RF-07 | La capa de RA mostrará el estado reconstructivo del yacimiento en distintas épocas históricas seleccionables por el usuario. | Alta |
| RF-08 | Se podrá activar y desactivar la capa de RA en cualquier momento sin interrumpir la navegación. | Alta |
| RF-09 | La aplicación detectará la orientación y la iluminación del entorno para ajustar la renderización de los modelos RA de forma realista. | Media |
| RF-10 | Se soportarán marcadores físicos (QR, marcadores fiduciales) como mecanismo alternativo de activación de RA cuando el posicionamiento GPS no sea preciso. | Alta |

### 5.3 Posicionamiento y Navegación

| ID | Requisito | Prioridad |
|----|-----------|-----------|
| RF-11 | La aplicación utilizará GPS para determinar la posición del usuario en tiempo real y mostrarla sobre el mapa del yacimiento. | Alta |
| RF-12 | Se empleará fusión de sensores (GPS + brújula + acelerómetro + barómetro) para mejorar la precisión del posicionamiento en exteriores. | Alta |
| RF-13 | En interiores o zonas de señal GPS degradada, la aplicación usará balizas Bluetooth Low Energy (BLE/iBeacon) o Wi-Fi Fingerprinting para mantener la localización. | Media |
| RF-14 | El sistema registrará la trayectoria completa del usuario durante la visita (track GPS) con una frecuencia configurable (mínimo cada 5 segundos). | Media |
| RF-15 | Los puntos de interés (POI) próximos al usuario (radio configurable, por defecto 20 m) se resaltarán automáticamente en el mapa y mediante notificación in-app. | Alta |
| RF-16 | La aplicación calculará y mostrará la ruta óptima a pie entre la posición actual del usuario y un POI seleccionado. | Media |
| RF-17 | Se ofrecerá una vista de brújula-RA que indique la dirección y la distancia a los POI cercanos cuando el usuario apunte con la cámara. | Alta |
| RF-18 | La precisión mínima requerida para activar contenidos de RA basados en posición será de ±5 m en exteriores. | Alta |
| RF-19 | El sistema almacenará los datos de posicionamiento de forma anónima y con consentimiento expreso del usuario, cumpliendo el RGPD. | Alta |

### 5.4 Recorridos Temporales

| ID | Requisito | Prioridad |
|----|-----------|-----------|
| RF-20 | La aplicación ofrecerá al menos tres recorridos temáticos predefinidos con diferentes duraciones estimadas (corto ≈ 30 min, medio ≈ 60 min, largo ≈ 90 min). | Alta |
| RF-21 | Cada recorrido estará asociado a una línea de tiempo histórica que permita al usuario visualizar la evolución del yacimiento (periodo ibérico, romano, medieval, etc.). | Alta |
| RF-22 | El usuario podrá crear recorridos personalizados seleccionando POI de su interés; la aplicación calculará el orden y tiempo estimado. | Media |
| RF-23 | Los recorridos incluirán hitos obligatorios y hitos opcionales claramente diferenciados en la interfaz. | Media |
| RF-24 | La aplicación registrará el tiempo real invertido en cada hito y en el recorrido completo, mostrando un resumen al finalizar. | Media |
| RF-25 | Se podrá pausar y reanudar un recorrido en cualquier momento, conservando el progreso entre sesiones. | Alta |
| RF-26 | Al completar un recorrido, la aplicación generará un resumen visual (mapa del trayecto, hitos visitados, tiempo empleado) exportable como imagen o PDF. | Baja |
| RF-27 | El sistema sincronizará el progreso de recorridos con la cuenta de usuario cuando haya conexión disponible. | Media |

### 5.5 Contenidos e Información

| ID | Requisito | Prioridad |
|----|-----------|-----------|
| RF-28 | Cada POI dispondrá de ficha de información con: título, descripción breve, descripción extendida, galería de imágenes, audio narrativo y, si procede, modelo 3D. | Alta |
| RF-29 | El usuario podrá filtrar los POI visibles por categoría temática (arquitectura, hallazgos, personajes históricos, etc.). | Media |
| RF-30 | La aplicación permitirá cambiar el idioma de la interfaz y los contenidos (español e inglés en la versión inicial). | Alta |
| RF-31 | Los contenidos descargados se almacenarán en caché local para su uso sin conexión; la app notificará al usuario si los contenidos están desactualizados. | Alta |
| RF-32 | Se incluirá un buscador de POI por nombre y categoría. | Media |

### 5.6 Gamificación e Interactividad

| ID | Requisito | Prioridad |
|----|-----------|-----------|
| RF-33 | Cada recorrido incluirá al menos un cuestionario o actividad interactiva para verificar la comprensión de los contenidos. | Media |
| RF-34 | La aplicación otorgará insignias digitales al completar recorridos, responder correctamente cuestionarios o descubrir POI ocultos. | Baja |
| RF-35 | Existirá un modo de exploración libre en el que el usuario acumule puntos de exploración según los POI visitados. | Baja |

### 5.7 Administración y Gestión de Contenidos (CMS)

| ID | Requisito | Prioridad |
|----|-----------|-----------|
| RF-36 | Existirá un panel de administración web (CMS) que permita al equipo de arqueología añadir, editar y eliminar POI y contenidos sin necesidad de actualizar la aplicación. | Alta |
| RF-37 | El CMS permitirá la gestión de recorridos: creación, edición, publicación y archivado. | Alta |
| RF-38 | El CMS mostrará estadísticas de uso: visitantes únicos, recorridos completados, POI más visitados y mapas de calor de trayectorias (datos anonimizados). | Media |
| RF-39 | El CMS gestionará las versiones de los modelos 3D y otros recursos digitales, permitiendo revertir a versiones anteriores. | Media |

---

## 6. Especificaciones de Accesibilidad

| ID | Requisito |
|----|-----------|
| ACC-01 | La interfaz cumplirá el nivel AA de las WCAG 2.1 en todos los componentes de UI que no dependan de RA. |
| ACC-02 | Todos los audios narrativos contarán con transcripción textual visible en pantalla (subtítulos). |
| ACC-03 | Los modelos 3D y elementos interactivos dispondrán de audiodescripción activable. |
| ACC-04 | La aplicación soportará los lectores de pantalla nativos de iOS (VoiceOver) y Android (TalkBack) en las pantallas que no requieran vista de cámara. |
| ACC-05 | Se ofrecerá un modo de alto contraste y la posibilidad de aumentar el tamaño de fuente sin pérdida de funcionalidad. |
| ACC-06 | El modo de RA dispondrá de una alternativa de navegación basada en texto y mapas estáticos para usuarios que no puedan utilizar la cámara. |
| ACC-07 | Los elementos interactivos tendrán un área táctil mínima de 44×44 píxeles lógicos, conforme a las guías de accesibilidad de Apple y Google. |

---

## 7. Criterios de Aceptación Generales

| ID | Criterio |
|----|----------|
| CA-01 | La aplicación se instala y ejecuta correctamente en dispositivos iOS 14+ y Android 9+ con soporte ARKit / ARCore. |
| CA-02 | El tiempo de carga inicial de la aplicación no supera los 3 segundos en conexión Wi-Fi estándar (≥ 20 Mbps). |
| CA-03 | La detección del posicionamiento GPS y la activación de la capa RA se producen en menos de 5 segundos tras el lanzamiento. |
| CA-04 | Todos los recorridos predefinidos han sido validados por el equipo de arqueología y pedagogía antes del lanzamiento. |
| CA-05 | La aplicación supera las pruebas de usabilidad con al menos el 80 % de los usuarios de cada perfil objetivo sin necesidad de asistencia externa. |
| CA-06 | No se producen fallos críticos (crashes) durante recorridos completos en el 99 % de las sesiones de prueba. |
| CA-07 | El consumo de batería durante un recorrido de 60 minutos con RA activa no supera el 25 % de la batería de un dispositivo de referencia. |
| CA-08 | El panel de administración (CMS) permite publicar un nuevo POI en menos de 10 minutos por un usuario sin formación técnica. |
| CA-09 | La aplicación cumple la normativa RGPD y la Ley Orgánica de Protección de Datos (LOPDGDD) en lo relativo al tratamiento de datos de posicionamiento. |

---

## 8. Requisitos No Funcionales Relacionados

| ID | Requisito |
|----|-----------|
| RNF-01 | La arquitectura del sistema soportará un mínimo de 200 usuarios simultáneos sin degradación perceptible del rendimiento. |
| RNF-02 | Los datos de usuario y posicionamiento se transmitirán cifrados (TLS 1.3 preferente, TLS 1.2 como mínimo aceptable). |
| RNF-03 | El sistema dispondrá de copias de seguridad diarias automatizadas del CMS y la base de datos de recorridos. |
| RNF-04 | El código fuente de la aplicación seguirá las guías de estilo acordadas y contará con cobertura de tests unitarios ≥ 70 % en la lógica de negocio. |

---

## 9. Glosario

| Término | Definición |
|---------|------------|
| RA | Realidad Aumentada: tecnología que superpone información digital (modelos 3D, textos, etc.) sobre la vista del mundo real a través de la cámara. |
| POI | Point of Interest (Punto de Interés): ubicación concreta del yacimiento asociada a contenidos digitales. |
| ARKit | Framework de RA de Apple para dispositivos iOS. |
| ARCore | Framework de RA de Google para dispositivos Android. |
| BLE | Bluetooth Low Energy: tecnología de comunicación inalámbrica de bajo consumo usada para posicionamiento en interiores. |
| CMS | Content Management System: panel web de gestión de contenidos. |
| glTF/GLB | Formato estándar de intercambio de modelos 3D optimizado para aplicaciones web y móviles. |
| RGPD | Reglamento General de Protección de Datos de la Unión Europea. |
| WCAG | Web Content Accessibility Guidelines: guías de accesibilidad del W3C. |
