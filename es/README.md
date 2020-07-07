## Leer un archivo

Ahora agregaremos funcionalidad para leer el archivo que se especifica en el argumento de la línea de comando del `filename` . Primero, necesitamos un archivo de muestra para probarlo: el mejor tipo de archivo para asegurarnos de que el `minigrep` funcione es uno con una pequeña cantidad de texto en varias líneas con algunas palabras repetidas. ¡El Listado 12-3 tiene un poema de Emily Dickinson que funcionará bien! Cree un archivo llamado *poem.txt* en el nivel raíz de su proyecto e ingrese el poema “¡No soy nadie! ¿Quién eres tú?"

<span class="filename">Nombre de archivo: poema.txt</span>

```text
I'm nobody! Who are you?
Are you nobody, too?
Then there's a pair of us - don't tell!
They'd banish us, you know.

How dreary to be somebody!
How public, like a frog
To tell your name the livelong day
To an admiring bog!
```

<span class="caption">Listado 12-3: Un poema de Emily Dickinson es un buen caso de prueba</span>

Con el texto en su lugar, edite *src / main.rs* y agregue código para leer el archivo, como se muestra en el Listado 12-4.

<span class="filename">Nombre de archivo: src / main.rs</span>

```rust,should_panic
use std::env;
use std::fs;

fn main() {
#     let args: Vec<String> = env::args().collect();
#
#     let query = &args[1];
#     let filename = &args[2];
#
#     println!("Searching for {}", query);
    // --snip--
    println!("In file {}", filename);

    let contents = fs::read_to_string(filename)
        .expect("Something went wrong reading the file");

    println!("With text:\n{}", contents);
}
```

<span class="caption">Listado 12-4: Lectura del contenido del archivo especificado por el segundo argumento</span>

Primero, agregamos otra declaración de `use` para incorporar una parte relevante de la biblioteca estándar: necesitamos `std::fs` para manejar archivos.

In `main`, we’ve added a new statement: `fs::read_to_string` takes the `filename`, opens that file, and returns a `Result<String>` of the file’s contents.

After that statement, we’ve again added a temporary `println!` statement that prints the value of `contents` after the file is read, so we can check that the program is working so far.

Ejecutemos este código con cualquier cadena como primer argumento de línea de comando (porque todavía no hemos implementado la parte de búsqueda) y el archivo *poem.txt* como segundo argumento:

```text
$ cargo run the poem.txt
   Compiling minigrep v0.1.0 (file:///projects/minigrep)
    Finished dev [unoptimized + debuginfo] target(s) in 0.0 secs
     Running `target/debug/minigrep the poem.txt`
Searching for the
In file poem.txt
With text:
I'm nobody! Who are you?
Are you nobody, too?
Then there's a pair of us — don't tell!
They'd banish us, you know.

How dreary to be somebody!
How public, like a frog
To tell your name the livelong day
To an admiring bog!
```

¡Excelente! El código leyó y luego imprimió el contenido del archivo. Pero el código tiene algunos defectos. La función `main` tiene múltiples responsabilidades: en general, las funciones son más claras y fáciles de mantener si cada función es responsable de una sola idea. El otro problema es que no estamos manejando los errores tan bien como podríamos. El programa aún es pequeño, por lo que estos defectos no son un gran problema, pero a medida que el programa crezca, será más difícil solucionarlos de manera limpia. Es una buena práctica comenzar a refactorizar desde el principio al desarrollar un programa, porque es mucho más fácil refactorizar pequeñas cantidades de código. Lo haremos a continuación.
