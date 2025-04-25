# Clase 10 - Modelado complejo y jerarquización en Blender

## 🎯 Objetivo de la clase

Aprender a modelar objetos de juego más detallados, organizarlos con jerarquías (padre-hijo), y exportarlos correctamente para su uso en Unity.

---

## 🧱 1. Modelado de objetos de juego (munición, recargas, power-ups)

### a) Crear un objeto más complejo

Ejemplo: Modelar una **poción mágica**.

1. `Shift + A > Mesh > UV Sphere` (base de la botella).
2. `Shift + A > Mesh > Cylinder` (cuello de la botella).
3. `Shift + A > Mesh > Cone` (tapa).

Usar `S`, `G` y `R` para posicionar y escalar cada parte.

### b) Aplicar modificadores básicos

- **Subdivision Surface:** suavizar mallas.
- **Mirror:** simetría en modelos.

Recordá siempre aplicar la escala (`Ctrl + A > Apply > Scale`) antes de exportar.

---

## 🏗️ 2. Agrupación por jerarquías (Padre-Hijo)

### ¿Por qué usar jerarquías?

- Permite mover, rotar o escalar todo el objeto como un conjunto.
- Facilita exportaciones organizadas a Unity.

### Cómo hacerlo:

1. Seleccionar primero los objetos hijos (ej: tapa y cuello).
2. Luego seleccionar el objeto principal (ej: cuerpo de la botella).
3. Presionar `Ctrl + P > Object` para hacer una relación padre-hijo.

Ahora, al mover el objeto padre, los hijos lo siguen.

---

## 🛠️ 3. Exportación a formatos FBX y OBJ

### a) Configuración para exportar

1. Ir a `File > Export > FBX (.fbx)` o `.obj`.
2. Activar:
   - **Apply Transform**
   - **Only Selected Objects**
3. Ajustar ejes:
   - Forward: `-Z Forward`
   - Up: `Y Up`

### b) Buenas prácticas

- Exportar todo el conjunto (padre e hijos).
- Mantener nombres descriptivos en Blender.
- Guardar directamente en la carpeta `Assets/Models` del proyecto Unity.

---

## 🖌️ 4. Bonus: exportar con mapeo UV simple

El mapeo UV permite que las texturas se proyecten correctamente sobre el modelo.

### Mapeo UV básico:

1. Seleccionar el objeto.
2. Entrar a `Modo Edición (Tab)`.
3. Seleccionar todo (`A`).
4. `U > Smart UV Project`.

Esto genera automáticamente un UVMap que Unity podrá utilizar para aplicar materiales o texturas.

---

## 📌 Tarea sugerida

1. Modelar un objeto compuesto (por ejemplo, una poción o un cofre).
2. Aplicar jerarquías (padre-hijo) para organizar las partes.
3. Realizar un mapeo UV básico para preparación de texturizado.
4. Exportar en formato `.fbx` o `.obj`.
5. Importar el modelo en Unity y colocarlo en una escena.

