# Sunscan
<div id='insignias' />
<a target="_blank" href="https://colab.research.google.com/github/EL-BID/Sunscan/blob/main/notebook/SunScan.ipynb">
  
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

***

SunScan es un proyecto que usa código abierto para ayudar a estimar la energía solar potencial sobre tejados usando imágenes satelitales y el modelo SAM (Segment anything by Meta)

<div id='índice' />

## Índice

* [Descripción del proyecto](#descripción-del-proyecto)

* [Guía de instalación](#configuracion-ambiente)

* [Guía de usuario](#demostracion-del-proyecto)

* [Licencia](#licencia)

* [Limitación de responsabilidades](#limitación-de-responsabilidades)

***
<div id='descripción-del-proyecto' />

## Descripción del Proyecto

SunScan es una herramienta diseñada para utilizar el modelo SAM (Segment Anything by Meta) con el propósito de detectar y segmentar tejados en imágenes satelitales. El enfoque principal es proporcionar una solución eficiente para la identificación automática de áreas de tejados, permitiendo así la estimación de la energía potencial disponible para la instalación de sistemas solares. Este proyecto aborda los desafíos asociados con la detección precisa de tejados en datos satelitales, mejorando la planificación y la implementación de proyectos de energía renovable.

### ***1 : Identificación y segmentación de los tejados***

Este paso implica el uso del modelo SAM (Segment Anything by Meta) para identificar y segmentar las áreas que corresponden a los tejados en una imagen satelital. El modelo se entrena para reconocer patrones y características que representan tejados, y luego aplica este conocimiento para segmentar las áreas relevantes en la imagen. A continuación se dar una corta descripción de cómo funciona SAM:

***Arquitectura y Aprendizaje Profundo:*** SAM incorpora una arquitectura de red neuronal profunda, generalmente basada en modelos convolucionales (CNNs) que son efectivos para el análisis de imágenes. Estas redes se entrenan para reconocer y segmentar patrones complejos en los datos visuales. La arquitectura de SAM está diseñada para ser adaptable, permitiendo que se ajuste a diferentes tipos de datos y tareas de segmentación. Utiliza capas convolucionales para extraer características de bajo nivel (como bordes y texturas) y capas más profundas para entender características de alto nivel (como formas y objetos específicos). Este enfoque jerárquico permite al modelo aprender una representación rica y detallada de los datos de entrada.

***Proceso de Segmentación y Meta-Aprendizaje:*** Lo que distingue a SAM es su capacidad para realizar meta-aprendizaje, es decir, aprender a aprender. En lugar de simplemente entrenarse en un conjunto fijo de imágenes, SAM utiliza técnicas de meta-aprendizaje para adaptarse rápidamente a nuevos tipos de datos o tareas de segmentación con una mínima cantidad de ejemplos de entrenamiento. Esto se logra a través de un proceso iterativo donde el modelo ajusta sus parámetros internos no solo para realizar bien en un conjunto de datos específico, sino también para ser capaz de transferir ese aprendizaje a nuevas tareas de manera eficiente. En la práctica, esto significa que SAM puede ser entrenado en un conjunto de imágenes y luego rápidamente ajustado para segmentar con precisión en un conjunto de datos completamente diferente.

***Aplicaciones y Optimización:*** En la segmentación de imágenes, como en el caso de los tejados en imágenes satelitales, SAM puede distinguir con precisión estas estructuras de otros elementos en la imagen. Esto se logra a través de la segmentación semántica, donde cada píxel de la imagen se clasifica en categorías relevantes (por ejemplo, tejado, suelo, vegetación). Para optimizar su rendimiento, SAM puede ser equipado con técnicas adicionales como la ampliación de datos (data augmentation), el aprendizaje de transferencia y la regularización, lo que mejora su capacidad de generalización y reduce el sobreajuste. Esta flexibilidad y adaptabilidad hacen de SAM una herramienta poderosa para aplicaciones que requieren una segmentación precisa y detallada en diversos dominios, desde el análisis de imágenes médicas hasta la vigilancia por satélite.



### ***2 : Área disponible***

Una vez que se han identificado y segmentado los tejados, se calcula el área disponible para la instalación de paneles solares. Este cálculo implica medir el área total de cada tejado segmentado. Dependiendo de la geometría del tejado, este proceso puede variar, pero comúnmente se utiliza la superficie plana proyectada del tejado.

### ***3 : Horas de sol***

Para estimar la energía potencial de cada tejado, es crucial conocer las horas de sol anuales en la ubicación específica de los tejados. Este dato se obtiene utilizando información climática y geográfica de la ubicación. Puedes integrar servicios o bases de datos de información climática para obtener este dato.

### ***4 : Enérgia solar por tejado***

Con el área disponible para paneles solares y las horas de sol anuales, se puede calcular la energía potencial de cada tejado. La fórmula general es:

Energía Potencial=Area Disponible×Horas de Sol Anuales×Rendimiento del Panel Solar×Eficiencia del Sistema

Esta fórmula tiene en cuenta factores como la eficiencia del panel solar y del sistema de conversión de energía.

### ***5 : Exportar los Resultados***

Para facilitar la visualización y análisis geoespacial, los resultados pueden ser exportados como un Shapefile. Un Shapefile es un formato de archivo comúnmente utilizado en SIG (Sistemas de Información Geográfica) que almacena información geoespacial. Puedes exportar los límites de los tejados y su información asociada a un Shapefile utilizando herramientas y bibliotecas como Geopandas.


## Guía de instalación

Instalación
Clonar el Repositorio
```bat
git clone https://github.com/tuusuario/SolarSatelliteAnalyzer.git
cd SolarSatelliteAnalyzer
```

Instalación de Dependencias:
```bat
pip install -r requirements.txt
```

El proyecto contiene la siguiente estructura de carpetas:
~~~
Sunscan:
    |--- notebook
    |--- scripts :
    |        |--- Processing
    |        |--- Estimation
~~~

- notebook : contiene el notebook de ejecución en google colab
- scripts : contiene las funciones de python que dan soporte al proyecto.

Para ejecutar el notebook se pueden seguir los pasos que están ahí mismo descritas.

## Licencia 

~~~
El siguiente proyecto ha sido financiado por el BID. Ver la siguiente licencia [LICENCIA](https://github.com/EL-BID/Plantilla-de-repositorio/blob/master/LICENSE.md)

Este proyecto utiliza el modelo "Segment Anything by Meta" (SAM), desarrollado por Meta. SAM se distribuye bajo la licencia Apache 2.0 license, y se puede encontrar más información en https://github.com/facebookresearch/segment-anything.

@article{kirillov2023segany,
  title={Segment Anything},
  author={Kirillov, Alexander and Mintun, Eric and Ravi, Nikhila and Mao, Hanzi and Rolland, Chloe and Gustafson, Laura and Xiao, Tete and Whitehead, Spencer and Berg, Alexander C. and Lo, Wan-Yen and Doll{\'a}r, Piotr and Girshick, Ross},
  journal={arXiv:2304.02643},
  year={2023}
}
~~~



***

<div id='limitación-de-responsabilidades' />

