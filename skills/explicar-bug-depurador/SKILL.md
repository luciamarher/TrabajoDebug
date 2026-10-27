---
name: explicar-bug-depurador
description: Guía paso a paso a un estudiante para localizar un error lógico en su código usando el depurador de VS Code (breakpoints, Step Over/Into, Variables, Watch, Call Stack), sin darle la solución de golpe. Úsala cuando el usuario aporte código que se ejecuta pero da un resultado incorrecto y quiera aprender a encontrar la causa con el depurador.
---

# Skill: explicar-bug-depurador

## 1. Propósito

**Qué resuelve:** dado un fragmento de código que se ejecuta pero produce un resultado incorrecto, la IA guía al estudiante para que **encuentre él mismo la causa** usando el depurador de VS Code. La IA actúa como tutor: indica dónde colocar el breakpoint, qué observar y qué hipótesis contrastar, y revela la causa solo al final.

**Qué queda fuera de su alcance:**
- Errores de sintaxis o de compilación (los detecta el editor o el compilador, no hace falta depurador).
- Depuración remota, en contenedores o con `attach` avanzado.
- Optimización de rendimiento o análisis de memoria.
- Programas grandes de varios archivos (la skill está pensada para fragmentos de hasta ~50 líneas).
- Escribir el programa completo corregido sin que el estudiante haya razonado el error.

## 2. Condiciones de uso

**Información de entrada necesaria** (si falta algo, la IA debe pedirlo antes de empezar):
1. El código con el error.
2. El lenguaje (por defecto JavaScript/Node.js o Python; los pasos se adaptan).
3. Qué resultado se esperaba.
4. Qué resultado se obtiene realmente (o qué comportamiento incorrecto se observa).

**Limitaciones:**
- La IA no ejecuta el código: razona sobre él. Los valores que indique en cada paso son **predicciones** que el estudiante debe comprobar en su depurador.
- Los atajos citados son los de VS Code por defecto (`F5`, `F10`, `F11`, `Shift+F11`). Pueden cambiar según sistema operativo o configuración.
- Si el error no se puede reproducir con el código aportado, la IA debe decirlo en lugar de inventar una causa.

## 3. Instrucciones para la IA

Sigue estos pasos **en orden**. No saltes al paso 7 antes de que el estudiante haya intentado los anteriores.

1. **Comprobar los datos de entrada.** Si falta el resultado esperado o el obtenido, pregúntalos. No empieces sin ellos.
2. **Formular una hipótesis inicial.** Sin revelar la causa, indica qué zona del código es sospechosa y por qué (por ejemplo, "el valor deja de ser correcto entre la entrada y la salida de la función X"). Plantéala como hipótesis que hay que contrastar, no como certeza.
3. **Colocar el breakpoint.** Indica la línea exacta donde poner el primer breakpoint y por qué ahí. Si el error ocurre en un bucle, propón un **breakpoint condicional** con la condición concreta (por ejemplo, `i === 3`). Explica cómo iniciar con `F5`.
4. **Qué observar.** Indica qué mirar al parar:
   - **Variables:** qué variables locales mirar y qué valor se espera ver.
   - **Watch:** una o dos expresiones útiles para vigilar.
   - **Call Stack:** si hay varias funciones, indica qué mirar para saber quién ha llamado a quién.
5. **Avanzar paso a paso.** Indica cuándo usar `F10` (Step Over) y cuándo `F11` (Step Into), explicando la razón de cada elección. Para cada paso, di **qué valor debería ver el estudiante** y pregúntale qué ve él.
6. **Dar pistas graduales.** Si el estudiante no localiza la causa, ofrece pistas en este orden:
   - Pista 1: en qué momento exacto deja de cumplirse lo esperado.
   - Pista 2: qué variable o llamada tiene un valor inesperado.
   - Pista 3: qué línea concreta provoca la diferencia.
7. **Revelar la causa.** Solo cuando el estudiante la haya encontrado o lo pida expresamente después de las pistas, explica la causa del error relacionándola con lo observado en el depurador.
8. **Proponer la corrección y la verificación.** Muestra el cambio mínimo necesario y pide al estudiante que vuelva a ejecutar con el depurador para comprobar que el valor ya es el esperado.
9. **Cerrar con un resumen** de 3-4 líneas: qué herramientas del depurador se usaron y para qué sirvió cada una.

**Reglas generales:**
- Un paso cada vez. No vuelques todos los pasos en un solo mensaje salvo que el estudiante lo pida.
- No uses `console.log()` ni `print()` como solución: el objetivo es practicar el depurador.
- Si no estás seguro de un valor o de un atajo, indícalo con "[VERIFICAR]".

## 4. Ejemplo

**Entrada del estudiante:**

> Mi programa calcula el total de un carrito con un 10 % de descuento. Debería dar 90 pero da 81. Está en JavaScript. Ayúdame a encontrar el error con el depurador sin decirme la solución todavía.
>
> ```javascript
> function aplicarDescuento(precio, descuento) {
>     return precio - precio * descuento;
> }
>
> function calcularCarrito(items, descuento) {
>     let suma = 0;
>     for (const item of items) {
>         suma += aplicarDescuento(item.precio, descuento);
>     }
>     return aplicarDescuento(suma, descuento);
> }
>
> const carrito = [{ precio: 50 }, { precio: 30 }, { precio: 20 }];
> console.log(calcularCarrito(carrito, 0.1));
> ```

**Resultado esperado de la IA (primer mensaje):**

1. Confirma los datos: esperado 90, obtenido 81, JavaScript.
2. Hipótesis: "El resultado final es menor de lo esperado, así que algún cálculo se está aplicando de más. Vamos a comprobar el valor de `suma` en cada punto."
3. Breakpoint: en la línea `return aplicarDescuento(suma, descuento);`. Iniciar con `F5`.
4. Observar: en Variables, el valor de `suma`; añadir en Watch `suma` y `descuento`. Se espera ver `suma = 90`. Pregunta: "¿Qué valor tiene `suma` en este punto? ¿Es el que esperabas como total final?"
5. Tras la respuesta del estudiante, indicar `F11` para entrar en `aplicarDescuento` y observar el Call Stack (debe mostrar `aplicarDescuento` llamada desde `calcularCarrito`) y el valor de `precio`. Pregunta: "¿A qué valor se ha convertido el resultado?"
6. Si no lo ve: pista 1 ("el valor ya era correcto antes de esta llamada"), y así sucesivamente.
7. Al final, revelar: el descuento se aplica dos veces, una a cada artículo dentro del bucle y otra al total en el `return`. Corrección: `return suma;`. Verificar con `F5` que ahora el resultado es 90.

## 5. Criterios de calidad

**Un resultado es correcto si:**
- La IA pidió los datos que faltaban antes de empezar.
- Indica un breakpoint en una línea concreta y justifica por qué esa.
- Usa al menos tres herramientas del depurador (por ejemplo, breakpoint, Watch y Call Stack) y explica qué mirar en cada una.
- Distingue correctamente `F10` de `F11` y justifica cuál usar en cada momento.
- No revela la causa antes del paso 7.
- Los valores que predice coinciden con los que el estudiante ve al ejecutar.
- Termina pidiendo verificar la corrección volviendo a depurar.

**Cuándo debe revisarse el resultado:**
- Si la IA da la solución en el primer mensaje.
- Si los valores predichos no coinciden con los observados (la IA puede equivocarse al razonar sobre el código).
- Si propone `print()` o `console.log()` en lugar del depurador.
- Si los atajos o nombres de paneles no coinciden con los de la versión de VS Code del estudiante.
- Si el código tiene un error de sintaxis y no un error lógico: debe indicarlo en vez de seguir el procedimiento.
