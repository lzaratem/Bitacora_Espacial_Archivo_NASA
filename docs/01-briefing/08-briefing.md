# BRIEFING DEL PROYECTO

__Proyecto:__ Bitácora Espacial Archivo NASA

__Grupo consultor:__ Grupo 8

__Integrantes:__ Henry Valencia, Lisehd Zarate

__Grupo cliente:__ Grupo 3

__Entrevistado:__ Daniel Muñoz, Omar Solarte

__Fecha:__ 13 de septiembre de 2026

__Duración de la entrevista:__ 15 minutos

# __1. EL PROBLEMA__

1.1 Descrito en una frase:
Un aficionado o estudiante de astronomía necesita explorar e inspeccionar material fotográfico de nebulosas y eventos cósmicos con sus metadatos científicos porque requiere información veraz para consulta académica o recreativa, pero actualmente se enfrenta a textos extensos sin jerarquía y a cargas lentas por imágenes de alta resolución no optimizadas.

1.2 Cómo se resuelve hoy, sin el producto:
Búsquedas genéricas en navegadores o consulta directa en repositorios sin filtros dinámicos, navegando entre descripciones largas y archivos pesados que ralentizan la carga en dispositivos móviles.

1.3 Costo del problema:
Pérdida de tiempo al filtrar información, alto consumo de datos móviles, frustración por lentitud de carga y abandono de la plataforma por sobrecarga de texto.

1.4 Frases textuales del cliente:

*  “Las fotos espaciales tardan una eternidad en cargar si estoy con datos y la pantalla se queda congelada.”
*  “Hay textos larguísimos sobre telescopios que no me dejan ver rápido la fecha o el centro de la NASA que tomó la foto.”

# __2. EL USUARIO__
  | Campo          | Usuario principal | Usuario secundario | 
  | ---            | ---               | ---                | 
  | Nombre y edad | Daniel, 21 años   | Omar, 45 años       | 
  |Ocupación o rol | Estudiante universitario / Aficionado | Docente de ciencias de colegio |  
  | Contexto de uso | Entre clases o transporte público | Salón de clase con proyector / PC |
  | Dispositivo | Smartphone Android / iOS | Laptop / Desktop |
  | Nivel tecnológico | Medio - Alto | Medio |
  | Objetivo principal | Buscar imágenes de nebulosas rápidamente | Encontrar material de apoyo visual por fecha/centro |
  | Principal frustración | Carga lenta y textos inacabables en pantalla pequeña | Dificultad para filtrar contenido relevante de forma clara |



# __3. LA TAREA PRINCIPAL__

3.1 Si solo pudiera hacer una cosa, sería:
Visualizar y filtrar una fotogalería astronómica de la NASA de manera fluida, accediendo al detalle de la imagen sin interrupciones por carga.

3.2 Pasos que sigue para lograrla:

* Ingresa a la bitácora y visualiza la cuadrícula de imágenes.
*  Aplica un filtro o buscador por palabra clave, centro de la NASA o fecha.
* Observa la tarjeta abreviada con el título, thumbnail optimizado y etiquetas.
* Despliega "Leer más" o abre el detalle para ver la descripción completa y la versión en alta resolución.

3.3 Información que necesita para decidir:
   Título, thumbnail de baja resolución (~thumb.jpg), fecha de creación, centro de la NASA responsable y palabras clave (tags).

   3.4 Información que sobra:
   Metadatos internos de servidor, rutas de origen de la API y bloques extensos de texto técnico expuestos desde la vista principal.
   
# __4. CONTENIDO Y DATOS__

   4.1 Datos que debe mostrar cada elemento del listado:

| Dato | ¿Imprescindible o adicional? | ¿Lo entrega la API? |
| ---            | ---               | ---                | 
| Título  | Imprescindible | Sí|
| Descripción  | Imprescindible | Sí |
| Fecha | Imprescindible | Sí |
| Centro NASA | Imprescindible | Sí |
| Palabras clave | Imprescindible | Sí |
| Thumbnail | Imprescindible | Sí |

4.2 Criterios de búsqueda y filtrado acordados:
Búsqueda por texto libre (palabras clave/título) e filtrado por centro de investigación de la NASA (ej. JPL, GSFC, MSFC).

4.3 Orden por defecto del listado:
Cronológico descendente (imágenes más recientes primero).

4.4 Qué hacer cuando un dato viene vacío:
• Texto / Centro: Mostrar placeholder "No especificado".
• Keywords: Ocultar el contenedor de etiquetas si el arreglo viene vacío.
• Imagen: Mostrar una imagen de reserva local (fallback) e informar al usuario.

# __5. ALCANCE__

5.1 Funcionalidades acordadas, en orden de prioridad:

| # | Funcionalidad | Prioridad | ¿Entra en la versión 1?|
| ---            | ---               | ---           | --- |
|1 | Búsqueda de imágenes en la API | Alta | Sí |
| 2 | Carga optimizada de imágenes (Thumbnails + Lazy Loading) | Alta | Sí |
| 3 | Truncado de texto ("Leer más" / line-clamp) | Alta | Sí |
| 4 | Filtrado por centro de investigación o palabras clave | Media | Sí |
| 5 | Descarga directa de la imagen en alta resolución (~orig.jpg) | Baja | No |

5.2 Fuera de alcance, acordado explícitamente:
• Registro o autenticación de usuarios.
• Módulo de "Guardar en favoritos" con almacenamiento en base de datos.
• Descarga de archivos de video o audio de la NASA.

# __6. RESTRICCIONES Y REFERENCIAS__

6.1 Referencias que le gustan al cliente y por qué:
APOD (NASA Astronomy Picture of the Day) y galerías tipo Pinterest por su distribución en mosaico fluido y carga progresiva.

6.2 Lo que quiere evitar:
Páginas con scroll infinito sin control de carga, bloques de texto continuo sin formato y tiempos de espera prolongados al abrir la vista principal.

6.3 Restricciones de conexión, dispositivo o accesibilidad:
• Debe ser responsive (adaptado a dispositivos móviles).
• La visualización del listado no debe colapsar en conexiones 3G/lentas.

6.4 Tono y estilo visual esperado:

[X] Sobrio [ ] Cercano [ ] Juvenil [X] Institucional [X] Minimalista [ ] Colorido [ ] Editorial [X] Técnico

# __7. CRITERIOS DE ÉXITO__

7.1 Cómo sabremos que funcionó:
El usuario navega la galería, realiza filtros por centro o fecha y consulta detalles sin notar retardos en la interfaz.

7.2 Indicador medible:
Tiempo de carga inicial de la galería inferior a 2 segundos en redes promedio y 0 interrupciones por imágenes congeladas.

7.3 Qué sería un fracaso:
Que la página descargue archivos de alta resolución directamente en el grid, provocando lentitud y desbordamiento de descripciones extensas.

# __8. CONSECUENCIAS PARA EL DISEÑO__

| Lo que dijo el cliente | Decisión de diseño que tomo | Pantalla o componente |
| ---            | ---               | ---                | 
| "Las fotos tardan mucho en cargar con datos" | Usar links[0].href (~thumb.jpg), loading="lazy" y skeleton loader | Tarjeta de Galería |
| "Hay textos larguísimos que estorban" | Truncar la descripción a 3 líneas con CSS (line-clamp) y botón "Leer más" | Tarjeta de Galería | 
| "Quiero buscar por centro de la NASA" | Incluir un desplegable/filtro por centro (JPL, GSFC, etc.) y barra de búsqueda | Encabezado / Filtros |
| "Casi siempre lo uso desde el celular" | Diseñar la interfaz con arquitectura movil | Todas las pantallas |
