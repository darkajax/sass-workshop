# sass-workshop

### Instalar Sass

```
sudo gem install sass
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

## Features
- 2 Tipos de sintaxis
- Shell interactivo
- Nesting
- Variables
- Imports/Partials
- Operaciones
- Mixins
- Funciones
- Placeholder selectors

## Sintaxis

![sass-vs-scss](/sass-vs-scss.jpg?raw=true "sass-vs-scss")

### Pros de Sass
- Más conciso (no {} ni ; además de usar + en lugar de @import por ejemplo), menos código
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
