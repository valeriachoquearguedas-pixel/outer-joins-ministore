# Outer Joins - MiniStore

**Nombre:** Valeria Choque

---

# Explicación de las consultas

## 1. ¿Por qué usaste LEFT JOIN para la Consulta 1 y no INNER JOIN? ¿Qué se perdería si usaras INNER JOIN?

Porque la tabla principal de la consulta es 'productos' y necesito mostrar todos los productos del catálogo, incluso aquellos que nunca fueron vendidos. Con LEFT JOIN, todas las filas de la tabla 'productos' aparecen en el resultado. 
Cuando un producto no tiene una venta asociada, las columnas de la tabla 'ventas' aparecen con valores NULL. Si hubiera utilizado un **INNER JOIN**, solo aparecerían los productos que tienen al menos una venta registrada. 
En este ejercicio no se mostrarían los productos:

- 108 – Hub USB-C 7p
- 109 – Parlante Bluetooth
---

## 2. ¿Por qué usaste RIGHT JOIN para la Consulta 2? ¿Qué tabla está a la izquierda y cuál a la derecha?

Utilicé RIGHT JOIN porque el objetivo es mostrar todas las ventas registradas, incluso aquellas que no tienen un producto correspondiente en el catálogo.
- La tabla de la izquierda es 'productos'.
- La tabla de la derecha es 'ventas'.

El RIGHT JOIN garantiza que todas las filas de la tabla 'ventas' aparezcan en el resultado.

Gracias a esto es posible identificar la venta con `producto_id = 999`, ya que ese producto no existe en el catálogo y las columnas provenientes de 'productos' aparecen con valores NULL.

---

## 3. ¿Qué representan los valores NULL en cada resultado?

Los valores NULL indican que no existe una coincidencia entre las tablas. Cuando venta_id es NULL, significa que el producto nunca fue vendido.
Cuando 'producto_id' de la tabla 'productos' es NULL, significa que existe una venta cuyo producto no figura en el catálogo.
Esto representa un registro huérfano o un posible error en la carga de datos.

---

## 4. ¿Cuándo usarías FULL OUTER JOIN en un caso real de negocio?

Utilizaría FULL OUTER JOIN cuando necesite realizar una auditoría completa de los datos y no quiera perder información de ninguna de las dos tablas.

Por ejemplo para:

- Detectar productos que nunca fueron vendidos.
- Encontrar ventas con productos inexistentes.
- Comparar información entre dos sistemas antes de una migración.
- Verificar la consistencia de los datos antes de generar reportes.
