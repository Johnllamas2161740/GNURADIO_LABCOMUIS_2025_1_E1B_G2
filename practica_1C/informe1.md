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
2 de marzo de 2025

---

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Asimismo, los autores asumen plena responsabilidad por la información contenida en este documento. 

Uso de IA: [Indicar si se usó IA y para qué aspectos específicos, por ejemplo: "Se utilizó ChatGPT para reformular secciones del texto y verificar gramática, pero el contenido técnico fue desarrollado íntegramente por los autores."]

---
## Contenido

### Resumen
A continuación se presentará en el siguiente informe de laboratorio la primera práctica del semestre en el cual nos familiarizaremos con el uso de tres equipos fundamentales, los cuales serán usados en los próximos meses, los cuales son el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000, en los cuales introduciremos sus principales especificaciones y cómo trabjan cada uno de ellos, para después empezar con la práctica simulando señales con diferentes tipos de ondas y amplitudes, en esta parte tendremos que teneer en cuenta ciertos factores como son el ancho de banda y frecuencias centrales entre otros para hacer nuestros respectivos análisis.

### Introducción
En el desarrollo de sistemas de comunicación modernos, la integración de hardware especializado y herramientas de software es esencial para validar conceptos teóricos y optimizar procesos prácticos. Este informe aborda el uso de tres dispositivos clave en un laboratorio de comunicaciones: el USRP 2920 (plataforma de radio definida por software), el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000, cuyo uso combinado permite explorar desde la generación de señales hasta su análisis en los dominios temporal y de frecuencia. A través de su interacción, se evidencian principios fundamentales como la teoría de muestreo, las limitaciones físicas en la adquisición de señales y el papel de herramientas como GNU Radio en la implementación de sistemas flexibles y adaptativos.  

La teoría de muestreo, basda en el teorema de Nyquist-Shannon, es un pilar crítico al trabajar con dispositivos como el USRP 2920. Por ejemplo, al configurar su frecuencia de muestreo, se define la fidelidad con la que una señal analógica es digitalizada. Si se alcanza el límite de Nyquist (muestreo a exactamente el doble del ancho de banda de la señal), se garantiza una reconstrucción teóricamente perfecta. Sin embargo, superar este umbral con una frecuencia de muestreo adecuada evita el aliasing, fenómeno que distorsiona irremediablemente la señal, como podría observarse en el osciloscopio RTB2004 mediante la aparición de componentes espectrales falsas. Por el contrario, una frecuencia de muestreo inadecuada, inferior a la requerida, no solo compromete la integridad de la señal, sino que también genera ambigüedades en su representación digital, un error que el analizador FPC1000 revelaría como superposición de frecuencias en el espectro.  

En este escenario, GNU Radio emerge como un aliado indispensable. Su arquitectura basada en bloques facilita el diseño de flujos de procesamiento de señales personalizados, integrando el USRP 2920 para transmisión/recepción y permitiendo validar resultados con los instrumentos de medición. Sus principales potenciales radican en la capacidad de prototipado rápido, la implementación de esquemas de modulación complejos y la experimentación con técnicas como el filtrado adaptativo o el manejo de señales en tiempo real. Además, GNU Radio permite visualizar en práctica cómo un muestreo incorrecto afecta a las etapas siguientes del sistema, reforzando la importancia de parámetros bien definidos.  

La combinación de estos dispositivos no solo subraya la relación independiente entre teoría y práctica, sino que también expone los riesgos de ignorar restricciones físicas y matemáticas en el procesamiento de señales. Así, este informe busca demostrar cómo un laboratorio equipado con herramientas versátiles y precisas, como las mencionadas, se convierte en un espacio idóneo para explorar los límites de las comunicaciones digitales y validar soluciones innovadoras ante desafíos como el aliasing o la optimización del ancho de banda.

### Procedimiento

### Actividad 1. Revisión de Especificaciones de los Equipos
A continuación se describen algunas especificaciones importantes sobre los equipos utilizado en la práctica.
#### USRP 2920:

<img src="https://github.com/user-attachments/assets/4ad3d115-dc44-4082-8e41-10f72034a658" alt="USRP 2920" width="300">

1. Rango de frecuencia: 50 MHz a 2.2 GHz.
2. Paso de frecuencia: <1 kHz.
3. Maxima potencia de salida (Pout): 50mW a 100 mW (17 dBm a 20 dBm).
4. Rango de ganancia: 0 a 31 dB.
5. Paso de ganancia: 1.0 dB.

#### Osciloscopio R&S RTB2004:

<img src="https://github.com/user-attachments/assets/36bab015-f3ee-41de-810a-c45eb8a5e04c" alt="USRP 2920" width="300">

1. Ancho de banda: 70 MHz a 300 MHz.
2. Frecuencia de muestreo: hasta 2.5 Gs/s (gigamuestras por segundo).
3. Profundidad de memoria: hasta 20 megamuestras.
4. Resolución del ADC: 10 bit.
5. Pantalla táctil capacitiva de 10.1”

#### Analizador de Espectros R&S FPC1000:

<img src=https://github.com/user-attachments/assets/5b431a0c-8743-4aeb-b34c-71f50436dc4f alt="USRP 2920" width="300">


1. Rango de frecuencia: 5 kHz to 1 GHz
2. Ancho de banda de resolución (RBW): desde 1 Hz hasta 3 MHz.
3. Conectividad remota (Wi-Fi y LAN).
4. Tiempo de barrido: 100 µs a 100 s para span = 0 Hz. 20 ms a 1000 s para 10 Hz ≤ span ≤ 600 MHz. (20 ms × span / 600 MHz) a 1000 s para span > 600 MHz
5. Rango de visualización: nivel de ruido mostrado hasta +30 dBm

### Actividad 2: Simulación de Señales en GNU Radio

- Al seleccionar Source Type: Float la gráfica de amplitud vs tiempo muestra una señal completamente real, la cual se visualiza de color azul, mientras tanto la magnitud del espectro es par con picos en 300 [Hz] y -300 [Hz], lo cual concuerda con lo esperado al seleccionar este tipo de señal y frecuencia.
![image](https://github.com/user-attachments/assets/83601a53-c3f7-48e3-aaba-02836c1e87ab)

- Al seleccionar Source Type: Complex la gráfica de amplitud vs tiempo muestra una señal compleja, la parte real es azul y la parte imaginaria es roja, el espectro muestra un solo pico en 300 [Hz].
![image](https://github.com/user-attachments/assets/712d1eeb-33fb-4a6f-8f0d-09c48f561b67)

- Cambiar la forma de la onda a una señal cuadrada modifica notablemente el espectro de la señal, que en caso de ser una señal real muestra multiples impulsos con simetria par, y en caso de ser una señal compleja el espectro es asimetrico.
![image](https://github.com/user-attachments/assets/5baf11d6-ba6e-486b-88c8-cc84a24f2e79)

- La forma de onda triangular muestra un comportamiento similar a la cuadrada en el sentido de que, si bien los espectros son diferentes, se mantiene la idea de que exoste simetria para para la señal real y asimetria para la señal compleja.
![image](https://github.com/user-attachments/assets/e2b69f65-5fd1-48f7-94fe-73c270289c70)


- Modificar la fase no tiene efecto en la grafica del espectro debido a que esta es una gráfica de magnitud, por otro lado, aumentar o disminuir la frecuencia cambia tanto la grafica de amplitud vs tiempo como los armonicos del espectro, se evidencia que los cambios hechos concuerdan con lo esperado en las gráficas.
![image](https://github.com/user-attachments/assets/b36c1b47-ea23-4541-858c-30402ebd2dc9)

- Modificar la amplitud hace que la gráfica del espectro se desplace verticalmente, se evidencia que aumentar o dismunirla tambien aumenta o disminuye la ganancia en [dB] respectivamente.
![image](https://github.com/user-attachments/assets/042b47b7-0edc-44f5-ac68-093a2d52b1d8)
![image](https://github.com/user-attachments/assets/2119bcad-d6cf-4970-a877-e33928d3592c)


- Aumentar el nivel de ruido distorsiona la onda para hacerla tener un comportamiento mas aleatorio e indeseado. Si el ruido es demasiado alto puede llegar al nivel de los armonicos e incluso cubrirlos, obstaculizando el analisis correcto del espectro.
![image](https://github.com/user-attachments/assets/f4e0150c-5aa3-47bb-bca0-91db67345ae5)
![image](https://github.com/user-attachments/assets/d41ad25a-525a-4fb5-9491-e5a872ef646c)



### Actividad 3: Transmisión y Medición de Señales con el USRP 2920

Hubo inconvenientes en la visualizacion de la señal transmitida por cable, especificamente ocurrió un desplazamiento del armonico que debia estar ubicado 100 MHz (portadora) + 1kHz (señal) y paso a estar ubicado en 100.1 MHz, o sea una diferencia de casi 100 kHz, que se mantenia a pesar de modificar la frecuencia en gnu radio.

![Sin título](https://github.com/user-attachments/assets/3477cc11-994b-4b3d-afdc-9f8ae6757e62)

Se observa un piso de ruido de -70 dBm para una RBW de 100 Hz, el piso de ruido normalizado se calcula de la siguiente forma:
![image](https://github.com/user-attachments/assets/5529e773-d326-4522-aea0-678a2b02a75d)

Volviendo al espectro de la señal, aparte de la incoherencia de desplazamiento en la frecuencia también hay armonicos indeseados generados cerca del pico mas alto, y la ganancia del transmisor que por defecto es de 30 dB no parece ser del todo exacta.
![image](https://github.com/user-attachments/assets/7f8ac6e3-3296-4b69-93c4-048c5326e2d2)
![image](https://github.com/user-attachments/assets/91953a48-bca9-4ef6-bef1-d8f992f2b2a2)

Al cambiar la forma de la onda coseno for una onda cuadrada cambia el espectro en gnu radio, en el analizador de espectro se observan los armonicos principales pero también otros indeseados.
![image](https://github.com/user-attachments/assets/ded9ac88-6758-4327-b594-b0b4d14662bc)
![image](https://github.com/user-attachments/assets/ccd5bfc1-0de2-4b0e-b0e9-a1ec7334aee1)




Lo siguiente fue conectar una antena a la entrada del analizador de espectros y observar el espectro de una señal FM (situada entre la 88 MHz y 108 MHz)
![Sin título](https://github.com/user-attachments/assets/ae41d35b-3879-4a53-aba1-e541f653d9ac)
La estacion seleccionada tiene una frecuencia central de 91.7 MHz. Para un span total de 1 MHz dividido en 10 partes se tiene que el span es de 100 kHz/div. Usando el metodo de -20dB para calcular el ancho de banda notamos que la potencia pico se encuentra cercana a -70dBm, al restar -20dBm llegaria a -90dBm, un valor para el cual el espectro alcanza a tomar aproximadamente 2 divisiones del span, y gracias a esto concluimos que el ancho de banda (BW) del espectro es de aproximadamente 200 kHz.
Para calcular la relacion señal a ruido (SNR) se toma la potencia máxima de la señal de -68.57 dBm que es la mostrada en el analizador de espectro en la frecuencia central, y el ruido que es de aproximadamente -95 dBm, se calcula SNR como:

![image](https://github.com/user-attachments/assets/7a0c1efc-0d4b-42ad-930b-7760dd87c94c)

A pesar de los inconvenientes ocurridos en la transmisión por cable se pudo observar correctamente el espectro mediante la antena en la frecuencia escogida. Al sintonizar otras frecuencias notamos picos de frecuencia similares a la escogida inicialmente, con una variacion de aproxinmadamente ±2 dB.

### Conclusiones
El desarrollo de este laboratorio, centrado en el uso del USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000, permitió no solo validar conceptos teóricos clave, sino también enfrentar desafíos prácticos que ayudaron en el aprendizaje. En particular, las complejidades prácticas del analizador de espectros, como la interpretación de componentes espectrales ambiguas o la calibración adecuada para señales de baja amplitud, destacaron la importancia de un enfoque meticuloso en la configuración de instrumentos. Estas dificultades, lejos de ser obstáculos, revelaron cómo factores como el ruido ambiental, la resolución de banda o la selección de span afectan la precisión de las mediciones, reforzando la necesidad de validar resultados con múltiples herramientas (comparando el espectro con la visualización temporal del osciloscopio).  

Aunque la teoría de muestreo, fundamentada en el teorema de Nyquist, se confirmó como esencial para evitar distorsiones como el aliasing, los problemas con el analizador FPC1000 evidenciaron que incluso un muestreo correcto puede verse comprometido si no se consideran interferencias o limitaciones del hardware. Por ejemplo, la aparición de armónicos no deseados en el espectro, inicialmente confundidos con aliasing, exigió un análisis cruzado con el USRP 2920 y GNU Radio para identificar su origen, demostrando así la interdependencia entre generación, captura y análisis de señales.  

La plataforma GNU Radio desempeñó un papel crucial para reducir estas complicaciones. Al permitir simular y ajustar parámetros de muestreo antes de implementarlos en el USRP 2920, se redujeron errores en la práctica y se facilitó la identificación de fallas en el analizador, como saturaciones o escalas de frecuencia mal configuradas. Además, su capacidad para generar señales de referencia ayudó a contrastar y corregir las mediciones obtenidas, subrayando su potencial como herramienta de diagnóstico en entornos complejos.  

En resumen, las dificultades enfrentadas con el analizador de espectros no invalidaron los objetivos del laboratorio, sino que ampliaron la comprensión de las limitaciones prácticas en el procesamiento de señales. Estos retos enfatizaron que, más allá de cumplir con el límite de Nyquist, es muy importante dominar el funcionamiento de los instrumentos y anticipar factores externos que distorsionan los resultados.

### Referencias

- [Rohde & Schwarz, 2017] Rohde & Schwarz, *R&S RTB2000 Digital Oscilloscope: User Manual*, Rohde & Schwarz, 2017
- [Rohde & Schwarz, 2017] Rohde & Schwarz, *R&S®FPC1000 Spectrum Analyzer: User Manual*, Rohde & Schwarz GmbH & Co. KG, 2017.
- [NI, 2025] National Instruments, *USRP-2920 Specifications*, National Instruments, Feb. 2025.

---

Volver al [INICIO](#laboratorio-de-comunicaciones)
