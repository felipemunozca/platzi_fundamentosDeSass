# Curso de Fundamentos de Sass: Crea tu Primera Landing Page

## Índice
* [¿Cómo funcionan los preprocesadores? Ventajas de utilizar uno](#id2)
* [Anatomía de un proyecto de SASS](#id3)
* [Estructura de la hoja de estilos y variables](#id4)
* [Uso de selectores, scope de las variables y shadowing](#id5)
* [At Rules: CSS y nesting](#id7)
* [Expresiones: Literales y Operaciones](#id8)
* [¿Qué es la herencia y cómo funciona en SASS?](#id10)
* [¿Qué es un mixin en CSS?](#id13)
* [Creación de nuestras propias funciones](#id15)
* [Aprende a instalar y configurar Sass mediante Node.js](#id20)

------------

## ¿Cómo funcionan los preprocesadores? Ventajas de utilizar uno [2/25]<a name="id2"></a>
### ¿Cómo funcionan los preprocesadores?
Un preprocesador es una herramienta que nos permite escribir pseudocódigo recibiendo como parámetro de entrada los estilos que posteriormente serán convertidos a CSS nativo. Podemos decir que funcionan de manera similar a los traductores pues al indicarle una sintaxis devuelve los valores en una sintaxis nueva.
En SASS se incluyen características adicionales, como variables, mixins, herencia de clases, entre otras, que hacen que el proceso de escritura de CSS sea más fácil y rápido.

Para poder hacer uso de un preprocesador, primero es necesario entender cómo funcionan los estilos CSS y el navegador. Los estilos CSS son interpretados y representados por el navegador, el cual se encarga de leer el código CSS y aplicarlo a los elementos o componentes HTML de la página. Es el navegador quien recorre la hoja de estilos, línea por línea, y asigna propiedades a los elementos de la página según lo indicado en el código CSS. Este proceso es fundamental para permitir que la página se estilice de la manera deseada, teniendo control sobre el diseño y la disposición de la página, proporcionando al usuario una experiencia visual atractiva, donde todos los elementos están estilizados y presentados de una manera agradable a la vista y fácil de interactuar.

### Ventajas de utilizar un Preprocesador
Los principales beneficios de usar un preprocesador como SASS son la rapidez y la productividad. Permitiendo que el código se pueda escribir de manera mucho más rápida y sencilla, ayudando a los desarrolladores a ahorrar tiempo y ser más productivos. También hacen que el mantenimiento del código sea más fácil, pues todos los estilos se guardan en un solo archivo. La reutilización de código es otro de los beneficios que nos trae el uso de un preprocesador, esto significa que los mismos estilos se pueden aplicar en varias páginas sin tener que escribir el código una y otra vez.
Finalmente el uso de preprocesadores nos permite que sea mucho más sencillo trabajar una página web de manera responsiva.

### Tipos de Preprocesadores
**[Stylus]**
Stylus es un lenguaje de programación de hojas de estilo en cascada (CSS) que se compila en CSS estándar, está basado en JavaScript. Hay algunas diferencias importantes entre Stylus y SASS. La sintaxis de Stylus es más simple y clara, mientras que la sintaxis de SASS se considera más profesional y compleja. Stylus ofrece una mejor portabilidad y es más fácil de usar. Sin embargo, SASS ofrece mayor soporte al ser utilizado con una mayor cantidad de lenguajes de programación.

**LESS**
Una de las principales diferencias entre LESS y Sass es que Sass está codificado en Ruby y, por lo tanto, se procesa del lado del servidor, mientras que Less es una biblioteca de JavaScript (Como Stylus) y se procesa del lado del cliente. Un ejemplo es la forma en que ambos lenguajes manejan las variables es distinta. En LESS, los nombres de las variables se inicializan con @ y en Sass los nombres de las variables se inicializan con el símbolo $.

------------

## Anatomía de un proyecto de SASS [3/25]<a name="id3"></a>
### El proceso de compilado
Par hacer uso de Sass dentro de nuestro proyecto tenemos que tener en cuenta 3 puntos importantes que forman parte del proceso de compilación:
1. Archivo de entrada (input file).
2. Archivo de salida (output file).
3. Los comandos para ejecutar y compilar Sass.

### Input file
El archivo de entrada es donde vamos a escribir nuestros estilos haciendo uso de la sintaxis de Sass. Este archivo tendrá una extension .scss

### Output file
El archivo de salida es donde se colocaran los estilos finales con CSS nativo, que provienen directamente del archivo de entrada.
**IMPORTANTE**: nunca se debe editar directamente el archivo de salida, ya que al compilar se borraran los cambios.

### Recomendaciones:
Como un estándar de desarrollo para cualquier programador es saber separar los archivos en carpetas diferentes, por lo que se deben crear dos carpetas separadas llamadas:
+ css
+ scss

Ademas dentro de cada carpeta puedo crear un archivo correspondiente pudiendo llevar el mismo nombre ambos, para indicar que representan lo mismo:
+ main.css    (archivo de salida)
+ main.scss   (archivo de entrada)

### Instalación de Sass
#### Linea de comando
Utilizando la terminal de node.js se puede utilizar el comando:

`npm install -g sass`

para instalar una copia global, para comprobar si se instalo correctamente, nuevamente abrir la terminal y escribir el comando:

`sass --version`

Y una ves que se comience a crear código desde el archivo de entrada, se debe compilar dicho código para que se vea reflejado en el archivo de salido, en la consola debo escribir la ruta donde esta el archivo junto con el nombre de los archivos de entrada y salida, esto se logra con el comando:

`sass ruta/nombre_archivo.scss ruta/nombre_archivo.css`

Pero cada vez que realice un cambio en el archivo de entrada, tendré que ejecutar este comando, lo que se volverá tedioso, es por eso que se recomienda dejar al compilador corriendo en modo automático con el comando:

`sass --watch ruta/nombre_archivo.scss ruta/nombre_archivo.css`

#### Extension Live Sass Compiler
Es una extension de Visual Studio Code que nos permite trabajar con SASS de una manera sencilla, ademas de compilar los estilos en tiempo real sin la necesidad de ejecutar los comandos manualmente.

------------

## Estructura de la hoja de estilos y variables [4/25]<a name="id4"></a>
### Estructura de la hoja de estilos
Algunas declaraciones **(statements)** contienen bloques y se definen entre un par de llaves **{ }**, son separados mediante un punto y coma **;**

### Top-level statements
Son las declaraciones que solo se pueden utilizar en la parte superior de la hoja de estilos. Algunos ejemplos son:
+ imports
+ definición de un mixin
+ definición de una función
+ módulos

###Universal statements
Son las declaraciones que podemos utilizar en cualquier parte de la hoja de estilos. Algunos ejemplos son:
+ variables
+ estructuras de control
+ las reglas @error, @warm y @debug
+ declaraciones CSS: reglas de estilos, at-rules y mixins.

### Variables
Una variable es un espacio de memoria asignado unicamente para almacenar un dato.
Las variables pueden ser declaradas en cualquier parte de una hoja de estilos.
Para asignar un valor a una variable se hace uso del símbolo **$** de esta manera es posible hacer el llamado dentro de la hoja de estilos. Algunos ejemplos serian:
+ $primary-colo: blue;
+ $secondary-color: green;
+ $title-color: purple;

### Existen diferencias entre variables CSS y Sass
#### Las variables CSS
Pueden tener diferentes valores para distintos elementos.
Son declarativas.

#### Las variables Sass
Tienen un valor único correspondiente a un elemento.
Son imperativas.

### !default flag
Dentro de Sass existe una flag llamada !default la cual se encarga de asignar un valor a la variable si y solo si esa variable no esta definida o su valor es null.

------------

## Uso de selectores, scope de las variables y shadowing [5/25]<a name="id5"></a>
### Selectores
Un selector de CSS define sobre que elementos se aplicará un conjunto de reglas CSS.
Existen selectores de tipo:
+ clase
+ id 
+ tipo
+ atributo

### ¿Qué es el scope?
El scope dentro de Sass hace referencia al contexto en el que son declaradas las variables y donde es posible hacer uso de estas mismas.

### Variables locales
Están declaradas dentro de un bloque { }.
Cualquier selector anidado puede acceder a las variables locales declaradas dentro del selector.

### Variables globales
Por default, todas las variables declaradas fuera de un selector son globales, esto significa que se puede acceder a ellas en cualquier parte de nuestra hoja de estilos.

### Shadowing
Es un concepto de Sass que se significa que las variables locales y globales pueden tener el mismo nombre, ya que se encuentran en diferente nivel del scope.
Esto puede ayudar a que no se llegue a modificar por error el valor de las variables globales. 

### !global flag
En caso de querer modificar el valor global de una variable dentro del scope de una variable global, se hace uso de la flag !global.

------------

## At Rules: CSS y nesting [7/25]<a name="id7"></a>
### At-rules CSS
Es una declaración que cumple con diferentes funciones, se inicializa con el símbolo arroba **@** y cuenta con una sintaxis propia.
Las At-rules dentro de Sass ayudan a mantener la compatibilidad con próximas versiones de CSS.

### Ejemplos de At-rules CSS
+ @use: ayudar a importar; módulos, estilos y funciones de otras hojas de estilos. La diferencia con @import es que import se encarga de hacer los estilos globales.
+ @function: permite crear funciones personalizadas, sin embargo Sass cuenta con funciones ya existentes.
+ @forward: Recibe como parámetro una URL y nos ayuda a cargar los estilos de nuestra hoja de estilos, es muy importante hacer uso de @use para que los módulos estén disponibles en nuestra hoja de estilos.
+ @extend: tiene que ver con el concepto de herencia.
+ @at-root: se encarga de cargar nuestros estilos en el root del css.

### Reglas At-rules que tienen que ver con la compilación
+ @error: sucede cuando existe un error en la compilación.
+ @warn: alerta que indica que tenemos que cambiar algo en el código que no esta funcionando bien.
+ @debug: para encontrar los errores de una manera mas sencilla.
+ @include: nos ayuda a invocar los mixins.
+ @for, @if, @each, @while: tienen que ver con estructuras de control, se pueden usar dentro de una función.

### Nesting o anidación de selectores
La anidación nos permite tener selectores dentro de otros, lo cual nos ayuda a simplificar el código, escribiendo los selectores en el orden que aparecen en el HTML.

------------

## Expresiones: Literales y Operaciones [8/25]<a name="id8"></a>
### Definición de expresión
Una expresión es todo aquello que va del lado derecho de una variable, admitiendo varios tipos de valores.
Las expresiones son mucho más poderosas que los valores CSS simples, ya que se pasan como argumentos a mixins y funciones.
Ejemplos de expresiones literales 
+ Números.
+ Strings o cadenas de texto.
+ Colores que pueden estar en diferentes formatos, como rgb, hexadecimal.
+ Booleanos
+ Null
+ Listas
+ Mapas

------------

## ¿Qué es la herencia y cómo funciona en SASS? [10/25]<a name="id10"></a>
### ¿Qué es la herencia?
Es un mecanismo mediante el cual un selector puede recibir estilos CSS que vienen de variables utilizadas previamente.

### Uso de herencia en Sass
La directiva @extend de Sass nos permite organizar código y crear CSS mas limpio.
Un código ejemplo seria:
```css
.error {
		border: 1px #f00;
		background-color: #fdd;
}

&--serious {
		@extend .error;
		border-width: 3px;
}
```

------------

## ¿Qué es un mixin en CSS? [13/25]<a name="id13"></a>
Los mixins permiten definir estilos que se pueden reutilizar en toda la hoja de estilos y facilitan evitar el uso de clases no semánticas.

### Uso de mixins en Sass
Se declara con la regla @mixin seguido del nombre que queremos asignar y se invoca con @include seguido del nombre del mixin.

Código de ejemplo:
```css
@mixin horizontal-list {
		li {
			 display: inline-block;
			margin-left: 2px;
			margin-right: 2em;
		}
}

nav ul {
		 @include horizontal-list;
}
```

### Argumentos en mixins
Existen mixins mas complejos que reciben parámetros argumentos. Un argumento es el nombre de una variable que está separada por una coma.
La utilidad de los mixins no sería tal si no tuvieran la capacidad de recibir argumentos.
```css
@mixin circulo ($width, $height, $color) {
		width: $width;
		height: $height;
		background: $color;
}
```

------------

## Creación de nuestras propias funciones [15/25]<a name="id15"></a>
### Funciones en Sass
Las funciones permiten definir operaciones complejas en valores de Sass.
Las funciones se definen usando la regla @function.

### Ejemplos de funciones
Sass como pre-procesador tiene una gran cantidad de funciones. Algunos ejemplos son:
1. Funciones RGB
2. Funciones HSL
3. Funciones de opacidad
4. Funciones de strings
5. Funciones sobre números

### Operaciones 
Sass es compatible con una gran cantidad de operadores útiles para trabajar con diferentes valores. Estos incluyen los operadores matemáticos estándar y operadores para varios otros tipos, por ejemplo: == y !=

### Jerarquía de los operadores
1. Los operadores unarios: not, +, -
2. Operadores *, /, %
3. Operadores +, -
4. Operadores >, >=, <, <=
5. Operadores de comparación == y !=
6. El operador lógico and
7. El operador lógico or
8. El operador de asignación =

### Declaración de una función
Las funciones se llaman utilizando la sintaxis de función CSS normal.
```css
@function pow($base, $exponent) {
		$result: 1;
		@for $_ from 1 through $exponent {
				$result: $result * $base;
		}
		@return $result;
}

.sidebar {
		float: left;
		margin-left: pow(4, 3) * 1px;
}
```

------------

## Aprende a instalar y configurar Sass mediante Node.js [20/25]<a name="id20"></a>
### Instrucciones para instalar y configurar Sass mediante Node.js
1. Abre una terminal y navega hasta la carpeta raíz de tu proyecto. Asegúrate de tener Node.js instalado en tu sistema. Puedes verificarlo escribiendo node -v en la terminal. Si no lo tienes instalado, ve al sitio web oficial de Node -> [node.org/en](https://nodejs.org/en) para descargarlo e instalarlo.

2. Ejecuta el siguiente comando para instalar Sass a nivel global:

	`npm install -g sass`

3. Ahora que tienes Sass instalado a nivel global, puedes compilar tus archivos Sass en CSS con el siguiente comando en la terminal:

	`sass input.scss output.css`

4. Reemplaza **“input.scss”** con la ruta y el nombre de tu archivo Sass, y **“output.css”** con la ruta y el nombre de tu archivo CSS de salida. Por ejemplo:

	`sass styles/main.scss styles/main.css`

5. Si quieres compilar automáticamente tus archivos Sass en CSS cada vez que hagas cambios, puedes usar la opción - - watch:

	`sass --watch styles/main.scss styles/main.css`

6. Si estás utilizando Node.js en tu proyecto, también puedes usar un paquete de npm llamado sass para compilar tus archivos Sass en CSS. Para instalarlo, ejecuta el siguiente comando:

	`npm install sass`

7. En tu archivo de configuración de Node.js (como package.json) agrega un script para compilar tus archivos Sass en CSS. Por ejemplo:
```
"scripts": {
		"build:css": "sass input.scss output.css"
}
```
8. Ahora puedes ejecutar el script con el siguiente comando:

	`npm run build:css`

Eso es todo. Con estas instrucciones deberías poder instalar y configurar Sass en tu proyecto de Node.js.