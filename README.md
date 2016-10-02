# Manual de referencia para el desarrollo de robots de Eurobot

Este trabajo de fin de carrera trata sobre el desarrollo de robots para la competición de robots [Eurobot](http://www.eurobot.org). Pretende ser un manual de referencia para todo aquel que quiera construir un robot para participar en Eurobot. El trabajo está basado en la experiencia adquirida en el desarrollo de este tipo de robots entre entre los años 2003 y 2015. Especialmente en el periodo entre 2010 y 2015.

Eurobot es una competición internacional cuyas reglas y temática el juego cambian cada año. El libro describe la mecánica, hardware y software relativos al desarrollo e implementación de las diferentes funcionalidades de un robot de Eurobot. El desarrollo e implementación de éstas, se han dividido en dos partes principales: la plataforma robótica base y los sistemas mecánicos de manipulación de elementos del juego.

La plataforma robótica se basa en un sistema de tracción diferencial que implementa un posicionamiento por odometría y un control de posición polar. La plataforma, además, utiliza sensores para detectar obstáculos y un sistema de balizas para la medir la posición de los robots oponentes, a partir del cual, se implementa la evitación de obstáculos. Mediante el estudio del modelo dinámico de la plataforma robótica, se determinan los límites de aceleración y velocidad, a partir de los cuales, dimensionar y especificar los elementos mecánicos y estructura de la misma.

El desarrollo hardware implementa una arquitectura que permite ser reutilizada en el desarrollo de nuevos robots de Eurobot. Se trata de un sistema embebido basado en microcontroladores dsPIC, que reparte sus recursos entre la implementación de la plataforma robótica y los sistema mecánicos.

El desarrollo software también está basado en una arquitectura pensada para ser reutilizada. Ésta, se organiza en capas y/o módulos funcionales con diferentes niveles de abstracción. El desarrollo software, incluye además, un simulador de los robots y del campo de juego. El entorno de simulación permite visualizar los movimientos de los robots sobre un campo de juego virtual y simular robots oponentes.

## Atribuciones

[Plantilla LaTeX TFG, TFC, Tesis del Dpto. de Electrónica de la Universidad de Alcalá (UAH)](https://www.depeca.uah.es/depeca/repositorio/otros/book-latex.zip)

## Licencia

![](./docs/licencia/by-sa.png)

All these products are released under [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

Todos estos productos están liberados mediante [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
