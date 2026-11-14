# **Chapter VIII: Experiment-Driven Development**

## **8.1. Experiment Planning**

### **8.1.1. As-Is Summary**

HipoSim es una plataforma digital orientada a facilitar la evaluación de créditos hipotecarios para compradores de primera vivienda y mejorar la gestión de potenciales clientes para las inmobiliarias.

Actualmente, la solución está conformada por cuatro componentes:

- **Landing Page:** presenta la propuesta de valor de HipoSim y permite realizar simulaciones hipotecarias básicas.
- **Native Mobile Application:** permite realizar simulaciones hipotecarias, consultar indicadores financieros y cronogramas de pagos, aplicar beneficios estatales, guardar y comparar escenarios hipotecarios y exportar reportes PDF.
- **Web Application:** permite a los asesores inmobiliarios consultar solicitudes, revisar simulaciones hipotecarias, actualizar estados y realizar el seguimiento de potenciales compradores.
- **RESTful API:** centraliza las operaciones de autenticación, simulación hipotecaria, persistencia de escenarios, gestión de leads y registro de eventos de uso.

#### Situación actual por segmento objetivo

| Segmento objetivo | Situación actual | Necesidad de validación |
|---|---|---|
| Compradores de primera vivienda | Disponen de herramientas para simular créditos, consultar cronogramas y comparar escenarios hipotecarios. | Evaluar si comprenden los resultados financieros y pueden identificar alternativas convenientes. |
| Inmobiliarias | Disponen de una plataforma para gestionar leads, consultar simulaciones y realizar el seguimiento comercial. | Evaluar si las funcionalidades se ajustan a sus procesos de atención y seguimiento de compradores. |

#### Hallazgos preliminares

A partir de las evaluaciones heurísticas y las entrevistas de validación realizadas durante el desarrollo de HipoSim, se identificaron los siguientes hallazgos:

- La precisión monetaria es importante para comparar escenarios hipotecarios.
- El resaltado de valores mínimos debe representar correctamente los escenarios empatados.
- La distribución de información al comparar tres escenarios presenta oportunidades de mejora.
- Los asesores inmobiliarios valoran positivamente la facilidad de navegación y la gestión de leads.
- La información financiera de los compradores resulta útil para orientar el seguimiento comercial.
- Existe interés en retomar el seguimiento de solicitudes previamente descartadas.
- Los asesores inmobiliarios mostraron interés en el acceso desde dispositivos móviles.
- La demostración del aplicativo móvil para compradores recibió una valoración favorable por parte de los asesores entrevistados.

Asimismo, se han incorporado mecanismos de registro de eventos anónimos para complementar las evaluaciones cualitativas mediante información sobre el comportamiento de los usuarios.

#### Justificación de la experimentación

Aunque las funcionalidades implementadas permiten atender las principales necesidades identificadas durante el desarrollo, todavía existen incertidumbres relacionadas con la facilidad de uso, la comprensión de los resultados financieros, la utilidad de las funcionalidades y su contribución a los objetivos de los usuarios.

Por ello, se aplicará Experiment-Driven Development (XDPD) para identificar incertidumbres, formular preguntas experimentales, priorizar oportunidades de aprendizaje y diseñar experimentos que permitan obtener evidencia para orientar las siguientes decisiones de desarrollo.

### **8.1.2. Raw Material: Assumptions, Knowledge Gaps, Ideas, Claims**

A partir del análisis de la situación actual de HipoSim, las entrevistas de validación, las evaluaciones heurísticas y las funcionalidades implementadas, se identificaron las siguientes premisas que servirán como punto de partida para el planeamiento experimental.

#### Assumptions (Supuestos)

| ID | Premisa | Segmento objetivo |
|---|---|---|
| AS-01 | Los compradores de primera vivienda pueden completar una simulación hipotecaria sin asistencia especializada. | Compradores |
| AS-02 | Los compradores comprenden mejor sus obligaciones financieras cuando consultan el cronograma de pagos. | Compradores |
| AS-03 | La comparación de escenarios hipotecarios facilita la identificación de alternativas de financiamiento convenientes. | Compradores |
| AS-04 | Los compradores consideran útil descargar un reporte PDF para revisar o compartir los resultados de una simulación. | Compradores |
| AS-05 | Los asesores inmobiliarios pueden gestionar y realizar el seguimiento de potenciales compradores utilizando HipoSim. | Inmobiliarias |

#### Knowledge Gaps (Vacíos de conocimiento)

| ID | Premisa | Segmento objetivo |
|---|---|---|
| KG-01 | Se desconoce qué proporción de compradores logra completar una simulación hipotecaria después de iniciarla. | Compradores |
| KG-02 | Se desconoce si los compradores interpretan correctamente indicadores financieros como la TCEA, el VAN y la TIR. | Compradores |
| KG-03 | No se ha determinado si los compradores identifican correctamente el escenario con menor cuota mensual y menor costo total. | Compradores |
| KG-04 | Se desconoce con qué frecuencia los compradores utilizan la exportación de reportes PDF después de realizar una simulación. | Compradores |
| KG-05 | No se ha determinado cuánto tiempo necesitan los asesores inmobiliarios para consultar y actualizar una solicitud. | Inmobiliarias |

#### Ideas (Ideas de mejora)

| ID | Premisa | Segmento objetivo |
|---|---|---|
| ID-01 | Incorporar explicaciones breves de los indicadores financieros para facilitar su comprensión. | Compradores |
| ID-02 | Mejorar la distribución visual de los importes monetarios al comparar tres escenarios hipotecarios. | Compradores |
| ID-03 | Unificar la precisión monetaria entre la lista de escenarios guardados y la pantalla de comparación. | Compradores |
| ID-04 | Evaluar la incorporación de una opción para retomar el seguimiento de solicitudes previamente descartadas. | Inmobiliarias |
| ID-05 | Evaluar la adaptación de la plataforma de asesores para facilitar su acceso desde dispositivos móviles. | Inmobiliarias |

#### Claims (Afirmaciones)

| ID | Premisa | Segmento objetivo |
|---|---|---|
| CL-01 | HipoSim simplifica el proceso de simulación de créditos hipotecarios para compradores de primera vivienda. | Compradores |
| CL-02 | La presentación del cronograma de pagos permite comprender mejor la distribución del capital y los intereses. | Compradores |
| CL-03 | El resaltado de valores mínimos y la presentación precisa de importes facilitan la comparación de escenarios hipotecarios. | Compradores |
| CL-04 | La exportación de reportes PDF facilita la consulta posterior y el intercambio de información financiera. | Compradores |
| CL-05 | La gestión centralizada de leads facilita el seguimiento comercial de potenciales compradores por parte de los asesores inmobiliarios. | Inmobiliarias |

Las premisas identificadas representan incertidumbres, oportunidades de mejora y afirmaciones que requieren evidencia adicional. Las valoraciones favorables obtenidas durante las entrevistas constituyen evidencia cualitativa preliminar, pero no permiten generalizar los resultados a todos los usuarios de HipoSim.

Estas premisas serán utilizadas para formular las preguntas experimentales, priorizar el Question Backlog y elaborar las correspondientes tarjetas de experimentos.

### **8.1.3. Experiment-Ready Questions**

A partir de las premisas identificadas en la sección Raw Material, se formularon preguntas experimentales orientadas a reducir las incertidumbres relacionadas con la usabilidad, comprensión financiera y utilidad de las funcionalidades de HipoSim.

Las preguntas se plantearon considerando los segmentos objetivo, las funcionalidades implementadas y la posibilidad de obtener evidencia mediante pruebas con usuarios, entrevistas de validación y registros de eventos de uso.

#### Preguntas experimentales principales

| ID | Experiment-Ready Question | Raw Material relacionado | Segmento objetivo | Evidencia requerida |
|---|---|---|---|---|
| ERQ-01 | ¿Qué proporción de compradores de primera vivienda logra completar una simulación hipotecaria sin asistencia? | AS-01, KG-01, CL-01 | Compradores | Simulaciones iniciadas y completadas, observación de usuarios y dificultades identificadas. |
| ERQ-02 | ¿En qué medida los compradores comprenden la distribución del capital, los intereses y los indicadores financieros presentados en HipoSim? | AS-02, KG-02, ID-01, CL-02 | Compradores | Respuestas correctas a preguntas de comprensión financiera y consulta del cronograma de pagos. |
| ERQ-03 | ¿Qué proporción de compradores identifica correctamente los escenarios con menor cuota mensual y menor costo total utilizando la funcionalidad de comparación? | AS-03, KG-03, CL-03 | Compradores | Resultados de tareas de comparación, respuestas correctas y dificultades observadas. |
| ERQ-04 | ¿Qué proporción de compradores exporta un reporte PDF después de completar una simulación y qué utilidad le atribuye? | AS-04, KG-04, CL-04 | Compradores | Eventos de exportación de PDF y valoraciones de los participantes. |
| ERQ-05 | ¿Con qué nivel de éxito y en cuánto tiempo los asesores inmobiliarios pueden consultar y actualizar solicitudes de potenciales compradores utilizando HipoSim? | AS-05, KG-05, CL-05 | Inmobiliarias | Tareas completadas, tiempo de ejecución, errores y valoraciones de los asesores. |

#### Preguntas experimentales complementarias

| ID | Experiment-Ready Question | Raw Material relacionado | Segmento objetivo | Evidencia requerida |
|---|---|---|---|---|
| ERQ-06 | ¿Una distribución visual mejorada de los importes facilita la lectura y comparación de tres escenarios hipotecarios? | ID-02 | Compradores | Comparación de tiempos, errores de interpretación y percepción de legibilidad entre alternativas de diseño. |
| ERQ-07 | ¿La presentación de importes con la misma precisión monetaria en todas las pantallas reduce las inconsistencias percibidas por los compradores? | ID-03 | Compradores | Errores de interpretación y valoraciones de consistencia antes y después de la mejora. |
| ERQ-08 | ¿La posibilidad de reactivar solicitudes descartadas facilita el seguimiento comercial de los asesores inmobiliarios? | ID-04 | Inmobiliarias | Pruebas con prototipos y valoraciones sobre la utilidad de la reactivación de solicitudes. |
| ERQ-09 | ¿Una interfaz adaptada a dispositivos móviles facilita la consulta y el seguimiento de solicitudes por parte de los asesores inmobiliarios? | ID-05 | Inmobiliarias | Pruebas de navegación móvil, tareas completadas y percepción de facilidad de uso. |

Las preguntas principales se relacionan con funcionalidades implementadas y permiten evaluar el estado actual del producto. Las preguntas complementarias exploran oportunidades de mejora identificadas durante las evaluaciones heurísticas y las entrevistas de validación.

Las entrevistas realizadas a los asesores inmobiliarios proporcionan evidencia cualitativa preliminar para ERQ-05, ERQ-08 y ERQ-09. Sin embargo, será necesario realizar mediciones adicionales para responder completamente estas preguntas.

Las preguntas formuladas serán incorporadas al Question Backlog, donde se priorizarán considerando su importancia para los segmentos objetivo, el impacto potencial sobre el producto y los recursos necesarios para obtener evidencia.
#### Clasificación de las preguntas experimentales

De acuerdo con XDPD, las preguntas experimentales se clasifican en dos tipos:

- **Belief-led Questions:** preguntas orientadas a contrastar creencias, suposiciones o afirmaciones previamente identificadas sobre el producto y sus usuarios.
- **Exploratory Questions:** preguntas orientadas a obtener conocimiento sobre aspectos cuyo comportamiento todavía se desconoce, sin establecer necesariamente una hipótesis inicial.

| ID | Tipo de pregunta | Justificación |
|---|---|---|
| ERQ-01 | Belief-led | Contrasta la creencia de que los compradores pueden completar una simulación sin asistencia. |
| ERQ-02 | Belief-led | Contrasta la creencia de que la información financiera facilita la comprensión del crédito. |
| ERQ-03 | Belief-led | Contrasta la creencia de que la comparación de escenarios facilita la identificación de alternativas convenientes. |
| ERQ-04 | Exploratory | Busca conocer la frecuencia de exportación y los motivos de uso de los reportes PDF. |
| ERQ-05 | Belief-led | Contrasta la creencia de que HipoSim facilita la gestión de solicitudes inmobiliarias. |
| ERQ-06 | Belief-led | Contrasta la premisa de que una distribución visual diferente mejora la legibilidad. |
| ERQ-07 | Belief-led | Contrasta la premisa de que una precisión monetaria uniforme reduce inconsistencias percibidas. |
| ERQ-08 | Belief-led | Contrasta la premisa de que retomar solicitudes descartadas aporta valor al seguimiento comercial. |
| ERQ-09 | Belief-led | Contrasta la premisa de que el acceso móvil facilita el seguimiento comercial. |

#### Aplicación de la técnica 5W1H

Para delimitar las preguntas experimentales se consideran los siguientes elementos:

| Elemento | Aplicación en HipoSim |
|---|---|
| Who (Quién) | Compradores de primera vivienda y asesores inmobiliarios. |
| What (Qué) | Usabilidad, comprensión financiera y utilidad de las funcionalidades. |
| Where (Dónde) | Landing Page, aplicación móvil y aplicación web. |
| When (Cuándo) | Durante la realización de tareas y el periodo de experimentación. |
| Why (Por qué) | Reducir incertidumbres y orientar las decisiones de desarrollo. |
| How (Cómo) | Mediante observación, pruebas con usuarios, entrevistas y registros de eventos anónimos. |

Esta clasificación permite distinguir las preguntas que requieren formular hipótesis de aquellas cuya finalidad principal es obtener conocimiento exploratorio.


### **8.1.4. Question Backlog**

El Question Backlog de HipoSim reúne las preguntas experimentales identificadas durante la fase de planeamiento. Su finalidad es priorizar las oportunidades de aprendizaje considerando la importancia de obtener evidencia antes de tomar decisiones sobre el producto.

A diferencia del Product Backlog, este artefacto organiza preguntas e incertidumbres que requieren investigación, en lugar de funcionalidades pendientes de implementación.

#### Criterios de priorización

Para establecer el orden de las preguntas experimentales se utilizan cuatro criterios:

- **Confidence (C):** nivel de confianza actual en el conocimiento o las creencias relacionadas con la pregunta.
- **Risk (R):** consecuencias negativas que podrían producirse si las premisas relacionadas con la pregunta fueran incorrectas.
- **Impact (IM):** impacto potencial de responder la pregunta sobre los usuarios y los objetivos del producto.
- **Interest (IN):** relevancia e interés de obtener la respuesta para los usuarios y stakeholders.

Para HipoSim se propone una escala de valoración del 1 al 5.

| Puntuación | Confidence | Risk | Impact | Interest |
|---|---|---|---|---|
| 1 | Muy baja | Muy bajo | Muy bajo | Muy bajo |
| 2 | Baja | Bajo | Bajo | Bajo |
| 3 | Moderada | Moderado | Moderado | Moderado |
| 4 | Alta | Alto | Alto | Alto |
| 5 | Muy alta | Muy alto | Muy alto | Muy alto |

Con la finalidad de priorizar las preguntas que presentan mayor necesidad de aprendizaje, se utiliza la siguiente expresión:

**Total Score = (6 - C) + R + IM + IN**

La confianza se incorpora de forma inversa, de modo que las preguntas con menor confianza inicial reciban mayor prioridad de investigación.

| Total Score | Prioridad |
|---|---|
| 17 - 20 | Alta |
| 12 - 16 | Media |
| 4 - 11 | Baja |

En caso de empate, se prioriza la pregunta que presenta mayor riesgo. Si el empate persiste, se considera el impacto potencial y posteriormente el interés.

#### Question Backlog priorizado

| Orden | ID | Pregunta experimental resumida | Why | C | R | IM | IN | Total | Prioridad |
|---|---|---|---|---|---|---|---|---|---|
| 1 | ERQ-01 | ¿Los compradores completan una simulación sin asistencia? | La simulación constituye el núcleo de la propuesta de valor. | 2 | 5 | 5 | 5 | 19 | Alta |
| 2 | ERQ-03 | ¿Los compradores identifican correctamente las alternativas hipotecarias de menor costo? | Una interpretación incorrecta puede afectar las decisiones financieras. | 2 | 5 | 5 | 5 | 19 | Alta |
| 3 | ERQ-02 | ¿Los compradores comprenden el cronograma y los indicadores financieros? | La comprensión financiera es fundamental para evaluar un crédito. | 2 | 5 | 5 | 4 | 18 | Alta |
| 4 | ERQ-05 | ¿Los asesores gestionan eficientemente las solicitudes? | La gestión comercial constituye la propuesta de valor para las inmobiliarias. | 3 | 5 | 5 | 5 | 18 | Alta |
| 5 | ERQ-04 | ¿Los compradores utilizan y consideran útiles los reportes PDF? | Permite determinar la relevancia de conservar los resultados financieros. | 1 | 3 | 4 | 5 | 17 | Alta |
| 6 | ERQ-06 | ¿Una mejor distribución visual facilita la comparación de tres escenarios? | Permite evaluar oportunidades de mejora en la legibilidad. | 3 | 3 | 4 | 4 | 14 | Media |
| 7 | ERQ-07 | ¿La precisión monetaria uniforme reduce inconsistencias percibidas? | Busca mejorar la consistencia de la información financiera. | 4 | 3 | 4 | 4 | 13 | Media |
| 8 | ERQ-08 | ¿La reactivación de solicitudes descartadas mejora el seguimiento comercial? | Permite evaluar una necesidad identificada durante las entrevistas. | 2 | 2 | 3 | 4 | 13 | Media |
| 9 | ERQ-09 | ¿Una interfaz móvil facilita la gestión de solicitudes por parte de los asesores? | Permite conocer el valor de acceder a la plataforma desde dispositivos móviles. | 2 | 2 | 3 | 3 | 12 | Media |

#### Justificación de la priorización

Las preguntas ERQ-01, ERQ-02 y ERQ-03 presentan niveles elevados de riesgo e impacto debido a su relación con la evaluación de créditos hipotecarios y la comprensión de las condiciones financieras.

Las preguntas ERQ-01 y ERQ-03 presentan la misma puntuación. Se establece inicialmente ERQ-01 como primera pregunta debido a que completar una simulación constituye un requisito previo para comparar escenarios hipotecarios.

La pregunta ERQ-05 presenta una confianza inicial moderada debido a las valoraciones favorables obtenidas durante las entrevistas con asesores inmobiliarios. Sin embargo, todavía se requiere evidencia cuantitativa sobre la ejecución de tareas.

La pregunta ERQ-04 presenta una confianza inicial muy baja debido a que no se dispone de resultados suficientes sobre la frecuencia de uso de los reportes PDF. Su carácter exploratorio permite obtener información que contribuya a orientar futuras decisiones.

Las preguntas complementarias conservan una prioridad media y podrán ser abordadas durante posteriores iteraciones de experimentación.

#### Estructura del Question Backlog

El Question Backlog de HipoSim se organiza considerando dos perspectivas complementarias:

- **Broad Question Backlog:** comprende las nueve preguntas experimentales, permitiendo mantener una visión amplia de las incertidumbres y oportunidades de aprendizaje relacionadas con ambos segmentos objetivo.
- **Deep Question Backlog:** comprende las cinco preguntas seleccionadas para desarrollar sus tarjetas de experimentos y profundizar en sus hipótesis, medidas, condiciones y métodos de evaluación.

#### Preguntas seleccionadas para experimentación

| Experiment ID | Question ID | Funcionalidad evaluada | Total Score | Prioridad |
|---|---|---|---|---|
| E01 | ERQ-01 | Simulación hipotecaria | 19 | Alta |
| E02 | ERQ-02 | Comprensión financiera | 18 | Alta |
| E03 | ERQ-03 | Comparación de escenarios hipotecarios | 19 | Alta |
| E04 | ERQ-04 | Exportación de reportes PDF | 17 | Alta |
| E05 | ERQ-05 | Gestión de leads inmobiliarios | 18 | Alta |

La valoración presentada corresponde a una priorización inicial basada en los conocimientos disponibles durante la planificación experimental. Las puntuaciones no representan resultados obtenidos mediante mediciones con usuarios.

Después de ejecutar los experimentos, el Question Backlog deberá actualizarse considerando la evidencia recopilada y los nuevos aprendizajes. Esta actualización será documentada en la sección 8.4.2. Re-scored and Re-prioritized Question Backlog.

### **8.1.5. Experiment Cards**

Las tarjetas de experimentos permiten estructurar las preguntas seleccionadas del Question Backlog y establecer los elementos necesarios para obtener evidencia que contribuya a la toma de decisiones sobre HipoSim.

Cada tarjeta presenta un lado frontal, que contiene la pregunta experimental, su motivación, la hipótesis y la Simplest Useful Thing (SUT), y un lado posterior, que establece las medidas, condiciones y escala del experimento.

Las hipótesis, condiciones y criterios de éxito establecidos corresponden a propuestas iniciales que serán desarrolladas durante la fase de Experiment Design.

#### Experiment Card E01: Simulación hipotecaria

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E01 |
| Question ID | ERQ-01 |
| Question Type | Belief-led |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿Qué proporción de compradores logra completar una simulación hipotecaria sin asistencia? |
| Why | La simulación hipotecaria constituye la funcionalidad principal de HipoSim. Es necesario determinar si los compradores pueden utilizarla sin depender de conocimientos financieros avanzados o asistencia especializada. |
| Hypothesis | Al menos el 80 % de los compradores participantes completará una simulación hipotecaria sin asistencia. |
| What (SUT) | Utilizar el formulario de simulación hipotecaria implementado en HipoSim y solicitar a los participantes que generen una simulación con datos de referencia. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Tasa de finalización, tiempo de ejecución, errores y solicitudes de ayuda. |
| Conditions | Los participantes recibirán los mismos datos de referencia y deberán completar la simulación sin instrucciones sobre el uso de la interfaz. |
| Scale | Prueba piloto propuesta con cinco compradores de primera vivienda. |
| Success Criteria | Al menos cuatro de los cinco participantes completan correctamente la simulación sin asistencia. |
| Evidence | Registro de observaciones y eventos simulation_started y simulation_completed, cuando estén disponibles. |

**Estado:** Pendiente de ejecución y medición experimental.

<div style="page-break-after: always;"></div>

#### Experiment Card E02: Comprensión financiera

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E02 |
| Question ID | ERQ-02 |
| Question Type | Belief-led |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿En qué medida los compradores comprenden la distribución del capital, los intereses y los indicadores financieros presentados en HipoSim? |
| Why | Presentar resultados financieros no garantiza que los compradores comprendan sus obligaciones económicas. Es necesario evaluar si la información permite interpretar correctamente las condiciones del crédito hipotecario. |
| Hypothesis | Al menos el 80 % de los participantes responderá correctamente tres de cuatro preguntas de comprensión financiera después de consultar los resultados y el cronograma de pagos. |
| What (SUT) | Utilizar la pantalla de resultados y el cronograma de pagos de una simulación hipotecaria previamente definida. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Número de respuestas correctas, porcentaje de participantes que alcanza el criterio de comprensión y dificultades identificadas. |
| Conditions | Todos los participantes consultarán la misma simulación y responderán preguntas sobre amortización, intereses, TCEA y costo total, sin recibir explicaciones adicionales durante la evaluación. |
| Scale | Prueba piloto propuesta con cinco compradores de primera vivienda. |
| Success Criteria | Al menos cuatro participantes responden correctamente tres o más de las cuatro preguntas. |
| Evidence | Cuestionarios de comprensión, registro de observaciones y evento schedule_opened, cuando esté disponible. |

**Estado:** Pendiente de ejecución y medición experimental.

<div style="page-break-after: always;"></div>

#### Experiment Card E03: Comparación de escenarios hipotecarios

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E03 |
| Question ID | ERQ-03 |
| Question Type | Belief-led |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿Qué proporción de compradores identifica correctamente los escenarios con menor cuota mensual y menor costo total utilizando la funcionalidad de comparación? |
| Why | Los compradores necesitan comparar alternativas de financiamiento antes de tomar una decisión. La identificación incorrecta de los valores mínimos podría generar interpretaciones equivocadas sobre las condiciones del crédito. |
| Hypothesis | Al menos el 80 % de los participantes identificará correctamente los escenarios con menor cuota mensual y menor costo total. |
| What (SUT) | Utilizar la pantalla de comparación de escenarios hipotecarios implementada en la aplicación móvil de HipoSim. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Tasa de respuestas correctas, tiempo de comparación, errores de interpretación y percepción de facilidad de uso. |
| Conditions | Los participantes compararán dos y tres escenarios previamente definidos. Se incluirán casos donde la menor cuota y el menor costo total correspondan a diferentes escenarios, así como casos con valores mínimos empatados. |
| Scale | Prueba piloto propuesta con cinco compradores de primera vivienda. |
| Success Criteria | Al menos cuatro participantes identifican correctamente ambas alternativas y reconocen los empates cuando se presentan. |
| Evidence | Registro de respuestas, capturas de la comparación, observaciones y evento scenarios_compared, cuando esté disponible. |

**Estado:** Cuenta con evidencia técnica preliminar documentada en el Capítulo VI. Pendiente de medición experimental con compradores.

<div style="page-break-after: always;"></div>

#### Experiment Card E04: Exportación de reportes PDF

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E04 |
| Question ID | ERQ-04 |
| Question Type | Exploratory |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿Qué proporción de compradores exporta un reporte PDF después de completar una simulación y qué utilidad le atribuye? |
| Why | Es necesario conocer si los compradores consideran relevante conservar o compartir los resultados financieros fuera de la aplicación. |
| Hypothesis | No aplica inicialmente, debido al carácter exploratorio de la pregunta. |
| What (SUT) | Utilizar la funcionalidad de exportación de reportes PDF disponible en la aplicación móvil de HipoSim. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Proporción de sesiones con exportación de reportes respecto a las sesiones con simulaciones completadas, motivos de uso y valoración de utilidad. |
| Conditions | Los participantes realizarán una simulación y podrán explorar libremente los resultados. No se les solicitará explícitamente descargar el PDF durante la medición de uso espontáneo. Posteriormente se consultará su percepción sobre la funcionalidad. |
| Scale | Prueba piloto propuesta con cinco compradores de primera vivienda y registros anónimos de uso disponibles durante el periodo experimental. |
| Success Criteria | Obtener evidencia suficiente para describir la frecuencia de exportación y los principales motivos de uso o desuso. |
| Evidence | Eventos simulation_completed y pdf_exported, entrevistas breves y registros de observación. |

**Estado:** Pendiente de ejecución y análisis de eventos.

<div style="page-break-after: always;"></div>

#### Experiment Card E05: Gestión de leads inmobiliarios

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E05 |
| Question ID | ERQ-05 |
| Question Type | Belief-led |
| Segmento objetivo | Asesores inmobiliarios |
| Question | ¿Con qué nivel de éxito y en cuánto tiempo los asesores inmobiliarios pueden consultar y actualizar solicitudes de potenciales compradores utilizando HipoSim? |
| Why | La gestión de leads constituye una funcionalidad fundamental para las inmobiliarias. Es necesario determinar si la plataforma facilita la consulta de solicitudes y el seguimiento comercial de los compradores. |
| Hypothesis | Los dos asesores de la prueba piloto podrán consultar y actualizar una solicitud correctamente en un tiempo máximo de tres minutos por participante, sin asistencia. |
| What (SUT) | Utilizar el dashboard, la bandeja de leads, la ficha de una solicitud y la funcionalidad de actualización de estados implementados en HipoSim. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Tasa de finalización de tareas, tiempo de ejecución, número de errores, solicitudes de ayuda y percepción de facilidad de uso. |
| Conditions | Los participantes recibirán una solicitud de referencia con datos ficticios y deberán localizarla, consultar su información financiera y actualizar su estado sin asistencia durante la tarea. |
| Scale | Prueba piloto propuesta con dos asesores inmobiliarios. |
| Success Criteria | Ambos participantes completan correctamente las tareas de consulta y actualización en un máximo de tres minutos por participante. |
| Evidence | Registro de observaciones, tiempos de ejecución, capturas y entrevistas de validación. |

**Estado:** Cuenta con evidencia cualitativa preliminar obtenida durante las entrevistas realizadas a Carlos Pebe y Selene Carhuayo. Las pruebas funcionales y valoraciones favorables se encuentran documentadas en el Capítulo VI. Los tiempos de ejecución y el cumplimiento de los criterios de éxito todavía requieren medición específica.

<div style="page-break-after: always;"></div>

#### Resumen de experimentos

| ID | Pregunta | Segmento | Funcionalidad | Estado |
|---|---|---|---|---|
| E01 | ERQ-01 | Compradores | Simulación hipotecaria | Planificado |
| E02 | ERQ-02 | Compradores | Comprensión financiera | Planificado |
| E03 | ERQ-03 | Compradores | Comparación de escenarios | Evidencia técnica preliminar |
| E04 | ERQ-04 | Compradores | Exportación de reportes PDF | Planificado |
| E05 | ERQ-05 | Inmobiliarias | Gestión de leads | Evidencia cualitativa preliminar |

Las cinco tarjetas establecen una base para la fase de Experiment Design. Las escalas propuestas corresponden a pruebas piloto exploratorias de alcance reducido y no permiten generalizar los resultados a toda la población objetivo.

Las hipótesis, medidas, condiciones, escalas y métodos de evaluación deberán ser revisados y desarrollados en la sección 8.2 antes de la ejecución formal de los experimentos.

## **8.2. Experiment Design**
### **8.2.1. Hypotheses**
### **8.2.2. Domain Business Metrics**
### **8.2.3. Measurements**
### **8.2.4. Conditions**
### **8.2.5. Scale Calculations and Decisions**
### **8.2.6. Methods Selection**
### **8.2.7. Data Analytics: Goals, KPIs and Metrics Selection.**
### **8.2.8. Web and Mobile Tracking Plan**
## **8.3. Experimentation**
### **8.3.1. To-Be User Stories**
### **8.3.2. To-Be Product Backlog**
### **8.3.3. Pipeline-supported, Experiment-Driven To-Be Software Platform Lifecycle**
#### **8.3.3.1. To-Be Sprint Backlogs**
#### **8.3.3.2. Implemented To-Be Landing Page Evidence**
#### **8.3.3.3. Implemented To-Be Frontend-Web Application Evidence**
#### **8.3.3.4. Implemented To-Be Native-Mobile Application Evidence**
#### **8.3.3.5. Implemented To-Be RESTful API and/or Serverless Backend Evidence**
#### **8.3.3.6. Team Collaboration Insights**
### **8.3.4. To-Be Validation Interviews**
#### **8.3.4.1. Interview Design**
#### **8.3.4.2. Interview Record**
## **8.4. Experiment Aftermath & Analysis**
### **8.4.1. Analysis and Interpretation of Results**
### **8.4.2. Re-scored and Re-prioritized Question Backlog**
## **8.5. Continuous Learning**
### **8.5.1. Shareback Session Artifacts: Learning Workflow**
## **8.6. To-Be Software Platform Pre-launch**
### **8.6.1. About-the-Product Intro Video**
### **8.6.2. Summary using Gees FrameWork**
