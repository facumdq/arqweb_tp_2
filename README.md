# arqweb_tp_2

Proyecto de prueba de la facultad (Arquitectura Web, TP 2). La página toma un JSON de gatas y sus gatitos, lo convierte en datos y lo muestra en pantalla.

El origen de los datos es el ejercicio [Test your skills: JSON](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Test_your_skills/JSON) de MDN:

`https://mdn.github.io/learning-area/javascript/oojs/tasks/json/sample.json`

## Qué muestra

- Una frase con los nombres de las madres. El último lleva "and" delante y un punto al final, sin importar cuántas gatas traiga el JSON.
- Una frase con el total de gatitos y cuántos son machos y hembras.
- Una tabla de madres: nombre, raza, color y cantidad de gatitos.
- Una tabla de gatitos: madre, nombre y sexo.

Con el JSON de ejemplo el resultado es: Lindy, Mina y Antonia; 8 gatitos, 3 machos y 5 hembras.

## Cómo está armado

| Archivo | Rol |
| --- | --- |
| `index.html` | Pide el JSON, arma el texto y las tablas, y revela el contenido al cargar. |
| `style.css` | Estilos de la página, las tablas y la transición de entrada. |

`fetch()` devuelve el JSON como texto en el parámetro `catString` de `displayCatInfo()`. Ahí se usa `JSON.parse()` para poder leer los objetos. Un ciclo recorre las madres y otro, anidado, recorre los gatitos de cada una.

`para1.textContent` y `para2.textContent` están dentro de `displayCatInfo()` porque `fetch()` es asíncrono. Esas líneas se ejecutan cuando la respuesta ya llegó. Si estuvieran al final del script, correrían antes, con las frases todavía vacías.

Al cargar la página, `window.onload` y el fin de `displayCatInfo()` agregan la clase `show` al `body`. Recién entonces el texto, los encabezados de tabla y las celdas pasan de ocultos a visibles, con transición.

## Cómo verlo

Hay que servirlo por HTTP. Abrir el archivo directo puede bloquear el `fetch()` al JSON externo.

```bash
python3 -m http.server 8765
```

Después entrar a [http://127.0.0.1:8765](http://127.0.0.1:8765).
