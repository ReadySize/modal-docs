# Documentación Técnica de Integración de la Aplicación Readysize

## Introducción

La aplicación Readysize se puede integrar fácilmente en cualquier sitio web mediante la inclusión del siguiente tag HTML en el código fuente:

```html
<script src="https://modal.readysize.ai/readysize/jsReadySize.js"></script>
```

Esta integración permite agregar funcionalidades adicionales al sitio web para interactuar con la librería de Readysize.

## Funcionalidades

### `openModal(codigoProducto, callbackRespuesta, params)`

La función `openModal` se utiliza para abrir un modal de Readysize en el sitio web. A continuación, se describen los parámetros y el formato de respuesta:

- `codigoProducto` (string): El código del producto que se desea consultar.

- `callbackRespuesta` (function): Una función de callback que se ejecutará cuando se obtenga una respuesta de la librería. Esta función recibirá un parámetro con la siguiente estructura:

  ```javascript
  {
    data: {
      tranSizeId: number,
      selectedSize: string
    }
  }
  ```

  - `tranSizeId` (number): El identificador de la transacción de tamaño.

  - `selectedSize` (string): El tamaño seleccionado para el producto.

- `params` (object) (opcional): Un objeto que puede contener los siguientes campos:

  - `staticImg` (string): La URL de la imagen del producto.

  - `sizes` (array de strings) (opcional): Las tallas en las que se publica el producto. Este campo es opcional y se utiliza en casos donde el código del producto se refiere a una codificación abstracta que agrupa varios SKUs con la misma guía de tallas.

  - `fitType` (number) (opcional): El tipo de ajuste del producto. Los valores esperados son:

    - `1`: Regular
    - `2`: Ajustado
    - `3`: Holgado

  Estos campos son opcionales y se utilizan para proporcionar información adicional sobre el producto al abrir el modal de Readysize.

### `addCart(tranSizeId)`

La función `addCart` se utiliza para agregar un producto al carrito de compras de Readysize. A continuación, se describe el parámetro:

- `tranSizeId` (number): El identificador de la transacción de tamaño del producto que se desea agregar al carrito.

### `isProductAvailable(codigoProducto)`

La función `isProductAvailable` se utiliza para verificar la disponibilidad de un producto en la librería de Readysize. Esta función devuelve un valor booleano que indica si el producto está disponible.

- `codigoProducto` (string): El código del producto que se desea verificar.

## Ejemplo de Uso

A continuación, se muestra un ejemplo de cómo utilizar las funcionalidades de la aplicación Readysize en tu sitio web:

```javascript
// Abrir el modal de Readysize para un producto con detalles adicionales
const params = {
  staticImg: "https://ejemplo.com/imagen-producto.jpg",
  sizes: ["S", "M", "L"],
  fitType: 1
};

openModal("producto123", function(respuesta) {
  console.log("Transacción de Tamaño ID: " + respuesta.data.tranSizeId);
  console.log("Tamaño Seleccionado: " + respuesta.data.selectedSize);
}, params);

// Agregar un producto al carrito de compras
addCart(123);

// Verificar la disponibilidad de un producto
const disponible = isProductAvailable("producto456");
if (disponible) {
  console.log("El producto está disponible en Readysize");
} else {
  console.log("El producto no está disponible en Readysize");
}
```

## Conclusiones

La integración de la aplicación Readysize en tu sitio web te permite aprovechar las funcionalidades de la librería para mejorar la experiencia del usuario al seleccionar tallas de productos. Las funciones proporcionadas son simples de usar y pueden personalizarse según las necesidades de tu sitio web.

¡Esperamos que esta documentación te ayude a integrar la aplicación Readysize con éxito en tu sitio web! Si tienes alguna pregunta adicional o necesitas asistencia, no dudes en contactarnos.
  
