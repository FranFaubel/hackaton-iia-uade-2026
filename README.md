# <M09> · <TUTOR DE IA PERSONALIZADO (EDUCACION)>

> **Hackatón IIA · UADE · 3.4.257.** Este README es la plantilla del grupo. En su fork, reemplacen todo lo que está entre `< >` y borren esta nota. Las bases están en `BASES.md` y su ficha en `problematicas/`.

**Integrantes:** <Francisco_Faubel> · <Benjamin_Ortiz>
**IA declarada:** <Chat_GPT>
**Pista:**<Reglas>
**Publicación en LinkedIn:**<link>

---

## 1. Formulación y PEAS

**La pregunta.** <Para cada estudiante que termina un tema, ¿aprobará la evaluación integradora del tema? SÍ (1) significa predecimos que aprobará; NO (0) significa predecimos que no aprobará. La etiqueta real (1/0) se conoce después y sirve para comprobar si la predicción fue correcta: no entra al sistema al decidir. Una predicción SÍ puede recomendar el avance; una predicción NO, continuar con el tema. La ficha no permite afirmar que predecir la aprobación sea equivalente a medir toda la comprensión autónoma.>

| PEAS | Tutor educativo con IA |
|---|---|
| Medida de rendimiento | <Priorizar la precisión de las predicciones SÍ y controlar especificidad, por el costo de los falsos positivos; reportar también sensibilidad y exactitud. Comparar contra las etiquetas de la integradora.> |
| Entorno | <lataforma de tutoría educativa; estudiante que acaba de finalizar un tema y tiene registro de ejercicios recientes..> |
| Actuadores | <	Emitir SÍ/NO y recomendar avanzar al tema siguiente (SÍ) o permanecer repasando el actual (NO)> |
| Sensores | <Únicamente el porcentaje de aciertos registrado en los últimos diez ejercicios, disponible antes de la evaluación integradora.> |

**Objetivo y métrica.** <El objetivo real es tomar una buena decisión de avance, evitando especialmente que avance un alumno que no aprobaría la integradora y sin retener innecesariamente a quien sí aprobaría. La métrica prioritaria es precisión: de todos los SÍ pronosticados, cuántos efectivamente aprobaron. La especificidad controla la proporción de NO reales que no fueron aprobados incorrectamente; la sensibilidad señala cuántos SÍ reales detectamos. La exactitud es complementaria y se compara con una línea base. Las métricas no son el objetivo educativo, sino medidas observables de predicción en este conjunto de datos.>

## 2. El sistema

**Cómo decide.** <Cómo decide. Es un único clasificador basado en dos reglas, con umbral fijo del 70 %:
1. SI aciertos >= 70, ENTONCES predecir SÍ (1).
2. SI aciertos < 70, ENTONCES predecir NO (0).
Cómo elegimos el umbral. El 70 % no fue elegido a ciegas antes de ver las etiquetas. Se seleccionó durante el diseño, examinando solo los casos 1–14 de entrenamiento, con preferencia por evitar falsos positivos y mantener una regla simple. No hay evidencia de que 70 sea el único valor correcto; por ejemplo, 69 %, 70 % y 75 % dan la misma matriz de entrenamiento en estos datos. No ajustamos el umbral utilizando los casos 15–20 de prueba. La comparación siguiente es una comprobación de sensibilidad del umbral, no una razón para seguir ajustándolo después de ver la prueba.
Umbral	VP / FN / FP / VN en entrenamiento	Exactitud de entrenamiento	Comentario
65 %	4 / 0 / 2 / 8	85,71 %	Detecta todos los SÍ, pero produce 2 falsos positivos.
67 %	4 / 0 / 1 / 9	92,86 %	Reduce a 1 falso positivo.
70 %	3 / 1 / 0 / 10	92,86 %	No tiene falsos positivos; sacrifica un SÍ real.
75 %	3 / 1 / 0 / 10	92,86 %	Mismo resultado aquí; no demuestra superioridad.
80 %	3 / 1 / 0 / 10	92,86 %	Mismo resultado en entrenamiento, aunque puede cambiar con otros casos.>

**Variables que usa y por qué.** <Utiliza aciertos (%): es una señal de rendimiento reciente, está disponible antes de decidir y se puede aplicar igual a un caso nuevo. Descartamos pistas solicitadas, tiempo por ejercicio y temas avanzados en la semana: no intervienen en esta regla. El número de temas avanzados es especialmente riesgoso como métrica de éxito porque puede premiar avanzar sin aprender. Nunca utilizamos el resultado real como entrada: hacerlo sería fuga de información. Tampoco afirmamos que el porcentaje de aciertos mida directamente la comprensión autónoma.
>


**Cómo se corre en vivo.** <En Colab, Python o manualmente: (1) leer el porcentaje de aciertos; (2) compararlo contra 70; (3) devolver SÍ si es mayor o igual, NO en caso contrario. Archivo: m09_reglas_final.py. Ejemplo: python m09_reglas_final.py --aciertos 68. Para varios casos: python m09_reglas_final.py --lista 68,70,81,42. Para auditar el conjunto oficial: python m09_reglas_final.py --auditar. Es posible resolverlo a mano sin ninguna herramienta.>

**Dos casos de ejemplo.**

| Caso inventado | Valores | Salida del sistema |
|---|---|---|
| <A> |<Aciertos=70%> | <SÍ (el límite se incluye)> |
| <B> | <Aciertos 69%> | <NO (está por debajo del límite)> |

## 3. Medición

**Entrenamiento (casos 1–14)**

| | Predice SÍ | Predice NO |
|---|---|---|
| **Real SÍ** | VP = <3> | FN = <1> |
| **Real NO** | FP = <0> | VN = <10> |

**Prueba (casos 15–20)**

| | Predice SÍ | Predice NO |
|---|---|---|
| **Real SÍ** | VP = <4> | FN = <0> |
| **Real NO** | FP = <0> | VN = <2> |

| Métrica | Entrenamiento | Prueba |
|---|---|---|
| Exactitud | <92.86%> | <100%> |
| Precisión | <100%> | <100%> |
| Sensibilidad | <75%> | <100%> |
| Especificidad | <100%> | <100%> |

Comprobación: 4 + 0 + 0 + 2 = 6.
Métrica	Entrenamiento	Prueba
Exactitud = (VP+VN)/total	13/14 = 92,86 %	6/6 = 100 %
Precisión = VP/(VP+FP)	3/3 = 100 %	4/4 = 100 %
Sensibilidad = VP/(VP+FN)	3/4 = 75 %	4/4 = 100 %
Especificidad = VN/(VN+FP)	10/10 = 100 %	2/2 = 100 %

**Entrenamiento contra prueba.** <La exactitud de prueba supera la de entrenamiento en 7,14 puntos porcentuales. No hay caída observada en los seis casos de prueba, pero esto no permite concluir que no exista sobreajuste ni que la generalización esté garantizada: el conjunto de prueba es muy pequeño y tiene una proporción de positivos diferente (4/6, frente a 4/14 en entrenamiento). La regla comete un FN en el caso 3, que aprueba con 67 % de aciertos. No corregimos el umbral en función de ese caso de prueba ni de los resultados de prueba.

Sensibilidad del umbral fuera del entrenamiento (solo análisis descriptivo, sin cambiar la regla). Con 70 %, en prueba se obtienen 4 VP, 0 FN, 0 FP y 2 VN. Si lo bajáramos a 65 %, aparecería 1 FP en prueba (caso 19); si lo subiéramos a 80 %, aparecería 1 FN (caso 17). Por eso el rendimiento del 70 % no demuestra que cualquier otro umbral funcione igual, ni que el valor sea universal.> 


## 4. El error más caro

<4. El error más caro
Priorizamos el falso positivo (FP): el tutor pronostica SÍ, pero el estudiante no aprueba la integradora. Según la ficha, hacerlo avanzar sin dominio puede acumular vacíos de conocimiento que se manifiesten en evaluaciones posteriores. Un FN también es perjudicial: retiene a quien sí podría aprobar, con riesgo de aburrimiento y abandono. La ficha no asigna costos numéricos, por lo que nuestra prioridad es una decisión explícita del equipo, no una equivalencia estadística demostrada.

Qué cambiamos para reducir FP. Comparamos una regla inicial aciertos >= 65 con la regla definitiva aciertos >= 70 usando solo entrenamiento:
Resultado (entrenamiento)	Umbral 65 %	Umbral 70 %
VP	4	3
FN	0	1
FP	2 (casos 9 y 14)	0
VN	8	10


Subir el umbral a 70 % elimina dos falsos positivos en entrenamiento, a cambio de un falso negativo adicional (caso 3). Este intercambio es consciente y coincide con nuestra prioridad declarada. No garantiza cero FP en estudiantes nuevos.>

## 5. ¿Comparado contra qué?

**Línea base trivial.** <Línea base trivial: predecir siempre NO, porque NO es la clase mayoritaria de entrenamiento (10 de 14). Esa política se fija usando entrenamiento y se aplica sin cambios a prueba.
Métrica de referencia	Línea base: siempre NO	Nuestra regla del 70 %
Exactitud entrenamiento	10/14 = 71,43 %	13/14 = 92,86 %
Exactitud prueba	2/6 = 33,33 %	6/6 = 100 %
Sensibilidad entrenamiento	0 %	75 %
Sensibilidad prueba	0 %	100 %


En la línea base la precisión es indefinida, porque nunca predice SÍ. La mejora en exactitud es de 21,43 puntos en entrenamiento y 66,67 puntos en prueba. Esa comparación no prueba éxito educativo general: mide la clasificación de estos casos..>

| Checklist (Clase 6) | Respuesta |
|---|---|
| ¿Qué datos? | <20 casos ficticios de M09; 14 para diseñar la regla y 6 reservados para prueba. Variables disponibles en la ficha, pero el clasificador solo usa aciertos.> |
| ¿Qué métrica? | <Prioridad a precisión y control de FP, más especificidad, sensibilidad y exactitud.> |
| ¿Comparado contra qué? | <Línea base fija siempre NO (71,43 % de exactitud en entrenamiento y 33,33 % en prueba).> |
| ¿Quién lo midió? | Cálculos reproducibles realizados con asistencia de ChatGPT a partir de la ficha proporcionada; deben ser comprobados y defendidos por Francisco Faubel y Benjamin Ortiz. No afirmamos validación externa o nota del evaluador que no tengamos.> |

## 6. Riesgo: el camino completo

<Datos → modelo → decisión → consecuencia. Se observa el porcentaje de aciertos de los últimos diez ejercicios → se aplica la regla SI–ENTONCES del 70 % → se predice SÍ/NO para aprobación de la integradora y se recomienda avanzar o continuar practicando → el alumno puede avanzar bien, ser retenido pese a poder aprobar (FN) o avanzar sin estar listo (FP).

Riesgo concreto: la plataforma muestra a los padres cuántos temas avanzó el estudiante semanalmente. Si se optimizara esa cifra, podría premiarse avanzar rápido en lugar de aprender. Por eso no la usamos ni como entrada del clasificador ni como métrica de éxito. Otro riesgo es que los aciertos en ejercicios recientes no reflejen toda la preparación para la integradora: el caso 3 evidencia ese límite. Los resultados no justifican afirmar que el tutor mide la comprensión autónoma>

## 7. Bitácora

**Uso de la IA**

| # | Qué le pedimos | Qué aceptamos | Qué rechazamos y por qué |
|---|---|---|---|
| 1| <Comparar Neurona, Reglas y Agente para M09> | <Pista Reglas: decisión clara y reproducible> | <Añadir complejidad no necesaria para una clasificación binaria con pocos datos.> |
| 2 | <Diseñar y probar reglas con los casos M09.> | <Un solo clasificador que utiliza aciertos, con umbral fijo> | <Usar como entrada la etiqueta real; sería fuga de información.> |
| 3 | <Calcular matrices, métricas y línea base.	> | <Recuento separado de 14/6 y referencia siempre NO> | <Presentar el 100 % en seis casos de prueba como garantía de generalización.> |
| 4 | <Revisar el error más caro.> | <Comparar umbrales en entrenamiento y mostrar FP frente a FN> | <Ocultar el FN del caso 3 o afirmar que todos los errores cuestan lo mismo.> |
| 5 | <Corregir las objeciones del evaluador de las corridas 1–4.	> | <Un único sistema medido y ejecutable (aciertos >= 70)> | <justificación honesta de selección del umbral y sensibilidad a moverlo.> |

**Corridas contra el evaluador**

| Corrida | Nota | Agujero que encontró | Qué cambiamos |
|---|---|---|---|
| 1 | <6> | <El sistema plantea evaluar cuatro dimensiones (C, A, R y U), pero los datos de M09.csv no contienen esas variables. En las matrices de confusión se utilizó realmente la variable Accuracy, con un umbral del 70%, para decidir entre SÍ y NO. Por lo tanto, el criterio utilizado para medir los resultados no coincide completamente con el objetivo planteado para el tutor. También falta explicar cómo se obtienen los puntajes C, A, R y U para un estudiante nuevo.> | <Aclaramos que las matrices y métricas calculadas corresponden a una clasificación basada exclusivamente en Accuracy ≥ 70%. Diferenciamos ese criterio inicial del objetivo final del tutor, que es evaluar el dominio autónomo. Incorporaremos un procedimiento concreto de evaluación para obtener C, A, R y U mediante actividades y preguntas específicas. También registramos la necesidad de realizar nuevas corridas contra el evaluador.> |
| 2 | <6> | <Reconocen que las matrices miden solo Accuracy ≥ 70%, no el sistema con C, A, R y U. Entonces, ¿qué significa SÍ en su tabla: aprobar la evaluación integradora o tener 70% de aciertos? ¿Qué pasa con un alumno que aprueba la integradora pero tiene 67% de aciertos?
> | <Definimos una rúbrica de cinco niveles, establecimos los criterios de evaluación de cada dimensión y diferenciamos la regla simplificada del objetivo final. También aclaramos el uso de las pistas, el tiempo y los temas avanzados.> |
| 3 | <6> | <No se presentó evidencia suficiente de que Accuracy represente la aprobación de la evaluación integradora. Además, faltaba explicar cómo se controla la consistencia de las correcciones de la IA. La bitácora tampoco incluía la segunda corrida.> | <Incorporamos el análisis de coincidencia entre las predicciones y las etiquetas reales, explicitamos las limitaciones de los datos, propusimos un mecanismo de control de consistencia de la rúbrica y completamos el registro de las corridas anteriores.
| 4 | <10> | <En la mesa, cambiá un caso (un alumno con 70% que no aprobó). ¿Cuánto les lleva recalcular precisión y especificidad sin IA y sin el script?
> | <.> |

