# Visión por Computadora II

Este repositorio contiene el trabajo final de la asignatura de Visión por Computadora II de la Carrera de Especialización en Inteligencia Artificial (CEIA) de la Universidad de Buenos Aires, titulado "Segmentación semántica y segmentación de instancias de órganos del tracto gastrointestinal".

## Descripción del problema
En 2019, se estima que 5 millones de personas fueron diagnosticadas con cáncer del tracto gastrointestinal en todo el mundo. De estos pacientes, aproximadamente la mitad son elegibles para la radioterapia, que generalmente se administra durante 10 a 15 minutos al día durante 1 a 6 semanas. Los oncólogos radioterápicos intentan administrar altas dosis de radiación utilizando haces de rayos X que apuntan a los tumores y evitan el estómago y los intestinos. Con tecnología más nueva, como imágenes de resonancia magnética integrada y sistemas de aceleración lineal, también conocidos como MR-Linacs, los oncólogos pueden visualizar la posición diaria del tumor y los intestinos, que puede variar día a día. En estas exploraciones, los oncólogos radiólogos deben delinear manualmente la posición del estómago y los intestinos para ajustar la dirección de los haces de rayos X para aumentar la administración de la dosis al tumor y evitar el estómago y los intestinos. Este es un proceso laborioso y lento que puede prolongar los tratamientos de 15 minutos al día a una hora al día, lo que puede ser difícil de tolerar para los pacientes, a menos que el aprendizaje profundo pueda ayudar a automatizar el proceso de segmentación. Un método para segmentar el estómago y los intestinos haría que los tratamientos fueran mucho más rápidos y permitiría que más pacientes recibieran un tratamiento más efectivo.

<p align="center">
  <img width="350" alt="qaBot" src="https://github.com/tmonreal/Computer_Vision_2/assets/84754265/cace82ef-e099-4bc1-92bd-8113df93a872">
</p>

*En esta figura, el tumor (línea rosada gruesa) está cerca del estómago (línea roja gruesa). Se dirigen altas dosis de radiación al tumor evitando el estómago. Los niveles de dosis están representados por el arcoíris de contornos, con las dosis más altas representadas por el rojo y las dosis más bajas representadas por el verde.*

## Dataset
El dataset empleado fue tomado de la competencia de Kaggle [UW-Madison GI Tract Image Segmentation](https://www.kaggle.com/competitions/uw-madison-gi-tract-image-segmentation/data).
Las anotaciones de entrenamiento se proporcionan como máscaras codificadas con RLE y las imágenes están en formato PNG en escala de grises de 16 bits.
El conjunto de datos se encuentra dividido por casos (diferentes pacientes) y días de muestra. En general, se tienen 140 slices por día.

## Modelos entrenados

### MASK R-CNN

<p align="center">
  <img width="500" alt="qaBot" src="https://github.com/tmonreal/Computer_Vision_2/assets/84754265/13d4abe7-6fdc-4f7a-becb-cdc2d73147bb">
</p>

- [Modelo clásico.](https://github.com/tmonreal/Computer_Vision_2/blob/main/%C3%93rganos_Mask_r_cnn.ipynb)
- [Modelo con backbone actualizado y aumento de datos.](https://github.com/tmonreal/Computer_Vision_2/blob/main/%C3%93rganos_Aumento_de_datos_Mask_r_cnn.ipynb)

### U-Net

<p align="center">
  <img width="500" alt="qaBot" src="https://github.com/tmonreal/Computer_Vision_2/assets/84754265/55919018-9478-4dd4-a799-4fa7e33b26ca">
</p>

- [Modelo clásico usando PyTorch.](https://github.com/tmonreal/Computer_Vision_2/blob/main/UNet.ipynb)
- [Modelo con backbone pre-entrenado usando `Segmentation Models`.](https://github.com/tmonreal/Computer_Vision_2/blob/main/UNet_pretrained.ipynb)

## Resultados y Conclusiones
- Se logró realizar la tarea de segmentación con diferentes grados de éxito.
- En cuanto a MASK R-CNN, el transfer learning permitió reducir el tiempo de entrenamiento en gran medida. Además, el aumento de datos permite extender el entrenamiento durante más epochs antes de alcanzar un sobre entrenamiento.

![image](https://github.com/tmonreal/Computer_Vision_2/assets/84754265/22a909ec-ea77-46fe-983a-8488809f4fe5)

- En cuanto a la U-Net, el transfer learning no aportó mejoras significativas en el tiempo de entrenamiento ni en las métricas.

![image](https://github.com/tmonreal/Computer_Vision_2/assets/84754265/c2599494-7496-4243-8ab3-338271825101)

- Se concluye que ambos modelos pueden mejorar si se realiza un entrenamiento durante un tiempo más prolongado.






