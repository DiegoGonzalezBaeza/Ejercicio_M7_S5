# Ejercicio_M7_S5
Proyecto educativo

```python
from django.db import models

class Fabrica(models.Model):
    nombre = models.CharField(max_length=100)

class Producto(models.Model):
    nombre = models.CharField(max_length=100)
    descripcion = models.TextField()
    precio = models.DecimalField(max_digits=10, decimal_places=2)
    fabrica = models.ForeignKey(Fabrica, on_delete=models.CASCADE, related_name="fabricas")
```

# Relación Uno a Muchos

Definición: Una instancia de Fabrica puede estar relacionada con muchos objetos del modelo Producto, pero cada Producto solo puede estar relacionado con una Fabrica.
Cómo se establece:
En el modelo Producto, el campo fabrica es una clave foránea (ForeignKey) que apunta al modelo Fabrica.
Detalles en el código:
ForeignKey(Fabrica):

Esto conecta el modelo Producto con Fabrica.
Especifica que cada producto pertenece a una única fábrica.
on_delete=models.CASCADE:

Si se elimina una instancia de Fabrica, todos los Producto relacionados también serán eliminados (acción en cascada).
related_name="fabricas":

Permite acceder a los productos relacionados desde una instancia de Fabrica de forma más intuitiva.