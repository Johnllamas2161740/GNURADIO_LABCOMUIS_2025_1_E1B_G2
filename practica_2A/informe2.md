# Laboratorio de Comunicaciones
## Universidad Industrial de Santander

---
# Práctica 2A: Modelo de canal

### Integrantes
- **John David Llamas Plata** - 2161740
- **Daniel Ricardo Guerrero Cruz** - 2200535

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
20 de marzo de 2025

---

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Asimismo, los autores asumen plena responsabilidad por la información contenida en este documento. 

Uso de IA: [Indicar si se usó IA y para qué aspectos específicos, por ejemplo: "Se utilizó ChatGPT para reformular secciones del texto y verificar gramática, pero el contenido técnico fue desarrollado íntegramente por los autores."]

---
## Contenido

### Resumen
En este segundo informe se presentan los resultados obtenidos en la segunda práctica del laboratorio de comunicaciones I, que está enfocado en el análisis de modelos de canal y sus efectos en señales transmitidas. Se realizaron simulaciones en GNU Radio y se hizo uso del osciloscopio y analizador de espectro para observar el efecto del ruido, la modulación, el filtro, etc. Además de esto, también está el efecto de atenuación en cables de diferentes longitudes y se evidenciado por la diferencia de potencia entre cada caso.

### Introducción
El estudio de los modelos de canal es fundamental en el análisis y diseño de sistemas de comunicación, ya que permite comprender cómo las señales se ven afectadas por distintos factores durante su transmisión. En esta práctica, se realizaron 4 actividades con un enfoque dirigido a evidenciar todo esto parte por parte. Inicialmente con las simulaciones en GNU Radio para observar el efecto del ruido y el filtrado sobre diferentes tipos de señales. Luego se utilizó el osciloscopio para examinar señales AM y evaluar la influencia de la atenuación y el ruido. También se uso el analizador de espectro para visualizar el impacto del ruido en la respuesta en frecuencia y se visualizo la distorsion por el offset de frecuencia y variación de la frecuencia de portadora, identificando cómo pequeñas variaciones pueden afectar la señal recibida.

### Procedimiento

### Actividad 1. Actividades de simulación de canal en GNU Radio

Se establece mediante prueba y error una frecuencia de muestreo de 25e6/32[Hz] = 78.1250[kHz] en GNU radio buscando que las señales puedan ser visualizadas correctamente sin que el computador se ralentice demasiado. Inicialmente generamos una señal senoidal de frecuencia 8[kHz], amplitud 0.5[V] y ruido de 0.09[V]. El filtro con frecuencias de corte 340[Hz] y 21.050[kHz] elimina el ruido en gran medida.
![image](https://github.com/user-attachments/assets/3ac17e59-2b61-4050-9250-4073f4f6cbf3)

En esta segunda imagen cambiamos la forma de onda por una cuadrada con frecuencia de 3.6[kHz], el filtrado no parece tener un resultado tan bueno como en el caso de la señal senoidal, probablemente se deba a que es más complicado filtrar una señal cuadrada, pues su espectro tiene una serie infinita de armónicos que pueden llegar a verse afectados por el filtro, mientras que la senoidal solo tiene la frecuencia fundamental.
![image](https://github.com/user-attachments/assets/c2b5ec21-ce45-483a-aaa8-6b7b626fb371)

Para esta señal triangular aumentamos el voltaje de ruido a 0.3[V], y notamos que las frecuencias de corte establecidas (340[Hz] y 21.050[kHz]) no son buenas porque el ancho de banda es innecesariamente grande para la frecuencia de la señal establecida en 3.6 [kHz], esto hace que el filtro deje pasar demasiado ruido, y para mejorar los resultados se priorizaría disminuir la frecuencia de corte alta a un valor más bajo, alrededor de 5[kHz].
![image](https://github.com/user-attachments/assets/acd20367-7410-4e68-b063-e943798d8855)

En las siguientes imagenes se muestra el efecto del ruido en el dominio de la frecuencia, se crean varios armonicos alrededor de la frecuencia fundamental.
![image](https://github.com/user-attachments/assets/3d494f87-bfe1-47df-be42-15da60e671b9)
![image](https://github.com/user-attachments/assets/953a1ab8-0f76-4f8c-ac4e-d2808f9e64f6)

Modificar las frecuencias de corte del filtro a 1.97[kHz] y 12.6[kHz] hace que el filtro no contenga la frecuencia de la señal de 1[kHz], esto hace que se elimine por completo. 
![image](https://github.com/user-attachments/assets/f00efeb4-c1f5-4ff9-83e7-c217ef66eafa)

Para esta señal triangular notamos como las frecuencias de corte del filtro no solo eliminan el ruido sino que pueden tener el efecto adverso de deformar la onda al eliminar las componentes de frecuencia esenciales que componen una señal triangular y la convierten en una senoidal.
![image](https://github.com/user-attachments/assets/b7efd8ca-2b91-4e45-8635-de726d55019f)
![image](https://github.com/user-attachments/assets/cc085435-7267-44a1-bbeb-849db7117501)

triangular_3
![image](https://github.com/user-attachments/assets/6f9a15e0-28a0-4c5b-9a74-572f20db5fa2)

triangular_4
![image](https://github.com/user-attachments/assets/1ab01d4a-ddf0-4fd7-bd77-c9cb76ce2570)


### Actividad 2: Fenómenos de canal en el osciloscopio

La señal transmitida es modulada en amplitud, para la frecuencia de portadora de 100[MHz] y la frecuancia de mensaje de 1[kHz] se observa en el osciloscopio que la señal es distinguible por como cambia la amplitud segun su forma mientras que la ondulación es indistinguble debido a la alta frecuencia.
![image](https://github.com/user-attachments/assets/022d888a-a73a-47d8-88a3-212a453b3bb5)

Se evidencia el efecto del ruido en la amplitud de la señal, en general es mucho más notable en el osciloscopio que en la simulación.
![image](https://github.com/user-attachments/assets/344aa7cb-3728-46c9-b8a3-4aeb68d617ec)
![image](https://github.com/user-attachments/assets/431a6291-44f1-472e-89ec-2b9b17c0a8af)

A mayor ruido menor es la diferencia entre la potencia de la señal y el ruido, por lo tanto, sabemos que la relaci+on señal a ruido disminuye para este caso, y seria mejorable aplicando el filtro pasabanda con unas frecuencias de corte adecuadas.

Modificar la frecuencia de portadora no tiene un efecto notable en el osciloscopio debido a que es una señal modulada en amplitud y la visualización en el osciloscopio es de la onda periodica, si la señal fuera FM se observaria como la onda se expande y se comprime. El efecto de usar cables de diferente longitud para la transmision es que entre mayor sea esta mayor es la atenuación, y por lo tanto en el osciloscopio se visualiza una señal de menor amplitud.

### Actividad 3: Fenómenos de canal en el analizador de espectro

El efecto que tiene el ruido en la respuesta en frecuencia de la señal consiste en que aumenta nivel de ruido en el analizador de espectro hasta estar al nivel de los armónicos y que estos ya no puedan ser identificados visualmente.
![image](https://github.com/user-attachments/assets/014aead3-217c-4e96-b8c3-3a8c25f68620)
![image](https://github.com/user-attachments/assets/0dac1060-4ac1-40dd-9f66-8dc291287f9c)

El mismo efecto evidenciado en la simulación de GNU radio
![image](https://github.com/user-attachments/assets/56c21060-30f4-4c3b-bfa3-a36da3c8aefa)
![image](https://github.com/user-attachments/assets/c7fbb41b-72f6-4989-b706-15a4c1f138ce)

Efecto de la desviación de frecuencia en el analizador de espectro.
![image](https://github.com/user-attachments/assets/1345018d-fd63-4306-a9e1-264c4f8503a3)

### Actividad 4:  Efectos de los fenómenos de canal en la conversión de frecuencia

En esta actividad notamos que modificar la frecuencia de portadora de, por ejemplo, 100[MHz] a 100.001[MHz] genera una distorsión y comportamiento inesperado por el desfase entre la señal transmitida y la recibida.
![image](https://github.com/user-attachments/assets/de5c9c88-14e9-4cc7-842d-56584a43fd6e)

Esta distorsión no es fija sino que es dependiente del momento en el cual ocurra el cambio de la frecuencia. Mediante prueba y error puede modificarse el parámetro hasta notar que la señal recibida coincide en gran medida con la transmitida.
![image](https://github.com/user-attachments/assets/69c22cff-42b8-4131-865d-90245b8ab6ef)
![image](https://github.com/user-attachments/assets/ebf89ea3-f750-40b8-8867-6febbf8e0034)
![image](https://github.com/user-attachments/assets/a8b1dfc5-72fb-43e0-93e5-ceffe9ed8e34)
![image](https://github.com/user-attachments/assets/f117fc87-e87e-446e-ba47-86376abbc31a)

Este fenómeno también es visualizable en el dominio de la frecuencia.  También se verifica que modificar el offset de la señal modifica el nivel de portadora, que corresponde a la frecuencia cero.
![image](https://github.com/user-attachments/assets/7393114f-3d93-4b5f-aa39-5bf12db5593b)
![image](https://github.com/user-attachments/assets/d0baff28-9859-4b76-9426-233607c52a5c)

Se midió la potencia para la misma señal utilizando cables de diferente longitud. Los resultados muestran que para el cable más corto la potencia recibida fue de 2.86[dBm] mientras que para el cable más largo fue de -5.52[dBm], la diferencia entre estas indica que existe una atenuacion de aproximadamente 8.38[dB] al usar el cable más largo en comparación al más corto.
![image](https://github.com/user-attachments/assets/ca5ba9d1-937b-40b1-b4e9-5bc9d82ab11b)

![image](https://github.com/user-attachments/assets/c409d702-cd5e-4c5f-98b7-c567f0a5b4e3)


### Conclusiones
En la actividad 1, al introducir voltaje de ruido notamos que este se aplica tanto a la parte real como la imaginaria de la señal, teniendo en cuenta que la parte imaginaria deberia ser un cero constante para una señal real podemos concluir que el ruido no permite que las señales reales sean perfectamente reales, pues siempre habrá una pequeña componente imaginaria que se busca minimizar con el filtro para que pueda ser despreciada.

---

Volver al [INICIO](#laboratorio-de-comunicaciones)
