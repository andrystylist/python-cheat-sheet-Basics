# python-cheat-sheet

## Subtitulos

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus malesuada scelerisque nibh, nec pellentesque nunc venenatis eget. Pellentesque fringilla sagittis pharetra. Phasellus a interdum felis. Cras scelerisque malesuada eleifend. Vestibulum ac placerat tortor. Phasellus varius sodales fringilla. Donec sed eros rhoncus, volutpat urna a, viverra odio. Quisque fermentum consectetur turpis, vel tristique ligula facilisis vitae. Integer porta sit amet dui in maximus. Suspendisse sodales mi metus, vitae accumsan velit imperdiet in. Fusce velit ligula, laoreet in ipsum a, interdum fringilla sem. Cras eu interdum dolor. Proin ut risus sollicitudin, vehicula purus cursus, sagittis nulla. Maecenas at lorem neque. Nam in massa est.

Nulla vel enim fringilla, tincidunt lorem ut, pulvinar quam. Morbi aliquet orci tellus, sit amet congue lacus varius vitae. In consectetur tristique ullamcorper. Donec nulla arcu, maximus sed leo id, malesuada congue nunc. Nunc velit neque, consequat at nibh tempus, dapibus porta nunc. Ut eu nunc ultrices, pharetra purus viverra, vehicula leo. Maecenas vel erat eu nunc vestibulum iaculis in id nulla. Pellentesque vehicula sapien tellus, ut hendrerit mauris cursus ut. Integer ac iaculis enim. Ut feugiat sed ipsum eu ullamcorper. Vestibulum malesuada malesuada tortor, imperdiet malesuada sapien porttitor non.

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
