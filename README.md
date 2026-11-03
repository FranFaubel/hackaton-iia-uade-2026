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

**Objetivo y métrica.** <Qué es lo que de verdad importa en su problema y con qué métrica lo van a medir. ¿Son lo mismo?>

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
