# 🧮 Calculadora Web en Vue

## 📌 Descripción

Este proyecto consiste en una **calculadora web** desarrollada con **Vue.js y JavaScript**, que simula una calculadora tradicional con restricciones específicas.

No permite ingreso manual: todo se realiza mediante botones.

---

## ⚙️ Tecnologías

* Vue.js
* JavaScript
* HTML
* CSS

---

## 🚫 Restricciones

### Entrada

* Sin `<input>`
* Máximo **10 caracteres**
* Se rechaza el carácter 11

### Validaciones

* División por 0 → `E`
* No permite operadores dobles (`++`, `//`, etc.)
* Permite negativos: `3 * -2`

### Resultados

* Más de 10 caracteres → `E`
* Error → `E`
* Negativos válidos

---

## ➕ Operaciones

* `+` suma
* `-` resta
* `*` multiplicación
* `/` división

### Prioridad

1. `*` y `/`
2. `+` y `-`

---

## 🧠 Memoria

* Guarda resultados automáticamente (`=`)
* Máximo **15 resultados**
* Elimina el más antiguo

### Navegación

* ↑ resultados anteriores
* ↓ resultados siguientes

---

## 🔤 Códigos especiales

| Código | Resultado |
| ------ | --------- |
| 705    | SOL       |
| 50538  | BESOS     |
| 50807  | LOBOS     |
| 376006 | GOOGLE    |

---

## 🎯 Regla especial

```
0 * 1 = 1111111111
```

---

## 🚀 Ejecutar

```bash
npm install
npm install mathjs
npm run dev
```

Abrir en:
http://localhost:5173

---


