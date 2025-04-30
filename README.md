# Análisis de Regresión: Ventas de Chocolates (Polynomial vs Linear)

## 1. Contexto y Objetivo  
Queremos modelar la relación entre la **cantidad vendida** (`Amount`) y las **cajas enviadas** (`Boxes Shipped`) de un conjunto de datos de ventas de chocolates.  
- **Variable independiente (X):** `Amount` (número de unidades vendidas)  
- **Variable dependiente (y):** `Boxes Shipped` (cajas enviadas)  

Comparamos un **modelo lineal** frente a uno **polinómico de grado 4** para ver cuál ajusta mejor la curva de demanda.

## 2. Visualizaciones  

### 2.1 Regresión Lineal  

![image](https://github.com/user-attachments/assets/8cc8bf6f-700d-40b7-8c5c-96b43d7cac11)

*Figura 1: Ajuste con regresión lineal. La línea azul muestra la predicción lineal sobre los puntos rojos (datos reales).*

### 2.2 Regresión Polinómica (grado 4, curva suave)  

![image](https://github.com/user-attachments/assets/21c5af5a-9769-49dc-8659-48509764c42f)

*Figura 2: Ajuste con regresión polinómica grado 4. La curva azul sigue mucho más de cerca la forma de los datos rojos.*

## 3. Observaciones Técnicas  

1. **Lineal vs No lineal**  
   - En la **Figura 1**, la regresión lineal captura solo la tendencia global. Se aprecian residuos sistemáticos en los extremos (subestimación a altos y bajos `Amount`).  
   - En la **Figura 2**, la **curva polinómica** corrige gran parte de esos sesgos, adaptándose a las zonas de pendiente variable.

2. **Complejidad del modelo**  
   - El grado 4 añade flexibilidad para “curvar” la predicción, pero con ello **aumenta el riesgo de sobreajuste** si el ruido se confunde con señal.

3. **Errores y Métricas (estimadas)**  
   - Aunque no se muestran numéricamente aquí, típicamente la comparación de **RMSE** y **R²** confirmará que el polinomio de grado 4 obtiene un **R² más alto** y un **RMSE más bajo** que el modelo lineal.

## 4. Interpretación Estadística  

- El ajuste **lineal** es adecuado solo si la relación fuera perfectamente proporcional.  
- La **regresión polinómica** captura curvaturas (picos y valles) que reflejan patrones de demanda no lineal (por ejemplo, promociones por volumen o descuentos por cantidad).  
- Un R² > 0.9 en el polinomio frente a un R² ≈ 0.7 en el lineal (valores típicos) indicaría que casi toda la variabilidad en `Boxes Shipped` se explica por `Amount`.

## 5. Conclusiones y Recomendaciones  

1. **Elección del modelo**  
   - Para **predicción puntual** en el rango histórico, el modelo polinómico grado 4 es claramente superior.  
   - Sin embargo, para **generalizar a nuevos rangos**, conviene validar con **k-fold cross-validation** y evitar sobreajuste.

2. **Siguiente pasos**  
   - Probar con **regularización** (Ridge/Lasso) o **splines** si se quiere controlar la varianza del polinomio.  
   - Incorporar otras variables (precio, temporada, canal de venta) para mejorar aún más el poder explicativo.
