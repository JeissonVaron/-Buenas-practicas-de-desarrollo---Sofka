# Buenas practicas de desarrollo

## Contenido
  1. [Introducción](#introducción)
  2. [Código limpio en javascript](#código-limpio-en-javascript)
  3. [Buenas practicas en Angular](#buenas-practicas-en-angular)
  4. [Código seguro en Angular](#código-seguro-en-angular)
  5. [Buenas practicas en React](#buenas-practicas-en-react)
  6. [Referencias](#referencias)

## Introducción

Las buenas prácticas para el desarrollo de software, son una compilación de métodos o técnicas que permiten llevar a cabo de manera óptima el conjunto de actividades que comprenden el desarrollo de un sistema de información.

![](https://lvivity.com/wp-content/uploads/2021/04/qc3.jpg)

### **¿Por qué necesitamos un buen código?**

Aunque es el compilador el que ejecuta cualquier programa de computadora, el código de software está escrito por personas y para personas, es por una razón que los lenguajes de programación de alto nivel tienen una sintaxis y comandos amigables para los humanos.

Este enfoque del desarrollo impone serios requisitos a la calidad del código, en particular a su legibilidad y comprensibilidad.

El principio rector es que un buen código es fácil de leer. Es lo más importante. Si una persona nueva lee un código y comprende bien de qué se trata, ese es un buen código.

## Código limpio en javascript

- [clean-code-javascript-es](https://github.com/andersontr15/clean-code-javascript-es)

## Buenas practicas en Angular

  1. Estructura de la aplicación

      El nivel de complejidad de la aplicación va a requerir mejor organización. Tener una estructura bien definida nos ayudará a pensar en escalabilidad.

      ![Estructura de la aplicación en Angular](https://miro.medium.com/max/622/1*Bso0b-u_AVGi_4x5CbpFfQ.png).

  2. Enrutamiento

      Para evitar posibles problemas de rendimiento en la carga de la aplicación, se hará uso del patrón carga diferida (Lazy-Loading (opens new window)), capacidad incorporada en Angular y que permite aplazar la carga de una parte particular de la aplicación hasta que sea realmente necesaria.

      Basta con definir correctamente las rutas de los módulos, para que apunte a un archivo de módulo que será cargado sólo cuando sea realmente necesario.

      ```
          const routes: Routes = [
          {
            path: 'feature1',
            loadChildren: () => import('./feature1/feature1.module').then(m => m.Feature1Module),
            canActivate: [AuthGuardService]
          },
          {
            path: 'feature2',
            loadChildren: () => import('./feature2/feature2.module').then(m => m.Feature2Module),
            pathMatch: 'full'
          },
          ...
        ```

  3. Aliases para la aplicación y entorno

      - Usar un alias para las carpetas y entornos de nuestra aplicación nos permitirá realizar importaciones de una manera más limpia y consistente a lo largo de la evolución de nuestra aplicación.
    
      ```
        import { AuthService } from '../../../.../core/services/auth.service';

        [vs]

        import { AuthService } from '@app/core';
      ```

  4. Compilación manual para producción

      Dadas las limitaciones de compilación para producción ofrecidas de manera predeterminada por Angular CLI en el archivo package.json, debemos hacer una pequeña personalización en dicho archivo para poder disponer de la posibilidad de compilar la aplicación con opciones específicas para su integración en producción.

      - ```
          {
            ...
            "scripts": {
              ...
              "build:prod": "ng build --prod --build-optimizer",
              ...
            }
            ...
          }
        ```

## Código seguro en Angular

- [Seguridad en Angular](https://runebook.dev/es/docs/angular/guide/security)

## Buenas practicas en React

  1. Estructura ordenadamente tus carpetas para que cualquiera entienda el proyecto
  2. Diseña componentes simples, reusables y de única responsabilidad

      React es muy flexible y los desarrolladores pueden crear componentes guiados por su imaginación, pero cuando esa flexibilidad se descontrola, empieza a jugar en contra de los principios de ingeniería aplicados al código.
  3. Don’t Repeat Yourself o DRY

      Esta buena práctica trasciende todas las barreras de la programación, aplica para cualquier aplicación en la actualidad pero nunca está de más recordarla.

      Es la regla en la que debes pensar siempre que estas a punto de `copiar y pegar` el código, copiarlo y pegarlo de StackOverflow no tiene nada de malo pero si ya tienes una porción de tú código que cumple la función que necesitas mejor intenta reutilizar lo que ya existe.

      ```
        const youtubers = [
          {nombre: "Luisito Comunica", contenido: "Viajes"}
          {nombre: "Jaime Altozano", contenido: "Musica"}
        ]

        // youtubers también puede llegar como props a este componente

        return (
          <div>
            {
              youtubers.map( (youtuber) => {
                return (
                  <Channel
                    nombre={youtuber.nombre}
                    contenido={youtuber.contenido}
                  />
                );
              } )
            }
          </div>
        );
      ```

  4. Todos los archivos relacionados a un componente deben estar en la misma carpeta

      ```
        components/header/index.js // exportar
        components/header/header.jsx // logica
        components/header/style.scss // estilos
        components/header/header.test.js // test
        components/header/useHeader.js // hooks
        ...
      ```

  5. Nombra tus componentes por lo que hacen

      `<ImagenAyuda ...props />`
  6. Debe ser testeable

      ![React Test](https://miro.medium.com/max/1072/1*aRU0itvptPQIGVKxUHj9Bg.png)

  7. Utilizar linters y tooling

      - ESLint - Analiza el código semanticamente y alerta si hay errores comunes.
      - Prettier - Formatea el código.
      - HTML Tidy - Corrector de HTML.
      - StyleLint - Linter de CSS

## Referencias

1. [WHAT IS BAD CODE, WHY IT IS DANGEROUS, AND HOW TO WRITE GOOD CODE](https://lvivity.com/how-to-write-good-code)
2. [clean-code-javascript-es](https://github.com/andersontr15/clean-code-javascript-es)
3. [Buenas prácticas en Angula](https://medium.com/angular-chile/buenas-pr%C3%A1cticas-en-angular-74663897c059)
4. [Arquitectura y buenas prácticas para una aplicación basada en Angular | Rafael Neto](https://rneto.es/blog/arquitectura-buenas-practicas-angular/#compilacion-manual-para-produccion)
5. [Angular Security](https://runebook.dev/es/docs/angular/guide/security#content-security-policy)
6. [10 buenas practicas que debes seguir con Reactjs en 2020](https://www.enbonnet.me/post/10-buenas-practicas-que-debes-seguir-con-reactjs-en-2020)
