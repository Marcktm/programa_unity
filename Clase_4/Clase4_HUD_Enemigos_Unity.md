# Clase 4 - HUD básico y enemigos simples (Basado en proyecto Crash Course)

## 📚 Proyecto Base

Usaremos como base el proyecto descargado de:

🔗 [https://github.com/mlepage/unity-crash-course](https://github.com/mlepage/unity-crash-course)

Clonarlo o descargarlo como ZIP y abrirlo en Unity.

---

## 🎯 1. Creación de HUD básico (puntaje y vidas)

### a) Crear HUD (Heads-Up Display)
- Dentro de la escena principal, crear un `Canvas`.

- Agregar un `Text` para el puntaje.

- Agregar otro `Text` para las vidas.

- Usar `TextMeshPro` si está disponible para mejor calidad de texto.


### b) Script para actualizar HUD

```csharp
using UnityEngine;
using UnityEngine.UI;

public class HUDController : MonoBehaviour
{
    public Text textoPuntaje;
    public Text textoVidas;
    public int puntaje = 0;
    public int vidas = 3;

    public void ActualizarPuntaje()
    {
        puntaje += 10;
        textoPuntaje.text = "Puntaje: " + puntaje;
    }

    public void PerderVida()
    {
        vidas--;
        textoVidas.text = "Vidas: " + vidas;
    }
}
```

- Asociar el `HUDController` al Canvas.

- Conectar los campos de texto en el Inspector.

---

## 🛡️ 2. Spawneo de enemigos con `Instantiate()`

### a) Crear Prefab de Enemigo
- Crear un GameObject enemigo (sprite, collider, rigidbody).
- Arrastrarlo a la carpeta `Prefabs` para crear el prefab.


### b) Script para spawnear enemigos

```csharp
using UnityEngine;

public class Spawner : MonoBehaviour
{
    public GameObject enemigoPrefab;
    public float intervalo = 2f;
    private float tiempoSiguienteSpawn;

    void Update()
    {
        if (Time.time > tiempoSiguienteSpawn)
        {
            Instantiate(enemigoPrefab, transform.position, Quaternion.identity);
            tiempoSiguienteSpawn = Time.time + intervalo;
        }
    }
}
```

- Crear un objeto vacío llamado `Spawner` y asignar este script.

---

## ⏱️ 3. Control del tiempo con `Time.deltaTime`

`Time.deltaTime` representa el tiempo entre frames y ayuda a que el movimiento sea **suave** y **consistente**.

### Ejemplo: mover enemigo hacia abajo

```csharp
public float velocidad = 3f;

void Update()
{
    transform.Translate(Vector2.down * velocidad * Time.deltaTime);
}
```

- Así, el enemigo se moverá hacia abajo sin importar los FPS del dispositivo.

---

## 🕹️ 4. Proyecto Integrador: Mini Survival

### Objetivos
- Los enemigos deben spawnearse automáticamente.

- Si un enemigo toca al jugador ➔ perder una vida.

- Al llegar a 0 vidas ➔ reiniciar el juego o mostrar "Game Over".

### Ejemplo de reinicio básico

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class GameOverManager : MonoBehaviour
{
    public HUDController hud;

    void Update()
    {
        if (hud.vidas <= 0)
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name);
        }
    }
}
```

- Asociar este script a un objeto `GameManager` en la escena.

- Asignar la referencia al HUD desde el Inspector.

---

## 📌 Tarea sugerida

1. Agregar un sistema de HUD mostrando puntaje y vidas.

2. Crear un prefab de enemigo y spawnearlo periódicamente.

3. Hacer que los enemigos se muevan usando `Time.deltaTime`.

4. Implementar el reinicio automático cuando se terminan las vidas.

