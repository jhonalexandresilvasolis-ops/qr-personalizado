# 🌴 Generador QR Personalizado — Butiá UTU Rocha

QR artístico generado con Python: colores institucionales, palmeras Butiá dibujadas con geometría real, texto, logo incrustado en el centro y verificación de contraste WCAG automática.

<div align="center">

![Ejemplo de QR generado](qr_butia_realista.png)

*QR funcional que apunta a [utu-rocha.netlify.app](https://utu-rocha.netlify.app)*

</div>

---

## 💡 ¿Por qué esto existe?

Este QR nació como complemento de un rediseño web para mi institución educativa. Un QR genérico en blanco y negro no transmite nada — uno con los colores institucionales, el símbolo de la butiá (palmera nativa de Rocha) y el logo de UTU sí.

El desafío técnico fue lograr que el QR sea **visualmente llamativo y siga siendo escaneable** — dos objetivos que se contradicen si no se manejan bien.

---

## ✨ Qué hace el generador

- 🎨 **Módulos QR con colores** — azul institucional y verde butiá alternados
- 🌅 **Fondo con gradiente radial** e irradiación solar (rayos decorativos)
- 🌴 **Palmeras Butiá dibujadas con geometría vectorial** via `cairocffi` — tronco, hojas, racimo de frutos en distribución esférica de 3 capas con brillo y sombras
- 🔘 **Ojos del QR circulares** (en lugar de los cuadrados estándar)
- 🏷️ **Texto "UTU"** tipografiado sobre el QR
- 🖼️ **Logo incrustado en el centro** (aprovecha la corrección de error H del estándar QR)
- 📊 **Métricas de calidad automáticas**: contraste WCAG 2.0, verificación de escaneabilidad, cumplimiento AA/AAA

---

## 🛠️ Librerías utilizadas

| Librería | Uso |
|---|---|
| `qrcode` | Generación de la matriz QR con corrección de error alta (H) |
| `Pillow (PIL)` | Composición de imágenes, gradientes, texto y capas RGBA |
| `numpy` | Gradiente radial y cálculos de luminancia WCAG |
| `cairocffi` | Dibujo vectorial de las palmeras (tronco, hojas, frutos) |
| `pyzbar` | Validación de escaneabilidad del QR generado *(opcional)* |

> `cairocffi` y `pyzbar` son opcionales — si no están instalados, el script igual funciona sin las palmeras y sin validación automática.

---

## 🚀 Cómo usarlo

### 1. Clonar el repositorio

```bash
git clone https://github.com/jhonalexandresilvasolis-ops/qr-personalizado.git
cd qr-personalizado
```

### 2. Instalar dependencias

```bash
pip install qrcode pillow numpy
# Opcionales (palmeras + validación):
pip install cairocffi pyzbar
```

### 3. Configurar tu URL y logo

Editá las líneas al final del archivo `generarQR.py`:

```python
URL = "https://tu-sitio.com/"       # URL que va a codificar el QR
LOGO = "logos/tu_logo.png"          # Ruta a tu logo (opcional)
```

### 4. Ejecutar

```bash
python generarQR.py
```

El QR se guarda en `output/qr_butia_realista.png` a 300 DPI, listo para imprimir.

---

## 📁 Estructura del proyecto

```
qr-personalizado/
├── generarQR.py       # Script principal
├── qr_butia_realista.png  # Ejemplo de salida
├── logos/
│   └── logo_utu.png       # Logo usado en el ejemplo
└── output/                # Carpeta de salida generada automáticamente
```

---

## 📊 Métricas del ejemplo generado

- **Contraste WCAG 2.0**: calculado automáticamente al generar
- **Corrección de error**: nivel H (30%) — permite que el logo cubra hasta un 30% del QR sin romper la lectura
- **Resolución de salida**: 300 DPI
- **Frutos en el racimo**: 65, distribuidos en 3 capas esféricas

---

## 📝 Notas

El QR del ejemplo apunta a [utu-rocha.netlify.app](https://utu-rocha.netlify.app), el rediseño web del que forma parte. Para adaptarlo a cualquier otro contexto, solo cambiás la URL, el logo y los colores en las constantes de la clase `GeneradorQROptimizado`.
