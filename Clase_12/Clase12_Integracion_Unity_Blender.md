# Clase 12 - Integración Unity + Blender

## 🎯 Objetivo de la clase

Aprender a importar modelos 3D animados de Blender hacia Unity, utilizarlos dentro de escenas y enlazarlos a la lógica de juego.

---

## 🔄 1. Importación de modelos 3D

### a) Opciones de importación

- Podés **exportar** desde Blender a `.fbx` o `.obj`.
- Unity también puede **abrir directamente archivos `.blend`**, pero se recomienda `.fbx` para mayor compatibilidad.

### b) Procedimiento de exportación

En Blender:

1. Seleccionar el objeto (y asegurarse de aplicar transformaciones con `Ctrl + A`).
2. `File > Export > FBX (.fbx)`.
3. Opciones importantes:
   - **Apply Transform:** Activado.
   - **Only Selected Objects:** Activado.
   - **Bake Animation:** Activado si contiene animaciones.
   - **Forward: -Z Forward**, **Up: Y Up**.

En Unity:

1. Copiar el `.fbx` en la carpeta `Assets/Models`.
2. Unity generará automáticamente el modelo y sus animaciones.

---

## 🎥 2. Uso de modelos animados dentro del juego

### a) Crear un prefab

1. Arrastrar el modelo importado desde `Assets` hacia la jerarquía.
2. Ajustar tamaño, posición y rotación.
3. Crear un `Prefab` para reutilizar.

### b) Configuración de Animator

- Unity detecta las animaciones del `.fbx`.
- Crear un `Animator Controller`.
- Asignar animaciones a estados (`Idle`, `Run`, `Rotate`, etc.).

### c) Control de animaciones por código

```csharp
Animator anim;

void Start()
{
    anim = GetComponent<Animator>();
    anim.Play("Idle");
}

void Update()
{
    if (Input.GetKeyDown(KeyCode.Space))
    {
        anim.Play("Salto");
    }
}
```

---

## 🛠️ 3. Interacción entre scripts y objetos importados

### a) Detectar colisiones

Si importaste un objeto para ser un ítem recolectable:

```csharp
void OnTriggerEnter2D(Collider2D other)
{
    if (other.CompareTag("Jugador"))
    {
        Debug.Log("Recolectado un objeto 3D");
        Destroy(gameObject);
    }
}
```

Recordá asignar correctamente los `Tags` en los objetos.

---

## 📦 4. Consejos de optimización

- Modelar en **low poly** para mejorar rendimiento.
- Reducir la cantidad de materiales usados en cada modelo.
- Verificar que las escalas de Blender coincidan con las de Unity (1 unidad = 1 metro).

---

## 📌 Desafío de integración

**Crear un objeto 3D animado en Blender y usarlo como Power-Up en Unity.**

Pasos:

1. Modelarlo en Blender.
2. Aplicar una animación básica (por ejemplo, rotación continua).
3. Exportarlo como `.fbx`.
4. Importarlo en Unity.
5. Hacer que el jugador pueda recolectarlo y sumar puntos.

---

