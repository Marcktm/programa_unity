# Clase 14 - Guardado y carga de progreso en Unity

## 🎯 Objetivo de la clase

Aprender a guardar y recuperar información como puntaje, niveles desbloqueados y preferencias del jugador, utilizando PlayerPrefs y serialización JSON.

---

## 💾 1. Guardado con PlayerPrefs

`PlayerPrefs` permite guardar valores simples como `int`, `float` y `string`.

### a) Guardar datos

```csharp
PlayerPrefs.SetInt("PuntajeMaximo", 500);
PlayerPrefs.SetString("NivelDesbloqueado", "Nivel2");
PlayerPrefs.Save(); // Opcional pero recomendado
```

### b) Leer datos

```csharp
int puntaje = PlayerPrefs.GetInt("PuntajeMaximo", 0);
string nivel = PlayerPrefs.GetString("NivelDesbloqueado", "Nivel1");
```

- El segundo parámetro es el valor por defecto si no existe.

### c) Eliminar datos

```csharp
PlayerPrefs.DeleteAll();
```

---

## 🧠 2. Guardado con JSON (avanzado)

Usamos JSON para guardar estructuras más complejas como configuraciones o múltiples variables juntas.

### a) Crear una clase para guardar datos

```csharp
[System.Serializable]
public class DatosJuego
{
    public int puntaje;
    public int vidas;
    public string nivel;
}
```

### b) Serializar y guardar en un archivo

```csharp
using System.IO;
using UnityEngine;

public class GuardadoJSON : MonoBehaviour
{
    public void GuardarDatos()
    {
        DatosJuego datos = new DatosJuego();
        datos.puntaje = 300;
        datos.vidas = 3;
        datos.nivel = "Nivel2";

        string json = JsonUtility.ToJson(datos);
        File.WriteAllText(Application.persistentDataPath + "/datos.json", json);
    }

    public void CargarDatos()
    {
        string path = Application.persistentDataPath + "/datos.json";
        if (File.Exists(path))
        {
            string json = File.ReadAllText(path);
            DatosJuego datos = JsonUtility.FromJson<DatosJuego>(json);
            Debug.Log("Puntaje cargado: " + datos.puntaje);
        }
    }
}
```

---

## 🔐 3. Carga automática al iniciar

Agregar la llamada a `CargarDatos()` en el método `Start()` de algún objeto persistente (`GameManager`).

---

## 👤 4. (Avanzado) Sistema de login ficticio

Crear una entrada donde el jugador ingresa su nombre y se guarda para personalizar la experiencia.

### a) Guardar el nombre

```csharp
public void GuardarNombre(string nombre)
{
    PlayerPrefs.SetString("NombreJugador", nombre);
}
```

### b) Mostrar en pantalla

```csharp
string nombre = PlayerPrefs.GetString("NombreJugador", "Jugador");
textoBienvenida.text = "¡Bienvenido, " + nombre + "!";
```

---

## 📌 Tarea sugerida

1. Implementar guardado de puntaje y nivel usando `PlayerPrefs`.
2. Crear una clase de datos y guardar información usando JSON.
3. Cargar los datos automáticamente al iniciar el juego.
4. (Opcional) Crear un sistema de ingreso de nombre con bienvenida personalizada.
