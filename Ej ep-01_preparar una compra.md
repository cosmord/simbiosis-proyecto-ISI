# Ejercicio 01: Preparar una compra

## 1. División de la Épica

### Épica original:
> Como cliente de una tiendo online quiero preparar mi compra, para elegir los productos y ajustar sus cantidades antes de confirmar el pedido.

Para dividirla correctamente, separamos la acción de "elegir" (añadir al carrito) de la acción de "ajustar" (modificar lo que ya está dentro), garantizando que cada historia aporte valor por sí misma.

#### Historia 1 (US-01): Elección de productos

[ ] Como cliente de una tienda online, quiero añadir productos a mi carrito desde el catálogo, para comenzar a preparar mi lista de compra.

#### Historia 2 (US-02): Ajuste de cantidades

[ ] Como cliente de una tienda online, quiero modificar la cantidad de unidades de los productos en mi carrito, para asegurar que compro exactamente lo que necesito antes de pagar.

---

## 2. Criterios de aceptación

### Historia 1 (US-01): Elección de productos

- Dado que tengo el [producto] en el catálogo, cuando hago clic en añadir al carrito incrementando en 1 la cantidad de unidades en el carrito, entonces el producto se añade a mi carrito de compras, se actualiza en numero de unidades, se muestra un mensaje de confirmación y se refleja en el total del pedido y el precio total se actualiza correctamente.

### Historia 2 (US-02): Ajuste de cantidades
- Dado que tengo [producto] en mi carrito, cuando se modifica la cantidad de unidades reduciendolo o aumentándo la cantidad de unidades, entonces el carrito se actualiza correctamente, se muestra un mensaje de confirmación y el precio total se ajusta según la nueva cantidad.