# tarea-3-semestre-parcial-3
## Alumno: Dante Gonzalez
## Profesor: Walter Mata
## Carrera: Computacion inteligente
## Grupo: D
## Diseño e Implementación de un Sistema de Gestión de Inventario para un Almacén
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
