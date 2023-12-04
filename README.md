# tarea-3-semestre-parcial-3
## Alumno: Dante Gonzalez
## Profesor: Walter Mata
## Carrera: Computacion inteligente
## Grupo: D
## Diseño e Implementación de un Sistema de Gestión de Inventario para un Almacén
---
Codigo: (en caso de no funcionar eliminar las fotos )
```
from guizero import App, PushButton, TextBox, Text, ListBox,Picture,Combo

productos = []

def agregar_producto():
    codigo = int(codigo_input.value)
    if any(producto[0] == codigo for producto in productos):
        detalle_producto.value = "Ya existe un producto con este código."
    else:
        descripcion = descripcion_input.value
        ubicacion = ubicacion_input.value
        precio = float(precio_input.value)
        cantidad = int(cantidad_input.value)
        proveedor = proveedor_input.value
        productos.append((codigo, descripcion, ubicacion, precio, cantidad, proveedor))
        lista_productos.append(codigo)
        detalle_producto.value = "Producto agregado correctamente"

def eliminar_producto():
    seleccion = lista_productos.value
    if seleccion is not None:
        productos[:] = [producto for producto in productos if producto[0] != seleccion]
        lista_productos.clear()
        for producto in productos:
            lista_productos.append(producto[0])
        detalle_producto.value = "Producto eliminado"
    else:
        detalle_producto.value = "Selecciona un producto para eliminar"

def mostrar_detalle_producto():
    seleccion = lista_productos.value
    detalles = ""
    for producto in productos:
        if producto[0] == seleccion:
            detalles = f"Codigo: {producto[0]}\nDescripción: {producto[1]}\nPrecio: {producto[2]}\nCantidad: {producto[3]}\nUbicación: {producto[4]}\nProveedor: {producto[5]}"
            break
    detalle_producto.value = detalles

def actualizar_producto():
    seleccion = lista_productos.value
    if seleccion is not None:
        for i, producto in enumerate(productos):
            if producto[0] == seleccion:
                productos[i] = (
                    int(codigo_input.value),
                    descripcion_input.value,
                    ubicacion_input.value,
                    float(precio_input.value),
                    int(cantidad_input.value),
                    proveedor_input.value
                )
                detalle_producto.value = "Producto actualizado"
                break
    else:
        detalle_producto.value = "Selecciona un producto para actualizar"

def entrada_producto():
    seleccion = lista_productos.value
    if seleccion is not None:
        for i, producto in enumerate(productos):
            if producto[0] == seleccion:
                productos[i] = (
                    producto[0],
                    producto[1],
                    producto[2],
                    producto[3],
                    producto[4] + int(cantidad_input.value),
                    producto[5]
                )
                detalle_producto.value = "Producto actualizado"
                break
    else:
        detalle_producto.value = "Selecciona un producto para actualizar"

def salida_producto():
    seleccion = lista_productos.value
    if seleccion is not None:
        for i, producto in enumerate(productos):
            if producto[0] == seleccion:
                productos[i] = (
                    producto[0],
                    producto[1],
                    producto[2],
                    producto[3],
                    producto[4] - int(cantidad_input.value),
                    producto[5]
                )
                detalle_producto.value = "Producto actualizado"
                break
    else:
        detalle_producto.value = "Selecciona un producto para actualizar"

def generar_alertas():
    for producto in productos:
        if producto[4] < 10:
            detalle_producto.value= f"Alerta: El stock del producto {producto[1]} es bajo."
        else:
            detalle_producto.value ="No hay alertas"


app = App(title="Inventario :D")
foto2 = Picture(app, image=r"c:\Users\dante\OneDrive\Escritorio\pollo.jpg",width=50,height=50)


codigo_label = Text(app, text="Código:",color="Red")
codigo_input = TextBox(app)
descripcion_label = Text(app,text="Descripción:",color="Red")
descripcion_input = TextBox(app)
precio_label = Text(app, text="Precio:",color="Red")
precio_input = TextBox(app)
cantidad_label = Text(app, text="Cantidad:",color="Red" )
cantidad_input = TextBox(app)
ubicacion_label = Text(app, text="Ubicación:",color="Red" )
ubicacion_input = TextBox(app)
proveedor_label = Text(app, text="Proveedor:",color="Red" )
proveedor_input = TextBox(app)
agregar_button = PushButton(app, text="Agregar Producto", command=agregar_producto)
eliminar_button = PushButton(app, text="Eliminar Producto", command=eliminar_producto)
actualizar_button = PushButton(app, text="Actualizar Producto", command=actualizar_producto)

lista_productos = ListBox(app, command=mostrar_detalle_producto, width=50, height=50)
detalle_producto = Text(app)

foto = Picture(app, image=r"c:\Users\dante\OneDrive\Escritorio\gallo.gif",width=50,height=50)


entrada_button = PushButton(app, text="Entrada", command=entrada_producto)
salida_button = PushButton(app, text="Salida", command=salida_producto)
alertas_button = PushButton(app, text="Generar Alertas", command=generar_alertas)
cerrar = PushButton(app, text="Cerrar Programa", command=app.destroy)

app.display()
```
---
funcionamiento:
![image](https://github.com/danteglez/tarea-3-semestre-parcial-3/assets/129199887/81895e50-80e1-4f58-8740-b463987708bc)
![image](https://github.com/danteglez/tarea-3-semestre-parcial-3/assets/129199887/80a8329f-79c9-4edf-9e6f-3cb985dcf8b9)
![image](https://github.com/danteglez/tarea-3-semestre-parcial-3/assets/129199887/c9c16ebe-b08a-47ce-a47a-3a79b5f57fdd)
---
## ¿Qué es un paradigma imperactivo?
La programación imperativa es el paradigma de programación más antiguo. En este paradigma, un programa consiste en una secuencia claramente definida de instrucciones para un ordenador. El código fuente de los lenguajes imperativos encadena instrucciones una detrás de otra que determinan lo que debe hacer el ordenador en cada momento para alcanzar un resultado deseado. Los valores utilizados en las variables se modifican durante la ejecución del programa. Para gestionar las instrucciones, se integran estructuras de control como bucles o estructuras anidadas en el código. Los lenguajes de programación imperativa más conocidos son: Fortran, Java, Pascal, ALGOL, C, C#, C++, Ensambladores, BASIC, COBOL, Python, Ruby.

### Ventajas 
1.-Sencillez en la estructura: Los lenguajes de programación imperativa son muy concretos y trabajan cerca del sistema. Esto hace que el código sea fácilmente comprensible.
2.-Control detallado: Este paradigma permite un control detallado sobre la máquina. Esto es especialmente útil para tareas que requieren manipulaciones a bajo nivel.
3.-Mayor abstracción: Los lenguajes de programación imperativa incorporan funciones de orden superior.
4.-Facilidad en la reutilización del código: Los lenguajes de programación imperativa facilitan la reutilización del código.
5.-Potencia y elegancia: Los lenguajes de programación imperativa son conocidos por su potencia y elegancia.
6.-Eficiencia en la escritura de programas: Este procedimiento tiene numerosas ventajas: de esta forma, los programas no solo se pueden escribir considerablemente más rápido, sino que las aplicaciones se pueden optimizar también de forma muy sencilla.

### Desventajas
1.-Ineficiencia: Los lenguajes de programación imperativa pueden ser ineficientes en comparación con los lenguajes de programación declarativ1.
2.-Falta de estandarización: Los lenguajes de programación imperativa pueden carecer de estandarización.
3.-Complejidad innecesaria: Los lenguajes de programación imperativa pueden añadir una complejidad innecesaria al código.
4.-Dificultad para dividir el trabajo y la ejecución simultánea: Los lenguajes de programación imperativa pueden tener dificultades para dividir el trabajo y la ejecución simultánea.

## ¿Qué es un paradigma declarativo?
la programación declarativa es un paradigma de programación en el que se describe el resultado final deseado, en lugar de mostrar todos los pasos de trabajo. Para alcanzar el objetivo, en la programación declarativa se determina automáticamente la vía de solución. Esto funciona siempre y cuando las especificaciones del estado final se definan claramente y exista un procedimiento de ejecución adecuado. Si se dan las dos condiciones, la programación declarativa es muy eficiente1. Los lenguajes de programación declarativa más conocidos son: Prolog, Lisp, Haskell, Miranda, Erlang, SQL.

### Ventajas 
1.-Código más corto y optimizado: Los lenguajes de programación declarativa a menudo permiten describir problemas de forma más corta y precisa que los lenguajes imperativos.
2.-Fácil de optimizar: Dado que los lenguajes declarativos describen el resultado deseado, en lugar de los pasos específicos para llegar allí, a menudo es más fácil para los compiladores e intérpretes optimizar el código.
3.-Mantenimiento independiente de la aplicación: Los lenguajes declarativos permiten un mantenimiento más sencillo del código.
4.-Elegancia, claridad, sencillez, potencia y concisión: Los lenguajes declarativos son conocidos por su elegancia, claridad, sencillez, potencia y concisión.
5.-Semánticas claras, simples y matemáticamente bien fundadas: Los lenguajes declarativos tienen semánticas claras, simples y matemáticamente bien fundadas.
6.-Software mejor preparado para el futuro: Este tipo de paradigma da como resultado un software mejor preparado para el futuro, ya que no es necesario determinar mediante qué procedimiento se alcanza un resultado.

### Desventajas 
1.-Descubrimiento del algoritmo básico: El principal obstáculo del paradigma declarativo es el descubrimiento del algoritmo básico para resolver problemas.
2.-Propósito específico: Los lenguajes declarativos tienden a ser de propósito específico, diseñados para usarse en aplicaciones particulares.
3.-Eficiencia: Otra desventaja de la programación declarativa está relacionada con la eficiencia.
4.-Carecen de librerías, interfaces con otros lenguajes y herramientas de depuración: Los lenguajes de programación declarativa pueden carecer de librerías, interfaces con otros lenguajes y herramientas de depuración.

### Conclucion
 tanto el paradigma imperativo como el declarativo tienen sus propias fortalezas y debilidades 
 El paradigma imperativo es más directo y explícito, lo que es especialmente útil para principiantes, tienes que dar paso a paso cada proceso por lo que puede dar problema y puede ser dificil de entender alfinal 
 el paradigma declarativo se centra mas en el resultado mas que en los pasos a seguir, puede ser mas facil para realizar problemas mas complicados y mas facil de leer las lineas de codigo, pero no se puede modificar tan facil los pasos que quieres que haga para solucionar un problema
