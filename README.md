# SVM-y-Multiple-Testing

Este proyecto analiza la expresión génica de distintos tipos de cáncer utilizando métodos de inferencia estadística y modelos de clasificación basados en Máquinas de Vectores de Soporte (SVM).

## Objetivos

- Comparar la expresión de genes entre distintas clases de cáncer mediante pruebas estadísticas (*t-test* y ANOVA).
- Aplicar métodos de corrección por comparaciones múltiples (Bonferroni, Holm y Benjamini–Hochberg) para controlar falsos positivos.
- Seleccionar genes significativamente diferentes entre clases.
- Entrenar y evaluar modelos **SVM** con distintos *kernels* (lineal, polinomial y radial) usando los genes más relevantes.
- Comparar el desempeño de los tres modelos con métricas de clasificación (accuracy, precision, recall y F1-score).

## Dataset

El conjunto de datos **Khan** contiene información de expresión génica estandarizada:

- **Número de muestras:** 83  
- **Número de variables (genes):** 2308  
- **Variable de salida:** `y`, que toma valores de **1 a 4**, representando distintos tipos de cáncer.  
- **Tipo de variables:** cuantitativas (niveles de expresión de genes).

Cada observación corresponde a una muestra biológica (por ejemplo, tejido) con la expresión medida para miles de genes.

## Metodología

1. **Análisis estadístico inicial**
   - Se verificó la ausencia de huecos en los datos.
   - Se compararon las medias de expresión entre las clases 2 y 4 mediante pruebas *t*.
   - Se aplicaron métodos de corrección de valores *p*:
     - Bonferroni (más estricto)
     - Holm–Bonferroni (moderado)
     - Benjamini–Hochberg (FDR, más flexible)

2. **Extensión a las cuatro clases**
   - Se utilizó **ANOVA (f_oneway)** para identificar genes con diferencias significativas entre las clases 1, 2, 3 y 4.

3. **Selección de características**
   - Se eligieron los genes con los valores *p* ajustados más bajos (más significativos) para construir los modelos predictivos.

4. **Modelado con SVM**
   - Se separaron los datos en entrenamiento (70%) y prueba (30%).
   - Se entrenaron tres modelos SVM:
     - Kernel lineal  
     - Kernel polinomial (grado 3)  
     - Kernel radial (RBF)
   - Se calcularon métricas de desempeño:
     - Accuracy  
     - Precision  
     - Recall  
     - F1-score  
   - Se compararon las matrices de confusión de cada modelo.


[Base de datos](https://github.com/NelsonAbad/SVM-y-Multiple-Testing/blob/fc5918699e06d19e24ea1a6d1ad9735d1f54ab64/A3.1%20Khan.csv)

[Reporte en .ipynb](https://github.com/NelsonAbad/SVM-y-Multiple-Testing/blob/fc5918699e06d19e24ea1a6d1ad9735d1f54ab64/A3.1%20SVM%20y%20Multiple%20Testing.ipynb)

[Reporte en HTML](A3.1%20SVM%20y%20Multiple%20Testing.html)
