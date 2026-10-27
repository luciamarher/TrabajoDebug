# Fuentes utilizadas

Estas fuentes se han utilizado para redactar, comprobar y diseñar [index.html](../index.html). Las tres primeras respaldan el contenido técnico sobre debugging; las dos últimas documentan el criterio utilizado para mejorar el frontend. El texto de la web está resumido con palabras propias; las respuestas de IA no se consideran fuentes verificadas.

| Fuente | Enlace o referencia | Información que respalda |
|---|---|---|
| Apuntes de depuración del proyecto | [`pps1_03 debug.md`](../pps1_03%20debug.md) | Definición de debugging, arquitectura DAP, configuración de sesiones, breakpoints, atajos, Variables, Watch, Call Stack, Debug Console y el ejemplo del índice fuera de rango. |
| Visual Studio Code: Debugging | [Documentación oficial](https://code.visualstudio.com/docs/editor/debugging) | Inicio de sesiones de depuración, `launch.json`, modos `launch` y `attach`, breakpoints, ejecución paso a paso y gestión de excepciones. |
| Visual Studio Code: Debug Console | [Documentación oficial](https://code.visualstudio.com/docs/editor/debugging#_debug-console-repl) | Evaluación de expresiones y consulta del estado del programa desde la consola de depuración. |
| Skill pública `design-taste-frontend` | [Repositorio original en GitHub](https://github.com/changemaner/design-taste-frontend) | Criterios para crear una interfaz frontend intencionada, evitar patrones visuales genéricos y revisar jerarquía, composición, responsive design y estados de interacción. |
| Skill `design-taste-frontend` en Skills.sh | [Ficha pública de la skill](https://www.skills.sh/leonxlnx/taste-skill/design-taste-frontend) | Descripción pública de la skill y de su uso como apoyo para rediseñar interfaces web. |

## Comprobaciones realizadas

- Se contrastaron las ideas clave de la web con los apuntes del proyecto.
- Se revisaron los conceptos de configuración, breakpoints y ejecución paso a paso en la documentación oficial de VS Code.
- Se verificó el ejemplo interactivo de `notas[i]`: con `i = 4`, el array `[7, 8, 6, 9]` ya no tiene un elemento válido.
- Se comprobó que la corrección propuesta es cambiar `i <= notas.length` por `i < notas.length`.
- Se utilizó `design-taste-frontend` únicamente como apoyo de diseño: no se empleó para validar afirmaciones técnicas sobre Visual Studio Code.
- Tras aplicar el rediseño, se comprobó que permanecían las seis ideas clave, los seis términos del glosario, la demostración interactiva, las fuentes y el comportamiento responsive.
