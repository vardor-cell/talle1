# Taller 1: Supervisión de la contratación pública de bienes (SECOP II)

**MINE-4101 Ciencia de Datos Aplicada, Universidad de los Andes, 2026-20**

## Integrantes

- Jorge Aleks Acosta Villate (202324675)
- Mateo Bernal Bonil (202510037)

## Objetivo

Ayudar a la oficina de control interno de una entidad del Estado a focalizar la supervisión de contratos de compraventa y suministro de bienes. Para eso identificamos qué características conocidas al momento de la firma (valor, modalidad, destino del gasto, sector, tipo de entidad, duración pactada) se asocian con desviaciones del plan inicial: adición de plazo, subejecución del presupuesto y cierre sin liquidar.

## Alcance

- **Fuente:** contratos de bienes publicados en SECOP II entre 2019 y 2025 (196.391 registros, 36 atributos).
- **Periodo analizado:** contratos firmados entre **2021 y 2024** (119.505). Se excluyen 2019–2020 por la baja calidad de registro durante la transición a SECOP II y la contratación de emergencia por COVID-19, y 2025 porque la mayoría de esos contratos aún no tiene un desenlace observable. La justificación con datos está en la sección 1.3 del notebook.
- Los valores monetarios se expresan en pesos constantes de 2024 (IPC, DANE).

## Conclusiones principales (insights)

1. **El valor del contrato es el principal factor de riesgo.** La adición de plazo pasa de 2,7 % en el quintil de menor valor a 15,2 % en el de mayor valor. Al controlar por las demás variables, cada vez que el valor se multiplica por 10, las probabilidades de adición se duplican (OR ≈ 2,1).
2. **El efecto de la modalidad se explica en buena parte por el tamaño.** La licitación pública tiene 25 % de adiciones frente a 6 % en mínima cuantía, pero a igual valor y duración la diferencia no es significativa (p ≈ 0,92). El régimen especial sí tiene un efecto propio: 73 % de contratos sin liquidar (OR ≈ 2,6).
3. **Los suministros subejecutan más del doble que las compraventas** (17,5 % vs 7,5 %), consistente con la figura de monto agotable. Las compraventas, en cambio, tienden más a la adición de plazo.
4. **La duración pactada es una alerta temprana:** la desviación va de 5 % (≤ 15 días) a ~16 % (> 90 días) y a 45 % en contratos de más de un año.
5. **Criterios sin valor práctico:** pyme, consorcio (se explica por el valor), género del representante legal y año de firma. Algunos son estadísticamente significativos, pero con tamaños de efecto despreciables.
6. **Con reglas simples** (valor ≥ $159 millones, duración > 90 días en licitación, subasta o menor cuantía, y sectores Trabajo y Planeación) se supervisaría el 29 % de los contratos, que concentra el 47 % de las desviaciones y el 91 % del valor. Estas reglas se validaron en 2024 con umbrales calculados en 2021–2023.
7. **El 37 % de los contratos terminados no registra facturación en SECOP II**, lo que es por sí mismo un problema de trazabilidad para el control.

Las recomendaciones completas y las limitaciones están en [`informe_ejecutivo.md`](informe_ejecutivo.md) y en la sección 4 del notebook.

## Organización del repositorio

```
.
├── README.md
├── requirements.txt
├── informe_ejecutivo.md                 # Punto 4: informe ejecutivo para control interno
├── data/                                # Aquí se descarga el dataset (no se versiona)
└── notebooks/
    └── taller1_secop_bienes.ipynb       # Puntos 1 a 4 (implementación + interpretación)
```

El notebook sigue la estructura del taller:

1. **Entendimiento inicial de los datos**: dimensiones, tipos, top 5 de atributos con análisis univariado, problemas de calidad y su tratamiento, elección del periodo.
2. **Estrategia de análisis**.
3. **Desarrollo**: construcción de las variables de desviación, análisis bivariado, 16 hipótesis contrastadas (chi-cuadrado, z de proporciones, Mann-Whitney, Spearman y regresión logística) con tamaño del efecto y corrección de Holm, validación temporal y reglas de focalización.
4. **Resultados**: criterios recomendados y limitaciones.

## Instrucciones de ejecución

Requiere Python 3.10 o superior.

```bash
git clone <url-del-repositorio>
cd <repositorio>
python -m venv .venv
source .venv/bin/activate        # En Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/taller1_secop_bienes.ipynb
```

Ejecutar todas las celdas en orden (*Kernel → Restart & Run All*). La ejecución completa toma menos de un minuto. El dataset no se incluye en el repositorio: la primera vez que se ejecuta, el notebook lo descarga automáticamente desde [Google Drive](https://drive.google.com/file/d/1R0pSXh2bgCoPKcXlAlafdavVwvzZX6AQ/view?usp=sharing) a `data/secop_bienes.parquet` usando `gdown` (requiere conexión a internet). También se puede descargar a mano y ponerlo en esa carpeta.

## Dependencias

pandas, numpy, pyarrow, scipy, statsmodels, scikit-learn, matplotlib, seaborn, jinja2, jupyter, gdown (ver `requirements.txt`). Probado con pandas 2.2 y 3.0.
