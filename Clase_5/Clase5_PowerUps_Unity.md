# Clase 5 - Power-Ups y Objetos Interactivos (Basado en proyecto Crash Course)

## 📚 Proyecto Base

Continuamos usando el proyecto descargado de:

🔗 [https://github.com/mlepage/unity-crash-course](https://github.com/mlepage/unity-crash-course)

---

## 🎯 1. Recolección de objetos

### a) Crear un Prefab de Power-Up
- Crear un objeto nuevo (ej: esfera brillante o estrella).

- Agregarle un `CircleCollider2D` y marcarlo como **Is Trigger**.

- Crear un prefab y guardarlo en la carpeta `Prefabs`.


### b) Script para recolectar Power-Ups

```csharp
using UnityEngine;

public class PowerUp : MonoBehaviour
{
    void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Jugador"))
        {
            Debug.Log("¡Power-Up recolectado!");
            Destroy(gameObject);
        }
    }
}
```

- Asignar el tag `Jugador` al personaje principal.

- Asociar el script al prefab del Power-Up.

---

## ⚡ 2. Activación de efectos por contacto

Podemos hacer que al recoger un Power-Up:
- Se aumente la velocidad.

- Se aumenten las vidas.

- Se active un escudo temporal.

### Ejemplo: Aumentar velocidad del jugador

```csharp
public class PowerUpVelocidad : MonoBehaviour
{
    public float aumentoVelocidad = 2f;
    public float duracion = 5f;

    void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Jugador"))
        {
            PlayerMovement movimiento = other.GetComponent<PlayerMovement>();
            if (movimiento != null)
            {
                StartCoroutine(AumentarVelocidad(movimiento));
            }
            Destroy(gameObject);
        }
    }

    IEnumerator AumentarVelocidad(PlayerMovement movimiento)
    {
        movimiento.velocidad *= aumentoVelocidad;
        yield return new WaitForSeconds(duracion);
        movimiento.velocidad /= aumentoVelocidad;
    }
}
```

- Este script supone que el jugador tiene un script `PlayerMovement` con una variable `velocidad`.


---

## 🎁 3. Diseño de cajas sorpresa y recompensas

Podés crear una caja sorpresa que al romperse o tocarla, libere un Power-Up.

### Caja sorpresa básica

- Crear un objeto "Caja".

- Asociar un Collider (Trigger).

- Al detectar colisión, instanciar un Power-Up aleatorio.

```csharp
public class CajaSorpresa : MonoBehaviour
{
    public GameObject[] powerUps;

    void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Jugador"))
        {
            int index = Random.Range(0, powerUps.Length);
            Instantiate(powerUps[index], transform.position, Quaternion.identity);
            Destroy(gameObject);
        }
    }
}
```

- Crear varios prefabs de Power-Ups diferentes y asignarlos en el Inspector.


---

## 📦 4. Extra: Sistema de inventario simple

Crear un inventario para guardar los objetos recolectados.

### Inventario básico

```csharp
using System.Collections.Generic;
using UnityEngine;

public class Inventario : MonoBehaviour
{
    public List<string> objetosRecolectados = new List<string>();

    public void AgregarObjeto(string nombreObjeto)
    {
        objetosRecolectados.Add(nombreObjeto);
        Debug.Log("Objeto agregado al inventario: " + nombreObjeto);
    }
}
```

- Al recolectar un Power-Up, llamar a `AgregarObjeto(nombre)` para registrarlo.


Ejemplo de llamada:

```csharp
GameObject jugador = GameObject.FindWithTag("Jugador");
jugador.GetComponent<Inventario>().AgregarObjeto("PowerUp Velocidad");
```

---

## 📌 Tarea sugerida

1. Crear 2 tipos de Power-Ups diferentes (ej: velocidad y vidas extra).

2. Crear una Caja Sorpresa que suelte un Power-Up aleatorio.

3. Implementar un pequeño inventario que guarde el nombre de los Power-Ups recolectados.

4. Probar la activación de efectos temporales usando corrutinas (`IEnumerator`).

