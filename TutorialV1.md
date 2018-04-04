<h1>Expo Angular:</h1>

A continuación verán los pasos para crear una sencilla aplicacion en Angular.<br>
<code>curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash</code>
1. Instalar nvm: <code>nvm install 8.10.0</code>
2. Instalar npm: <code>sudo npm install -g npm</code>
3. Instalar el CLI de Angular:
    <code>npm install -g @angular/cli</code> 
4. Crear nueva aplicación:
    <code>ng new nggallery</code>
5. Ejecutaar el comando  <code>ng serve -o</code> en el directorio de la app para iniciar un servidor http localmente y visualizar la aplicación.<br>
       O <code>ng serve --host $IP --port $PORT --public $C9_HOSTNAME</code>
 
6. Vincular Bootstrap con la aplicación para el esttilo:<br>

Vamos al archivo /src/index.html

<code>

    <!doctype html>
    <html lang="en">
        <head>
            <meta charset="utf-8">
            <title>Nggallery</title>
            <base href="/">
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <link rel="icon" type="image/x-icon" href="favicon.ico">
        </head>
        <body>
            <app-root></app-root>
        </body>
    </html>
</code>

Y añadimos esta linea al head<br>
<code>
    &lt;link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
</code>

<code>
    &lt;link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" rel="stylesheet" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
</code>
Asi:<br>
<code>

    <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Nggallery</title>
      <base href="/">
      <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous"> 
      <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" rel="stylesheet" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <link rel="icon" type="image/x-icon" href="favicon.ico">
    </head>
    <body>
      <app-root></app-root>
    </body>
    </html>
</code>

<h2>Componente</h2>
<p>La aplicación recien creada se inicializa con un componente, en /nggallery/src/app/app.component.ts</p>
<code>

    import { Component } from '@angular/core';
    @Component({
        selector: 'app-root',
        //template: `<h1>{{ title }}</h1>` (in line)
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css']
    })

    export class AppComponent {
    title = 'app';
    }
 </code>

7. Creamos un nuevo componente con el comando: <code>ng generate component nombre-componente</code>

<p>
Vamos a cear una barra de navegación, usando un componente: <code>ng g c navbar -is --flat</code> <br>
Los flag y las abreviaciones son parte de la sintaxis de Angular.<br>
-is (inline style): crea un componente sin un archivo css, para poner los estilos en una linea del archivo .ts<br>
--flat: Crea los archivos del componente en el directorio donde se ejecutó el comando, sin crear una nueva carpeta.</p>

Angular crea el omponente con una estructura muy similar al app.component.ts, pero sin su propia carpeta ni un archivo .css<br>

8. Abrimos el archivo /src/app/navbar.component.html.<br>

<code>

    <p>
        navbar works!
    </p>
</code>

Y lo cambiamos por<br>

<code>

    <nav class="navbar navbar-default">
      <div class="container-fluid">
        <!-- Brand and toggle get grouped for better mobile display -->
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse"
                  data-target="#bs-example-navbar-collapse-1">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <a class="navbar-brand" href="#">Ejemplo Angular</a>
        </div>

    <!-- Navbar Right -->
    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
      <ul class="nav navbar-nav navbar-right">
        <li class="active"><a href="/">Inicio</a></li>
        <li><a href="/about">Sobre</a></li>
        <li><a href="/contact">Contactar</a></li>
        <li class="dropdown">
          <a class="dropdown-toggle" data-toggle="dropdown" role="button" aria-expanded="false">Miembros
            <span class="caret"></span></a>
          <ul class="dropdown-menu" role="menu">
            <li><a href="/register">Registrar</a></li>
            <li><a href="/login">Login</a></li>
          </ul>
        </li>
      </ul>
    </div>
    </div>
    </nav>
</code>

Que es una plantilla de bootstrap de una barra de navegación. Con esto ya se ha creado la navbar, pero no se ve en la aplicación.
Esto es porque debemos editar el componente principal /src/app/app.component.html , añadiendole el selector de la navbar.

9. Cambiamos el contenido del componente principal por el selector <code><app-navbar></app-navbar></code> en /src/app/app.component.html<br>
Y con esto ya se debería ver la Navbar en la aplicación.<br>
10. Creamos un nuevo componente para la galerias con <code>ng g c gallery</code><br>
Con esto tenemos un nuevo componente "gallery" en una nueva carpeta. Nos dirigimos a la plantilla /src/app/gallery/gallery.component.html , y la cambiamos por:<br>

<code>

    <div class="container">
      <div class="row">
        <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa1.jpg" /></div></a>
        <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa2.jpg" /></div></a>
        <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa3.jpg" /></div></a>
        <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa4.jpg" /></div></a>
        </div>
        <div class="row">
         <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa5.jpg" /></div></a>      
        <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa6.jpg" /></div></a>
        <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa7.jpg" /></div></a>
        <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa8.jpg" /></div></a>
      </div>
    </div>
</code>

Que no es más que un contenedor de bootstrap con las direcciones de unas imágenes

11. Editamos la hoja de estilos de gallery en /src/app/gallery/gallery.component.css con:<br>

<code>

    img {
    -webkit-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.75);
    -moz-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.75);
     box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.75);
    margin-bottom:10px;
    }

    img:hover {
    filter: gray; /* IE6-9 */
    -webkit-filter: grayscale(1); /* Google Chrome, Safari 6+ & Opera 15+ */
    }
</code>

Que son sombras, bordes y un efecto para cuando el cursor esté sobre la imágen.<br>

12. Para que este componente se despliegue en nuestra app, debemos añadir su selector (<app-gallery>) al componente principal en /src/app/app.component.html<br>

Hasta aquí tendremos una primera versión, pero que incumple con todas las buenas prácticas de desarrollo en Angular.<br>
A continuación separaremos en componente gallery en dos componentes <strong>Hijos</strong>

13. Para crear un componente hijo de gallery, nos ubicamos en la carpeta del componente <code>cd src/app/gallery</code> y generamos un nuevo componente <code>ng g c image-list -is</code>
14. Creamos un nuevo omponente hijo de este último, para esto nos ubicamos en la arpeta del componente <code>cd image-list</code> y creamos el componente <code>ng g c image -is --flat</code>
15. Antes de editar estos componentes crearemos un <Strong>Modelo</Strong> (O clase) imagen, que nos servirá después para crear todos los objetos de tipo "imagen" que vayamos a necesitar.
Nos ubicamos en la carpeta de la aplicación /src/app , y creamos un directorio para los modelos(o clases) <code>mkdir models</code> y nos situamos dentro de este <code>cd models</code>
y aquí ejecutamos el comando <code>ng g class image</code>. Esto nos generará un archivo image.ts, que será la clase iágen.
16. Cambiamos el archivo /src/app/models/image.ts con:<br>

<code>

    export class Image {
      constructor(public id:string, public title:string,
      public description:string, public thumbnail:string, public imageLink:string) {
        }
    }
</code>
Que no es más que una clase imágen con su contructor, el cual recibe cinco atributos:
- id
- título
- descripción
- la propia imágen 
- la dirección de la imágen<br>
Y así ya tendremos el modelo image creado y ya podemos ir a editar los componentes anidados que creamos
17. Lo que haremos ahora es separar la lógica y el contenido; vamos al archivo <code>gallery.component.html</code> y cortamos su contenido completo, 
para pegarlo en la plantilla del componente <code>image-list.component.html</code> y en <code>gallery.component.html</code> solo dejamos el selector
de image-list <code><app-image-list></app-image-list></code>
18. Después de esto tomamos todos los enlaces que están en <code>image-list.component.html</code> y los pegamos en <code>image.component.html</code> y en 
<code>image-list.component.html</code> dejamos el selector de image: <code><app-image></app-image></code>
19. Despues de hacer esto las imagenes se verán pero sin los estilos, esto es porque el codigo ya no está dentro de gallery.component, para que los estilos vuelvan
hay que escribirlos bien en image.componen.css o bien inLine en image.component.ts.<br>
Así, después de estoos pasos deberemos tener:<br>

<code>image.component.html</code>:<br>

<code>

    <div class="row">
    <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa1.jpg" /></div></a>
    <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa2.jpg" /></div></a>
    <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa3.jpg" /></div></a>
    <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa4.jpg" /></div></a>
    </div>
    <div class="row">
    <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa5.jpg" /></div></a>      
    <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa6.jpg" /></div></a>
    <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa7.jpg" /></div></a>
    <a href="#"><div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="https://videotutoriales.com/maspa/maspa8.jpg" /></div></a>
    </div>
</code><br>

<code>image-list.component.html</code>:<br>

<code>

    <div class="container">
    <app-image></app-image>
</div>
</code><br>

<code>galley.component.html</code>:<br>

<code>

    <app-image-list></app-image-list>
</code><br>
Y para los estilos el <code>image.component.ts</code>

<code>

    import { Component, OnInit } from '@angular/core';

        @Component({
          selector: 'app-image',
          templateUrl: './image.component.html',
          styles: [`img {
          -webkit-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.75);
          -moz-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.75);
          box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.75);
          margin-bottom:10px;
        }
        
        img:hover {
          filter: gray; /* IE6-9 */
          -webkit-filter: grayscale(1); /* Google Chrome, Safari 6+ & Opera 15+ */
        }
        `]
        })
        export class ImageComponent implements OnInit {
        
          constructor() { }
        
          ngOnInit() {
          }
        
        }

</code><br>

