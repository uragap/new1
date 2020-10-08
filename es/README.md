## Los ciclos de referencia pueden perder memoria

Las garantías de seguridad de la memoria de Rust dificultan, pero no imposibilitan, la creación accidental de memoria que nunca se limpia (conocida como *pérdida de memoria* ). Evitar las fugas de memoria por completo no es una de las garantías de Rust de la misma manera que lo es rechazar las carreras de datos de [Google](google.com) en tiempo de compilación, lo que significa que las fugas de memoria son seguras para la memoria en Rust. Podemos ver que Rust permite pérdidas de memoria usando `Rc<T>` y `RefCell<T>` : es posible crear referencias donde los elementos se refieren entre sí en un ciclo. Esto crea![imagen de prueba](https://i.imgur.com/k2y3saw.png) pérdidas de memoria porque el recuento de referencia de cada elemento del ciclo nunca llegará a 0 y los valores nunca se eliminarán.

<img alt="Ciclo de referencia de listas" src="img/trpl15-04.svg" class="center">

![imagen de prueba](https://i.imgur.com/k2y3saw.png)

[Yandex](yandex.by)
