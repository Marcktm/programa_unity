# Clase 13 - Menús y navegación entre escenas en Unity

## 🎯 Objetivo de la clase

Aprender a crear un menú principal funcional con botones para iniciar juego, ver créditos y salir, y configurar la navegación entre escenas dentro de Unity.

---

## 🖥️ 1. Crear menú principal

### a) Crear nueva escena

- `File > New Scene` y guardar como `MenuPrincipal`.

### b) Añadir elementos UI

- Crear un objeto `Canvas`.
- Agregar:
  - `Text` o `TextMeshPro` como título.
  - Tres `Buttons`: Jugar, Créditos, Salir.

### c) Estética básica

- Ajustar tamaño y posición de los botones.
- Usar imágenes personalizadas si se desea.
- Aplicar fuente con TextMeshPro.

---

## 🔁 2. Navegación entre escenas

### a) Agregar escenas al Build

- `File > Build Settings`
- Click en `Add Open Scenes` para agregar:
  - `MenuPrincipal`
  - `Juego`
  - `Creditos` (si existe)

### b) Script de navegación

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class MenuManager : MonoBehaviour
{
    public void Jugar()
    {
        SceneManager.LoadScene("Juego");
    }

    public void Creditos()
    {
        SceneManager.LoadScene("Creditos");
    }

    public void Salir()
    {
        Application.Quit();
    }
}
```

- Asignar este script a un objeto vacío (por ejemplo, `MenuManager`).
- En cada botón, enlazar la función correspondiente desde el Inspector (`OnClick()`).

---

## 📽️ 3. Animaciones de UI

### a) Transiciones suaves

- Usar `Animator` en el Canvas o en botones individuales.
- Crear transiciones entre estados: `Idle`, `Seleccionado`, `Presionado`.

### b) Activar animaciones por código (opcional)

```csharp
public Animator animadorUI;

public void MostrarMenu()
{
    animadorUI.SetTrigger("Mostrar");
}
```

---

## 🧪 4. Escena de créditos (opcional)

- Crear escena `Creditos`.
- Agregar texto con los nombres del equipo o agradecimientos.
- Botón para volver al menú (`SceneManager.LoadScene("MenuPrincipal")`).

---

## 📌 Tarea sugerida

1. Crear una nueva escena llamada `MenuPrincipal` con UI funcional.
2. Agregar botones: `Jugar`, `Créditos`, `Salir`.
3. Crear la escena de `Créditos` con un botón de retorno.
4. Configurar navegación con `SceneManager`.
5. (Opcional) Añadir animaciones suaves de transición en los botones del menú.

