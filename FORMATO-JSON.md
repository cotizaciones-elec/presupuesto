# Formato del JSON de cotización

La página abre un archivo `.json`. El archivo debe incluir el nombre del cliente y una lista de productos. En la tabla se pueden editar el precio unitario, el descuento y el proveedor; el total se recalcula al editar.

Al abrir el archivo con **Abrir cotización**, la página guarda el permiso del archivo para que **Guardar cambios** pueda intentar sobrescribirlo; el navegador puede pedir autorización. Si el navegador no permite sobrescribir el archivo, o se abrió con el selector alternativo, **Guardar cambios** descarga el JSON actualizado. También puedes usar **Descargar copia JSON** para conservar el original.

## Nombre del archivo

Usa este formato:

```text
nombre_del_cliente_d_m_a.json
```

Donde `d` es el día, `m` el mes y `a` el año de creación de la cotización. Por ejemplo, para **Constructora Ejemplo**, creada el 6 de noviembre de 2026:

```text
constructora_ejemplo_6_11_2026.json
```

El nombre del cliente del archivo debe coincidir con el valor de `cliente` en el JSON. Para formar el nombre, usa minúsculas, reemplaza espacios por guiones bajos y omite acentos.

## Estructura

```json
{
  "cliente": "Constructora Ejemplo",
  "productos": [
    {
      "producto": "Taladro inalámbrico",
      "cantidad": 2,
      "marca": "Bosch",
      "modelo": "GSB 18V-50",
      "imagen": "imagenes/taladro.jpg",
      "fichaTecnica": "https://ejemplo.com/ficha-taladro.pdf",
      "precioUnitario": 3499.00,
      "descuentoPorcentaje": 10,
      "proveedor": "Ferretería Central"
    }
  ]
}
```

## Campos

| Campo | Descripción |
|---|---|
| `cliente` | Nombre del cliente. Debe coincidir con el nombre incluido en el archivo. |
| `productos` | Lista de productos de la cotización. |
| `producto` | Nombre o descripción del producto. |
| `cantidad` | Cantidad cotizada; debe ser un número igual o mayor que cero. |
| `marca` | Marca del producto. |
| `modelo` | Modelo del producto. |
| `imagen` | URL o ruta de la imagen. Se muestra la imagen en la tabla y se puede abrir en otra pestaña al hacer clic; puede dejarse como cadena vacía (`""`). |
| `fichaTecnica` | URL o ruta del documento de ficha técnica. Puede dejarse como cadena vacía (`""`). |
| `precioUnitario` | Precio de una unidad; debe ser un número igual o mayor que cero. |
| `descuentoPorcentaje` | Descuento porcentual de `0` a `100`. Si se omite, se usa `0`. |
| `proveedor` | Nombre del proveedor. |

El total por producto se calcula así:

```text
cantidad × precioUnitario × (1 − descuentoPorcentaje ÷ 100)
```

Guarda el archivo con codificación UTF-8 y extensión `.json`. Asegúrate de usar comillas dobles y no agregar comas después del último elemento de un objeto o lista.
