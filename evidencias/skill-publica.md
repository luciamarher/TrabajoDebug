# Skill pública: `design-taste-frontend`

## Nombre y fuente original

- **Nombre:** `design-taste-frontend`
- **Fuente original:** [GitHub - changemaner/design-taste-frontend](https://github.com/changemaner/design-taste-frontend)
- **Referencia alternativa:** [design-taste-frontend en Skills.sh](https://www.skills.sh/leonxlnx/taste-skill/design-taste-frontend)

La skill se presenta como una guía para crear o rediseñar interfaces frontend con una dirección visual intencionada y evitar diseños genéricos o repetitivos producidos por IA.

## Propósito

Su propósito es ayudar a planificar y mejorar la interfaz visual de una página web. Para ello propone:

- Partir del objetivo, el público y el contenido de la página antes de elegir estilos.
- Crear una identidad visual coherente, en lugar de combinar componentes sin criterio.
- Cuidar la jerarquía tipográfica, el color, el espaciado y la composición.
- Evitar patrones visuales repetidos o poco diferenciados.
- Revisar aspectos de responsive design, accesibilidad y estados de interacción.

La skill no sustituye la comprobación del contenido, la revisión de las fuentes ni las pruebas funcionales de la página.

## Tarea concreta para la que se diseñó

La utilizamos para rediseñar el frontend de la página didáctica sobre **depuración en Visual Studio Code**, manteniendo el contenido educativo y la demostración interactiva.

La tarea consistía en mejorar únicamente la presentación visual de [`index.html`](../index.html), sin modificar:

- Las seis ideas clave sobre debugging.
- El glosario.
- La demostración del error `i <= notas.length`.
- Los enlaces y las fuentes.
- La lógica de los botones `F10 · avanzar` y `Reiniciar`.

## Aplicación en este proyecto y resultado obtenido

Aplicamos la skill para revisar la dirección visual existente y realizar una mejora del frontend. Las decisiones principales fueron:

- Crear una identidad editorial y técnica, adecuada para una guía de programación.
- Usar una paleta basada en azul profundo, verde azulado y ámbar.
- Separar visualmente el contenido general de los fragmentos de código mediante tipografía monoespaciada.
- Reforzar la jerarquía del encabezado principal y de las secciones.
- Mejorar la navegación interna y los estados `hover`, `focus` y `disabled`.
- Organizar las ideas clave, el flujo de depuración y el glosario con una composición más clara.
- Mantener la adaptación a pantallas estrechas mediante reglas responsive.

El resultado fue una página más diferenciada y legible, sin cambiar el contenido didáctico ni el comportamiento de la demostración. Después del cambio se verificó que seguían presentes las seis ideas, los seis términos del glosario, las fuentes, la demostración y los controles interactivos.

## Límites, riesgos y aspectos revisados

La skill es una herramienta de apoyo al diseño, no una fuente de información técnica sobre Visual Studio Code. Revisamos estos aspectos:

- **Contenido:** no se aceptaron nuevas afirmaciones técnicas por el mero hecho de que una propuesta visual las sugiriera.
- **Funcionalidad:** se comprobó que los identificadores y el script de la demostración no fueran eliminados ni modificados accidentalmente.
- **Responsive design:** se conservaron las reglas para móvil y se revisó que la navegación y las columnas pudieran adaptarse.
- **Accesibilidad:** se mantuvieron el HTML semántico, los focos visibles, los textos alternativos implícitos de los controles y los mensajes dinámicos de estado.
- **Contraste:** se ajustaron colores y superficies para conservar una lectura clara.
- **Dependencia de la IA:** las propuestas de la skill se revisaron y se aplicaron solo cuando eran compatibles con el objetivo de la actividad.
- **Licencia y uso:** se consultó la fuente original antes de describir la skill; no se ejecutó código incluido en ella ni se le concedieron permisos adicionales.

## Conversación original relacionada

La utilización se realizó en la conversación de Copilot del **22 de octubre de 2026**, en la que se solicitó modificar el frontend sin cambiar el contenido. El intercambio original debe conservarse completo mediante `Copy All` en [`conversaciones-ia/`](../conversaciones-ia/), siguiendo las instrucciones de la actividad. Esta documentación resume la aplicación y no sustituye a la conversación original.

