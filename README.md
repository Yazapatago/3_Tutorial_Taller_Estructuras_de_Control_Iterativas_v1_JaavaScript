# 3_Tutorial_Taller_Estructuras_de_Control_Iterativas_v1_JavaScript
Taller 3 de JavaScript para compañeros del SENA de la carrera de ADSO

# Estructuras de Control Iterativas - Repitiendo Tareas

Hasta ahora, nuestros programas ejecutan instrucciones una tras otra, o toman decisiones para seguir un camino u otro. Pero, ¿qué pasa si necesitamos repetir un conjunto de instrucciones varias veces? Por ejemplo, imprimir los números del 1 al 10, o pedirle al usuario datos hasta que ingrese uno válido. Para esto, JavaScript nos ofrece las estructuras de control iterativas, también conocidas como bucles o ciclos.

---

## 9.1 Bucles `while`: Repetir Mientras se Cumpla una Condición

El bucle `while` ejecuta un bloque de código repetidamente mientras una condición especificada sea `true`.

**Concepto de Bucle:**  
Imagina que tienes que dar 5 vueltas a una pista. Cada vuelta es una iteración. Realizas la acción de "dar una vuelta" repetidamente hasta que completas las 5. Un bucle `while` funciona de manera similar:  
1. Verifica una condición.  
2. Si la condición es `true`, ejecuta el bloque de código dentro del bucle.  
3. Vuelve al paso 1.  
4. Si la condición es `false`, el bucle termina y el programa continúa con las instrucciones que siguen después del bucle.

### Sintaxis y Funcionamiento:
```javascript
while (condicionDeContinuacion) {
  // Bloque de código que se repite
  console.log("Dentro del bucle while.");
  // Es CRUCIAL que algo dentro del bucle eventualmente haga
  // que la condicionDeContinuacion se vuelva false.
}
// Código después del bucle
console.log("El bucle while ha terminado.");
```

- **CondicionDeContinuacion**: Una expresión booleana. Mientras sea `true`, el bucle sigue. Cuando se vuelve `false`, el bucle para.
- **Condición de terminación:** Es el estado que hace que la condición de continuación se vuelva ```False```, permitiendo que el bucle termine. Es vital asegurarse de que esta condición de terminación se pueda alcanzar.
- **Bucles Infinitos y Cómo Evitarlos:** Un bucle infinito ocurre si la ```condicion_de_continuacion``` nunca se vuelve ```False```. El programa se quedará "atrapado" ejecutando el cuerpo del bucle para siempre (o hasta que lo detengas manualmente).
**Causa común:** Olvidar actualizar dentro del bucle la variable que forma parte de la condición.

### Ejemplos Prácticos:

```javascript
// Ejemplo 1: Contar del 1 al 5
let contador = 1;  // 1. Inicializar la variable de control
console.log("Iniciando conteo con while:");
while (contador <= 5) {  // 2. Condición de continuación
  console.log(`Número: ${contador}`);
  contador += 1;  // 3. Actualizar la variable de control (¡CRUCIAL!)
}
console.log("Conteo finalizado.");

// Ejemplo 2: Pedir una contraseña hasta que sea correcta
const contrasenaSecreta = "SENA2025";
let intentoUsuario = ""; // Inicializar con algo que no sea la contraseña

console.log("\n--- Sistema de Acceso ---");
while (intentoUsuario !== contrasenaSecreta) {
  intentoUsuario = prompt("Ingresa la contraseña: ");
  if (intentoUsuario !== contrasenaSecreta) {
    console.log("Contraseña incorrecta. Intenta de nuevo.");
  }
}
console.log("¡Acceso concedido!");

// Ejemplo 3: Sumar números hasta que el usuario ingrese 0
let sumaTotal = 0;
let numeroIngresado = -1; // Inicializar para que entre al bucle

console.log("\n--- Sumadora (ingresa 0 para terminar) ---");
while (numeroIngresado !== 0) {
  const numeroIngresadoTexto = prompt("Ingresa un número (o 0 para salir): ");
  numeroIngresado = parseInt(numeroIngresadoTexto);
  sumaTotal += numeroIngresado;
  console.log(`Suma parcial: ${sumaTotal}`);
}
console.log(`La suma total de los números ingresados es: ${sumaTotal}`);
```

---

## ¡A Tu Teclado!

### Ejercicio 9.1.1: Cuenta Regresiva
Escribe un programa que use un bucle `while` para mostrar una cuenta regresiva desde 5 hasta 1, y luego imprima **"¡Despegue!"**.

```javascript
// Escribe tu código aquí
console.log("Iniciando cuenta regresiva...");
let numeroRegresivo = 5;
while (numeroRegresivo >= 1) {
  console.log(`Número: ${numeroRegresivo}`);
  numeroRegresivo -= 1;
}
console.log("¡Despegue!");
```

---

### Ejercicio 9.1.2: Tabla de Multiplicar Simple
Pide al usuario un número entero. Luego, usa un bucle `while` para mostrar los primeros 10 resultados de la tabla de multiplicar de ese número.  
Ejemplo (si ingresa 7):  
7 x 1 = 7  
7 x 2 = 14  
...  
7 x 10 = 70

```javascript
const numero = parseInt(prompt("Ingrese un número: "));
let cont = 1;

while (cont <= 10) {
  const multiplicar = numero * cont;
  console.log(`${numero} x ${cont} = ${multiplicar}`);
  cont += 1;
}
console.log("Finalizado...");
```

---

## 9.2 Bucles `for`: Iterando Sobre Secuencias

El bucle `for` se utiliza para iterar (recorrer uno por uno) sobre los elementos de una secuencia (como una cadena de texto o un array) o cualquier objeto iterable. Es ideal cuando sabes de antemano cuántas veces quieres repetir algo o cuando quieres procesar cada elemento de una colección.

### Sintaxis y Funcionamiento:
```javascript
for (let variableIteradora of secuenciaOIterable) {
  // Bloque de código que se ejecuta para cada elemento
  console.log(`Elemento actual: ${variableIteradora}`);
}
// Código después del bucle
console.log("El bucle for ha terminado.");
```

- `secuenciaOIterable`: Puede ser una cadena de texto, un array (ej: `[1, 2, 3]`), etc.  
- `variableIteradora`: En cada iteración, toma el valor del siguiente elemento.

**Iteración sobre Secuencias:**  
- **Cadenas de Texto (`string`):** Recorre cada carácter.  
- **Arrays (`array`):** Colecciones ordenadas (ej: `[1, 2, 3, "hola"]`). Recorre cada elemento.

**Bucle `for` con Contadores (similar a `range()` en Python):**  
Usa un `for` tradicional con inicialización, condición y actualización.

### Ejemplos Prácticos:

```javascript
// Ejemplo 1: Iterar sobre una cadena de texto
const mensaje = "Hola SENA!";
console.log("Iterando sobre cada carácter:");
for (let caracter of mensaje) {
  console.log(`Carácter: ${caracter}`);
}

// Ejemplo 2: Iterar sobre una lista (array)
const frutas = ["Manzana", "Banano", "Naranja"];
console.log("\nIterando sobre frutas:");
for (let fruta of frutas) {
  console.log(`Fruta: ${fruta}`);
}

// Ejemplo 3: Usando for con contador (similar a range)
console.log("\nConteo del 0 al 4:");
for (let i = 0; i < 5; i++) {
  console.log(`Número: ${i}`);
}

// Ejemplo 4: Tabla de multiplicar con for
const numeroTabla = parseInt(prompt("Ingresa un número para la tabla: "));
console.log(`Tabla de multiplicar del ${numeroTabla}:`);
for (let multiplicador = 1; multiplicador <= 10; multiplicador++) {
  console.log(`${numeroTabla} x ${multiplicador} = ${numeroTabla * multiplicador}`);
}
```

---

## ¡A Tu Teclado!

### Ejercicio 9.2.1: Contar Vocales en una Palabra
Pide al usuario una palabra. Usa un bucle `for` para iterar sobre cada carácter y contar cuántas vocales (a, e, i, o, u) hay.

```javascript
const palabra = prompt("Ingresa una palabra: ").toLowerCase();
let contadorVocales = 0;
const vocales = "aeiou";

for (let caracter of palabra) {
  if (vocales.includes(caracter)) {
    contadorVocales += 1;
  }
}
console.log(`La palabra "${palabra}" tiene ${contadorVocales} vocales.`);
```

---

### Ejercicio 9.2.2: Suma de Números en un Array
Dado un array de números (ej: `[1, 2, 3, 4, 5]`), usa un bucle `for` para calcular y mostrar la suma de sus elementos.

```javascript
const numeros = [1, 2, 3, 4, 5];
let suma = 0;

for (let num of numeros) {
  suma += num;
}
console.log(`La suma de los números es: ${suma}`);
```

---

## 9.3 Controlando Bucles con `break` y `continue`

- `break`: Sale inmediatamente del bucle.  
- `continue`: Salta el resto del código en la iteración actual y pasa a la siguiente.

### Ejemplos Prácticos:

```javascript
// Ejemplo con break
console.log("Búsqueda con break:");
for (let i = 1; i <= 10; i++) {
  if (i === 5) {
    console.log("¡Encontrado el 5! Saliendo del bucle.");
    break;
  }
  console.log(`Número: ${i}`);
}

// Ejemplo con continue
console.log("\nNúmeros pares del 1 al 10 (saltando impares con continue):");
for (let i = 1; i <= 10; i++) {
  if (i % 2 !== 0) {
    continue; // Salta si es impar
  }
  console.log(`Número par: ${i}`);
}
```

---

## ¡A Tu Teclado!

### Ejercicio 9.3.1: Búsqueda con `break`
Usa un bucle `for` sobre un array de nombres. Si encuentras "Juan", imprime "¡Encontrado!" y sal del bucle con `break`.

```javascript
const nombres = ["Ana", "Pedro", "Juan", "Maria"];
for (let nombre of nombres) {
  if (nombre === "Juan") {
    console.log("¡Encontrado Juan!");
    break;
  }
  console.log(`Nombre: ${nombre}`);
}
```

---

### Ejercicio 9.3.2: Saltar Múltiplos de 3 con `continue`
Usa un bucle `for` del 1 al 10. Si el número es múltiplo de 3, salta con `continue`. Imprime los demás.

```javascript
for (let i = 1; i <= 10; i++) {
  if (i % 3 === 0) {
    continue;
  }
  console.log(`Número: ${i}`);
}
```

---

## ¡Desafíate!

### Reto 9.1: Juego de Adivinanza con Intentos Limitados
Crea un juego donde el usuario adivine un número secreto (1-100) con hasta 5 intentos. Usa `while` y `break` si adivina.

```javascript
const numeroSecreto = Math.floor(Math.random() * 100) + 1;
let intentos = 0;
const maxIntentos = 5;

console.log("¡Adivina el número secreto (1-100)! Tienes 5 intentos.");

while (intentos < maxIntentos) {
  const intento = parseInt(prompt(`Intento ${intentos + 1}: Ingresa un número: `));
  intentos++;

  if (intento === numeroSecreto) {
    console.log("¡Felicidades! Adivinaste el número.");
    break;
  } else if (intento < numeroSecreto) {
    console.log("Muy bajo.");
  } else {
    console.log("Muy alto.");
  }

  if (intentos === maxIntentos) {
    console.log(`Se acabaron los intentos. El número era ${numeroSecreto}.`);
  }
}
```

---

### Reto 9.2: Factorial de un Número
Pide un número positivo. Calcula su factorial usando un bucle `for` o `while`.

```javascript
const numero = parseInt(prompt("Ingresa un número positivo para calcular su factorial: "));
let factorial = 1;

for (let i = 1; i <= numero; i++) {
  factorial *= i;
}
console.log(`El factorial de ${numero} es: ${factorial}`);
```

---

## Reto 10.1: Mini-Simulador de Cajero Automático

```javascript
let saldoCuenta = 1000000.0;
console.log("--- Bienvenido al Cajero Automático SENA ---");

while (true) {
  console.log("\nMenú de Opciones:");
  console.log("1. Consultar Saldo");
  console.log("2. Depositar Dinero");
  console.log("3. Retirar Dinero");
  console.log("4. Salir");
  const opcionTexto = prompt("Seleccione una opción: ");

  if (!opcionTexto || isNaN(opcionTexto)) {
    console.log("Error: Por favor, ingrese un número para la opción.");
    continue;
  }

  const opcion = parseInt(opcionTexto);

  if (opcion === 1) {
    console.log(`Su saldo actual es: $${saldoCuenta.toFixed(2)}`);
  } else if (opcion === 2) {
    const deposito = parseFloat(prompt("Ingrese la cantidad a depositar: "));
    if (deposito > 0) {
      saldoCuenta += deposito;
      console.log(`Depósito exitoso. Nuevo saldo: $${saldoCuenta.toFixed(2)}`);
    } else {
      console.log("Error: La cantidad debe ser positiva.");
    }
  } else if (opcion === 3) {
    const retiro = parseFloat(prompt("Ingrese la cantidad a retirar: "));
    if (retiro > 0 && retiro <= saldoCuenta) {
      saldoCuenta -= retiro;
      console.log(`Retiro exitoso. Nuevo saldo: $${saldoCuenta.toFixed(2)}`);
    } else if (retiro > saldoCuenta) {
      console.log("Error: Saldo insuficiente.");
    } else {
      console.log("Error: La cantidad debe ser positiva.");
    }
  } else if (opcion === 4) {
    console.log("Gracias por usar el Cajero Automático SENA. ¡Vuelva pronto!");
    break;
  } else {
    console.log("Opción no válida.");
  }
}
```

---

¡Muy bien! Has cubierto una parte fundamental de la programación: cómo hacer que tus programas repitan tareas de manera eficiente. Los bucles son herramientas que usarás constantemente.
