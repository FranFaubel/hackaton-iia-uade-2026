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

**Cómo decide.** <Neurona: pesos y sesgo. Reglas: la lista de reglas si‑entonces. Agente: la regla con la que elige la acción.>

**Variables que usa y por qué.** <Cuáles usa, cuáles descarta y por qué.>

**Cómo se corre en vivo.** <Pasos concretos para resolver un caso nuevo: link al Colab, a la planilla o la cuenta a mano.>

**Dos casos de ejemplo.**

| Caso inventado | Valores | Salida del sistema |
|---|---|---|
| A | <…> | <SÍ/NO> |
| B | <…> | <SÍ/NO> |

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
