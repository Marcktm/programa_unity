# Clase 7 - Entorno completo e integración de sonido (Basado en proyecto Crash Course)

## 📚 Proyecto Base

Continuamos usando como base el repositorio:
🔗 [https://github.com/mlepage/unity-crash-course](https://github.com/mlepage/unity-crash-course)

---

## 🌄 1. Diseño del escenario jugable

### a) Creación del entorno
- Agregar un fondo (sprite o imagen).
- Incluir elementos como plataformas, paredes o zonas de peligro.
- Usar `Tilemap` si querés construir con bloques.

### b) Organización jerárquica
- Crear una carpeta vacía en la Jerarquía llamada `Escenario`.
- Agrupar allí todos los elementos del nivel para mantener orden.

### c) Capas de colisión
- Configurar `Layer` y `Tag` para distinguir enemigos, jugador, y objetos.

---

## 🔊 2. Sonidos de ambiente y efectos

### a) Añadir AudioSource
- Seleccionar un objeto (ej: cámara o GameManager).
- Agregar componente `AudioSource`.
- Cargar un archivo de sonido `.wav` o `.mp3` en la carpeta `Assets/Sounds`.

### b) Reproducir sonido de ambiente

```csharp
void Start()
{
    GetComponent<AudioSource>().Play();
}
```

- Activá `Loop` si querés que se repita indefinidamente.

---

## 🎧 3. Efectos de colisión y sonidos de acción

### a) Sonido al recoger power-up

```csharp
public AudioClip sonidoPowerUp;
public AudioSource fuente;

void OnTriggerEnter2D(Collider2D other)
{
    if (other.CompareTag("Jugador"))
    {
        fuente.PlayOneShot(sonidoPowerUp);
        Destroy(gameObject);
    }
}
```

- Asignar los clips desde el Inspector.

### b) Sonido de golpe o daño

```csharp
public AudioClip golpe;
public AudioSource audioJugador;

public void ReproducirGolpe()
{
    audioJugador.PlayOneShot(golpe);
}
```

- Llamar a esta función desde el evento de daño.

---

## 🎼 4. Música de fondo

- Crear un objeto `AudioManager` o usar la `Main Camera`.
- Asignar un `AudioSource` con volumen bajo y Loop activado.
- Reproducir música en `Start()` como ambientación.

---

## 🔁 5. Uso del sistema de audio de Unity

### AudioClip vs AudioSource

| Componente    | Función                                                  |
|---------------|-----------------------------------------------------------|
| AudioClip     | Archivo de sonido en sí (MP3, WAV).                       |
| AudioSource   | Reproductor que ejecuta el AudioClip en una ubicación.   |

Podés tener un `AudioSource` global o múltiples para objetos individuales.

---

## 📌 Tarea sugerida

1. Agregar música de fondo a la escena principal.
2. Incluir efectos de sonido para:
   - Recolección de objetos
   - Daño al jugador
   - Aparición de enemigos
3. Diseñar el entorno jugable completo, agregando obstáculos y decoraciones.
4. Organizar la escena usando vacíos padres (`GameObject > Create Empty`).

