# Clase 15 - Personalización y estética del jugador en Unity

## 🎯 Objetivo de la clase

Permitir al jugador modificar su apariencia, guardar sus elecciones, y aplicar los cambios automáticamente en cada escena.

---

## 🎨 1. Menú de personalización

### a) Crear menú con botones de elección

- Crear una nueva UI con:
  - Colores disponibles (botones o íconos).
  - Skins o accesorios (si se usan sprites o modelos diferentes).
  - Botón de confirmar y volver al menú.

### b) Aplicar la personalización

```csharp
public class Personalizador : MonoBehaviour
{
    public SpriteRenderer jugador;
    public Color[] colores;

    public void CambiarColor(int index)
    {
        jugador.color = colores[index];
        PlayerPrefs.SetInt("ColorSeleccionado", index);
    }
}
```

- Asignar los colores en el Inspector.
- Llamar la función desde cada botón de color.

---

## 💾 2. Guardado de estética del jugador

### a) Guardar con PlayerPrefs

```csharp
PlayerPrefs.SetInt("ColorSeleccionado", index);
PlayerPrefs.Save();
```

### b) Aplicar al iniciar

```csharp
void Start()
{
    int colorIndex = PlayerPrefs.GetInt("ColorSeleccionado", 0);
    jugador.color = colores[colorIndex];
}
```

- Esto asegura que se conserve la personalización entre escenas o sesiones.

---

## 👕 3. Skins alternativos (opcional)

- En vez de cambiar color, podés cambiar directamente el sprite del personaje.

```csharp
public Sprite[] skins;

public void CambiarSkin(int index)
{
    jugador.sprite = skins[index];
    PlayerPrefs.SetInt("SkinSeleccionado", index);
}
```

---

## 🧩 4. Aplicación automática en cada escena

### a) Usar un objeto persistente

```csharp
void Awake()
{
    DontDestroyOnLoad(this.gameObject);
}
```

- Esto mantiene el objeto de personalización vivo entre escenas.

### b) O aplicar siempre al cargar una escena

- Crear un script que busque el personaje y le aplique el color o sprite almacenado.

---

## 📌 Tarea sugerida

1. Crear un menú de personalización con al menos 3 colores.
2. Guardar la elección del jugador con PlayerPrefs.
3. Aplicar el color automáticamente al cargar la escena del juego.
4. (Opcional) Usar sprites diferentes como skins alternativos.

