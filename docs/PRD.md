# PRD · <M-music-player>

> Documento de requisitos del producto (Product Requirements Document).
> Complétalo en el Sprint 0 (historia H0.3) y pide la aprobación del profesor en un Issue.
> Cada requisito funcional (RF) se convierte en un Issue con la plantilla "Historia de usuario".

| Campo | Valor |
| --- | --- |
| Alumno |MariaAMN |
| Proyecto n.º |1|
| Sitio de referencia |Spotify |
| Compañero revisor |Jeison Pernia |
| URL desplegada | (se completa en el Sprint 5) |

## 1. Problema

Algunos reproductores de música web son pesados o sobrecargan la interfaz con anuncios y menús complejos. Los usuarios necesitan una aplicación ligera, rápida que les permita organizar su catálogo de música local o en streaming y gestionar listas de reproducción sin interrupciones.
## 2. Usuarios

- **Usuario principal:** Estudiante o usuario que busca escuchar música en la web de forma ágil desde su laptop o teléfono móvil.
- **Usuario secundario:** Profesor académico que evalúan la calidad del código y el rendimiento del mismo.
## 3. Objetivo y métrica de éxito

Objetivo: Permitir la reproducción continua de canciones y la gestión de playlists en menos de 3 clics.
Metrica:Carga inicial de la aplicación en menos de 3 segundos y reproducción inmediata al hacer clic en un tema.

## 4. Alcance del MVP

Entre 5 y 8 funcionalidades que SÍ entran este semestre.

1. Exploración del catálogo de canciones y álbumes.
2. Controles completos de audio (Play, Pause, Anterior, Siguiente, Barra de progreso).
3. Creación y edición de listas de reproducción (Playlists). 
4. Gestión de cola de reproducción. 
5. Búsqueda y filtrado rápido por canción o artista.

### Funcionalidades → carpetas de `src/` (screaming architecture)

Cada funcionalidad del alcance será una carpeta en `src/`. Nómbralas en inglés y en plural.

| Funcionalidad | Carpeta |
| --- | --- |
|Reproductor de audio |`src/player` | 
| Listas de reproducción | `src/playlists` | 
| Catálogo de canciones | `src/tracks` | 
| Usuarios / Perfiles | `src/users` |


## 5. Fuera de alcance

Lo que NO vas a construir.

- Descarga de archivos de audio a la memoria local. 
- Integración con APIs externas de pago (como Spotify SDK comercial). 
- Sistema de pagos o suscripciones Premium.

## 6. Requisitos funcionales

| ID | Requisito | Prioridad (alta, media, baja) |
| --- | --- | --- |
| RF-01 | Reproducir, pausar y saltar pistas de audio | Alta | 
| RF-02 | Crear y guardar listas de reproducción personalizadas | Alta | 
| RF-03 | Buscar canciones por título o artista | Media | | RF-04 | Visualizar la cola de canciones pendientes | Media |

## 7. Requisitos no funcionales

- Responsive, móvil primero (375 px y 1280 px).
- Lighthouse ≥ 90 en Accesibilidad y Buenas prácticas.
- 0 errores en la consola del navegador.
- Funciona con 10.000 registros sin congelarse.

## 8. Modelo de datos

Diagrama entidad-relación y tablas PostgreSQL con tipos, claves y restricciones.
GitHub dibuja diagramas Mermaid; edita este ejemplo:

```mermaid erDiagram USUARIO ||--o{ PLAYLIST : crea 
PLAYLIST ||--|{ PLAYLIST\_TRACK : contiene 
TRACK ||--o{ PLAYLIST\_TRACK : pertenece\_a USUARIO {
   int id PK 
   text nombre
  text email 
  } 
   PLAYLIST {
  int id PK
  int usuario\_id FK
   text titulo 
   timestamptz creado\_en
  } 
  TRACK { 
  int id PK 
  text titulo 
  text artista 
  text url\_audio 
  }

## 9. Reto técnico distintivo

Implementación de estructuras de datos propias en `src/shared/structures/` para gestionar el bucle de reproducción sin depender de librerías externas. 

## 10. Riesgos y preguntas abiertas

Optimización del almacenamiento de archivos de audio de gran tamaño.
