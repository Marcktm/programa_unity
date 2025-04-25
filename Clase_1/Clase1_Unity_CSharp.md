# Clase 1 - Introducción a Unity y Programación en C#

# NO se agregan fotos ya que va a ir variando el Ide según se vaya actualizando

## 🧠 ¿Qué es Unity?

**Unity** es un motor de desarrollo de videojuegos que permite crear experiencias interactivas en 2D, 3D, realidad aumentada (AR) y realidad virtual (VR). Es multiplataforma, lo que significa que podés exportar tu juego a:

- PC (Windows, Mac, Linux)
- Móviles (Android, iOS)
- Consolas (PlayStation, Xbox, Nintendo)
- Web (WebGL)
- VR/AR (Meta Quest, Hololens, etc.)

Unity usa principalmente **C#** como lenguaje de programación, aunque también puede trabajar con Visual Scripting (programación por bloques).

## 🧭 Navegación por la Interfaz de Unity

Cuando abrís el Unity Editor vas a encontrarte con varias ventanas:

- **Scene (Escena):** Es donde construís el mundo del juego.
- **Game (Juego):** Vista previa del juego como lo verá el jugador.
- **Hierarchy (Jerarquía):** Muestra todos los objetos de la escena.
- **Inspector:** Muestra y permite modificar las propiedades del objeto seleccionado.
- **Project:** Es tu carpeta de archivos, donde están los assets (recursos).
- **Console:** Muestra errores, advertencias y mensajes del sistema o tus scripts.

### Tips:

- Usá la rueda del mouse para **hacer zoom** en la escena.
- Mantené clic con el botón derecho y mové el mouse para **rotar la vista**.
- Clic izquierdo + ALT te permite **mover la vista lateralmente**.

## 🛠️ Consideraciones según la plataforma

Cuando creás un proyecto nuevo en Unity, elegí si será:

- **2D:** Ideal para juegos de plataformas, puzzles, etc.
- **3D:** Para mundos tridimensionales con perspectiva.

Luego, podés configurar el **Build Settings** (Archivo > Build Settings) para seleccionar la plataforma objetivo:

| Plataforma     | Consideraciones técnicas                          |
|----------------|----------------------------------------------------|
| Android/iOS    | Necesitás SDKs y configuraciones específicas.     |
| WebGL          | No todos los efectos gráficos son compatibles.     |
| PC             | Mayor libertad, pero se debe optimizar recursos.  |

## 🧑‍💻 Ejercicios Introductorios de C# (en Unity)

**1. Tu primer script en C#:**

```csharp
using UnityEngine;

public class HolaMundo : MonoBehaviour
{
    void Start()
    {
        Debug.Log("¡Hola mundo desde Unity!");
    }
}
```

**2. Variables y Condicionales:**

```csharp
using UnityEngine;

public class VidaJugador : MonoBehaviour
{
    public int vida = 100;

    void Start()
    {
        if (vida <= 0)
        {
            Debug.Log("Game Over");
        }
        else
        {
            Debug.Log("¡Todavía estás vivo!");
        }
    }
}
```

**3. Movimiento simple:**

```csharp
using UnityEngine;

public class MovimientoSimple : MonoBehaviour
{
    public float velocidad = 5f;

    void Update()
    {
        float movimiento = Input.GetAxis("Horizontal");
        transform.Translate(Vector3.right * movimiento * velocidad * Time.deltaTime);
    }
}
```

## 🔣 Ejercicios Básicos de C# (Programación general)

**1. ¿Qué es una variable?**

Una variable es un espacio de memoria donde se almacena un valor. Por ejemplo:

```csharp
int edad = 23;
string nombre = "Marcos";
```

**2. Suma de dos números:**

```csharp
int a = 5;
int b = 3;
int suma = a + b;
Console.WriteLine("La suma es: " + suma);
```

**3. Uso de condicionales:**

```csharp
int nota = 8;
if (nota >= 6)
{
    Console.WriteLine("Aprobado");
}
else
{
    Console.WriteLine("Desaprobado");
}
```

**4. Bucle while:**

```csharp
int i = 0;
while (i < 5)
{
    Console.WriteLine("Número: " + i);
    i++;
}
```

**5. Función simple:**

```csharp
int Sumar(int x, int y)
{
    return x + y;
}
```

## 💻 Editor Online Gratuito de C# para practicar

🔗 [https://dotnetfiddle.net/](https://dotnetfiddle.net/)

Es un entorno online interactivo para programar en C#, ideal para probar lógica antes de llevarla a Unity.

## 🎯 Tarea sugerida

1. Instalar Unity Hub y crear tu primer proyecto 2D.
2. Recorrer la interfaz, identificar cada panel.
3. Crear un objeto `GameObject` y agregarle un script propio (como `HolaMundo.cs`).
4. Probar al menos 2 ejercicios de C# en DotNetFiddle.
5. Investigar qué plataforma te gustaría trabajar (Web, Android, PC, etc.) y anotar por qué.
