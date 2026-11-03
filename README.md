# <M09> · <TUTOR DE IA PERSONALIZADO (EDUCACION)>

> **Hackatón IIA · UADE · 3.4.257.** Este README es la plantilla del grupo. En su fork, reemplacen todo lo que está entre `< >` y borren esta nota. Las bases están en `BASES.md` y su ficha en `problematicas/`.

**Integrantes:** <Francisco Faubel> · <Benjamin Ortiz>
**IA declarada:** <Chat GPT>
**Pista:** <Reglas >
**Publicación en LinkedIn:** <link>

---

## 1. Formulación y PEAS

**La pregunta.** <¿El estudiante realmente comprendió los conocimientos y es capaz de aplicarlos de manera autónoma, sin depender de herramientas de inteligencia artificial o ayuda externa?
SÍ significa que el estudiante demuestra comprensión conceptual, puede explicar su razonamiento y resolver ejercicios nuevos sin asistencia externa.
NO significa que todavía no existen evidencias suficientes de aprendizaje autónomo: puede responder correctamente, pero presenta dificultades para explicar, justificar o aplicar los conocimientos por sí mismo.>

| PEAS | Tutor educativo con IA |
|---|---|
| Medida de rendimiento | <Nivel de comprensión conceptual, capacidad de resolver problemas nuevos, justificación del razonamiento, transferencia de conocimientos y retención a largo plazo.> |
| Entorno | <Plataforma educativa personalizada donde interactúan estudiantes, contenidos, evaluaciones y tutor de IA.> |
| Actuadores | <Generar ejercicios personalizados, realizar preguntas de seguimiento, solicitar justificaciones, brindar explicaciones y adaptar la dificultad.> |
| Sensores | <Respuestas, procedimientos, tiempo de resolución, errores, justificaciones, desempeño en evaluaciones sin asistencia y evolución del estudiante.> |

**Objetivo y métrica.** <Que el estudiante comprenda y pueda aplicar los conocimientos de manera autónoma, sin depender de una IA para resolver las actividades.No buscamos que simplemente apruebe un ejercicio, sino que pueda demostrar que aprendió.
La métrica principal de nuestro sistema será el porcentaje de dominio autónomo del contenido, cuyo objetivo es determinar si el estudiante realmente comprendió lo aprendido y si es capaz de aplicarlo sin depender de herramientas externas o de inteligencia artificial.

Para calcularlo, proponemos dividir la evaluación en cuatro dimensiones, asignándoles diferentes ponderaciones según la importancia que tienen para demostrar un aprendizaje real:

Comprensión conceptual (25%): evalúa si el estudiante puede explicar los conceptos con sus propias palabras y demostrar que entiende qué está haciendo. Le asignamos un 25% porque comprender la teoría es la base necesaria para poder aplicar cualquier conocimiento.
Aplicación práctica (30%): mide la capacidad de resolver ejercicios y situaciones nuevas utilizando los conocimientos adquiridos. Le damos el mayor peso, un 30%, porque consideramos que la verdadera comprensión se demuestra principalmente cuando el alumno puede utilizar lo aprendido en problemas que no conoce previamente.
Justificación del razonamiento (25%): analiza si el estudiante puede explicar los pasos que siguió, justificar sus decisiones y argumentar por qué llegó a determinado resultado. Le asignamos un 25% porque no alcanza con obtener una respuesta correcta: también es importante comprender el procedimiento que permitió llegar a ella.
Autonomía (20%): evalúa si el estudiante puede resolver las actividades sin recibir ayuda externa ni utilizar herramientas de IA durante la evaluación. Le asignamos un 20% porque buscamos comprobar que los conocimientos fueron incorporados y que el alumno puede utilizarlos por sus propios medios.

De esta manera, la métrica final se obtiene combinando los resultados de las cuatro dimensiones, dando mayor importancia a la aplicación práctica, sin dejar de lado la comprensión, el razonamiento y la autonomía.>

## 2. El sistema

**Cómo decide.** <Nuestro sistema utiliza un conjunto de reglas SI-ENTONCES para evaluar el aprendizaje del estudiante y determinar qué acciones educativas debe realizar el tutor de inteligencia artificial.

El objetivo no es simplemente comprobar si el alumno respondió correctamente, sino identificar si comprendió los conceptos, puede aplicarlos, justificar sus procedimientos y resolver problemas de manera autónoma.

Para tomar decisiones, el sistema utiliza cuatro variables, cada una con una puntuación de 0 a 100:

Comprensión conceptual: 25%.
Aplicación práctica: 30%.
Justificación del razonamiento: 25%.
Autonomía: 20%.

Estas ponderaciones permiten calcular un indicador general denominado porcentaje de dominio autónomo.

Fórmula del indicador:

Dominio autónomo = (C × 0,25) + (A × 0,30) + (R × 0,25) + (U × 0,20)

Donde:

C: comprensión conceptual.
A: aplicación práctica.
R: justificación del razonamiento.
U: autonomía.

Las decisiones se toman mediante las siguientes reglas:

Reglas de evaluación:

SI el dominio autónomo es igual o superior al 70% Y las cuatro dimensiones tienen al menos 60 puntos, ENTONCES el estudiante demuestra un nivel suficiente de comprensión y puede avanzar al siguiente contenido.
SI la comprensión conceptual es inferior a 60 puntos, ENTONCES el tutor debe ofrecer explicaciones alternativas, ejemplos y material de apoyo.
SI la aplicación práctica es inferior a 60 puntos, ENTONCES el tutor debe generar ejercicios progresivos para que el estudiante aprenda a utilizar los conocimientos adquiridos.
SI la justificación del razonamiento es inferior a 60 puntos, ENTONCES el tutor debe realizar preguntas de seguimiento para que el alumno explique los procedimientos y decisiones que tomó.
SI la autonomía es inferior a 60 puntos, ENTONCES el tutor debe proponer actividades de resolución independiente, reduciendo progresivamente las ayudas y pistas.
SI el estudiante no alcanza el 70% de dominio autónomo, ENTONCES debe continuar trabajando sobre los contenidos que presentan dificultades antes de avanzar.

Las reglas pueden activarse simultáneamente cuando el estudiante presenta dificultades en más de una dimensión.

De esta manera, el sistema no solamente determina si el alumno comprendió el contenido, sino que identifica qué necesita mejorar y selecciona la estrategia educativa más adecuada.>

**Variables que usa y por qué.** <Nuestro sistema utiliza cuatro variables principales:

1. Comprensión conceptual (25%)

Evalúa si el estudiante entiende los conceptos y puede explicarlos con sus propias palabras. Permite identificar si realmente comprendió la teoría o simplemente memorizó una respuesta.

2. Aplicación práctica (30%)

Evalúa si puede utilizar los conocimientos adquiridos para resolver ejercicios nuevos y situaciones diferentes de las que ya practicó. Le asignamos la mayor ponderación porque consideramos que la capacidad de aplicar lo aprendido es una de las evidencias más importantes de comprensión.

3. Justificación del razonamiento (25%)

Analiza si puede explicar los pasos que siguió, justificar sus decisiones y comprender por qué llegó a determinado resultado. Permite diferenciar entre obtener una respuesta correcta y comprender el procedimiento utilizado.

4. Autonomía (20%)

Evalúa si puede resolver actividades por sus propios medios, sin recibir pistas ni asistencia durante las evaluaciones de comprobación. Permite determinar si incorporó los conocimientos y puede utilizarlos independientemente del tutor.

Variables descartadas:

Tiempo de resolución: cada estudiante tiene su propio ritmo y tardar más no significa necesariamente comprender menos.
Ortografía y redacción: no determinan necesariamente el dominio del contenido.
Cantidad de respuestas correctas: no demuestra por sí sola que exista comprensión real.
Estilo de escritura: no permite determinar de manera confiable si una respuesta fue generada por IA.>


**Cómo se corre en vivo.** <El sistema funciona mediante un ciclo de enseñanza, evaluación y retroalimentación.

Paso 1. Diagnóstico inicial

El tutor presenta preguntas y ejercicios para identificar los conocimientos previos y las dificultades del estudiante.

Paso 2. Enseñanza personalizada

La inteligencia artificial explica los conceptos, proporciona ejemplos y propone actividades adaptadas al nivel de conocimiento del alumno.

Paso 3. Práctica guiada

El estudiante resuelve ejercicios y recibe correcciones, explicaciones y pistas cuando las necesita.

Paso 4. Evaluación de comprensión

El tutor presenta problemas nuevos y solicita explicaciones para comprobar si el estudiante puede aplicar y justificar lo aprendido.

Paso 5. Evaluación de autonomía

Se realiza una actividad de comprobación sin asistencia del tutor ni herramientas externas, para obtener evidencias de que el alumno puede resolver por sus propios medios.

Paso 6. Aplicación de reglas

El sistema asigna una puntuación a cada una de las cuatro dimensiones, calcula el porcentaje de dominio autónomo y evalúa las condiciones establecidas.

Paso 7. Retroalimentación y adaptación

Según las reglas que se activen, el tutor decide si el estudiante puede avanzar o si necesita reforzar determinados conocimientos.

Este proceso se repite hasta que el alumno demuestra un nivel suficiente de comprensión y autonomía.>

**Dos casos de ejemplo.**

| Caso inventado | Valores(C, A, R, U) | Salida del sistema |
|---|---|---|
| Estudiante que comprende los conceptos, resuelve ejercicios nuevos, justifica sus procedimientos y trabaja de manera autónoma. | <C: 85, A: 90, R: 80, U: 85. Dominio: 85,25%.> | <SÍ. Demuestra un nivel suficiente de comprensión y puede avanzar> |
| Estudiante que conoce los conceptos, pero tiene dificultades para aplicarlos y justificar sus procedimientos. | <C: 80, A: 45, R: 50, U: 85. Dominio: 63%.> | <NO. Necesita reforzar la aplicación práctica y el razonamiento.> |

## 3. Medición

**Entrenamiento (casos 1–14)**

| | Predice SÍ | Predice NO |
|---|---|---|
| **Real SÍ** | VP = <> | FN = <> |
| **Real NO** | FP = <> | VN = <> |

**Prueba (casos 15–20)**

| | Predice SÍ | Predice NO |
|---|---|---|
| **Real SÍ** | VP = <> | FN = <> |
| **Real NO** | FP = <> | VN = <> |

| Métrica | Entrenamiento | Prueba |
|---|---|---|
| Exactitud | <> | <> |
| Precisión | <> | <> |
| Sensibilidad | <> | <> |
| Especificidad | <> | <> |

**Entrenamiento contra prueba.** <¿Hay diferencia? ¿Por qué? ¿Sobreajuste o generalización?>

## 4. El error más caro

<¿Es peor el falso positivo o el falso negativo en su problema? ¿Por qué, según la ficha? ¿Qué cambiaron en el sistema para cometer menos ese error?>

## 5. ¿Comparado contra qué?

**Línea base trivial.** <Qué resultado saca un sistema que responde siempre lo mismo, y cómo se compara el suyo.>

| Checklist (Clase 6) | Respuesta |
|---|---|
| ¿Qué datos? | <> |
| ¿Qué métrica? | <> |
| ¿Comparado contra qué? | <> |
| ¿Quién lo midió? | <> |

## 6. Riesgo: el camino completo

<Datos → modelo → decisión → consecuencia aplicado a su caso. Al menos un riesgo concreto.>

## 7. Bitácora

**Uso de la IA**

| # | Qué le pedimos | Qué aceptamos | Qué rechazamos y por qué |
|---|---|---|---|
| 1 | <> | <> | <> |

**Corridas contra el evaluador**

| Corrida | Nota | Agujero que encontró | Qué cambiamos |
|---|---|---|---|
| 1 | <> | <> | <> |
