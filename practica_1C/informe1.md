# Laboratorio de Comunicaciones
## Universidad Industrial de Santander

---
# Práctica 1: Mediciones de potencia y frecuencia

### Integrantes
- **John David Llamas Plata** - 2161740
- **Daniel Ricardo Guerrero Cruz** - 2200535

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
19 de febrero de 2025

---

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Asimismo, los autores asumen plena responsabilidad por la información contenida en este documento. 

Uso de IA: [Indicar si se usó IA y para qué aspectos específicos, por ejemplo: "Se utilizó ChatGPT para reformular secciones del texto y verificar gramática, pero el contenido técnico fue desarrollado íntegramente por los autores."]

---
## Contenido

### Resumen
Descripción en no más de 150 palabras del contenido de la práctica. Debe ser conciso y brindar una idea clara sobre el trabajo realizado y sus conclusiones.

**Palabras clave:** de 2 a 5 palabras clave. 

### Introducción
Cada práctica contará con preguntas orientadoras para la elaboración de la introducción. Por ejemplo: 
- ¿Qué tan importante es la teoría de muestreo en el procesamiento de señales?
- ¿Cuáles son los principales potenciales de GNURADIO en el laboratorio de comunicaciones?
- ¿Qué pasa cuando se alcanza el límite de Nyquist?
- ¿Qué tan alta debe ser la relación entre la frecuencia de muestreo y la frecuencia de la señal para visualizar la señal correctamente?
- ¿Cuándo es importante interpolar una señal?
- ¿Cuándo es importante diezmar una señal?
- ¿Qué pasa cuando se asigna una frecuencia de muestreo inadecuada?

### Procedimiento

### Actividad 1. Revisión de Especificaciones de los Equipos
USRP 2920:
1. Rango de frecuencia: 50 MHz a 2.2 GHz.
2. Paso de frecuencia: <1 kHz.
3. Maxima potencia de salida (Pout): 50mW a 100 mW (17 dBm a 20 dBm).
4. Rango de ganancia: 0 a 31 dB
5. Paso de ganancia: 1.0 dB

Osciloscopio R&S RTB2004:
1. 4 canales analógicos cn ancho de banda de 300 MHz.
2. Rango de voltaje: +-5V a +- 50V (con atenuación de la sonda)
3. Tasa de muestreo: Máximo 5 GSa/s en 2 canales activos. 2.5 GSa/s (con los 4 canales analógicos activos).
4. 
5. 

Analizador de Espectros R&S FPC1000:
1. 
2. 
3. 
4. 
5. 
###Actividad 2: Simulación de Señales en GNU Radio

###Actividad 3: Transmisión y Medición de Señales con el USRP 2920


### Conclusiones
Se sintetizan los principales aportes y puntos relevantes de la práctica, evitando repetir lo ya consignado en las otras secciones del informe. 

### Referencias
Ejemplo de referencia:

- [Proakis, 2014] J. Proakis, M. Salehi. Fundamentals of communication systems. 2 ed. England: Pearson Education Limited, 2014. p. 164-165, 346. Chapter 5 In: [Biblioteca UIS](https://uis.primo.exlibrisgroup.com/permalink/57UIDS_INST/63p0of/cdi_askewsholts_vlebooks_9781292015699)

---
# Ejemplos usando Markdown

Volver al [INICIO](#laboratorio-de-comunicaciones)

## Inclusión de Imágenes
### Imagen de referencia dentro del repositorio:
![Networking](my%20file/test.png)

### Imagen de fuente externa
![GNU Radio logo](https://kb.ettus.com/images/thumb/5/50/gnuradio.png/600px-gnuradio.png)

### Uso de html para cambiar escala de la imagen
<img src="https://kb.ettus.com/images/thumb/5/50/gnuradio.png/600px-gnuradio.png" alt="GNU Radio Logo" width="300">

## Creación de hipevínculos 
- [Aprende Markdown](https://markdown.es/)
- [Más acerca de Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [Abrir documento en el repositorio](my%20file/test_file.txt). Si hay espacios en la ruta de su archivo, reemplácelos por `%20`.
- Ir a una sección de este documento. Por ejemplo: [Ir a Contenido](#contenido) Tenga en cuenta escribir el título de la sección en minúsculas y los espacios reemplazarlos por guiones.
## Uso de Expresiones Matemáticas
Se pueden incluir ecuaciones en el archivo `README.md` utilizando sintaxis similar a [LaTeX](https://manualdelatex.com/tutoriales/ecuaciones):

### Ecuaciones en Línea
```
La energía de una señal exponencial es $E = \int_0^\infty A^2 e^{-2t/\tau} dt$.
```
**Salida renderizada:**
La energía de una señal exponencial es $E = \int_0^\infty A^2 e^{-2t/\tau} dt$.

### Ecuaciones en Bloque
```
$$E = \int_0^\infty A^2 e^{-2t/\tau} dt = \frac{A^2 \tau}{2}$$
```
**Salida renderizada**
$$E = \int_0^\infty A^2 e^{-2t/\tau} dt = \frac{A^2 \tau}{2}$$

## Creación de Tablas

**Tabla 1.** Ejemplo de tabla en Markdown.

| Parámetro | Valor |
|-----------|-------|
| Frecuencia (Hz) | 1000 |
| Amplitud (V) | 5 |
| Ciclo útil (%) | 50 |

## Inclusión de código

```python
def hello_world():
    print("Hello, World!")
```

También es posible resaltar texto tipo código como `print("Hello, World!")`.

---

Volver al [INICIO](#laboratorio-de-comunicaciones)ile
