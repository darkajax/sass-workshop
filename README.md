# sass-workshop

### Temas
- Setting up
- Features

### Cómo instalar Sass?

#### Mac

```
sudo gem install sass
```

#### Linux (habiendo instalado Ruby previamente)
```
sudo su -c "gem install sass"
```

### Verificar
  
```
sass -v
```

### Forma básica de importar
```
sass input.scss output.css
```

### Wacha el archivo ese :sunglasses:
```
sass --watch input.scss:output.css
```

### Wacha la carpeta
```
sass --watch styles:css
```

### Estilos de output
- nested (default)
- compact
- expanded
- compressed

#### Uso
```
sass --watch styles:css --style compressed
sass --watch styles:css -t compact
```

#### Este código:
```scss
.widget-social {
    text-align: right;

    a,
    a:visited {
        padding: 0 3px;
        color: #222222;
        color: rgba(34, 34, 34, 0.77);
     }

    a:hover {
        color: #B00909;
    }

}
```

#### Compila a (nested):
```css
.widget-social {
  text-align: right; }
  .widget-social a,
  .widget-social a:visited {
    padding: 0 3px;
    color: #222222;
    color: rgba(34, 34, 34, 0.77); }
  .widget-social a:hover {
    color: #B00909; }
```

#### Compila a (expanded):
```css
.widget-social {
  text-align: right;
}
.widget-social a,
.widget-social a:visited {
  padding: 0 3px;
  color: #222222;
  color: rgba(34, 34, 34, 0.77);
}
.widget-social a:hover {
  color: #B00909;
}
```

#### Compila a (compact):
```css
.widget-social { text-align: right; }
.widget-social a, .widget-social a:visited { padding: 0 3px; color: #222222; color: rgba(34, 34, 34, 0.77); }
.widget-social a:hover { color: #B00909; }
```

#### Compila a (compressed):
```css
.widget-social{text-align:right}.widget-social a,.widget-social a:visited{padding:0 3px;color:#222222;color:rgba(34,34,34,0.77)}.widget-social a:hover{color:#B00909}
```


## Features
- 2 Tipos de sintaxis
- Nesting
  - Parent selector (`&`)
- Imports/Partials
- Placeholder selectors
- SassScript
  - Shell interactivo
  - Comments
  - Variables
    - Interpolación
  - Diferentes tipos de datos
  - Operaciones
  - Funciones "predefinidas"
  - Condicionales
  - Mixins
  - Funciones "propias"

## Sintaxis

![sass-vs-scss](/sass-vs-scss.jpg?raw=true "sass-vs-scss")

### Pros de Sass
- Más conciso (no `{}` ni `;` además de usar `+` en lugar de `@import`, por ejemplo), menos código
- Fácil de leer

### Pros de SCSS
- Más flexible/expresivo
- Siendo una extensión de la sintaxis de CSS, cualquier archivo CSS es un archivo SCSS válido con el mismo significado

### Convertir de Sass a SCSS
```
sass-convert style.sass style.scss
```

### Convertir de SCSS a Sass
```
sass-convert style.scss style.sass
```

## Nesting
#### Este código:
```scss
main p {
  color: #00ff00;
  width: 97%;

  .redbox {
    background-color: #ff0000;
    color: #000000;
  }
}
```

#### Compila a:

```css
#main p {
  color: #00ff00;
  width: 97%; }
  #main p .redbox {
    background-color: #ff0000;
    color: #000000; }
```

## Imports / Partials
La directiva `@import` se utiliza para incluir otros archivos en un archivo de Sass. Los parciales son archivos que no generan css y que se utilizan para incluir código de un archivo a otro, su nombre empieza con `_` (`_partial.scss`).

## Placeholder selectors
El selector lleva `%` antes de su nombre y se utiliza con `@extend`

## Shell Interactivo
![interactive-shell](/interactive-shell.png?raw=true "interactive-shell")

## Comments

#### Este código:
```scss
/* This comment is
 * several lines long.
 * since it uses the CSS comment syntax,
 * it will appear in the CSS output. */
body { color: black; }

// These comments are only one line long each.
// They won't appear in the CSS output,
// since they use the single-line comment syntax.
a { color: green; }
```

#### Compila a:
```scss
/* This comment is
 * several lines long.
 * since it uses the CSS comment syntax,
 * it will appear in the CSS output. */
body {
  color: black; }

a {
  color: green; }
```

## Variables
```scss
$variable:  1px;
```

#### Este código:
```scss
$variable:   'something';
$variable:   'something else' !default;
$variable-2: 'some other thing' !default; 

.test {
  content: $variable;
  content: $variable-2;
}
```

#### Compila a:
```css
.test {
  content: 'something';
  content: 'some other thing';
}

```

```scss
.class1 {
  $scope-variable: red;
}
```

```scss
.class2 {
  $globalized-variable: blue !global;
}
```

**Nota:** `-` y `_` son intercambiables en nombres de variables y otros identificadores de Sass (por ejemplo `$variable_1` = `$variable-1`

### Interpolación

#### Este código:
```scss
$class-part: 'part';

.{#class-part}-1 {
  width: 500px;
}
```

#### Compila a:
```css
.part-1 {
  width: 500px;
}
```

## Tipos de datos
- numbers (e.g. `1.2`, `13`, `10px`)
- strings of text, with and without quotes (e.g. `"foo"`, `'bar'`, `baz`)
- colors (e.g. `blue`, `#04a3f9`, `rgba(255, 0, 0, 0.5)`)
- booleans (e.g. `true`, `false`)
- nulls (e.g. `null`)
- lists of values, separated by spaces or commas (e.g. `1.5em 1em 0 2em, Helvetica, Arial, sans-serif`)
- maps (e.g. `(key1: value1, key2: value2)`)

## Operaciones
- Numéricas
- Color
- Strings
- Booleanas

**Nota:** Todos los tipos de datos soportan los operadores de igualdad (== and !=).

#### Numéricas
- Suma +
- Resta -
- Multiplicación *
- División /
- Modulo %

**Nota:** Existen casos especiales respecto a las restas y a las divisiones. **[más detalles aquí](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#division-and-slash)**

#### Color
Mismas operaciones que en el caso de las numéricas, pero por partes (r/g/b)

#### Strings
- Concatenación +
**Nota:** Si una variable con comillas se concatena a otra sin comillas, el resultado tendra comillas, si es tan en el órden opuesto el resultado **no** tendrá comillas.

#### Booleanas
- and
- or
- not

## Funciones "predefinidas"

#### Este código:
```scss
p {
  color: hsl(0, 100%, 50%);
}
// O el siguiente equivalente con argumentos explícitos
// p {
//  color: hsl($hue: 0, $saturation: 100%, $lightness: 50%);
// }

```

#### Compila a:
````css
p {
  color: #ff0000; }
```

**[Lista de funciones "predefinidas"](http://sass-lang.com/documentation/Sass/Script/Functions.html)**

## Condicionales
- if()

```scss
if(true, 1px, 2px) => 1px
if(false, 1px, 2px) => 2px
```
- @if (y @else if / @else)
- @for
- @each
- @hwhile

## Mixins
Se usan `@mixin` e `@include`

## Funciones "propias"
Se usa `@function`
