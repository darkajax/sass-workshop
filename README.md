# sass-workshop

### Temas
- Setting up
- Features
- Tips

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
- SassScript
  - Shell interactivo
  - Comments
  - Variables
    - Interpolación
  - Diferentes tipos de datos
  - Operaciones
  - Condicionales
  - Mixins
  - Funciones
- Nesting
  - Parent selector (`&`)
- Imports/Partials
- Placeholder selectors

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

### Operaciones

