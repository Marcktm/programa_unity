# Clase 3 - Programación básica en C# y eventos en Unity

## 🧠 1. Sintaxis de C#, variables, condicionales

### a) Variables en C#

```csharp
int edad = 20;
float velocidad = 3.5f;
string nombre = "Marcos";
bool estaSaltando = false;
```

### b) Estructuras condicionales

```csharp
if (edad >= 18)
{
    Debug.Log("Es mayor de edad");
}
else
{
    Debug.Log("Es menor de edad");
}
```

- `==` Igualdad
- `!=` Distinto
- `&&` Y lógico
- `||` O lógico

---

## 🎮 2. Eventos de colisión

### a) `OnCollisionEnter` – Detectar colisiones físicas

```csharp
void OnCollisionEnter2D(Collision2D col)
{
    Debug.Log("Colisión con: " + col.gameObject.name);
}
```

- Este evento se dispara cuando un objeto con Rigidbody2D y Collider2D colisiona con otro.

### b) `OnTriggerEnter` – Detectar entrada en zonas Trigger

```csharp
void OnTriggerEnter2D(Collider2D other)
{
    if (other.CompareTag("Jugador"))
    {
        Debug.Log("¡El jugador entró en la zona!");
    }
}
```

- Asegurate de marcar `Is Trigger` en el Collider para que esto funcione.

---

## 🧩 3. Componentes y su manipulación por código

### a) Cambiar color desde el código

```csharp
void Start()
{
    GetComponent<SpriteRenderer>().color = Color.red;
}
```

### b) Cambiar posición de un GameObject

```csharp
void Update()
{
    transform.position = new Vector3(0, 2, 0);
}
```

### c) Acceder y modificar componentes

```csharp
Rigidbody2D rb;

void Start()
{
    rb = GetComponent<Rigidbody2D>();
    rb.gravityScale = 2;
}
```

---

## 🌀 4. Avanzado: patrones de movimiento programados

### a) Movimiento oscilante con `Mathf.Sin`

```csharp
public float velocidad = 2f;
public float amplitud = 3f;

void Update()
{
    float nuevaY = Mathf.Sin(Time.time * velocidad) * amplitud;
    transform.position = new Vector3(transform.position.x, nuevaY, transform.position.z);
}
```

### b) Movimiento en círculo

```csharp
public float radio = 2f;
public float velocidadAngular = 2f;

void Update()
{
    float x = Mathf.Cos(Time.time * velocidadAngular) * radio;
    float y = Mathf.Sin(Time.time * velocidadAngular) * radio;
    transform.position = new Vector3(x, y, 0);
}
```

---

## 📌 Tarea sugerida

1. Crear un objeto que cambie de color al colisionar con otro.
2. Usar `OnTriggerEnter2D` para activar un evento (mensaje, sumar puntos, etc.).
3. Programar un objeto con un patrón de movimiento (circular u oscilante).
4. Practicar estructura `if/else` modificando comportamientos según variables.
