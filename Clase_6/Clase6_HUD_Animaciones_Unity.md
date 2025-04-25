# Clase 6 - HUD Avanzado y Animaciones (Basado en proyecto Crash Course)

## 📚 Proyecto Base

Seguimos trabajando con el proyecto:

🔗 [https://github.com/mlepage/unity-crash-course](https://github.com/mlepage/unity-crash-course)

---

## 🎯 1. Barras de vida y puntaje acumulado

### a) Crear barra de vida con Slider
- En el Canvas, agregar un `Slider`.

- Quitar la opción `Interactable`.

- Renombrarlo como `BarraVida`.


### b) Script para manejar vida

```csharp
using UnityEngine;
using UnityEngine.UI;

public class VidaJugador : MonoBehaviour
{
    public Slider barraVida;
    public float vidaMaxima = 100f;
    public float vidaActual;

    void Start()
    {
        vidaActual = vidaMaxima;
        barraVida.maxValue = vidaMaxima;
        barraVida.value = vidaActual;
    }

    public void RecibirDanio(float cantidad)
    {
        vidaActual -= cantidad;
        barraVida.value = vidaActual;

        if (vidaActual <= 0)
        {
            Debug.Log("Jugador derrotado");
        }
    }
}
```

- Asociar el Slider desde el Inspector.


### c) Puntaje acumulado

- Continuar usando el HUD de Clase 4.

- Agregar botón o evento que aumente puntaje al matar enemigos o recolectar objetos.

---

## 🎬 2. Animator Controller: Transiciones de animación

### a) Crear animaciones
- Seleccionar el jugador.

- Ir al menú `Window > Animation > Animation`.

- Crear animaciones como `Idle`, `Correr`, `Golpear`.


### b) Crear Animator Controller
- Unity lo genera automáticamente con las animaciones.

- Acceder al `Animator` y definir las transiciones entre estados.

### c) Controlar animaciones con código

```csharp
Animator anim;

void Start()
{
    anim = GetComponent<Animator>();
}

void Update()
{
    float movimiento = Input.GetAxis("Horizontal");
    anim.SetFloat("Velocidad", Mathf.Abs(movimiento));
}
```

- En el `Animator`, crear un parámetro float llamado `Velocidad`.

- Usar `Blend Tree` para animar correr/pararse.

---

## 🎞️ 3. Integración de animaciones al control del personaje

- Activar animación de salto, ataque o daño según acciones.


### Ejemplo: animación al saltar

```csharp
if (Input.GetKeyDown(KeyCode.Space))
{
    anim.SetTrigger("Saltar");
}
```

- Agregar `Trigger` en el Animator y asociar transición.


---

## 💥 4. Bonus: Animaciones del HUD

### a) Animación de texto al recibir daño

- Agregar una animación en el `Text` de vidas/puntaje.

- Animar tamaño o color al recibir daño o ganar puntos.


### b) Script para activar animación

```csharp
public Animator hudAnimador;

public void MostrarImpacto()
{
    hudAnimador.SetTrigger("Impacto");
}
```

- Asignar un `Animator` al objeto de texto del HUD.

- Crear una animación simple que aumente escala o cambie color.

---

## 📌 Tarea sugerida

1. Agregar una barra de vida visual al jugador usando `Slider`.

2. Crear animaciones básicas del jugador (Idle, Correr, Saltar).

3. Controlar transiciones de animaciones desde C#.

4. Agregar una animación al HUD al recibir daño o sumar puntos.

