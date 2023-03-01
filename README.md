# Robot-Cartesiano-3GDL

Dana Marian Rivera Oropeza - A00830027
Daniela Berenice Hernández de Vicente - A01735346
Alejandro Armenta Arellano - A01734879	

Se declaran las variables simbólicas, por el tipo de robot, no se usan los ángulos, solo se considera el largo de cada articulación, y en la configuración se pone 1 porque el tipo de movimiento es prismático

``` matlab
RP=[1 1 1];
```

Se hacen los cambios en las articulaciones, para que cuadren según las posiciones, alineando el eje de Z primero y después el eje en X, a partir de esas rotaciones es que se obtiene la matriz de rotación, la matriz de posición es indiferente en este caso por el tipo de robot que estamos modelando, entonces es indistinta la posición en el vector

``` matlab 
P(:,:,1)=[l1;0;0];

R(:,:,1)=[0 0 -1;
          0 1 0;
          1 0 0];
```

Sin embargo en la última articulación no se realiza la rotación ya que el movimiento es lineal, solo tiene un movimiento hacia adelante y atrás por lo que solo se usa la matriz identidad ya que no se afecta por las posiciones del plano rotacional como en las articulaciones anteriores donde se debe considerar la posición de los planos.

Finalmente como en los códigos pasados generamos las matrices de transformación y los algoritmos para obtener las velocidades en cada una de las articulaciones, esto a partir de los cálculos para la amtriz jacobiana, dentro de este algoritmo se calcula la velocidad para las articulaciones prismáticas y rotacionales, se hacen las derivadas parciales para el plano X, Y y Z y se obtienen las velocidades

Finalmente el código nos regresa estas matrices como resultado, dando la velocidad lineal y angular:

![image](https://user-images.githubusercontent.com/100874942/222006795-ed839197-3c41-417c-a63d-32f851a5c53f.png)
