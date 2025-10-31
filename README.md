# Evidencia_TC1001S
Evidencia para la semana tec TC1001S, recibe imagenes con texto (en espanol) y los convierte a un archivo docx, los traduce y/o los convierte en audio dependiendo de la eleccion del usuario
Con este código se busca obtener texto a partir de fotos tomadas para poder generar documentos de tipo docx y así editarlos a gusto del usuario.
Como extra se agregaron otras funciones para traducir el texto y convertirlo a audio. 

# Librerias: 
- Cv2:  para el procesamiento de imágenes
- pytesseract: detección y extracción de texto de las imágenes
- Googletrans: traduce el texto 
- Gtts: convierte texto a voz (Google text to speech)
- Docx: crea y modifica archivos de Word
- Os: modificar e interactuar con archivos y rutas del sistema
# Funciones:
- Text_extraction: recibe la ruta de la imagen y carga la imagen con ayuda de la librería cv2, convierte la imagen en escala de grises para separar el texto del fondo y encuentra el umbral óptimo automáticamente además de que se configura tesseract para que trabaje con el idioma en espanol.
  - thresh = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)[1]: TRESH_BINARY especifica el tipo de umbralización que se aplicará, TRESH_OTSU utiliza el algoritmo de Otsu, el cual es bastante útil cuando la imagen posee dos picos en su histograma
  - Se configura tesseract para utilizar idioma espanol (-l spa) especificando el modo de motor OCR con segmentación de página (--oem 3 –psm 6)
- Sanitize_for_xml: recibe el texto extraído y lo limpia haciéndolo válido para XML borrando caracteres de control y permitiendo caracteres especiales
- Translate_text: recibe el texto a traducir y su idioma destino
- text_to_speech : recibe el texto a convertir, el lenguaje del mismo y lo convierte en audio
- Export_docx: recibe el texto a guardar, un encabezado y el nombre del archivo además de llamar la función sanitize_for_xml para limpiar el texto y agregarlo al documento

