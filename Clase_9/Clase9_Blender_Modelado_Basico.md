# Clase 9 - Introducción a Blender y modelado básico

## 🎯 Objetivo de la clase

Introducir el uso de **Blender** como herramienta de modelado 3D, y preparar modelos básicos para su uso dentro de Unity.

---

## 🧰 1. Instalación y exploración de Blender

### a) Descarga e instalación

- Sitio oficial: [https://www.blender.org/download/](https://www.blender.org/download/)
- Disponible para Windows, macOS y Linux.
- Recomendado instalar la versión **más reciente**.

### b) Primeros pasos en la interfaz

- **Viewport 3D:** área de trabajo para modelar.
- **Toolbar (izquierda):** herramientas de transformación.
- **Outliner (arriba derecha):** jerarquía de objetos.
- **Properties (abajo derecha):** configuración del objeto activo.
- **Timeline:** para animaciones.

### c) Atajos útiles

- `G` – mover
- `S` – escalar
- `R` – rotar
- `X/Y/Z` – restringir a eje
- `Tab` – cambiar entre modo objeto y modo edición
- `Shift + A` – añadir nuevo objeto

---

## 🧱 2. Modelado básico: objetos de salud o power-ups

### a) Crear un objeto simple

1. Presionar `Shift + A > Mesh > UV Sphere` o `Cube`.
2. Escalar con `S` y mover con `G`.
3. Usar `Ctrl + A > Apply > Scale` para aplicar escala final.

### b) Editar vértices

1. Entrar en `Modo Edición` (`Tab`).
2. Seleccionar vértices, caras o aristas.
3. Modificar con herramientas de mover (`G`), escalar (`S`) o extruir (`E`).

---

## 🎨 3. Principios de low poly y jerarquías

### a) ¿Qué es low poly?

- Es un estilo con **pocos polígonos**, ideal para juegos.
- Reduce carga gráfica, mejora rendimiento en dispositivos móviles.

### b) Consejos

- Usar figuras simples.
- Evitar subdivisiones innecesarias.
- Optimizar mallas para no sobrecargar Unity.

### c) Jerarquías en objetos

- Unir objetos mediante `Ctrl + P` (Padre-Hijo).
- Organiza componentes complejos, por ejemplo: un ítem con efecto brillante.

---

## 🖌️ 4. Extra: añadir materiales y colores básicos

### a) Crear un nuevo material

1. Seleccionar el objeto.
2. Ir a la pestaña `Material Properties` y crear nuevo.
3. Cambiar color en `Base Color`.

### b) Aplicar múltiples materiales (opcional)

- Seleccionar caras específicas en Modo Edición.
- Asignar diferentes materiales a cada grupo de caras.

---

## 📦 5. Exportar para usar en Unity

- Ir a `File > Export > FBX (.fbx)` o `.obj`.
- Opciones recomendadas:
  - **Apply Transform**: Activado
  - **Only Selected Objects**: Activado
  - **Forward: -Z Forward**, **Up: Y Up** (compatibilidad con Unity)

Guardar en la carpeta `Assets/Models` de tu proyecto Unity.

---

## 📌 Tarea sugerida

1. Descargar e instalar Blender.
2. Modelar un objeto simple: una esfera, una estrella o un cubo.
3. Aplicar un color básico como material.
4. Exportarlo en `.fbx` y cargarlo en tu proyecto de Unity.
5. Usar el objeto en una escena dentro de Unity como decorativo o power-up.

