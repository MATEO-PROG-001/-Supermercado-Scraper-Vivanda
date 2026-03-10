#  Supermercado Scraper — Vivanda (CORD API)

Scraper de productos alimenticios para el supermercado **Vivanda** usando la API pública de [CORD.pe](https://cord.pe). Extrae precios, descuentos, marcas y disponibilidad por categoría, y exporta todo a un archivo Excel listo para analizar.

---

##  ¿Qué hace este script?

1. **Obtiene todas las categorías** disponibles en la tienda desde la API de CORD.
2. **Filtra subcategorías** de interés dentro del área de alimentos (lácteos, bebidas, carnes, frutas, etc.).
3. **Extrae los productos** de cada subcategoría con paginación automática.
4. **Calcula descuentos** comparando precio de lista vs precio final.
5. **Exporta los datos** a un archivo `.xlsx` sin duplicados por SKU.

---

## Categorías cubiertas
Se decidio trabajar de forma experimental con las categorias que cubren la parte de alimentos y bebidadas no alcoholicas.

| Categoría |
|-----------|       
| Lácteos y Huevos |
| Abarrotes |
| Quesos y Fiambres |
| Bebé e Infantil |
| Carnes, Aves y Pescados |
| Congelados |
| Frutas y Verduras |
| Pollo Rostizado y Comidas Preparadas |
| Panadería y Pastelería |
| Bebidas |
| Desayunos |

---

## Datos extraídos por producto

| Campo | Descripción |
|---|---|
| `CATEGORIA` | Categoría principal |
| `SUBCATEGORIA` | Subcategoría del producto |
| `sku` | Código único del producto |
| `nombre` | Nombre del producto |
| `marca` | Marca |
| `precio_lista` | Precio regular (sin descuento) |
| `precio_final` | Precio de venta actual |
| `descuento_monto` | Ahorro en soles (S/) |
| `descuento_porcentaje` | Porcentaje de descuento |
| `disponible` | Si está en stock (`VERDADERO` / `FALSO`) |
| `fecha_scraping` | Fecha en que se ejecutó el script |
| `tienda` | Nombre de la tienda (`Vivanda`) |

---

## Instalación

```bash
# Clona el repositorio
git clone https://github.com/MATEO-PROG-001/-Supermercado-Scraper-Vivanda.git
cd tu-repo

# Instala las dependencias
pip install requests pandas openpyxl
```

---

## Uso

```bash
python scraper.py
```

El script genera automáticamente el archivo **`supermercado_alimentos.xlsx`** en el directorio actual.

---

## Estructura del proyecto

```
.
├── scraper.py                  # Script principal
├── supermercado_alimentos.xlsx # Output generado (ignorado por git)
└── README.md
```

---

## Configuración

En la parte superior del script puedes ajustar las siguientes variables:

```python
STORE_ID = "496509ff-eaf8-4be8-bdb0-9fad838779ec"  # ID de la tienda en CORD
TIENDA   = "Vivanda"                                 # Nombre de la tienda
```

Para scrapear otra tienda disponible en CORD, basta con cambiar el `STORE_ID`.

---

## Notas

- Se incluye un `time.sleep(0.3)` entre requests para no saturar la API.
- Los duplicados se eliminan por `sku` antes de exportar.
- La API no requiere autenticación (pública).

---

## Licencia

MIT — libre para usar, modificar y distribuir.

## Contexto académico

Este proyecto fue desarrollado con fines de aprendizaje y para enriquecer mi portafolio personal. 
Su objetivo es practicar técnicas de web scraping, consumo de APIs REST y manejo de datos con Python.
No tiene ningún fin comercial
