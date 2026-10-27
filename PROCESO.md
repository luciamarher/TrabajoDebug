# PROCESO.md

---

#### Paso 1: Creación de estructura de carpetas de trabajo

Antes de nada, hemos repartido la realización del trabajo entre todos los integrantes de la siguiente manera:

- Mario y Argenis: Realización, documentación de la skill propia.
- Lucía: Aplicación y documentación de skill pública.
- Rubén: Documentación del [proceso.md](http://proceso.md).

Hemos utilizado en esta caso el Copilot integrado en Visual para que automáticamente nos cree en local la estructura de directorios que vamos a usar para realizar el trabajo:

repositorio/
├── [README.md](http://readme.md/)
├── index.html
├── [PROCESO.md](http://proceso.md/)
├── conversaciones-ia/
├── evidencias/
│   ├── [fuentes.md](http://fuentes.md/)
│   ├── [skill-publica.md](http://skill-publica.md/)
│   └── [prueba-skill-propia.md](http://prueba-skill-propia.md/)
└── skills/
└── nombre-skill/
└── [SKILL.md](http://skill.md/)

El prompt es el siguiente:

> “*Creame en esta carpeta esta estructura para el repositorio. La carpeta repositorio es TrabajoDebug*”
> 

#### Paso 2: Elección del contenido para la web

Necesitamos que se cumplan los siguientes requisitos:

- Una introducción breve al tema y a su utilidad.
- Entre **5 y 7 ideas clave**, explicadas con palabras propias.
- Un glosario de al menos 5 términos.
- Una demostración, ejemplo práctico o diagrama relacionado con el tema.
- Las fuentes utilizadas, identificadas mediante enlaces o referencias claras.

También que la web debe ser clara, navegable y legible tanto en ordenador como en una pantalla estrecha.

Para ello, hemos utilizado la misma IA para obtener asesoramiento sobre qué contenido del tema escoger para la web. De este modo, sabremos cuáles son los puntos clave en los que nos deberíamos enfocar. El prompt es el siguiente:

> “*En base a los apuntes de debug y lo que tiene que incluir la web, elige el contenido mas importante de los apuntes cumpliendo con lo que debe incluir la web*”
> 

El contenido que ha elegido es el siguiente:

- Introducción breve sobre la utilidad del debugging.
- 6 ideas clave:
    1. Qué es un depurador.
    2. Inicio de sesiones con `F5`, `launch` y `attach`.
    3. Breakpoints.
    4. Control paso a paso con `F5`, `F10` y `F11`.
    5. Variables, Watch, Call Stack y Debug Console.
    6. Estrategia sistemática para localizar errores.
- Demostración interactiva del error `i <= notas.length`.
- Flujo de depuración en cinco pasos.
- Glosario con 6 términos.

Además, con este prompt nos creó directamente el `index.html` de la web. 

#### Paso 3: Modificación del frontend con skill pública

Al ver que el resultado era bastante bueno, decidimos quedarnos con el código de la página pero decidimos entre todos aplicar una skill pública para modificar el diseño del frontend.

La skill seleccionada se puede encontrar en la siguiente dirección:

[design-taste-frontend — leonxlnx/taste-skill](https://www.skills.sh/leonxlnx/taste-skill/design-taste-frontend)

Para instalarla hemos necesitado seguir los siguientes pasos:

1. Instalar GitHub en Windows.
2. Desde cmd, ir a la ruta del repositorio y ejecutar el siguiente comando:

```bash
npx skills add https://github.com/leonxlnx/taste-skill --skill design-taste-frontend
```

Una vez instalada, le hemos dado la instrucción a la IA para que la aplique a lo que ya teníamos:

> “*Usa la skill `design-taste-frontend` para modificar el frontend de la pagina sin cambiar el contenido*”
>También le pedimos que nos documentara lo realizado con la skill pública en el archivo `skill-publica.md` con el siguiente prompt:
>  “*Documenta en skill-publica la skill design-taste-frontend que hemos utilizado para el frontend siguiendo las indicaciones*”
