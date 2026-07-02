# Clasificador de Objetos Escolares con Teachable Machine

# Integrantes del grupo:

- Daniel Sierra
- Alejandro Camacho
- Jonathan Luna

## Descripción del Problema

Este proyecto busca automatizar el reconocimiento de objetos escolares (Mouse, Botella, Celular, Cuaderno) mediante visión por computadora usando una webcam, para ayudar a tareas como organización de escritorios, inventario visual o accesibilidad. Se escogieron estas cuatro clases porque tienen formas, colores y texturas distintas entre sí, lo que facilita que la red neuronal las diferencie, aunque Mouse y Celular comparten algunas características (superficie oscura y brillante) que permiten analizar después dónde el modelo tiene más dificultad.

---

## Clases Utilizadas

- Mouse
- Botella
- Celular
- Cuaderno

---

## Dataset Utilizado

Las imágenes se capturaron con webcam directamente en Teachable Machine, variando posición del objeto, distancia a la cámara, iluminación, fondo y forma de sostener el objeto. Esta variedad es clave porque una red neuronal no memoriza "el objeto" como tal, sino los patrones de píxeles que ha visto durante el entrenamiento; entre más variados sean los ejemplos, mejor generaliza el modelo ante situaciones nuevas.

Dataset completo: [Muestras-TeachableMachine](https://drive.google.com/drive/folders/1FISQ6j8ugypUCnap2dTUTlK9rIJUjjel?usp=drive_link)

---

## Cantidad de Imágenes por Clase

| Clase     | Cantidad de imágenes |
|-----------|----------------------|
| Mouse     | 63                   |
| Botella   | 89                   |
| Celular   | 73                   |
| Cuaderno  | 93                   |

---

## Explicación Técnica

La IA no ve objetos como los vemos nosotros. Cada imagen de la webcam se descompone en píxeles, y cada píxel se representa con valores numéricos de color (RGB, de 0 a 255). Esos números pasan por la red neuronal en un proceso llamado Forward Pass: la información atraviesa las capas de la red, donde se hacen operaciones matemáticas usando los pesos neuronales (valores ajustados durante el entrenamiento). Las primeras capas detectan patrones simples (bordes, contornos); las capas más profundas combinan esos patrones en formas y texturas más complejas. Al final, la red no dice "esto ES un mouse": calcula, para cada clase, una probabilidad (clasificación) según qué tanto se parecen los patrones numéricos actuales a los que vio en el entrenamiento (reconocimiento de patrones). Por eso la vista previa muestra porcentajes en vez de un sí o no. En resumen, la red asocia píxeles, colores y formas con una etiqueta mediante relaciones matemáticas, no entiende qué es el objeto.

---

## Casos Donde el Modelo Funciona Correctamente

En las pruebas realizadas con la webcam en vivo, el modelo clasificó correctamente y con alta confianza cada uno de los cuatro objetos: Botella (100%), Celular (99%), Mouse (100%) y Cuaderno (100%).

![Predicción Botella] (capturas/botella.jpeg)

![Predicción Celular] (capturas/celular.jpeg)

![Predicción Mouse] (capturas/mouse.jpeg)

![Predicción Cuaderno] (capturas/cuaderno.jpeg)

Esto indica que, para condiciones similares a las del dataset de entrenamiento (mismo fondo, iluminación parecida, forma similar de sostener el objeto), el modelo generaliza bien y distingue claramente las cuatro clases entre sí.

---

## Casos Donde el Modelo Falla

En las pruebas realizadas no se presentaron fallos: el modelo acertó con alta confianza en las cuatro clases probadas. Aun así, es de esperarse que dude o falle ante cambios drásticos de iluminación, fondos nuevos no vistos en el entrenamiento, objetos parcialmente tapados, o confusión entre Mouse y Celular por ser ambos oscuros y de tamaño similar. Estos posibles fallos se explican por: calidad del dataset (imágenes repetidas en el mismo contexto), ruido visual (sombras o fondos variables), datos insuficientes o desbalanceados entre clases, similitud entre clases parecidas, y sobreajuste (el modelo memoriza detalles específicos del entrenamiento en vez de generalizar).

---

## Reflexión Crítica

### ¿La IA realmente entiende lo que ve?

No. La IA no tiene conciencia de qué es un mouse, una botella, un celular o un cuaderno, ni sabe para qué sirven. Lo que hace es un proceso matemático y estadístico: convierte la imagen en números, los pasa por la red (Forward Pass) usando pesos aprendidos en el entrenamiento, y calcula qué tan probable es que esos patrones correspondan a cada clase enseñada. Reconoce patrones estadísticos en píxeles, no objetos; por eso puede acertar con 100% de confianza en condiciones similares a su entrenamiento, y fallar completamente ante algo nuevo que un humano identificaría sin problema. No hay comprensión real, solo reconocimiento de patrones basado en probabilidades.
