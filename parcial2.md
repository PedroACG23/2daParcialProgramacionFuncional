# Universidad de Colima, Facultad de Ingenieria Mecanica y Electrica, Pedro Andrés Castillo Gildo 3B Ingenieria en computacion intelignete
## Archivo de notas realizadas en la segunda parcial de clases en la materia Programacion Funcional
## 2.1 Funciones
### 2.1.1 Introducción a las funciones

* Prácticamente todos los lenguajes de programación actuales permiten una forma de crear funciones definidas por el usuario.
* No siempre se denominan funciones.
* En otros lenguajes pueden llamarse:
  * Subrutinas
  * Procedimientos
  * Métodos
  * Subprogramas

#### 2.1.1.2 Definición y ventajas de su uso

* Una función es una relación o mapeo entre una o más entradas y un conjunto de salidas.
* En matemáticas, una función normalmente se representa como $$ y = f(x)$$
* f es una función que opera sobre la entrada x
* La salida de la función es y

------------------------------

* Las funciones de programación son mucho más generalizadas y versátiles que esta definición matemática.
* En programación, una función es un bloque de código independiente para una tarea específica o un grupo de tareas relacionadas.
* Ejemplos:
  * id()
  * len()
  * max()
  * min()

python
x = 10
id(x)
max(1, 2, 3, 4, 5)


* *Supuesto:*
* Al escribir un código específico útil, conforme se realice el desarrollo, es probable que ese segmento de código se use con frecuencia y se tiene que repetir muchas veces en la aplicación.
* Se podría replicar el código todas las veces que sea necesario (copy & paste)
* Si después es necesario modificar el código en cuestión por:
  * algún problema que deba solucionarse o 
  * necesita mejoras de alguna manera.
  * y hay copias del código esparcidas por toda su aplicación se deberán realizar los cambios necesarios en todos lados.<br><br>
* *Solución:*
* Definir una función de Python que realice la tarea.
* En cualquier lugar de la aplicación donde necesite realizar la tarea, simplemente se llama a la función.
* En el futuro, si decide cambiar cómo funciona, entonces solo se necesita cambiar el código en una ubicación, que es el lugar donde está defina la función.
* Los cambios se realizarán de manera automática en todos los lugares donde sea llamada la función.
----------
* Esto podría decirse que es:
  * Abstracción
  * Reusabilidad
* Sigue el principio del desarrollo de software de no repetirse a sí mismo (DRY: Don't Repeat Yourself)
* Principal motivación para el uso de funciones.
-------
* Las funciones permiten Modularidad
* Ejemplo de código sin modularidad
python
# Programa Principal

# Código para leer un archivo csv
<sentencia 1>
<sentencia 2>
<sentencia 3>

# Código para procesar los datos de un archivo csv
<sentencia 4>
<sentencia 5>
<sentencia 6>

# Código para guardar los nuevos datos en el archivo csv
<sentencia 7>
<sentencia 8>
<sentencia 9>


* Ejempo con código modular:
python

# Función para leer un archivo csv
def read_file():
    <sentencia 1>
    <sentencia 2>
    <sentencia 3>

# Función para procesar los datos de un archivo csv
def process_file():
    <sentencia 4>
    <sentencia 5>
    <sentencia 6>

# Función para guardar los nuevos datos en el archivo csv
def write_file():
    <sentencia 7>
    <sentencia 8>
    <sentencia 9>

# Programa Principal
read_file()
process_file()
write_file()


* Separación de espacios de nombres (Namespace)
* Un espacio de nombres es una región de un programa en la que los identificadores tienen significado.
* Cuando se invoca una función de Python, se crea un nuevo espacio de nombres para esa función, uno que es distinto de todos los demás espacios de nombres que ya existen.
* Las variables se pueden definir y usar dentro de una función de Python incluso si tienen el mismo nombre que las variables definidas en otras funciones o en el programa principal. 
* no habrá confusión ni interferencia porque se mantienen en espacios de nombres separados.
* Cuando escribe código dentro de una función, puede usar nombres e identificadores de variables sin preocuparse de si ya se usan en otros lugares fuera de la función.
* Esto ayuda a minimizar considerablemente los errores en el código.

python
def a():
    x = "Hola"
    print(f"{x}:{id(x)}")

def b():
    x = "Hola"
    print(f"{x}:{id(x)}")

x = "Hola"
a()
b()
print(f"{x}:{id(x)}")


python
def c():
    global x
    x = "Bye"
    print(id(x))

c()
print(id(x))
x = 10
print(id(x))

def d():
    print(x)

d()


python
def e():
    y = "mundo"
    print(id(y))

print(y) #no es lo mismo parametrosn y agrumentos
#una funcion se asigna cuando retorna un valor
#una funcion se invoca cuando no retorna nada****

#### 2.1.1.3 Declaración y llamada de funciones.

* Una función se declaran con la palabra reservada def
* Una función puede recibir parámetros
* Una función puede retornar un valor, varios o ninguno
* Cuando no retorna nada de manera explícita, siempre retorna None
* Una función puede ser recursiva
* Sintaxis general de una función:

 python
def <function_name>([<parameters>]):
    <statement(s)>


Donde:
| Elemento        | Significado                                                                      |
|-----------------|----------------------------------------------------------------------------------|
|def              | Palabra clave para indicar que se está *def*iniendo una función                |
|<function_name>  | Un identificador de Python válido que nombra a la función                        |
|\<parameters>    | Lista opcional separada por comas de parámetros que se pueden pasar a la función |
|:                | Símbolo que indica el final del encabezado o firma de la función de Python       |
|<statement(s)>   | Bloque de sentencias válidas de Python                                           |

* Para llamar a la función:
 python
<function_name>([<arguments>])

* <arguments> son los valores pasados a la función.
* Corresponden a los <parameters> en la definición de la función.
* Se puede definir una función que no acepte ningún argumento, pero los paréntesis aún son necesarios.
* Tanto una definición de función como una llamada a función siempre deben incluir paréntesis, aunque estén vacíos.


python
def mi_funcion():
    msg = "denttro de mi_funcion"
    print(msg)

print("antes de llamar a mi_funcion")
mi_funcion()
print("despues de llamar a mi_funcion")


#### 2.1.1.4 Parámetros y argumentos.

* Sintaxis de una función:

 python
def <function_name>([<parameters>]):
    <statement(s)>


* Llamada de una función:

python
<function_name>([<arguments>])


##### Argumentos posicionales (obligatorios)
* La forma más sencilla de pasar argumentos a una función de Python es con argumentos posicionales u obligatorios.
* En la definición de la función se especifica una lista de parámetros separados por comas dentro del paréntesis:

python
def productos(producto, cantidad, precio):
    print(f" {cantidad} {producto} cuestan {precio} pesos")

productos("manzanas", 5, 7.5)


* Los parámetros (producto, cantidad y precio) se comportan como variables definidas localmente en la función.
* Cuando se llama a la función, los argumentos que se pasan ("manzanas", 5, 7.5) están vinculados a los parámetros en orden
* Como si fuera una asignación de variables:

| Parámetro | Argumento |
|-----------|-----------|
|producto   |manzanas   |
| cantidad  | 5         |
| precio    | 7.5       |

* Los argumentos posicionales son la forma más sencilla de pasar datos a una función
* Ofrecen la menor flexibilidad.
* El orden de los argumentos en la llamada debe coincidir con el orden de los parámetros en la definición. 
* Por supuesto, no hay nada que nos impida cambiar el orden especificado en la definición de la función

python
productos(5, 7.5,"manzanas")


* Si se invoca la función con menos valores:

python
productos("manzanas", 5)

* Si se invoca la función con más valores:
python
productos("manzanas", 5, 7.5, "prod003")


python
productos("manzanas", 5)

python
productos("manzanas", 5, 7.5, "prod003")


##### Argumentos nombrados o de palabra clave (Keyword arguments)

* Cuando se invoca a una función se pueden especificar los argumentos en el formato <palabra_clave>=\<valor>.
* Cada <palabra_clave> debe coincidir con un parámetro en la definición de la función de Python. 
* Por ejemplo, la función productos() se puede invocar con argumentos de palabras clave de la siguiente manera:

python
productos(producto="manzanas", cantidad=5, precio=7.5)


* Ahora sí es posible cambiar el orden de los parametros

python
productos(cantidad=5,producto="manzanas", precio=7.5)

python
productos(precio=7.5, producto="manzanas", cantidad=5 )


* Si una palabra clave no corresponde marca error
* de nueva cuenta todos los parámetros son necesarios

python
productos(precio=7.5, producto="manzanas", cant=5 )

* Los argumentos de palabras clave permiten flexibilidad en el orden en que se especifican los argumentos de una función
* El número de argumentos sigue siendo estricto, deben estar todos.
* Se puede llamar a una función utilizando argumentos posicionales y de palabras clave
* Todos los argumentos posicionales deben ir primero

python
productos("manzanas", cantidad=5, precio=7.5)

python
productos("manzanas", 5, precio=7.5)

python
productos(producto="manzanas", 5, precio=7.5)


python
productos(producto="manzanas", cantidad=5, 7.5)

##### Parámetros por defecto (default)

* Se especifica en una definición de función de Python de la forma <nombre>=\<valor>
* \<valor> se convierte en un valor predeterminado para ese parámetro.
* Se denominan parámetros predeterminados u opcionales. 
* Ejmplo:

python
def productos(producto="productos", cantidad="0", precio=0.0):
    print(f" {cantidad} {producto} cuestan {precio} pesos")

# Invocación sin argumentos
productos()

python
# Invocación con argumentos posicionales
productos("manzanas",5,5.5)

python
# Invocación con argumentos nombrados o de palabra clave
productos(producto="manzanas", cantidad=5, precio=5.5)

python
# Invocación con argumentos posicionales y nombrados o de palabra clave
productos("manzanas", cantidad=5, precio=5.5)

python
# Invocación con argumentos posicionales, nombrados o de palabra clave y opcionales
productos("manzanas", cantidad=5)

#### Valores de parámetros predeterminados mutables

* Ejemplo:

python
def my_function(my_list=[]):
    my_list.append('???')
    return my_list

python
my_function(["a", "b", "c"])


python
my_function([1, 2, 3, 4, 5])

python
#Si se llama sin ningún argumento
print(my_function())
print(my_function())
print(my_function())



python
#Si se llama sin ningún argumento
print(my_function())
print(my_function())
print(my_function())


python
suma()
suma()
suma()

python
x=10
id(x)

python
x=11
id(x)

python
numero=10
id(numero)

python
global num
num = 5
print(id(num))

def a():
    print(num)
    print(id(num))
    num = 10

def b():
    y=num+10
    print(y)

a()
b()

num = 10
print(id(num))

x=5
print('*'*20)

* Es mejor usar un argumento predeterminado que no especifique ningún argumento

python
def f(my_list=None):
    if my_list is None:
        my_list = []
    my_list.append('###')
    return my_list


print(f())
print(f())
print(f())

python
print(f(['a', 'b', 'c']))


print(f([1, 2, 3, 4, 5]))

### 2.1.2 Retorno de Valores y uso de la palabra clave return.
* Una instrucción return en una función de Python tiene dos propósitos:
1. Al terminar la función devuelve el control de ejecución a partir de donde se llamó.
2. Proporciona un mecanismo para regresar datos donde se llamó o asignó.

python
def f1():
    print("Hola")
    print("Mundo")
    return

f1()

python
def f2():
    print("Hola")
    print("Mundo")

f2()

* return no necesita estar al final de una función.
* Pueden aparecer en cualquier parte del cuerpo de una función
* Puede aparecer incluso varias veces
* Ejemplo:


#### 2.1.2.2 Funciones sin valor de retorno (None).

python
def f(x):
    if x < 0:
        return
    if x > 10:
        return
    print(x)

python
f(-3)

python
f(15)

python
f(8)


* Puede usarse para la comprobación de errores

python
def f():
    if error_cond1:
        return
    if error_cond2:
        return
    if error_cond3:
        return

    <normal processing>

* Cuando no se da ningún valor de retorno, una función devuelve el valor especial None

python
def f():
    return


print(f())

* Lo mismo pasa si el cuerpo de la función no contiene alguna declaración

python
def g():
    pass


print(g())

* None es falso cuando se evalúa de manera booleana
python
def f():
    return

def g():
    pass


if f() or g():
    print('yes')
else:
    print('no')

python
def f():
    return True

def g():
    pass


if f() or g():
    print('yes')
else:
    print('no')

* Los enteros en Python son inmutables
* Una función de Python no puede cambiar un argumento entero por efecto secundario
* Ejemplo>

python
def double(x):
    x *= 2


x = 5
double(x)
x

python
def double(x):
    x *= 2

x = 5
x = double(x)
print(x)

*  Hay casos en que es posible modificar un argumento por efecto secundario
*  Usar un valor de retorno puede ser más claro
*  Ejemplo:

python
def double_list(x):
    i = 0
    while i < len(x):
            x[i] *= 2
            i += 1


a = [1, 2, 3, 4, 5]
double_list(a)
a

* Usando return
python
def double_list(x):
    r = []
    for i in x:
            r.append(i * 2)
    return r


a = [1, 2, 3, 4, 5]
a = double_list(a)
a


#### 2.1.2.1 Valor de retorno en funciones.
python
def double(x):
    x *= 2
    return x


x = 5
double(x)
x

python
def double(x):
    x *= 2
    return x

x = 5
x = double(x)
x

python
def f():
    return 'Hola'


s = f()
s
* Una función puede devolver cualquier tipo de objeto.
* Ejemplo: diccionario
python
def f():
    return dict(name_1='Hugo', name_2='Paco', name_3='Luis')


f()

f()['name_1']

* Se puede devolver un fragmento de una cadena
python
def f():
    return 'Hola Mundo'


f()[5:]

* Retornar listas que se pueden indizar o dividir
python
def f():
    return ['a', 'b', 'c', 'd', 'e']


f()
f()[2]
f()[::-1]

* Si se especifican varias expresiones separadas por comas en una instrucción, se empaquetan y se devuelven como una tupla

def f():
    return 'Hugo', 'Paco', 'Luis', 'Donald'


type(f())
names = f()
names

python
a, b, c, d = f()
print(f'a = {a}, b = {b}, c = {c}, d = {d}')


#### 2.1.3.4 Parámetros variables (`args` y `*kwargs`).

* En ocasiones, cuando se está definiendo una función, es posible que no sepa de antemano cuántos argumentos va a tomar.
* Ejemplo: Se desea escribir una función de Python que calcule el promedio de varios valores.

python
#Opción 1
def avg(a, b, c):
    return (a + b + c) / 3

avg(1, 2, 3)


Restricciones:
* el número de argumentos aprobados debe coincidir con el número de parámetros declarados.
* No funciona esta implementación para cualquier cantidad de valores distinta a tres

Si se define la función con parámetros opcionales:
python
def avg(a, b=0, c=0):
    match True:
        case True if b==0 and c==0:
            avg = a
        case True if c==0:
            avg = (a + b)/2
        case _:
            avg = (a + b + c)/3

    return avg

avg(5)
avg(5,4)
avg(5,4,3)

* Se podría enviar una lista como argumento
python
def avg(nums):
    total = 0
    for v in nums:
            total += v
    return total / len(a)


avg([1, 2, 3])
avg([1, 2, 3, 4, 5])

* Funciona si es una tupla
python
avg((1, 2, 3, 4, 5))

* Funciona con un set
python
avg({1, 2, 3, 4, 5})


* Otra forma de pasar a una función un número variable de argumentos con empaquetado y desempaquetado de tupla de argumentos utilizando el operador asterisco (*).
* Cuando el nombre de un parámetro en una definición de función está precedido por un asterisco (*), indica el empaquetado de tupla de argumentos. 
* Todos los argumentos correspondientes en la llamada a la función se empaquetan en una tupla a la que la función puede hacer referencia por el nombre de parámetro dado. 
* Ejemplo:
python
def f(*args):
    print(f"args: {args}")
    print(f"Tipo: {type(args)}, Longitud: {len(args)}")
    print("Valores")
    for x in args:
            print(f"{x}",end="|")
f(1, 2, 3)

```python
f("Hugo", "Paco", "Luis", "Donald")

* El promedio se obtendrá así:
python
def avg(*args):
    total = 0
    for i in args:
        total += i
    return total / len(args)


avg(1, 2, 3)

python
avg(1, 2, 3, 4, 5)

python
def avg(*args):
    return sum(args) / len(args)


avg(1, 2, 3, 4, 5)

* Desempaquetamiento de la tupla
python
def f(x, y, z):
    print(f'x = {x}')
    print(f'y = {y}')
    print(f'z = {z}')


f(1, 2, 3)

python
t = ("Hugo", "Paco", "Luis")
f(*t)

* Se puede aplicar a sets y listas
python
s = {1,2,3}
f(*s)

python
l = [1, 2, 3]
f(*l)

* Se pueden empaquetar y desempaquetar tuplas al mismo tiempo:
python
def f(*args):
    print(type(args), args)


names = ["Hugo", "Paco", "Luis"]
f(*names)

#### Empaquetado de argumentos tipo diccionario
* El doble asterisco (**) se puede usar con parámetros de función y argumentos de Python para especificar el empaquetado y desempaquetado de diccionarios.
* Indica que se espera que los argumentos correspondientes sean pares key=value
* Se empaquetan en un diccionario:
python
def f(**kwargs):#Dos asteriscos significa que va a ser diccionario
    print(kwargs)
    print(type(kwargs))
    for key, val in kwargs.items():
            print(key, '->', val)


f(name_1 = "Hugo", name_2 = "Paco", name_3 = "Luis")

python

names = {"name_1": "Hugo", "name_2": "Paco", "name_3" : "Luis"}
f(**names)

* Desempaquetado de los argumentos tipo diccionario
python
def f(a, b, c, e):
    print(f'a = {a}')
    print(f'b = {b}')
    print(f'c = {c}')
    print(f'e = {e}')


d = {'a': 'Hugo', 'b': "Paco", 'c': 'Luis', 'e': 'Daisy'}
f(**d)

* Equivalente a:
python
f(a='Hugo', b="Paco", c='Luis')

* Otra forma de hacerlo es:
python
f(**dict(a='Hugo', b='Paco', c='Luis'))
names = dict(a='Hugo', b='Paco', c='Luis')
names

* Combinación de todo
python
def f(a, b, *args, **kwargs):
    print(f'a = {a}')
    print(f'b = {b}')
    print(f'args = {args}')
    print(f'kwargs = {kwargs}')


f(1, 2, 'Hugo', 'Paco', 'Luis', x=5, y=10, z=15)
f(1, 2)

#### Desempaquetamiento múltiple
python
def f(*args):
    for i in args:
            print(i)


a = [1, 2, 3]
t = (4, 5, 6)
s = {9, 8, 7} #No es ordenado

f(*a)
f(*a, *t,)
f(*t, *a, *s)

python
def f(*args):
    l = []
    for i in args:
            l.append(i)
    return l


a = [1, 2, 3]
t = (4, 5, 6)
s = {7, 8, 9}

nums = f(*a, *t, *s)
nums

#### Desempaquetamiento múltiple de diccionarios
python
def f(**kwargs):
    for k, v in kwargs.items():
            print(k, '->', v)


d1 = {'a': 1, 'b': 2}
d2 = {'x': 3, 'y': 4}

f(**d1, **d2)

* Se puede usar con iterables
python
def f(*args):
    for i in args:
            print(i)


f(*[1, 2, 3], *[4, 5, 6])

python
def f(**kwargs):
    for k, v in kwargs.items():
            print(k, '->', v)


f(**{'a': 1, 'b': 2}, **{'x': 3, 'y': 4})

#### Argumentos solo de palabra clave
python
def oper(x, y, *, op='+'):
    if op == '+':
            return x + y
    elif op == '-':
            return x - y
    elif op == '/':
            return x / y
    else:
            return None

oper(x=5, y=3, op='+')

oper(5, y=3, op='+')
oper(3, 4, op='+')
oper(3, 4, op='/')
oper(3, 4, "Hola")
oper(3, 4, '+')

#### Argumentos solo posicionales
python
def f(x, y, /, z):
    print(f'x: {x}')
    print(f'y: {y}')
    print(f'z: {z}')
f(1, 2, 3)
f(1, 2, z=3)
f(x=1, y=2, z=3)

* Combinación de solo posición y solo palabra clave (nombrado) en la misma definición de función
python
def f(x, y, /, z, w, *, a, b):
    print(x, y, z, w, a, b)
f(1, 2, z=3, w=4, a=5, b=6)
f(1, 2, 3, w=4, a=5, b=6)
f(x=1, y=2, z=3, w=4, a=5, b=6)
f(1, 2, 3, 4, a=5, b=6)
f(1, 2, 3, 4, 5, 6)

#### Docstrings

* *Docstrings* son cadenas de texto que se encuentran en la primera línea de una función, clase, módulo o método.
* Se utilizan para documentar el código y se pueden acceder a través del atributo `_doc_`.
* Ejemplo:

python
def avg(*args):
    """Returns the average of a list of numeric values."""
    return sum(args) / len(args)

python
def avg(*args):
    """
        Returns the average of a list of numbers values
        Example
        avg(1, 2, 3)
        output:
        2.0
    """



    return sum(args) / len(args)


#repeal reval input
print(avg.__doc__)
avg
print(avg.__doc__)


#### 2.1.4 Funciones como Objetos



#### 2.1.4.1 Asignación de funciones a variables.



##### Escriba una función double que obtenga el doble de un valor mediante el uso de una variable.

python
# Definir la función double
def double(x:int)->int:
    return x * 2

# Asignar la función double a la variable my_double
my_double = double
print(type(my_double))

# Llamar a la función a través de la variable
result = my_double(5)

# Imprimir el resultado
print(result)

#Las funciones se pueden asignar

# * Este programa define una función llamada `double` que toma un argumento `x` y devuelve el doble del mismo.
# * La función `double` se asigna a la variable `my_double`.
# * La función `my_double` se llama con el argumento 5 y el resultado se asigna a la variable `result`. 
# * Finalmente, el programa imprime el valor de `result` en la pantalla, que es el resultado de llamar a la función `double` con el argumento 5.


#### 2.1.4.2 Paso de funciones como argumentos.



##### Escriba un programa que mediante el uso de dos funciones: double() y cuad(), se pueda obtener el cuadrado del doble de un número entero. La función double debe ser usada como argumento de cuad.

python
def double(x:int)->int:
    return x * 2

# Llamar a la función a través de la variable
doble = double(3)

def cuad(f):
    return f ** 2

cuadrado = cuad(doble)
print(cuadrado)

#No es lo mismo enviar como argumento una variable que enviar una funcion


# * Este programa define dos funciones, `double` y `cuad`
# * las utiliza para calcular el cuadrado del doble de un número. 
# * Primero, la función `double` multiplica su argumento por 2 y lo devuelve.
# * Luego, la función `cuad` toma un argumento `f` y devuelve el cuadrado de `f`.
# * El programa asigna la función `double` a la variable `my_double`, llama a `my_double` con el argumento 5 y asigna el resultado a la variable `doble`.
# * Finalmente, el programa llama a `cuad` con `doble` como argumento y asigna el resultado a la variable `cuadrado`, que se imprime en pantalla.

##### Escriba ahora un programa que eleve una lista de números al cuadrado. La función se debe llamar elevar_numeros y debe recibir como argumento la lista y la función cuad, que es la que va a elevar el número al cuadrado.

python
def cuad(n:int)->int:
    return n ** 2


def elevar_numeros(lista, cuad):
    lista_cuadrados = []
    for num in lista:
        lista_cuadrados.append(cuad(num))
    return lista_cuadrados


lista = [1, 2, 3, 4, 5]
print(elevar_numeros(lista, cuad))

python
def cuad(n:int)->int:
    return n ** 2


def elevar_numeros(lista): #Cuad es global no necesito enviarlo como argumento a menos que se iguale a otra variable
    lista_cuadrados = []
    for num in lista:
        lista_cuadrados.append(cuad(num))
    return lista_cuadrados


lista = [1, 2, 3, 4, 5]
print(elevar_numeros(lista))


python
def elevar_numeros(lista):
    lista_cuadrados = []
    for num in lista:
        lista_cuadrados.append((lambda x: x **2)(num))
    return lista_cuadrados


lista = [1, 2, 3, 4, 5]
print(elevar_numeros(lista))


# * Este programa define dos funciones, `cuad` y `elevar_numeros`, se utilizan para calcular el cuadrado de cada número en una lista.
# * La función `cuad` toma un argumento `n` y devuelve el cuadrado de `n`.
# * La función `elevar_numeros` toma una lista y una función como argumentos, y devuelve una lista que contiene el resultado de aplicar la función a cada elemento de la lista original.
# * En este caso, la función `elevar_numeros` llama a la función `cuad` para cada número en la lista y devuelve una lista de los cuadrados correspondientes.
# * El programa crea una lista de números del 1 al 5, llama a la función `elevar_numeros` con la lista y la función `cuad` como argumentos, y luego imprime la lista resultante de cuadrados en la pantalla.

###### Escriba un programa que eleve a la potencia y cada uno de los elementos de una lista. Use la función elevar_números que reciba la lista y la potencia, y dentro de esta use la función potencia que se encargará de elevar a la potencia y cada elemento de la lista.

python
def potencia(x,y): #pow(x,y)
    for _ in range(y):
        x = x * y
    return x


def elevar_numeros(lista, y):
    lista_potencias = []
    for num in lista:
        lista_potencias.append(pow(num,y))
    return lista_potencias


lista = [1, 2, 3, 4, 5]
print(elevar_numeros(lista, 2))



# * Este programa define dos funciones: `potencia` y `elevar_numeros`
# * Permite elevar cada número en una lista a una potencia dada.
# * La función `potencia` toma dos argumentos, `x` y `y`, y devuelve `x` elevado a la potencia `y`.
# * La función utiliza un ciclo `for` para multiplicar `x` por `y` `y` veces.
# * La función `elevar_numeros` toma una lista y un número `y` como argumentos, y devuelve una lista que contiene el resultado de elevar cada elemento de la lista a la potencia `y`.
# * La función `elevar_numeros` llama a la función `potencia` para cada número en la lista y agrega el resultado a una nueva lista.
# * El programa crea una lista de números del 1 al 5, llama a la función `elevar_numeros` con la lista y el número 2 como argumentos, y luego imprime la lista resultante de números elevados al cuadrado en la pantalla.

#### 2.1.4.3 Funciones anónimas (lambda functions).

# Las funciones lambda en Python son funciones anónimas que se pueden definir en una sola línea de código. 
# 
# - Las funciones lambda:
#     * se definen utilizando la palabra clave `lambda`, seguida de los argumentos de la función separados por comas y luego dos puntos.
#     * es una expresión que se evalúa y devuelve como resultado.
#     - son funciones anónimas, lo que significa que no tienen un nombre definido.
#     - se pueden asignar a una variable y luego llamar a través de esa variable.
#     - se utilizan comúnmente como argumentos de otras funciones, como `map()`, `filter()`, `reduce()`, etc.
#     - son útiles para escribir código más conciso y legible (cuando se trabaja con funciones simples y de una sola línea)

python
def identity(x):
    return x

print(identity(3)) #Eesto es reutilizable porque si quiero cambiar el valor de identity puedo hacerlo

#Son funciones sin nombre y se diseñaron para ejecutarse una sola vez

python
lambda x: x
#print((lambda x: x*2)(5))
y = lambda x: x
y(5)

#Es una funcion compactada

python
add_one = lambda x: x+1
add_one(5)

python
lambda x: x + 1

python
(lambda x: x + 1)(2)
python

python
# puede ser nombrada

add_one = lambda x: x + 1
add_one(2)

python
def add_one(x):
    return x + 1


python
(lambda x,y: x/y)(10,y=1)

def division(x,y=1):
    return x/y


division(5)
 


#### 2.1.5 Recursión
#### 2.1.5.1 Definición de funciones recursivas.

# * Una definición recursiva es aquella en la que el término definido aparece en la propia definición.
# * Capacidad de una función de llamarse a sí misma
# * La mayoría de los problemas de programación se pueden resolver sin recursividad. 
# * Entonces... la recursividad no suele ser necesaria.
# --------
# * El recorrido de estructuras de datos en forma de árbol es un ejemplo.
# * Debido a que se trata de estructuras anidadas, se ajustan fácilmente a una definición recursiva.
# * Es probable que un algoritmo no recursivo para recorrer una estructura anidada sea algo burdo.
# * Una solución recursiva puede ser más elegante y eficiente.


python
def f():
    x = 10
    f()

    #Recursion es una funcion que se llama asi misma
    #El caso base va a ser el mecanismo de salida de las funciones recursivas

python
f()

# Para conocer el límite de recursión
python
import sys
print(sys.getrecursionlimit())

python
from sys import getrecursionlimit
print(getrecursionlimit())


# Se puede modificar el límite de recursión
python
sys.setrecursionlimit(500)

python
f()


# * Las funciones recursivas suelen un patrón:
#     * Hay uno o más casos base que se pueden resolver directamente sin necesidad de más recursividad.
#     * Cada llamada recursiva acerca progresivamente la solución a un caso base (mecanismo de retorno).


#### 2.1.5.2 Casos base y casos recursivos.

# * Ejemplo: Cuenta regresiva hasta cero

# cuenta regresiva no recursiva (iterativa)
python
def cuenta_regresiva(n):
    while n >= 0:
        print(n)
        n -= 1

cuenta_regresiva(5)

# cuenta regresiva recursiva
python
def cuenta_regresiva(n):
    print(n)
    if n == 0:
        return                      # Fin de la recursión, caso base
    else:
        cuenta_regresiva(n - 1)     # Llamada recursiva


cuenta_regresiva(5)

# * El caso base se produce cuando n es cero, momento en el que se detiene la recursividad.
# * En la llamada recursiva, el argumento es uno menos que el valor actual de n, por lo que cada recursividad se acerca al caso base.

# * Ejemplo: Calcular el factorial

# Función factorial no recursiva (iterativa)
python
def factorial(n):
    result = 1
    for i in range(1, n+1):
        result *= i
    return result


# función factorial recursiva
python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))

# %%
def factorial(n):
    return 1 if n <= 1 else n * factorial(n - 1)


print(factorial(5))

python
def factorial(n):
    print(f"factorial() llamado con n = {n}")
    return_value = 1 if n <= 1 else n * factorial(n -1)
    print(f"-> factorial({n}) retorna {return_value}")
    return return_value


factorial(5)

# * Calcular el tiempo de ejecución (evaluación empírica)
# * timeit(<command>, setup=<setup_string>, number=<iterations>)


# Ejemplo iterativo
python
from timeit import timeit

timeit("print(string)", setup="string='Hola Mundo'", number=100)

#Jamas probar un algoritmo y entregar los resultados probandolo en computadras distintas


# Performance algoritmo factorial iterativo
python
from timeit import timeit

setup_string = """
print("Iterativo:")
def factorial(n):
    result = 1
    for i in range(2, n + 1):
        result *= i
    return result
"""

from timeit import timeit
timeit("factorial(4)", setup=setup_string, number=10000000)


# Performance algoritmo factorial iterativo
python
from timeit import timeit

setup_string = """
print("Recursive:")
def factorial(n):
    return 1 if n <= 1 else n * factorial(n - 1)
"""

from timeit import timeit
timeit("factorial(4)", setup=setup_string, number=10_000_000)


python
#Usando reduce
setup_string = """
from functools import reduce
print("reduce():")
def factorial(n):
    return reduce(lambda x, y: x * y, range(1, n + 1) or [1])
"""

from timeit import timeit
timeit("factorial(4)", setup=setup_string, number=10000000)


# Python ya tiene una función factorial
python
from math import factorial
factorial(4)

python
setup_string = "from math import factorial"

from timeit import timeit
timeit("factorial(4)", setup=setup_string, number=10_000_000)


#### 2.1.6 Documentación y Comentarios
#### 2.1.6.1 Uso de docstrings para documentar funciones.

python
def suma(a, b):
    """
    This function adds two numbers.
    Parameters:
    a (int): The first number.
    b (int): The second number.
    Returns:
    int: The sum of a and b.
    """
    return a + b

def resta(a, b):
    """
    This function subtracts two numbers.
    Parameters:
    a (int): The first number.
    b (int): The second number.
    Returns:
    int: The difference between a and b.
    """
    return a - b

def multiplicacion(a, b):
    """
    This function multiplies two numbers.
    Parameters:
    a (int): The first number.
    b (int): The second number.
    Returns:
    int: The product of a and b.
    """
    return a * b

def division(a, b):
    """
    This function divides two numbers.
    Parameters:
    a (int): The first number.
    b (int): The second number.
    Returns:
    float: The quotient of a and b.
    """
    return a / b

#Comentarios de documentacion

python
print(suma.__doc__)


#### 2.1.6.2 Comentarios relevantes en el código.


python
def suma(a:int, b:int):
    """
    This function adds two numbers.
    Parameters:
    a (int): The first number.
    b (int): The second number.     esto es comentario de documentacion
    Returns:
    int: The sum of a and b.
    """
    # Check if both a and b are integers ( esto es un cometario de segmento de codigo)
    if not isinstance(a, int) or not isinstance(b, int):
        print("Both a and b should be integers.")
        return None

    # Add a and b
    result = a + b

    # Print the result
    print(f"The sum of {a} and {b} is {result}.")

    return result


python
print(suma(1.0,5))


#### 2.1.7 Módulos y Organización:**

#### 2.1.7.1 Creación de módulos con funciones.
# 1. Crear la carpeta calculadora
# 2. Crear el archivo _init_.py
# 3. Crear el archivo que tendrá las funciones: calculos.py
# 4. Crear las funciones dentro de calculos.py


#### 2.1.7.2 Importación de funciones desde módulos.


#### 2.1.8 Pruebas y Depuración:


python

#import unittest


def suma(a, b):
    """
    This function adds two numbers.
    Parameters:
    a (int): The first number.
    b (int): The second number.
    Returns:
    int: The sum of a and b.
    """
    return a + b

def resta(a, b):
    """
    This function subtracts two numbers.
    Parameters:
    a (int): The first number.
    b (int): The second number.
    Returns:
    int: The difference between a and b.
    """
    return a - b

assert suma(2, 3) == 5.0, "debería ser 5"
assert suma(-2, 3) == 1, "debería ser 1"
assert suma(0, 0) == 0, "debería ser 0"
assert suma(-3,-3) == -6, "debería ser -6"

assert resta(2, 3) == -1, "debería ser -1"
assert resta(-2, 3) == -5, "debería ser -5"
assert resta(0, 0) == 0, "debería ser 0"


#### Codigo de una calculadora
python
""" import calculadora.calculos as calc  #"as" es un alias 
print(calc.suma.__doc__)
print(calc.suma(2, 3))
 """
#-----------------------------------------------------------------------------------------------------------
from calculadora import calculos

print(calculos.suma(2, 3))
print(calculos.resta(2, 3))
print(calculos.multiplicacion(2, 3))
print(calculos.division(2, 3))
print(calculos.cuadrado(2))

#------------------------------------------------------------------------------------------------------------

from calculadora.calculos import *

print(suma(2, 3))
print(resta(2, 3))

#---------------------------------------------------------------------------------------------------------------------
from calculadora.calculos import suma

print(suma(2, 3))
print(resta(2, 3))

#---------------------------------------------------------------------------------------------------------------------
from calculadora.calculos import suma as sumar
from calculadora.calculos import resta as restar #Alias

print(sumar(2, 3))
print(restar(2, 3))

python
def suma(a, b):
    """
    comentarios de la funcion suma
    """
    return a + b


def resta(a, b):
    return a - b


def multiplicacion(a, b):
    return a * b


def division(a, b):
    if b == 0:
        raise ZeroDivisionError("Division by zero")
    return float(a / b)


def cuadrado(a):
    return a ** 2
