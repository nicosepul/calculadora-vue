🧮Calculadora Web en Vue
📌 Descripción

Este proyecto consiste en el desarrollo de una calculadora web implementada con Vue.js y JavaScript, la cual simula el comportamiento de una calculadora tradicional, incorporando restricciones y validaciones específicas.

La aplicación no permite ingreso manual de datos, sino que todas las operaciones se realizan mediante botones, asegurando el control total de las entradas del usuario.

⚙️ Tecnologías utilizadas
Vue.js
JavaScript
HTML
CSS
🚫 Restricciones del sistema
🔹 Entrada de datos
No existe un <input> editable
Todo se ingresa mediante botones
Máximo 10 caracteres en pantalla
Si se intenta ingresar un carácter número 11 → se rechaza
🔹 Validaciones

La calculadora evita operaciones inválidas como:

División por cero → muestra "E"
Operadores consecutivos (++, **, //, etc.)
Se permite negativo después de operador
👉 Ejemplo válido: 3 * -2
🔹 Resultados
Si el resultado tiene más de 10 caracteres → muestra "E"
Si ocurre un error → muestra "E"
Números negativos se muestran correctamente con -
Si el número negativo supera los 10 caracteres → "E"
➕ Operaciones disponibles
Suma +
Resta -
Multiplicación *
División /
📊 Prioridad de operaciones
Multiplicación y división
Suma y resta
🧠 Sistema de memoria
Cada vez que se presiona =:
El resultado se guarda automáticamente
Máximo de memoria: 15 resultados
Si se supera el límite:
Se elimina el más antiguo
🔼 Navegación
Botón ↑ → muestra resultados anteriores
Botón ↓ → avanza en los resultados
Si no hay más → pantalla vacía
🔤 Códigos numéricos especiales

La calculadora interpreta ciertas combinaciones numéricas como texto.

Ejemplos:

Código	Resultado
705	SOL
35007	LOOSE
58008	BOOBS
7734	HELL

Estas conversiones se realizan al presionar =.

🎯 Regla especial del sistema

Existe una regla especial definida:

0 * 1 = 1111111111

Al ingresar esta operación, la calculadora muestra diez unos en pantalla.

🎨 Interfaz
Diseño simple y funcional
Uso de CSS Grid para organizar botones
Pantalla alineada a la derecha (estilo calculadora clásica)
🚀 Ejecución del proyecto
Instalar dependencias:
npm install
Ejecutar proyecto:
npm run dev
Abrir en navegador:
http://localhost:5173