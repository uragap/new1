### Haga clic para copiar

Haga clic para copiar se habilita automáticamente para todos los bloques de código.

### Caso especial: Plantillas - &#123; &#123;}}

Si necesita incluir plantillas en sus ejemplos de código, asegúrese de escapar de ellas.

Por ejemplo:

<pre class="prettyprint">
<pre class="prettyprint"><Polymer-media-query query = "max-width: 640px" queryMatches = "&amp;#123; {isPhone}}"></pre>
</pre>




Si está en línea, deberá envolverlo en un bloque `<code>` lugar de backticks.

<pre class="prettyprint">* Enlace de datos bidireccional declarativo: <code><input id="input" value="&amp;#123;{foo</code>}}"></pre>

## Imágenes

Al agregar un subtítulo, ajuste las imágenes en bloques `<figure>` e, idealmente, use imágenes receptivas con el atributo `scrset` cuando sea posible. Asegúrese de incluir también atributos `alt` para sus imágenes.

<figure><img src="https://placehold.it/350x150" alt="Imagen de muestra"><figcaption> Este título debe usarse para describir la imagen. </figcaption></figure>

Por ejemplo:

```
<figure>
  <img src="https://placehold.it/350x150" alt="sample image">
  <figcaption>This caption should be used to describe the image.</figcaption>
</figure>
```

Nota: Las imágenes optimizadas se sirven automáticamente solo para `index.yaml` páginas `index.yaml` , simplemente proporcione una versión 2x, y el servidor hará el resto.

Puede aplicar `class="screenshot"` a una imagen para darle un borde que la desplace del texto cercano. Esto se usa generalmente para capturas de pantalla que tienen fondos blancos y que de otra manera se pierden en la página. No lo use para imágenes que no lo necesitan.
