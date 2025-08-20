# 📉 TelecomX – Parte 2: Predicción de Cancelación (Churn)

Este repositorio resume el trabajo del **Challenge TelecomX (Parte 2)** enfocado en la **predicción de cancelación de clientes (churn)**.  
El objetivo es desarrollar modelos de Machine Learning que permitan anticipar qué clientes tienen mayor probabilidad de cancelar y proponer estrategias de retención basadas en los resultados.

El informe completo, con visualizaciones, correlaciones y desempeño de modelos, se encuentra en el notebook del proyecto.

---

## 📂 Estructura del proyecto
- `Notebooks` → Notebook principal con el análisis y modelado: **TelecomX_2.ipynb**  
- `Data` → Dataset limpio exportado desde la Parte 1: **telecom_clean.csv**  
- `README.md` → Este documento.  

El notebook realiza:
- Limpieza y preprocesamiento de datos (eliminación de columnas irrelevantes, imputación de nulos, codificación con OneHotEncoder).  
- Exploración de balance de clases y correlaciones.  
- Análisis dirigido (contrato vs churn, gasto total vs churn).  
- Entrenamiento de modelos (Regresión Logística y Random Forest).  
- Evaluación con métricas y visualización de matrices de confusión/curvas ROC.  
- Interpretación de importancia de variables y conclusiones estratégicas.

---

## ▶️ Cómo ejecutar el proyecto
1. Abre el notebook en **Google Colab** o **Jupyter Notebook**.  
2. Ejecuta las celdas en orden. Se cargará `telecom_clean.csv`, se aplicará el preprocesamiento (encoding, imputación, estandarización cuando necesario) y luego se entrenarán los modelos.  
3. Revisa la sección final con métricas de desempeño y conclusiones.  
---

## 📊 Resultados principales
**Tamaño de muestra:** 5.813 clientes (después de limpiar registros `no answer`).  

### 1) Balance de clases (CustomerChurn)
- **Stayed (0):** ~71%  
- **Churned (1):** ~26%  
- **Eliminados (-1 / no answer):** ~3%  

Existe **desbalance moderado**, mitigado con `class_weight="balanced"` en los modelos.

### 2) Modelos evaluados
- **Regresión Logística (con normalización):**  
  - Accuracy: ~74%  
  - Precision: ~51%  
  - Recall: ~78%  
  - F1: ~61%  
  - ROC-AUC: ~84%  

- **Random Forest (sin normalización):**  
  - Accuracy: ~78%  
  - Precision: ~62%  
  - Recall: ~46%  
  - F1: ~53%  
  - ROC-AUC: ~82%  

### 3) Insights de variables
- **Contrato month-to-month** → principal predictor de churn.  
- **Tenure (antigüedad)** bajo → alto riesgo de cancelación.  
- **Cargos mensuales altos** → asociados a mayor deserción.  
- **Ausencia de TechSupport y OnlineSecurity** → duplica probabilidad de churn.  
- **Método de pago Electronic check** → mayor volatilidad.  

---

## 🧭 Conclusiones e Insights
1. **Contratos mensuales** son el mayor factor de riesgo → clientes con este plan muestran ~40% churn.  
2. **Clientes nuevos (Tenure ≤ 12 meses)** presentan mayor deserción → etapa crítica de onboarding.  
3. **Servicios de soporte y seguridad (TechSupport, OnlineSecurity)** reducen churn casi a la mitad → gran oportunidad de cross-sell defensivo.  
4. **Método de pago Electronic check** correlaciona con más cancelaciones → migrar a métodos automáticos mejora retención.  
5. **Altos cargos mensuales** sin beneficios adicionales generan deserción → sensibilidad al precio percibido.  

---

## 🧩 Recomendaciones
- **Migración de contratos:** diseñar campañas para mover clientes de *month-to-month* a contratos anuales/bianuales con descuentos o bundles.  
- **Early-life care:** programas de fidelización y contacto proactivo en los primeros 90–120 días.  
- **Cross-sell estratégico:** ofrecer **TechSupport** y **OnlineSecurity** como paquetes de fidelización.  
- **Incentivar métodos de pago automáticos:** perks para quienes migren de Electronic check a débito automático/tarjeta.  
- **Gestión de valor/precio:** revisar pricing de planes **Fiber optic** y cargos altos, comunicando beneficios tangibles.  

---

## ❗ Posibles problemas y soluciones
- **Valores nulos (NaN):** fueron tratados con imputación (mediana/moda).  
- **Desbalance de clases:** mitigado con `class_weight="balanced"`, pero se sugiere probar técnicas de oversampling (SMOTE).  
- **Overfitting potencial en Random Forest:** ajustar hiperparámetros (n_estimators, max_depth).  

---

## 🚀 Tecnologías utilizadas
- **Python 3.x**  
- `pandas` / `numpy` → manipulación y preparación de datos  
- `matplotlib` / `seaborn` → visualizaciones  
- `scikit-learn` → pipelines de ML, modelos y métricas  
- Google Colab / Jupyter → entorno de ejecución  

---

## 👩‍💻 Autora
Proyecto desarrollado por **Josefina Magini**  
Challenge Final – *Data Science Student*  
TelecomX — Parte 2
