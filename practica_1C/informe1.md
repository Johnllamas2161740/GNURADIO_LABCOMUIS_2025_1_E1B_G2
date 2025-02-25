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

<img src="https://github.com/user-attachments/assets/4ad3d115-dc44-4082-8e41-10f72034a658" alt="USRP 2920" width="300">

1. Rango de frecuencia: 50 MHz a 2.2 GHz.
2. Paso de frecuencia: <1 kHz.
3. Maxima potencia de salida (Pout): 50mW a 100 mW (17 dBm a 20 dBm).
4. Rango de ganancia: 0 a 31 dB.
5. Paso de ganancia: 1.0 dB.

Osciloscopio R&S RTB2004:

<img src="https://github.com/user-attachments/assets/36bab015-f3ee-41de-810a-c45eb8a5e04c" alt="USRP 2920" width="300">

1. Ancho de banda: 70 MHz a 300 MHz.
2. Frecuencia de muestreo: hasta 2.5 Gs/s (gigamuestras por segundo).
3. Profundidad de memoria: hasta 20 megamuestras.
4. Resolución del ADC: 10 bit.
5. Pantalla táctil capacitiva de 10.1”

Analizador de Espectros R&S FPC1000:

<img src=https://github.com/user-attachments/assets/5b431a0c-8743-4aeb-b34c-71f50436dc4f alt="USRP 2920" width="300">


1. Rango de frecuencia: 5 kHz to 1 GHz
2. Ancho de banda de resolución (RBW): desde 1 Hz hasta 3 MHz.
3. Conectividad remota (Wi-Fi y LAN).
4. Tiempo de barrido: 100 µs a 100 s para span = 0 Hz. 20 ms a 1000 s para 10 Hz ≤ span ≤ 600 MHz. (20 ms × span / 600 MHz) a 1000 s para span > 600 MHz
5. Rango de visualización: nivel de ruido mostrado hasta +30 dBm

### Actividad 2: Simulación de Señales en GNU Radio

Al seleccionar Source Type: Float la gráfica de amplitud vs tiempo muestra una señal completamente real, reconocible por ser de color azul, mientras tanto la magnitud del espectro es par con picos en 300 [Hz] y -300 [Hz], lo cual concuerda con lo esperado al seleccionar este tipo de señal y frecuencia.
![image](https://github.com/user-attachments/assets/83601a53-c3f7-48e3-aaba-02836c1e87ab)

complex

![image](https://github.com/user-attachments/assets/712d1eeb-33fb-4a6f-8f0d-09c48f561b67)

square
![image](https://github.com/user-attachments/assets/5baf11d6-ba6e-486b-88c8-cc84a24f2e79)

triangle
![image](https://github.com/user-attachments/assets/e2b69f65-5fd1-48f7-94fe-73c270289c70)

frecuencia y fase
![image](https://github.com/user-attachments/assets/b36c1b47-ea23-4541-858c-30402ebd2dc9)


### Actividad 3: Transmisión y Medición de Señales con el USRP 2920


### Conclusiones
Se sintetizan los principales aportes y puntos relevantes de la práctica, evitando repetir lo ya consignado en las otras secciones del informe. 

### Referencias
Ejemplo de referencia:

- [Proakis, 2014] J. Proakis, M. Salehi. Fundamentals of communication systems. 2 ed. England: Pearson Education Limited, 2014. p. 164-165, 346. Chapter 5 In: [Biblioteca UIS](https://uis.primo.exlibrisgroup.com/permalink/57UIDS_INST/63p0of/cdi_askewsholts_vlebooks_9781292015699)

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
