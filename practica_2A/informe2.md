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
A continuación se presentará en el siguiente informe de laboratorio la segunda práctica del semestre en el cual

### Introducción
En

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

triangular
![image](https://github.com/user-attachments/assets/022d888a-a73a-47d8-88a3-212a453b3bb5)

senoidal
![image](https://github.com/user-attachments/assets/344aa7cb-3728-46c9-b8a3-4aeb68d617ec)

senoidal con ruido
![image](https://github.com/user-attachments/assets/431a6291-44f1-472e-89ec-2b9b17c0a8af)


### Actividad 3: Fenómenos de canal en el analizador de espectro

captura?
![image](https://github.com/user-attachments/assets/832fdd2a-7af4-4cff-8a6b-84f8f6021b88)

triangularact2
![image](https://github.com/user-attachments/assets/56c21060-30f4-4c3b-bfa3-a36da3c8aefa)

triangularact2_2
![image](https://github.com/user-attachments/assets/c7fbb41b-72f6-4989-b706-15a4c1f138ce)



### Actividad 4:  Efectos de los fenómenos de canal en la conversión de frecuencia

visualizar_g_compleja

![image](https://github.com/user-attachments/assets/24049f1d-b9c0-4c47-a020-093f2cb4b06d)

carrier_daña_señal
![image](https://github.com/user-attachments/assets/de5c9c88-14e9-4cc7-842d-56584a43fd6e)

freq_offset1
![image](https://github.com/user-attachments/assets/69c22cff-42b8-4131-865d-90245b8ab6ef)

freq_offset2
![image](https://github.com/user-attachments/assets/ebf89ea3-f750-40b8-8867-6febbf8e0034)

freq_offset3
![image](https://github.com/user-attachments/assets/a8b1dfc5-72fb-43e0-93e5-ceffe9ed8e34)

freque_offset4
![image](https://github.com/user-attachments/assets/f117fc87-e87e-446e-ba47-86376abbc31a)

freq_offset5_espectro
![image](https://github.com/user-attachments/assets/7393114f-3d93-4b5f-aa39-5bf12db5593b)

observacion_ganancia
![image](https://github.com/user-attachments/assets/d0baff28-9859-4b76-9426-233607c52a5c)


### Conclusiones
En la actividad 1, al introducir voltaje de ruido notamos que este se aplica tanto a la parte real como la imaginaria de la señal, teniendo en cuenta que la parte imaginaria deberia ser un cero constante para una señal real podemos concluir que el ruido no permite que las señales reales sean perfectamente reales, pues siempre habrá una pequeña componente imaginaria que se busca minimizar con el filtro para que pueda ser despreciada.
### Referencias (#####################)

- [Rohde & Schwarz, 2017] Rohde & Schwarz, *R&S RTB2000 Digital Oscilloscope: User Manual*, Rohde & Schwarz, 2017
- [Rohde & Schwarz, 2017] Rohde & Schwarz, *R&S®FPC1000 Spectrum Analyzer: User Manual*, Rohde & Schwarz GmbH & Co. KG, 2017.
- [NI, 2025] National Instruments, *USRP-2920 Specifications*, National Instruments, Feb. 2025.

---

Volver al [INICIO](#laboratorio-de-comunicaciones)
