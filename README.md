# Proyecto_Vision_Artificial_YOLO
Proyecto final de Visión Artificial utilizando modelos YOLO
Markdown
# Proyecto Final de Visión Artificial: Detección y Clasificación de Naranjas con YOLOv8

## Integrantes del Equipo
* Héctor Manuel Castañeda Godoy
* Alan Bladimir Almaraz Cortes

---

## Objetivo del Proyecto
Entrenar un modelo de detección de objetos de la familia YOLOv8 para identificar y clasificar el estado de naranjas en 4 categorías distintas: **Comestible, Dañada, Inmadura y Podrida**. Se utilizó un dataset alojado en Roboflow para el entrenamiento y validación del modelo.

## Instrucciones para ejecutar el código

Para reproducir este proyecto y ejecutar el modelo de detección, sigue los siguientes pasos:

1. **Clonar el repositorio:**
```bash
   git clone [PON_AQUI_LA_URL_DE_SU_GITHUB]
   cd [  Proyecto_Vision_Artificial_YOLO ]
Instalar las dependencias:
Asegúrate de tener Python instalado y ejecuta el siguiente comando para instalar las librerías necesarias ubicadas en el archivo requirements.txt:

Bash
   pip install -r requirements.txt
Ejecutar el Notebook:
Abre el archivo principal utilizando Jupyter Notebook o Google Colab:

Bash
   jupyter notebook Proyecto.ipynb
Ejecuta las celdas en orden. Nota: Para la descarga del dataset, es necesario contar con una API Key válida de Roboflow. Las imágenes resultantes de la inferencia se guardarán automáticamente en la carpeta runs/detect/predict.


Caso de Estudio: Integración en un Entorno Industrial
1. Problema a resolver
En las empacadoras de cítricos, la selección y clasificación de la fruta se realiza a menudo de forma manual. Esto es un proceso lento y propenso a errores humanos por fatiga visual, lo que permite que fruta en mal estado llegue al consumidor final. El problema a resolver es automatizar la inspección visual en una línea de producción, clasificando en tiempo real las naranjas en 4 estados (Comestible, Dañada, Inmadura y Podrida) para separar la merma de la fruta apta para venta.


2. Descripción del hardware propuesto
Para implementar este modelo YOLOv8 en una planta empacadora real, proponemos el siguiente hardware:

Cámaras de Visión Industrial: Dos cámaras industriales GigE Vision de alta velocidad, montadas cenitalmente con iluminación LED tipo domo para eliminar sombras y reflejos en la cáscara.

Procesador (Edge Computing): Un equipo de grado industrial como una NVIDIA Jetson Orin Nano o una IPC con GPU, capaz de correr la inferencia de YOLOv8 en milisegundos.

Maquinaria de Transporte: Una banda transportadora de rodillos que haga rotar levemente las naranjas para que las cámaras puedan captar la mayor parte de su superficie.

Control y Actuadores: Un PLC (Controlador Lógico Programable) que reciba los datos del procesador para comandar un sistema de rechazo neumático (brazos deflectores o sopladores de aire).


3. Flujo de funcionamiento
Adquisición: Las naranjas avanzan por la banda transportadora. Un sensor fotoeléctrico detecta su paso y envía un trigger a la cámara para capturar la imagen.

Inferencia con YOLOv8: La imagen pasa a la NVIDIA Jetson, donde el modelo entrenado procesa la imagen y asigna una etiqueta (Comestible, Dañada, Inmadura o Podrida) según las características visuales detectadas.

Comunicación Industrial: Mediante un protocolo como Profinet o Modbus TCP, el script de Python le envía al PLC la clasificación de la naranja en curso.

Acción de Selección:

Si la etiqueta es Comestible, el PLC deja que la naranja continúe hacia el área de empaquetado.

Si la etiqueta es Dañada, Podrida o Inmadura, el PLC calcula el retraso según la velocidad del encoder de la banda y activa el expulsor neumático exacto, desviando la naranja hacia el contenedor de merma correspondiente.
