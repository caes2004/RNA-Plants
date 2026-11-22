# 🌿 Identificador de hojas con CNN

Página web que reconoce **185 especies de árboles** a partir de la foto de una hoja, tomada con el celular. La predicción se hace en el navegador con TensorFlow.js.

- **Modelo:** MobileNetV2 con *transfer learning* (Keras/TensorFlow), exportado a TensorFlow.js.
- **Dataset:** [LeafSnap](http://leafsnap.com/dataset/), de Kumar et al. (2012), *Leafsnap: A Computer Vision System for Automatic Plant Species Identification*, ECCV.

## Estructura

```
hojas-cnn/
├── index.html          ← la página (cámara + predicción)
└── model/              ← aquí van los archivos que genera el notebook
    ├── model.json
    ├── group1-shard*.bin
    └── labels.json
```

## Pasos

### 1. Entrenar el modelo (Google Colab)
1. Abre `entrenar_cnn_hojas.ipynb` en https://colab.research.google.com (Archivo → Subir notebook).
2. Ve a **Entorno de ejecución → Cambiar tipo de entorno → GPU T4**.
3. Ejecuta **Entorno de ejecución → Ejecutar todas**. Tarda unos 30–45 minutos.
4. Al final se descarga `modelo_web.zip`. Guarda también las gráficas y métricas para el informe.

### 2. Poner el modelo junto a la página
Descomprime `modelo_web.zip` **dentro de la carpeta `model/`**.

### 3. Publicar en GitHub Pages (el enlace que pide el profesor)
1. Crea un repositorio público en GitHub, por ejemplo `hojas-cnn`.
2. Sube `index.html` y la carpeta `model/` (*Add file → Upload files*).
3. Ve a **Settings → Pages → Branch: `main` / root → Save**.
4. En 1–2 minutos queda en: `https://TU-USUARIO.github.io/hojas-cnn/`

> La cámara del celular solo funciona con **HTTPS**, y GitHub Pages ya lo trae. Si abres `index.html` con doble clic, el modelo no carga: hay que servirlo desde una URL.

### Probar en el computador antes de publicar
```bash
cd hojas-cnn
python -m http.server 8000
# abrir http://localhost:8000
```

## Consejos para la foto
- Una sola hoja, centrada, ocupando la mayor parte del cuadro.
- Fondo claro y liso (una hoja de papel blanco funciona muy bien).
- Buena luz y sin sombras fuertes.
