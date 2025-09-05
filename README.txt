
¿Qué es la herencia en TS y cómo se implementa (extends / super)?
es una caracteristica indispensable en la (POO) permite que una clase derivada o subclase cree jerarquias de clases y extender su funcionalidad sin modificar el codigo de la clase base
la heriencia puede funcionar de distintas formas una de las mas destacada es.
Reutilizando codigo, la sub clase puede usar las caracteristicas de la clase padre sin reescribirlas
para utilizar este metodo es importante comprender:
clase base (super clase): la clase de la cual se hereda
clase derivada (subclase): la clase que hereda de otra clase
extends: en ts se utuliza para definir la heriencia de una clase
super: se usa dentro de una clase derivada para llamar al constructor dela clase base y se asegura que la inicializacion sea la adecuada.

// CLASE BASE (Superclase)
class Animal {
    // Propiedad
    nombre: string;
    
    // Constructor
    constructor(nombre: string) {
        this.nombre = nombre;
    }
    
    // Método
    hacerSonido(): void {
        console.log(`${this.nombre} hace un sonido.`);
    }
}

// CLASE DERIVADA (Subclase) - Hereda de Animal usando 'extends'
class Perro extends Animal {
    // Propiedad adicional específica de Perro
    raza: string;
    
    // Constructor que llama al constructor de la clase base con 'super()'
    constructor(nombre: string, raza: string) {
        super(nombre); // Llama al constructor de Animal
        this.raza = raza;
    }
    
    // Sobrescritura de método (override)
    hacerSonido(): void {
        console.log(`${this.nombre} (${this.raza}) dice: ¡Guau guau!`);
    }
    
    // Nuevo método específico de Perro
    moverCola(): void {
        console.log(`${this.nombre} mueve la cola felizmente.`);
    }
}

// Uso de las clases
const miAnimal = new Animal("Genérico");
const miPerro = new Perro("Fido", "Labrador");

miAnimal.hacerSonido(); // Output: Genérico hace un sonido.
miPerro.hacerSonido();  // Output: Fido (Labrador) dice: ¡Guau guau!
miPerro.moverCola();    // Output: Fido mueve la cola felizmente.


en este codigo:
extends es la que genera la conexion es decir perro hereda de animal
super() llama al constructor base
se sobre escribe cuano la clase perro redefine el metodo (hacer sonido()) con algo especifico
la clase perro añade un metodo moverCola() que no estaba establecida previamente}


¿Qué significa polimorfismo en el contexto de TS?

en ts se refiere a la capacidad de tratar objetos de distintas clases como si fuesen comunes, para que el mismo metodo se comporte de forma distinta segun que objeto se utilize
se puede implementar de dos formas,
dinamica, las clases hijas pueden implementar un metodo con el mismo nombre que las clases padre, con logicas diferentes
por ejemplo seria calcularArea() la clase seria circulo pero eta puede actuar de diferentes formas  como calcular un area o en una clase el rectangulo como comun ambas seran tratadas como figuras 
estatico, se crean multiples fuonciones al tiempo con el mismo nombre pero en distintas listas por ejemplo la funcion buscar () puede tener una version que tome un id y otra que tome un nombre 
en ts nos ofrece flexibilidad  ya que permite escribir codigos con variedad de objetos sin conocer los tipos, tambien facilita la reutilizacion de codigos en diferentes contextos.

¿Qué son las clases abstractas y qué diferencia tienen con una clase normal?

las clases abstractas no pueden instanciarse, por ejemplo no se pueden crear objetos apartir de estas, mas bien actuan como una plantilla para otras clases.
las clases normales pueden instanciarse su principal diferencia  es la necesidad de que los metodos abstractos sean complementados por sus clases hijas

¿Qué es una interface en TS y en qué se diferencia de una clase abstracta?

la interface es un "contrato" que indica las propiedades y metodos que una clase debe tener pero no implementa, la clase abstracta puede tener clases abstracctas y ademas miembros concretos que si se implementan permitiendo compartir codigo y comportamiento con sus clases hijas
la principal diferencia es  que las interfaces solo verifican los tipos y no generarn codigo las clases abstractas pueden ser instanciadas

Ejemplo mínimo de cada pilar de POO en TS (una línea de código por concepto).

// 1. ENCAPSULACIÓN: Ocultar detalles internos usando modificadores de acceso
class CuentaBancaria { private saldo: number = 0; }

// 2. HERENCIA: Crear una clase derivada de una clase base
class Animal { moverse() {} }
class Perro extends Animal { ladrar() {} }

// 3. POLIMORFISMO: Mismo método, implementaciones diferentes
class Gato extends Animal { moverse() { console.log("El gato camina") } }
class Pajaro extends Animal { moverse() { console.log("El pájaro vuela") } }

// 4. ABSTRACCIÓN: Definir estructura sin implementación completa
abstract class Vehiculo { abstract acelerar(): void; }
class Coche extends Vehiculo { acelerar() { console.log("Acelerando coche") } }

Investigar y realizar la configuración de TypeScript con Node JS y VS Code.

Para configurar TypeScript en Node.js con VS Code, instala Node.js y VS Code, inicializa un proyecto Node.js (npm init), instala TypeScript y las dependencias necesarias, crea un archivo tsconfig.json para configurar el compilador, y finalmente, puedes ejecutar o depurar tu código TypeScript directamente desde la terminal o el entorno de depuración de VS Code

pasos 

validar que cuentes con

node.js
VS code

crear e iniciar el proyecto
podemos crear la carpeta de manera manual o ejecutar

mkdir mi-proyecto
cd mi-proyecto

npm init vue@latest

al finalizar la instalacion 

cd mi-proyecto-vue
npm install

para que el proecto este bien configurado con ts
en el archivo tsconfig.json verifica que exista
{
  "extends": "@vue/tsconfig/tsconfig.dom.json",
  "include": ["env.d.ts", "src/**/*", "src/**/*.vue"],
  "exclude": ["src/**/__tests__/*"],
  "compilerOptions": {
    "composite": true,
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}

y luego ejecuta el proyecto con 

# Servidor de desarrollo
npm run dev

# Compilar para producción
npm run build

# Preview de producción
npm run preview

