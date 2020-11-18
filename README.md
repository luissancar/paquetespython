

# Módulos, paquetes y paquetes redistribuibles en Python.

## Módulos.

Un _módulo_ es un archivo de Python cuyos objetos (funciones, clases, etc.) pueden ser accedidos desde otro archivo. Se trata simplemente de una forma de organizar grandes códigos.

Creamos dentro de una carpeta un fichero llamado operaciones.py
```
def sumar(a, b):
return a + b

def restar(a, b):
return a - b

def mult(a, b):
return a \* b

def div(a, b):
return a / b
```
Otro llamado principal.py
```
import operaciones

print(operaciones.sumar(4,5))
```
Podemos llamar a todas las funciones del fichero operaciones.

Si el archivo operaciones.py contiene muchas funciones, clases, etc, y sólo queremos utilizar unas pocas (utilizando menos memoria RAM).
```
from operaciones import sumar

print(sumar(4,5))
```
En este caso no es necesario utilizar el nombre del módulo delante del nombre de la función, en el caso de querer utilizar todas las funciones, podemos utilizar.
```
from operaciones import *

print(restar(4,5))
print(sumar(4,5))
```
Paquetes.

Los paquetes pueden contener módulos y otros paquetes. Son directorios. El único requisito es que contengan un archivo llamado \_\_init\_\_.py.

Creamos un directorio llamado paquete\_operaciones. En el interior debemos crear un archivo vacio llamado \_\_init\_\_.py.

Crearemos un fichero llamado operacionesbasicas.py
```
def sumar(a, b):
return a + b

def restar(a, b):
return a - b
```
Y otro llamado operacionestrigonometricas.py
```
import math

def seno(i):
return math.sin(math.pi/i)

def coseno(i):
return math.cos(math.pi/i
```
Creamos un archivo Python en la raíz del proyecto.
```
from paquete\_operaciones import operacionestrigonometricas

print(operacionestrigonometricas.seno(6))
```
O
```
from paquete\_operaciones.operacionestrigonometricas import seno

print(seno(6))
```
Este llamaría a las funciones del paquete operacionestrigonometricas, podría crear subpaquetes, paquetes dentro de un paquete.

Paquetes distribuibles.

Un paquete distribuible se puede utilizar desde cualquier proyecto Python sin la necesidad de que el paquete esté en la carpeta del proyecto. En la raíz del proyecto creamos un fichero llamado setup.py.

Desde consola nos tenemos que posicionar en el directorio del proyecto, y tecleamos:
```
python setup.py sdist
```
Se habrá creado una nueva carpeta llamada dist, y en ella encontraremos un fichero comprimido. Este fichero es nuestro distribuible y ahora podríamos compartirlo con todo el mundo para que puedan instalar nuestro paquete.

Para instalarlo en nuestro ordenador o en otro ordenador, nos posicionamos en la carpeta dist, escribimos el siguiente comando:
```
pip3 install paqueteoperaciones-1.0.tar.gz
```
El paquete está instalado y se puede utilizar desde cualquier carpeta de nuestro sistema.
