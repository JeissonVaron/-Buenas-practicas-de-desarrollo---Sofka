# Buenas practicas de desarrollo en Angular

## Contenido
  1. [Código limpio en javascript](#código-limpio-en-javascript)
  2. [Buenas practicas en Angular](#buenas-practicas-en-angular)
  3. [Código seguro en Angular](#código-seguro-en-angular)
  4. [Formularios reactivos en Angular Platzi](#formularios-reactivos-en-angular-platzi)
  5. [Referencias](#referencias)

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

## Formularios reactivos en Angular [Platzi](https://platzi.com/blog/angular-reactive-forms/)

  Los formularios son muy, muy importantes, aunque pueden volverse algo complejos. Debes aprender a manejarlos profesionalmente para tener las validaciones adecuadas, integrar bien tus estilos, mostrar los errores de forma correcta y entendible, etc.

  Para esto Angular nos proporciona dos módulos para construir nuestros formularios: FormsModule para crear Template Driven Forms (formularios en plantillas) y ReactiveFormsModule para crear Reactive Forms (o formularios reactivos).
  
  Los Formularios Reactivos nos proveen de una manera de manejar las entradas de datos del usuario cuyos valores cambian en el tiempo. Cada cambio que ocurre en el formulario devuelve un nuevo estado, lo que ayuda a mantener la integridad del modelo entre cada cambio.
  ![](https://static.platzi.com/media/user_upload/image3-a4e0cbe3-3d59-4d75-ae70-24477ae1a37e.jpg)

  En este caso tenemos directivas como FormGroup y FormControlName para asociar la referencia de nuestro formulario al template, pero cada campo tiene asociado un ‘FormControl’ al cual podríamos especificar su estado inicial y, por supuesto, las validaciones.
  ![](https://static.platzi.com/media/user_upload/image2-4a5fa07b-b027-44f0-9016-4c08b47fbaa4.jpg)

  De esta forma podemos igualmente mostrar mensajes más apropiados al usuario de acuerdo al tipo de error y estado de este campo:
  ![](https://static.platzi.com/media/user_upload/image5-d64ebc62-a719-4839-a2f6-a5cd797ff469.jpg)

***FormGroup*** y ***FormControl*** nos dan un gran poder. En grandes rasgos, los ***Reactive Forms*** nos permiten crear formularios con código más limpio y mantenible gracias a características como:
1. Validaciones asíncronas
2. Validaciones personalizadas y grupales
3. Pruebas unitarias a formularios
4. Formularios y campos dinámicos
5. ¡Y muchas más!

## Referencias

1. [WHAT IS BAD CODE, WHY IT IS DANGEROUS, AND HOW TO WRITE GOOD CODE](https://lvivity.com/how-to-write-good-code)
2. [clean-code-javascript-es](https://github.com/andersontr15/clean-code-javascript-es)
3. [Buenas prácticas en Angula](https://medium.com/angular-chile/buenas-pr%C3%A1cticas-en-angular-74663897c059)
4. [Arquitectura y buenas prácticas para una aplicación basada en Angular | Rafael Neto](https://rneto.es/blog/arquitectura-buenas-practicas-angular/#compilacion-manual-para-produccion)
5. [Angular Security](https://runebook.dev/es/docs/angular/guide/security#content-security-policy)
6. [Cómo crear formularios locos en Angular: Reactive Forms vs. Template Driven Forms](https://platzi.com/blog/angular-reactive-forms/)