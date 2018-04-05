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
En este punto la aplicación sigue funcionando mostrando las imágenes y sigue mejor la metodología de Angular, pero ahora usaremos una mejor manera de almacenar nuestras imagenes
esto lo vamos a hacer utilizando el modelo (clase) image para crear estas imágenes.<br>
20. Primero vamos a /src/app/image-list.component.ts  y en la primera linea, donde están los import, añadimos <i><code>Input</code></i>.<br>
<code>import { Component, OnInit, Input} from '@angular/core';
</code><br>
@Input es otro decoradorque tambien está en la libreria Core de angular y permite la comunicación entre componentes
21. En el mismo archivo añadimos otro import, para importar el modelo imágen:<br>
<code>import {Image} from '../../models/image'</code><br>
Con esto ya tenemos el Modelo dentro del componente image-list, y lo podemos usar.
22. En el mismo archivo ubicamos la zona del <i>export</i> y allí declaramos nuestra primera imágen:<br>

<code>

    export class ImageListComponent implements OnInit {
    image = new Image ('1', 'Primera Imagen', 'Descripción primera imagen','https://videotutoriales.com/maspa/maspa1.jpg','https://videotutoriales.com/maspa/maspa1-1.jpg');
    constructor() { }

    ngOnInit() {
        }
    }
</code>

Para que se muestres esta imagen desde aquí y no como lo veníamos haciendo debemos ir al archivo <i>image-list.component.html</i>
y añadir al selector de image un input binding como este <code><app-image [image]="image"></app-image></code> <br>
Lo que hacemos aqui, con los <<[ ]>> es permitir el paso de datos de un componente a un componente hijo (<i>image-list</i> a <i>image</i>)<br>
23. Ahora vamos a editar el omponente image en <i>image.component.ts</i>, añadimos tambien el <i>input</i> al <i>import</i> e importamos el modelo image
<br><code>
import { Component, OnInit, Input} from '@angular/core';<br>
import {Image} from '../../models/image'
</code>
24. Aqui mismo, en el export (la clase) añadimos <code>@Input() image: Image</code>
Utilizamos el decorador <i>@inpput</i> para decirle a un componente que tome un input de otro componente, en este caso
<i>image</i> toma input del componente <i>image-list</i> y le indicamos que lo que tiene que tomar son los objetos de tipo image.<br>
25. Con esto ya podemos acceder a la imagen que queremos mostrar en la vista de <i>image.component.html</i>, para esto nos vamos a ese archivo y
remplazamos su contenido por:

<code>

    <a href="#">
        <div class="col-md-3 col-sm-4 col-xs-6"><img class="img-responsive" src="{{image.thumbnail}}" /></div>
    </a>
</code><br>
Aqui usamos la notación << {{ }} >> (Template binding) para que muestre el enlace a la miniatura de la imagen, sin tener que volverlo a escribir.
<br> Si abrimos la aplicación después de hacer esto se debe ver solo una imágen, esto es porque solo hemos creado una.<br>
26. Lo que sigue es cambiar esa únia imágen por una lista de imágenes. Vamos al archivo <i>image-list.component.ts</i> que es donde creamos el 
objeto image, entonces sustituimos la declaración de este objeto image por:<br>

<code>

    images: Image[] = [
       new Image ('1', 'Primera Imagen', 'Descripción Primera imagen', 'https://videotutoriales.com/maspa/maspa1.jpg', 'https://videotutoriales.com/maspa/maspa1-1.jpg'),
       new Image ('2', 'Segunda Imagen', 'Descripción Segunda imagen', 'https://videotutoriales.com/maspa/maspa2.jpg', 'https://videotutoriales.com/maspa/maspa2-1.jpg'),
       new Image ('3', 'Tercera Imagen', 'Descripción Tercera imagen', 'https://videotutoriales.com/maspa/maspa3.jpg', 'https://videotutoriales.com/maspa/maspa3-1.jpg'),
       new Image ('4', 'Cuarta Imagen', 'Descripción Cuarta imagen', 'https://videotutoriales.com/maspa/maspa5.jpg', 'https://videotutoriales.com/maspa/maspa5-1.jpg'),
       new Image ('5', 'Quinta Imagen', 'Descripción Quinta imagen', 'https://videotutoriales.com/maspa/maspa4.jpg', 'https://videotutoriales.com/maspa/maspa4-1.jpg'),
       new Image ('6', 'Sexta Imagen', 'Descripción Sexta imagen', 'https://videotutoriales.com/maspa/maspa6.jpg', 'https://videotutoriales.com/maspa/maspa6-1.jpg'),
       new Image ('7', 'Séptima Imagen', 'Descripción Séptima imagen', 'https://videotutoriales.com/maspa/maspa7.jpg', 'https://videotutoriales.com/maspa/maspa7-1.jpg'),
       new Image ('8', 'Octava Imagen', 'Descripción Octava  imagen', 'https://videotutoriales.com/maspa/maspa8.jpg', 'https://videotutoriales.com/maspa/maspa8-1.jpg'),
       ];    
</code><br>

Esto es un array de imágenes, ahora vamos a actualizar la plantilla.
27. Vamos a la plantilla <i>image-list.component.html</i> y ubicamos el selector <i><app-image></i> y cambiamos su contenido por
<code> <app-image *ngFor="let image of images" [image]="image"></app-image> </code><br>
Donde usamos la directiva *ngFor para iterar sobre la lista de imágenes (igual que un for), lo que le decimos a Angular es que itere dentro del tag <i><app-image></i>
y para cada 'image' del arreglo 'images' haga lo que hacía cuando solo era una imágen.<br>
En este punto la aplicación debe verse como se veía otra vez.<br>

Siguiendo el MVC no es correcto que un componente no debe encargarse de crear las imágenes, para solucionarlo lo que haremos será crear un service
<h3>Service</h3>
28. Creamos un directorio <code>mkdir services</code> en la raiz de la app <i>/src/app</i> y nos situamos en el <code>cd services</code> para crear el servicio ejecutamos: 
<code>ng g s image</code>
29. Para poder consumir este servicio debemos proveerlo, esto lo hacemos añadiendolo al arreglo <i>providers</i> en <i>/src/app/app.module.ts</i>

<code>

    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';

    import {ImageService} from './services/image.service';

    import { AppComponent } from './app.component';
    import { NavbarComponent } from './navbar.component';
    import { GalleryComponent } from './gallery/gallery.component';
    import { ImageListComponent } from './gallery/image-list/image-list.component';
    import { ImageComponent } from './gallery/image-list/image.component';
    @NgModule({
      declarations: [
        AppComponent,
        NavbarComponent,
        GalleryComponent,
        ImageListComponent,
        ImageComponent
      ],
      imports: [
        BrowserModule
      ],
      providers: [ImageService],
      bootstrap: [AppComponent]
    })
    export class AppModule { }
    
</code><br>
30. Lo que sigue es pasar la creación de las imagenes de <i>image-list</i> a el nuevo servicio, importamos entonces en <i>image.service.ts</i>
31. el modelo image y cortamos el arreglo generador de imágenes a la clase <i>ImageService</i>:<br>

<code>

    import { Injectable } from '@angular/core';
    import {Image} from '../models/image';
    @Injectable()
    export class ImageService {
    	images: Image[] = [
           new Image ('1', 'Primera Imagen', 'Descripción Primera imagen', 'https://videotutoriales.com/maspa/maspa1.jpg', 'https://videotutoriales.com/maspa/maspa1-1.jpg'),
           new Image ('2', 'Segunda Imagen', 'Descripción Segunda imagen', 'https://videotutoriales.com/maspa/maspa2.jpg', 'https://videotutoriales.com/maspa/maspa2-1.jpg'),
           new Image ('3', 'Tercera Imagen', 'Descripción Tercera imagen', 'https://videotutoriales.com/maspa/maspa3.jpg', 'https://videotutoriales.com/maspa/maspa3-1.jpg'),
           new Image ('4', 'Cuarta Imagen', 'Descripción Cuarta imagen', 'https://videotutoriales.com/maspa/maspa5.jpg', 'https://videotutoriales.com/maspa/maspa5-1.jpg'),
           new Image ('5', 'Quinta Imagen', 'Descripción Quinta imagen', 'https://videotutoriales.com/maspa/maspa4.jpg', 'https://videotutoriales.com/maspa/maspa4-1.jpg'),
           new Image ('6', 'Sexta Imagen', 'Descripción Sexta imagen', 'https://videotutoriales.com/maspa/maspa6.jpg', 'https://videotutoriales.com/maspa/maspa6-1.jpg'),
           new Image ('7', 'Séptima Imagen', 'Descripción Séptima imagen', 'https://videotutoriales.com/maspa/maspa7.jpg', 'https://videotutoriales.com/maspa/maspa7-1.jpg'),
           new Image ('8', 'Octava Imagen', 'Descripción Octava  imagen', 'https://videotutoriales.com/maspa/maspa8.jpg', 'https://videotutoriales.com/maspa/maspa8-1.jpg'),
           ];    

      constructor() { }
    }
</code><br>
El decorados @Injectable se usa para poder "inyectar" el servicio a cualquier componente.

32. Y para pedir las imagenes añadimos una funcipon abajo del constructor:<br> 
<code>getImages() {<br>
    return this.images;<br>
  }</code><br>

33. Con el servicio listo para ser consumido, vamos a <i>image-list.component.ts</i> e importapos el servicio<br>
<code>import {ImageService} from '../../services/image.service';</code><br>
En donde estaba el arreglo de las imagenes dejamos un arreglo vacío: <code>images: Image[] = [];</code><br>
Y llamamos al servicio en ngOnInit con <code>this.images = this.imageService.getImages();</code>, despues de haberlo declarado en el constructor:<br>
<code>constructor(private imageService:ImageService) { }</code>.<br>
El archivo <i>image-list.component.ts</i> final debe verse así:

<code>

    import { Component, OnInit, Input } from '@angular/core';
    import { Image } from '../../models/image';
    import {ImageService} from '../../services/image.service';
    @Component({
      selector: 'app-image-list',
      templateUrl: './image-list.component.html',
      styles: []
    })
    export class ImageListComponent implements OnInit {
       images: Image[] = [];  

      constructor(private imageService:ImageService) { }

      ngOnInit() {
        this.images = this.imageService.getImages();
      }
    }

</code>
34. Ahora vamos a hacer interactiva la galeria, para esto necesitamos otro componente, hijo de gallery. Nos ubicamos en gallery <code>cd src/app/gallery</code>
y creamos el nuevo componente <code>ng g c image-detail</code>
35. Vamos al archivo image-list.component.html y le agregamos un evento de click al selector <i><app-image></i>: 
<code><app-image *ngFor="let image of images" [image]="image" (click)="onSelect(image)"></app-image></code><br>
36. Ahora crearemos el método onSelected(). Vamoas al archivo <i>image-list.component.ts</i> y en el <i>export</i> bajo el array <i>image</i>
agregamos <code>selectedImage: Image;</code>, y en la zona de las funciones, abajo de <i>ngOnInit</i> añadimos la funcion: <br>
<code>onSelect(image: Image) {<br>
  this.selectedImage = image;<br>
}</code><br>
37. Ahora que al hacer click si se selecciona una imágen, ya la podemos enviar al nuevo componente que creamos y para que este sea visible 
ubicamos su selector,<br> <code><app-image-detail [selectedImage]="selectedImage"></app-image-detail></code>, en la parte superior del archivo <i>image-list.component.html</i>
38. Nos vamos al <i>image-detail.component.ts</i>, importamos el input y el modelo image<br>
<code>
import { Component, OnInit, Input } from '@angular/core';<br>
import { Image } from '../../models/image';
</code><br>
Y en el export añadimos <code>@Input() selectedImage: Image;</code>
39. Ahora ya podemos configurar la plantilla <i>image-detail.component.html</i> asi:<br>

<code>

    <div *ngIf="selectedImage">
      <div class="container image-detail">
        <div class="row">
          <div class="col-sm-8 col-xs-12">
            <img [src]="selectedImage.imageLink" class="img-responsive">
          </div>
          <div class="col-sm-4 col-xs-12">
            <h1>{{selectedImage.title}}</h1>
            <p>{{selectedImage.description}}</p>
          </div>
        </div>
      </div>
    </div>
</code>
La directiva *ngIf se encarga de que la plantilla no se despliegue si no se tiene ninguna imágen selecionada.
40. Para terminar con esta pllantilla, le agregamos una propiedad de margen a sus estilos: <br>

<code>

    .image-detail {
      margin: 20px auto;
    }
</code>
<h3>Routing</h3>
41. Para generar las rutas vamos a hacer uso de otros dos componentes, entonces ejecutamos:<br>
<code>ng g c contact</code> y <code>ng g c about</code>.<br>
42. Las rutas se definen en el <i>app.module.ts</i>, primero importamos routes <code>import {Routes, RouterModule} from '@angular/router';</code> 
y luego sobre NGModule definimos otro arreglo con las rutas:

<code>

    const appRoutes: Routes = [
    { path: '', redirectTo:'/gallery', pathMatch: 'full'},
    { path: 'gallery', component: GalleryComponent},
    { path: 'contact', component: ContactComponent},
    { path: 'about', component: AboutComponent} 
    ];
</code><br>
En la parte final del archivo añadimos a los imports <code>RouterModule.forRoot(appRoutes),</code>
Una vez creadas ya podemos decirla a Angular que utilice ApppRoutespara determinar nuestras rutas 
Angular cuenta con una directiva <i><router-outlet></i> que un tag que indica donde serán reenderizados los contenidos de cada ruta
43. Vamos al archivo <i>app.component.html</i> y reemplazamos el selector de <<gallery>> con el de <<router-outler>><br>
Podemos ver que en la app se sigue viendo la galería, aunque el tan ya no está. Esto quiere decir que el sistema de enrutamiento esta fincionando bien.
<p>Tal como está ahora la aplicación recarga la página cada vez que cambia de ruta, esto desperdicia una de las mejores características
de Angular. Para cambiar esto Angular tiene una directiva de enrutamiento muy útil que permite enlazar a ortas rutas sin tener que 
recargar toda la página: <i>[routerLink]</i></p>
44. Vamos a la plantilla del navBar que es el componente que nos esta ayudando a movernos entre las rutas y cambiamos los enlaces html 
por enlaces con routerLink, a demás existe otra directiva <i>[routerLinkActive]</i> que nos dice si el enlace apunta a la ruta actual, con esta podemos darle
estilo a la navBar:<br>

<code>

    <li routerLinkActive="active"><a [routerLink]="['/gallery']">Inicio</a></li>
        <li routerLinkActive="active"><a [routerLink]="['/about']">Sobre</a></li>
        <li routerLinkActive="active"><a [routerLink]="['/contact']">Contactar</a></li>
</code>
Con este 'simple' cambio las rutas de la app estan arregladas y estilizadas.
45. Ahora tenemos un problema con las imágenes, todas estan sirviendo como links para la página principal y no se dejan ver. Para solucionar
esto vamos a <i>image.component.html</i> y eliminamos el tag 'href', despues de quitarlo funciona bien, pero el puntero no cambia cuando está
sobre las imágenes.. Esto se soluciona fácilmente añadiendo a la hoja de estilos:<br>

<code>
    a:hover{
        cursor:pointer
    }
</code>
