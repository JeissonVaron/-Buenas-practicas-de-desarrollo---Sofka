# Buenas practicas de desarrollo en React

## Contenido
  1. [Código limpio en javascript](#código-limpio-en-javascript) 
  2. [Buenas practicas en React](#buenas-practicas-en-react)
  3. [Referencias](#referencias)

## Código limpio en javascript

- [clean-code-javascript-es](https://github.com/andersontr15/clean-code-javascript-es)

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
3. [10 buenas practicas que debes seguir con Reactjs en 2020](https://www.enbonnet.me/post/10-buenas-practicas-que-debes-seguir-con-reactjs-en-2020)
