# Clase 2 - Proyecto 2D en Unity

## 🎮 1. Repaso de elementos de interfaz (UI) y escenas

### a) Crear proyecto 2D
- Abrir Unity Hub.
- Crear un nuevo proyecto seleccionando la plantilla **2D**.
- Nombrarlo como: `JuegoPongUnity`.

### b) Crear escena inicial: Texto y botón de inicio
- Ir al menú `File > New Scene` y guardar como `MenuInicio`.
- Agregar un objeto UI `Text` y un `Button`.
- Cambiar el texto a “¡Bienvenido al juego!” y en el botón poner “Iniciar”.

### c) Crear escena de juego: Pelota y raqueta
- Crear nueva escena llamada `Juego`.
- Agregar dos objetos:
  - `Pelota` con un Sprite circular.
  - `Raqueta` con un Sprite rectangular.

### d) Cambio de escena con C#

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class CambiarEscena : MonoBehaviour
{
    public void IrAEscenaJuego()
    {
        SceneManager.LoadScene("Juego");
    }
}
```

- Asociar este script al botón de inicio, vinculando el evento `OnClick()` con la función `IrAEscenaJuego()`.

---

## ⚙️ 2. Componentes y física de elementos básicos

### a) Rigidbody
- Agregá un `Rigidbody2D` a la pelota.
- Permite que la pelota responda a la gravedad y colisiones físicas.

### b) Colliders
- Agregar `BoxCollider2D` a la raqueta.
- Agregar `CircleCollider2D` a la pelota.
- Permiten detectar y responder a colisiones.

### c) Triggers

**¿Qué son?**

- Un `Trigger` es un Collider con la opción `Is Trigger` activada.
- No bloquea físicamente, pero detecta cuando algo lo atraviesa.
- Usado para generar eventos (como sumar puntos o activar animaciones).

---

## 🧪 3. Ejemplos tipo PONG

### a) Rigidbody
```csharp
// Agregalo a la pelota para que caiga por gravedad
// o se mueva al colisionar
Rigidbody2D rb = GetComponent<Rigidbody2D>();
rb.gravityScale = 1.0f;
```

### b) Collider
- La pelota rebota contra la raqueta.
- Ambos tienen colliders para detectar el impacto.

### c) Trigger

```csharp
void OnTriggerEnter2D(Collider2D other)
{
    if (other.gameObject.CompareTag("Pelota"))
    {
        Debug.Log("¡Pelota pasó por el área!");
    }
}
```

---

## 💻 4. Clase básica de programación en C#

### a) Script para un contador activado por trigger

```csharp
using UnityEngine;
using UnityEngine.UI;

public class Contador : MonoBehaviour
{
    public int puntos = 0;
    public Text textoPuntos;

    void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Pelota"))
        {
            puntos++;
            textoPuntos.text = "Puntos: " + puntos;
        }
    }
}
```

### Instrucciones:
- Asignar el tag “Pelota” a la pelota.
- Crear un `Text` en la UI para mostrar los puntos.
- Asociar el `Text` al campo `textoPuntos` en el Inspector.

---

## 📝 Tarea sugerida

1. Crear un menú con botón que lleva a la escena del juego.
2. Diseñar una escena tipo PONG con raqueta y pelota.
3. Usar Rigidbody, Collider y Trigger para definir las físicas.
4. Agregar un contador de puntos que aumenta al pasar por un Trigger.
