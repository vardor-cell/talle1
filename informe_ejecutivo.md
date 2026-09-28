# Informe ejecutivo: focalización de la supervisión de contratos de bienes

**Para:** Oficina de Control Interno
**Base:** 119.505 contratos de compraventa y suministro de bienes publicados en SECOP II, firmados entre 2021 y 2024 (valores en pesos constantes de 2024)

## El problema

El equipo de supervisión no puede hacerle seguimiento cercano a cada contrato. Buscamos qué características conocidas **al momento de la firma** anticipan que un contrato se desvíe del plan inicial, para concentrar el esfuerzo donde más rinde.

Medimos tres tipos de desviación:

| Desviación | Tasa | Base |
|---|---|---|
| Adición de plazo | 7,9 % | Todos los contratos |
| Subejecución (pagado < 90 % del valor) | 13,0 % | Contratos terminados con facturación registrada |
| Terminado o cerrado sin liquidar | 56,5 % | Contratos terminados o cerrados |

## Hallazgos principales

1. **El valor del contrato es el mejor predictor.** La adición de plazo pasa de 2,7 % en el 20 % de contratos más pequeños a 15,2 % en el 20 % más grande. Controlando por las demás variables, cada vez que el valor se multiplica por 10, las probabilidades de adición se duplican.
2. **La modalidad pesa menos de lo que parece.** La licitación pública tiene 25 % de adiciones frente a 6 % en mínima cuantía, pero a igual valor y duración la diferencia no es significativa. La excepción es el **régimen especial**, con 73 % de contratos sin liquidar (2,6 veces más probabilidades que la mínima cuantía).
3. **Compraventas y suministros fallan de forma distinta.** Las compraventas se retrasan más; los **suministros subejecutan más del doble** (17,5 % vs 7,5 %), algo esperable en contratos de monto agotable, pero que inmoviliza presupuesto.
4. **La duración pactada es una alerta temprana.** La desviación pasa de 5 % en contratos de 15 días o menos a ~16 % en los de más de 90 días, y llega a 45 % en los de más de un año.
5. **Inversión y entidades territoriales** tienen más contratos sin liquidar (+7 y +12 puntos porcentuales).
6. **No sirven para focalizar:** si el proveedor es pyme o consorcio, el género del representante legal ni el año de firma. Sus diferencias son despreciables o desaparecen al controlar por el valor.

## Criterios de focalización recomendados

| Prioridad | Criterio | Enfoque de la supervisión |
|---|---|---|
| 1 | Valor ≥ **$159 millones** (percentil 80) | Integral |
| 2 | Duración pactada > 90 días en licitación, subasta inversa o menor cuantía | Cronograma y ejecución |
| 3 | Duración pactada > 1 año | Integral |
| 4 | Suministros de valor alto | Seguimiento financiero y liberación oportuna de saldos |
| 5 | Régimen especial y entidades territoriales | Liquidación y cierre |
| 6 | Destino inversión | Cronograma |
| 7 | Sectores Trabajo y Planeación | Integral |

**Impacto esperado** (reglas calculadas con 2021–2023 y probadas en contratos de 2024): con los criterios 1, 2 y 7 se supervisaría el **29 % de los contratos**, que concentra el **47 % de las desviaciones** y el **91 % del valor contratado**. Esos contratos se desvían 1,64 veces más que el promedio.

## Recomendación adicional

El 37 % de los contratos terminados no tiene facturación registrada en SECOP II. Recomendamos exigir a los supervisores el registro de pagos y liquidaciones en la plataforma; sin esa información, cualquier control de ejecución financiera queda incompleto.

## Limitaciones

- La subejecución solo se puede medir en contratos con pagos registrados (63 % de los terminados).
- No todos los contratos deben liquidarse por ley; el indicador de "sin liquidar" sobrestima el incumplimiento.
- El dataset no incluye adiciones en valor, que son una fuente importante de sobrecostos.
- Los resultados muestran asociaciones, no causas. La capacidad predictiva es moderada (AUC 0,67): los criterios ordenan el riesgo, pero no reemplazan el criterio del supervisor.
- Se excluyeron 2019–2020 (registro incompleto, transición a SECOP II y emergencia COVID) y 2025 (contratos aún en ejecución).
