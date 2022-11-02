# python-cheat-sheet

## Subtitulos

### Sub-Subtitulos

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

```python
class Producto:
    next_id: int = 1

    def __init__(self, nombre: str, precio: float) -> None:
        self.id = Producto.next_id
        self.nombre = nombre
        self.precio = precio
        Producto.next_id += 1

    def __repr__(self) -> str:
        return f"""Producto(id={self.id}, nombre={self.nombre}, precio={self.precio})"""
```
