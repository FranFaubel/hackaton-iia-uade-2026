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

**Entrenamiento contra prueba.** <Al comparar los resultados del entrenamiento con los de prueba, observamos que el sistema obtiene un 92,86% de exactitud durante el entrenamiento y un 100% en los casos de prueba.

Esto significa que el sistema logra clasificar correctamente todos los casos que no utilizó para establecer su funcionamiento.

No observamos indicios de sobreajuste, ya que el rendimiento no disminuye al evaluar casos nuevos. Por el contrario, mejora respecto del entrenamiento, lo que representa una primera evidencia favorable de generalización.

Sin embargo, debemos considerar que el conjunto de prueba contiene solamente seis casos, por lo que no podemos garantizar que estos resultados se mantengan con una cantidad mayor de estudiantes.

Durante el entrenamiento se produjo un falso negativo en el caso 3. Este estudiante obtuvo un 67% de aciertos, pero su resultado real era SÍ. Al no alcanzar el umbral del 70%, nuestro sistema lo clasificó incorrectamente como NO.

Este caso demuestra una de las limitaciones de utilizar únicamente el porcentaje de aciertos: un estudiante puede comprender un tema aunque no alcance exactamente el umbral establecido.

Conclusión:

Los resultados muestran que nuestro sistema tiene un buen desempeño inicial para clasificar el rendimiento de los estudiantes. Sin embargo, el porcentaje de aciertos no garantiza por sí solo que exista una comprensión real de los conocimientos.

Por este motivo, nuestro tutor incorpora una segunda instancia de evaluación, en la que la inteligencia artificial analiza la comprensión conceptual, la aplicación práctica, la justificación del razonamiento y la autonomía.

De esta manera, buscamos que el sistema no confunda una respuesta correcta con un aprendizaje verdaderamente adquirido.

Si bien el sistema obtuvo un 100% en todas las métricas del conjunto de prueba, este resultado debe interpretarse con cautela debido a que solamente contamos con seis casos. Además, los datos presentan una separación relativamente clara respecto del umbral de clasificación establecido. Por lo tanto, este resultado no garantiza que el sistema mantenga el mismo rendimiento ante una muestra más amplia y diversa. Será necesario realizar nuevas pruebas con estudiantes reales para evaluar su capacidad de generalización.

>

## 4. El error más caro

<¿Qué es peor: el falso positivo o el falso negativo?

En nuestro tutor educativo, el falso positivo ocurre cuando el sistema considera que un estudiante comprendió un tema, cuando en realidad todavía no lo domina.

El falso negativo ocurre cuando el sistema considera que un estudiante no comprendió un tema, aunque realmente sí lo haya aprendido.

Consideramos que el falso positivo es más perjudicial, por las siguientes razones:

El estudiante puede avanzar a contenidos nuevos sin tener los conocimientos necesarios.
Puede acumular dificultades que afecten su aprendizaje futuro.
La plataforma puede mostrarles a los padres que el estudiante avanzó de tema, generando una percepción equivocada de su progreso.
El tutor deja de ofrecerle herramientas de refuerzo cuando todavía las necesita.

En cambio, un falso negativo puede provocar que un estudiante que sí comprendió tenga que realizar ejercicios adicionales o repetir una explicación. Aunque esto puede generar frustración y pérdida de tiempo, no implica necesariamente que avance con conocimientos incompletos.

¿Qué cambiamos en el sistema para cometer menos ese error?

Incorporamos una segunda instancia de evaluación antes de permitir que el estudiante avance de tema.

A partir de ahora, no alcanza con obtener un 70% de aciertos para considerar que comprendió.

El tutor deberá:

Presentar un ejercicio nuevo que evalúe el mismo concepto.
Solicitar que el estudiante explique cómo llegó al resultado.
Comprobar si puede aplicar el conocimiento en una situación diferente.
Realizar una actividad de resolución autónoma, sin pistas ni asistencia.

Nueva regla SI-ENTONCES:

SI el estudiante obtiene al menos un 70% de aciertos, PERO no demuestra comprensión, aplicación y razonamiento en la evaluación complementaria, ENTONCES el sistema no confirma el dominio del tema y propone actividades de refuerzo.

SI supera ambas instancias, ENTONCES el sistema considera que existen evidencias suficientes para avanzar.

Conclusión

Priorizamos reducir los falsos positivos porque nuestro objetivo es garantizar que el estudiante adquiera conocimientos sólidos antes de avanzar hacia nuevos contenidos. Preferimos que el tutor solicite una comprobación adicional antes que considerar aprendido un tema que el alumno todavía no domina.>

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
