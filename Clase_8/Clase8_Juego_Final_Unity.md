# Clase 8 - Revisión final y juego cerrado (Basado en proyecto Crash Course)

## 📚 Proyecto Base

Continuamos utilizando el proyecto de:
🔗 [https://github.com/mlepage/unity-crash-course](https://github.com/mlepage/unity-crash-course)

---

## 🐞 1. Pulido de bugs comunes

### a) Revisión de errores en consola
- Verificar que no existan errores de compilación ni advertencias.
- Utilizar `Debug.Log()` para identificar puntos de falla.

### b) Verificar colisiones
- Asegurarse de que los `Colliders` y `Triggers` estén bien configurados.
- Confirmar que los `Rigidbody2D` estén en objetos que se deben mover.

### c) Revisión de scripts
- Revisar scripts que estén duplicando lógica.
- Eliminar código innecesario o no utilizado.

---

## 🧱 2. Organización de assets y prefabs

### a) Estructura recomendada de carpetas

```
Assets/
├── Animations/
├── Audio/
├── Materials/
├── Prefabs/
├── Scenes/
├── Scripts/
├── Sprites/
└── UI/
```

### b) Uso correcto de prefabs
- Todos los objetos que se repitan (enemigos, ítems, decoraciones) deben ser `Prefabs`.
- Permite modificar desde un único lugar.

---

## 📦 3. Exportación del proyecto como .exe

### a) Configurar Build Settings
- Ir a `File > Build Settings`.
- Elegir plataforma: `PC, Mac & Linux Standalone`.
- Arrastrar la escena principal a la lista.
- Click en `Build` y elegir carpeta de salida.

### b) Opciones recomendadas
- Resolución fija (ej. 1280x720).
- Pantalla completa desactivada para pruebas.
- Icono personalizado si es posible.

---

## 🔁 4. Extra: integración con Git (opcional)

### a) ¿Por qué usar Git?
- Guarda versiones del proyecto.
- Permite volver atrás si algo falla.
- Facilita trabajar en equipo.

### b) Archivos a ignorar
Crear un archivo `.gitignore` con lo siguiente:

```
[Ll]ibrary/
[Tt]emp/
[Oo]bj/
[Bb]uild/
Builds/
*.csproj
*.unityproj
*.sln
*.user
.vscode/
```

---

## 🎮 Proyecto final

Tu proyecto debe incluir:
- Menú funcional
- Mecánicas básicas completas
- HUD y sonidos
- Enemigos y power-ups
- Pulido de errores
- Exportación ejecutable

---

## 📌 Tarea final

1. Revisar y corregir errores en consola.
2. Asegurarse de que el juego esté completo y funcional.
3. Organizar las carpetas del proyecto.
4. Exportar el juego como archivo ejecutable (`.exe`) para PC.
5. (Opcional) Subir el juego a [Itch.io](https://itch.io) para compartirlo públicamente.

