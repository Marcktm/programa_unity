# Clase 11 - Animaciones 3D con keyframes y curvas en Blender

## 🎯 Objetivo de la clase

Aprender a crear animaciones básicas utilizando **keyframes** y **curvas de animación** en Blender, y exportarlas para su uso en Unity.

---

## 🎬 1. Keyframes, Timeline y animación básica

### a) ¿Qué es un keyframe?

- Un **keyframe** es un marcador que guarda el valor de una propiedad (posición, rotación, escala) en un momento específico del tiempo.

Cuando Blender interpola entre keyframes, crea la animación.

### b) Crear una animación simple

1. Seleccionar un objeto.
2. Posicionar el objeto en el frame 1.
3. Presionar `I > Location` para insertar un keyframe de posición.
4. Moverse al frame 60.
5. Mover el objeto y presionar nuevamente `I > Location`.
6. Reproducir animación (`Espacio`).

---

## 📈 2. Uso de curvas de animación (Graph Editor)

### a) ¿Qué es el Graph Editor?

- Es una herramienta para editar suavizados y aceleraciones en las animaciones.

### b) Editar curvas

1. Abrir el `Graph Editor` en una nueva ventana.
2. Seleccionar una curva (por ejemplo, `X Location`).
3. Modificar los manejadores para cambiar la aceleración/desaceleración.

### c) Consejos

- Curvas suaves = animaciones naturales.
- Curvas abruptas = movimientos rápidos o bruscos.

---

## 📦 3. Exportación de animaciones hacia Unity

### a) Guardar las acciones

- Cada animación (acción) debe estar guardada en el `Action Editor` en Blender.
- Poner nombres descriptivos (ej: `Idle`, `Bounce`, `Rotate`).

### b) Exportar como FBX

1. `File > Export > FBX (.fbx)`.
2. Opciones:
   - **Bake Animation:** Activado.
   - **Apply Transform:** Activado.
   - **Only Selected Objects:** Activado.

Al importar en Unity:
- Cada `Action` de Blender aparecerá como una animación en el `Animator`.

---

## 🛠️ 4. Ejemplos prácticos

### a) Animar un objeto que sube y baja (Idle animado)

```plaintext
Frame 1: posición inicial (0, 0, 0)
Frame 30: posición arriba (0, 2, 0)
Frame 60: vuelve a posición inicial (0, 0, 0)
```

Loop de subida y bajada.

### b) Rotación infinita (rueda o moneda)

1. Frame 1: Rotación Z en 0°.
2. Frame 60: Rotación Z en 360°.
3. Insertar keyframes en ambos puntos.

En Unity, configurar la animación en loop.

---

## 📌 Tarea sugerida

1. Crear una animación simple de movimiento (por ejemplo, un objeto que sube y baja).
2. Crear una animación de rotación continua.
3. Exportar ambas animaciones en un único archivo `.fbx`.
4. Importar en Unity y configurar las animaciones en el Animator.

