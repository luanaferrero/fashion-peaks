# Guía de Uso en Google Colab: Proyecto Fashion Peaks

Esta carpeta contiene todos los archivos necesarios para ejecutar y entrenar los modelos de **Fashion Peaks** en **Google Colab** de forma ordenada, sin errores de rutas ni dependencias faltantes.

---

## 📁 Contenido de esta Carpeta (`Fashion_Peaks_Colab`)

- **Notebooks de trabajo (Nuevos y mejorados)**:
  1. `01_nuevo_crear_corpus_colab.ipynb`: Generador unificado de espectros e imágenes (soporta modo `v1_linea`, `v2_sombreado` y `v3_regresion`).
  2. `02_nuevo_entrenamiento_clasificacion.ipynb`: Entrenamiento de la CNN de clasificación con división real Train / Val / Test (70/15/15) y checkpointing.
  3. `02_nuevo_entrenamiento_regresion.ipynb`: Entrenamiento de la CNN para **Regresión Continua de Área** (solución al problema del rango 9250 a 17250).
  4. `03_nuevo_evaluar_y_metricas.ipynb`: Comparación de modelos, métricas (MAE, RMSE, $R^2$), gráficas de dispersión y matrices de confusión.

- **Datos y Modelos incluidos**:
  - `fileBase_2000x1900.dat` y `fileCesio_2000x1900.dat`: Datos brutos de espectrometría gamma Monte Carlo.
  - `imagenes_entrenamiento/`: 2000 imágenes pre-generadas con labels clasificados en 40 intervalos.
  - `imagenes_entrenamiento_regresion/`: 2000 imágenes pre-generadas con labels continuos de área ($0$ a $20.000$).
  - `modelos_guardados/`: Contiene `modelo_original_profesor.pth` y recibirá los nuevos modelos entrenados.

---

## 🚀 Paso a Paso para Usar en Google Colab

### Paso 1: Subir la carpeta a Google Drive
1. Abrí tu [Google Drive](https://drive.google.com/).
2. Arrastrá y soltá la carpeta completa **`Fashion_Peaks_Colab`** en tu unidad principal (`Mi unidad` / `MyDrive`).
   > *Ruta esperada en Drive*: `/content/gdrive/MyDrive/Fashion_Peaks_Colab`

### Paso 2: Abrir los Notebooks en Colab
1. Dentro de tu Google Drive, entrá a la carpeta `Fashion_Peaks_Colab`.
2. Hacé clic derecho sobre el notebook que quieras correr (por ejemplo, `02_nuevo_entrenamiento_regresion.ipynb`) y seleccioná **Abrir con > Google Colaboratory**.
3. **Activar Acelerador por GPU (Opcional pero recomendado)**:
   - En el menú superior de Colab, andá a: `Entorno de ejecución` > `Cambiar tipo de entorno de ejecución`.
   - En *Acelerador de hardware*, elegí **T4 GPU** y guardá.

### Paso 3: Flujo de Ejecución Recomendado

Dado que las imágenes ya se encuentran generadas dentro de la carpeta:
1. **Entrenar Regresión**: Abrir y ejecutar todas las celdas de `02_nuevo_entrenamiento_regresion.ipynb`.
   - Demora aproximada: 1 a 2 minutos con GPU (o ~4 minutos con CPU).
   - Generará y guardará: `modelos_guardados/modelo_regresion_mejorado.pth`.
2. **Entrenar Clasificación (Opcional para comparar)**: Ejecutar `02_nuevo_entrenamiento_clasificacion.ipynb`.
   - Generará y guardará: `modelos_guardados/modelo_clasificacion_mejorado.pth`.
3. **Evaluar y Comparar**: Ejecutar `03_nuevo_evaluar_y_metricas.ipynb` para ver el gráfico comparativo y comprobar cómo la regresión resuelve la confusión en el rango 9250 - 17250.
