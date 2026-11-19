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
| AS-06 | El periodo de gracia ayuda a los compradores cuyas primeras cuotas no caben en su presupuesto. | Compradores |
| AS-07 | Una decisión hipotecaria toma varias sesiones, y guardar escenarios hace que el comprador vuelva a la aplicación (hipótesis H4 del Capítulo I). | Compradores |
| AS-08 | Un simulador transparente hace que más compradores busquen contacto después de simular (hipótesis H1 del Capítulo I). | Compradores |

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
| ERQ-04 | ¿En qué proporción de sesiones móviles con simulaciones completadas se exporta posteriormente un reporte PDF y qué utilidad le atribuyen los compradores? | AS-04, KG-04, CL-04 | Compradores | Eventos de exportación de PDF y valoraciones de los participantes. |
| ERQ-05 | ¿Con qué nivel de éxito y en cuánto tiempo los asesores inmobiliarios pueden consultar y actualizar solicitudes de potenciales compradores utilizando HipoSim? | AS-05, KG-05, CL-05 | Inmobiliarias | Tareas completadas, tiempo de ejecución, errores y valoraciones de los asesores. |

#### Preguntas experimentales complementarias

| ID | Experiment-Ready Question | Raw Material relacionado | Segmento objetivo | Evidencia requerida |
|---|---|---|---|---|
| ERQ-06 | ¿Una distribución visual mejorada de los importes facilita la lectura y comparación de tres escenarios hipotecarios? | ID-02 | Compradores | Comparación de tiempos, errores de interpretación y percepción de legibilidad entre alternativas de diseño. |
| ERQ-07 | ¿La presentación de importes con la misma precisión monetaria en todas las pantallas reduce las inconsistencias percibidas por los compradores? | ID-03 | Compradores | Errores de interpretación y valoraciones de consistencia antes y después de la mejora. |
| ERQ-08 | ¿La posibilidad de reactivar solicitudes descartadas facilita el seguimiento comercial de los asesores inmobiliarios? | ID-04 | Inmobiliarias | Pruebas con prototipos y valoraciones sobre la utilidad de la reactivación de solicitudes. |
| ERQ-09 | ¿Una interfaz adaptada a dispositivos móviles facilita la consulta y el seguimiento de solicitudes por parte de los asesores inmobiliarios? | ID-05 | Inmobiliarias | Pruebas de navegación móvil, tareas completadas y percepción de facilidad de uso. |
| ERQ-10 | ¿Qué proporción de las simulaciones completadas usa periodo de gracia, y las simulaciones con gracia terminan más veces en un envío a una inmobiliaria? | AS-06 | Compradores | Propiedades `graceType` y `graceMonths` de los eventos `simulation_completed` y `lead_sent`. |
| ERQ-11 | ¿Qué proporción de las sesiones móviles con una simulación completada guarda un escenario, y los compradores con escenarios vuelven en días distintos? | AS-07 | Compradores | Eventos `simulation_completed` y `scenario_saved`, y fechas de los escenarios guardados por Comprador en la API. |
| ERQ-12 | ¿Qué proporción de las sesiones con una simulación completada termina en un mensaje de contacto en el Landing Page o en un envío consentido a una inmobiliaria en la aplicación? | AS-08 | Compradores | Eventos `simulation_completed`, `contact_message_sent` y `lead_sent` por sesión. |

Las preguntas principales se relacionan con funcionalidades implementadas y permiten evaluar el estado actual del producto. Las preguntas complementarias exploran oportunidades de mejora identificadas durante las evaluaciones heurísticas y las entrevistas de validación.

Las entrevistas realizadas a los asesores inmobiliarios proporcionan evidencia cualitativa preliminar para ERQ-05, ERQ-08 y ERQ-09. Sin embargo, será necesario realizar mediciones adicionales para responder completamente estas preguntas.

Las preguntas formuladas serán incorporadas al Question Backlog, donde se priorizarán considerando su importancia para los segmentos objetivo, el impacto potencial sobre el producto y los criterios de priorización definidos en el Question Backlog.

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
| ERQ-10 | Belief-led | Contrasta la premisa de que la gracia es útil para el comprador y no lo aleja del contacto con una inmobiliaria. |
| ERQ-11 | Belief-led | Contrasta la hipótesis H4 de que guardar escenarios favorece el retorno. |
| ERQ-12 | Belief-led | Contrasta la hipótesis H1 de que el simulador lleva a buscar contacto. |

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

En caso de empate, se prioriza la pregunta que presenta mayor riesgo. Si el empate persiste, se considera el impacto potencial y posteriormente el interés. Si todos estos criterios coinciden, se consideran las dependencias entre las preguntas.

#### Question Backlog priorizado

| Orden | ID | Pregunta experimental resumida | Why | C | R | IM | IN | Total | Prioridad |
|---|---|---|---|---|---|---|---|---|---|
| 1 | ERQ-01 | ¿Los compradores completan una simulación sin asistencia? | La simulación constituye el núcleo de la propuesta de valor. | 2 | 5 | 5 | 5 | 19 | Alta |
| 2 | ERQ-03 | ¿Los compradores identifican correctamente las alternativas hipotecarias de menor costo? | Una interpretación incorrecta puede afectar las decisiones financieras. | 2 | 5 | 5 | 5 | 19 | Alta |
| 3 | ERQ-05 | ¿Los asesores gestionan eficientemente las solicitudes? | La gestión comercial constituye la propuesta de valor para las inmobiliarias. | 3 | 5 | 5 | 5 | 18 | Alta |
| 4 | ERQ-02 | ¿Los compradores comprenden el cronograma y los indicadores financieros? | La comprensión financiera es fundamental para evaluar un crédito. | 2 | 5 | 5 | 4 | 18 | Alta |
| 5 | ERQ-04 | ¿Los compradores utilizan y consideran útiles los reportes PDF? | Permite determinar la relevancia de conservar los resultados financieros. | 1 | 3 | 4 | 5 | 17 | Alta |
| 6 | ERQ-06 | ¿Una mejor distribución visual facilita la comparación de tres escenarios? | Permite evaluar oportunidades de mejora en la legibilidad. | 3 | 3 | 4 | 4 | 14 | Media |
| 7 | ERQ-07 | ¿La precisión monetaria uniforme reduce inconsistencias percibidas? | Busca mejorar la consistencia de la información financiera. | 4 | 3 | 4 | 4 | 13 | Media |
| 8 | ERQ-08 | ¿La reactivación de solicitudes descartadas mejora el seguimiento comercial? | Permite evaluar una necesidad identificada durante las entrevistas. | 2 | 2 | 3 | 4 | 13 | Media |
| 9 | ERQ-09 | ¿Una interfaz móvil facilita la gestión de solicitudes por parte de los asesores? | Permite conocer el valor de acceder a la plataforma desde dispositivos móviles. | 2 | 2 | 3 | 3 | 12 | Media |
| 10 | ERQ-11 | ¿Los compradores guardan escenarios y vuelven a la aplicación? | Valida la hipótesis H4 de retención del Capítulo I. | 2 | 4 | 4 | 4 | 16 | Media |
| 11 | ERQ-12 | ¿Las simulaciones completadas terminan en contacto? | Valida la hipótesis H1 de conversión del Capítulo I. | 3 | 4 | 5 | 4 | 16 | Media |
| 12 | ERQ-10 | ¿Se usa el periodo de gracia y cómo se relaciona con el envío a inmobiliarias? | Permite decidir si la gracia merece más protagonismo en el formulario. | 2 | 3 | 3 | 3 | 13 | Media |

#### Justificación de la priorización

Las preguntas ERQ-01, ERQ-02 y ERQ-03 presentan niveles elevados de riesgo e impacto debido a su relación con la evaluación de créditos hipotecarios y la comprensión de las condiciones financieras.

Las preguntas ERQ-01 y ERQ-03 presentan la misma puntuación. Se establece inicialmente ERQ-01 como primera pregunta debido a que completar una simulación constituye un requisito previo para comparar escenarios hipotecarios.

Ante el empate de ERQ-05 y ERQ-02, se prioriza ERQ-05 por su mayor interés, dado que ambas presentan el mismo riesgo e impacto.

La pregunta ERQ-05 presenta una confianza inicial moderada debido a las valoraciones favorables obtenidas durante las entrevistas con asesores inmobiliarios. Sin embargo, todavía se requiere evidencia cuantitativa sobre la ejecución de tareas.

La pregunta ERQ-04 presenta una confianza inicial muy baja debido a que no se dispone de resultados suficientes sobre la frecuencia de uso de los reportes PDF. Su carácter exploratorio permite obtener información que contribuya a orientar futuras decisiones.

Las preguntas complementarias conservan una prioridad media y podrán ser abordadas durante posteriores iteraciones de experimentación.

#### Estructura del Question Backlog

El Question Backlog de HipoSim se organiza considerando dos perspectivas complementarias:

- **Broad Question Backlog:** comprende las doce preguntas experimentales, permitiendo mantener una visión amplia de las incertidumbres y oportunidades de aprendizaje relacionadas con ambos segmentos objetivo.
- **Deep Question Backlog:** comprende las seis preguntas seleccionadas para desarrollar sus tarjetas de experimentos y profundizar en sus hipótesis, medidas, condiciones y métodos de evaluación.

#### Preguntas seleccionadas para experimentación

| Experiment ID | Question ID | Funcionalidad evaluada | Total Score | Prioridad |
|---|---|---|---|---|
| E01 | ERQ-01 | Simulación hipotecaria | 19 | Alta |
| E02 | ERQ-02 | Comprensión financiera | 18 | Alta |
| E03 | ERQ-03 | Comparación de escenarios hipotecarios | 19 | Alta |
| E04 | ERQ-04 | Exportación de reportes PDF | 17 | Alta |
| E05 | ERQ-05 | Gestión de leads inmobiliarios | 18 | Alta |
| E06 | ERQ-11 | Guardado de escenarios y retorno | 16 | Media |
| E07 | ERQ-06 | Distribución visual de la comparación de escenarios | 14 | Media |
| E08 | ERQ-07 | Precisión monetaria uniforme | 13 | Media |
| E09 | ERQ-08 | Reactivación de solicitudes descartadas | 13 | Media |
| E10 | ERQ-09 | Gestión de solicitudes desde el móvil | 12 | Media |
| E11 | ERQ-10 | Periodo de gracia y envío a inmobiliarias | 13 | Media |
| E12 | ERQ-12 | Conversión de la simulación a contacto | 16 | Media |

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
| Hypothesis | Al menos el 80 % de los participantes responderá correctamente al menos cinco de seis preguntas de comprensión financiera después de consultar los resultados y el cronograma de pagos. |
| What (SUT) | Utilizar la pantalla de resultados y el cronograma de pagos de una simulación hipotecaria previamente definida. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Número de respuestas correctas, porcentaje de participantes que alcanza el criterio de comprensión y dificultades identificadas. |
| Conditions | Todos los participantes consultarán la misma simulación y responderán seis preguntas sobre amortización, intereses, TCEA, VAN, TIR y costo total, sin recibir explicaciones adicionales durante la evaluación. |
| Scale | Prueba piloto propuesta con cinco compradores de primera vivienda. |
| Success Criteria | Al menos cuatro de los cinco participantes responden correctamente cinco o más de las seis preguntas. |
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
| Question | ¿En qué proporción de sesiones móviles con simulaciones completadas se exporta posteriormente un reporte PDF y qué utilidad le atribuyen los compradores? |
| Why | Es necesario conocer si los compradores consideran relevante conservar o compartir los resultados financieros fuera de la aplicación. |
| Hypothesis | No aplica inicialmente, debido al carácter exploratorio de la pregunta. |
| What (SUT) | Utilizar la funcionalidad de exportación de reportes PDF disponible en la aplicación móvil de HipoSim. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Proporción de sesiones móviles con al menos una exportación de PDF posterior a una simulación completada en la misma sesión, respecto al total de sesiones móviles con simulaciones completadas durante el periodo experimental. Se registrarán también los motivos de uso y la valoración de utilidad de los participantes. Las sesiones no equivalen necesariamente a personas únicas. |
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

#### Experiment Card E06: Guardado de escenarios y retorno

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E06 |
| Question ID | ERQ-11 |
| Question Type | Belief-led |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿Qué proporción de las sesiones móviles con una simulación completada guarda un escenario, y los compradores con escenarios vuelven en días distintos? |
| Why | La hipótesis H4 del Capítulo I sostiene que una decisión hipotecaria se toma en varias sesiones. Si los compradores no guardan escenarios ni vuelven, el historial no aporta retención y conviene replantearlo. |
| Hypothesis | Al menos el 25 % de las sesiones móviles con una simulación completada guarda un escenario, y al menos el 20 % de los compradores con escenarios los guarda en dos o más días distintos. |
| What (SUT) | Utilizar el botón Guardar escenario de la pantalla de resultados y la pantalla Mis escenarios de la aplicación móvil. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Sesiones con `scenario_saved` respecto a las sesiones con `simulation_completed`, y número de días distintos con escenarios guardados por Comprador. |
| Conditions | Uso libre de la versión distribuida por Firebase App Distribution. No se pide a los participantes que guarden escenarios: se mide el uso espontáneo. Las cuentas de demostración y las sesiones del equipo se excluyen. |
| Scale | Sesiones móviles registradas durante dos semanas, con un mínimo de 15 sesiones con simulación completada. |
| Success Criteria | Se cumplen los dos umbrales de la hipótesis. |
| Evidence | Eventos `simulation_completed` y `scenario_saved`, y fechas de creación de la tabla `scenarios`. |

**Estado:** Pendiente de ejecución y análisis de eventos.

<div style="page-break-after: always;"></div>

#### Experiment Card E07: Distribución visual de la comparación de escenarios

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E07 |
| Question ID | ERQ-06 |
| Question Type | Belief-led |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿Una distribución visual mejorada de los importes facilita la lectura y comparación de tres escenarios hipotecarios? |
| Why | La evaluación heurística del Capítulo VI (problema #3) identificó que, al comparar tres escenarios, los importes extensos ocupan varias líneas por el ancho de las columnas. Antes de rediseñar la pantalla es necesario comprobar si una distribución alternativa reduce el esfuerzo de lectura sin introducir errores de interpretación. |
| Hypothesis | Con la distribución mejorada, el tiempo medio para identificar el escenario de menor cuota mensual y el de menor costo total entre tres escenarios se reduce al menos en 20 % respecto de la distribución actual, sin que aumenten los errores de interpretación. |
| What (SUT) | Dos prototipos estáticos de la pantalla de comparación con los mismos tres escenarios: la distribución actual de la aplicación y una distribución alternativa con los importes en una sola línea, columnas de ancho adaptable y tamaño de texto ajustado. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Tiempo para identificar los escenarios de menor cuota mensual y menor costo total con cada distribución, número de respuestas incorrectas y legibilidad percibida en una escala de 1 a 5. |
| Conditions | Cada participante evalúa ambas distribuciones con dos conjuntos de escenarios de dificultad equivalente. El orden de las distribuciones se alterna entre participantes para controlar el efecto de aprendizaje. No se explica la interfaz durante la tarea. |
| Scale | Prueba piloto propuesta con cinco compradores de primera vivienda, con diseño intra-sujeto. |
| Success Criteria | El tiempo medio con la distribución mejorada es al menos 20 % menor que con la actual, el número de respuestas incorrectas no supera al de la distribución actual y la legibilidad promedio es de 4 o más. |
| Evidence | Registro de tiempos y respuestas, capturas de ambos prototipos y cuestionario de legibilidad. |

**Estado:** Pendiente de ejecución. Se basa en el problema #3 de la evaluación heurística documentada en el Capítulo VI.

<div style="page-break-after: always;"></div>

#### Experiment Card E08: Precisión monetaria uniforme

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E08 |
| Question ID | ERQ-07 |
| Question Type | Belief-led |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿La presentación de importes con la misma precisión monetaria en todas las pantallas reduce las inconsistencias percibidas por los compradores? |
| Why | La lista Mis escenarios presenta importes redondeados, mientras que la pantalla de comparación los muestra con dos decimales (problema #4 del Capítulo VI). Esta diferencia puede llevar al comprador a pensar que una misma cifra cambió entre pantallas y reducir su confianza en los resultados financieros. |
| Hypothesis | Con la precisión monetaria unificada, menos participantes perciben diferencias entre las cifras de un mismo escenario que con la versión actual: como máximo uno de cinco, con una consistencia percibida promedio de 4 o más en una escala de 1 a 5. |
| What (SUT) | Una versión de prueba de la aplicación (variante `demo`) en la que Mis escenarios utiliza el mismo formato monetario de dos decimales que la pantalla de comparación, contrastada con la versión actual. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Participantes que reportan diferencias entre las cifras de un mismo escenario en Mis escenarios y en la comparación, respuestas a preguntas de verificación de cifras y consistencia percibida en una escala de 1 a 5. |
| Conditions | Cada participante revisa los mismos escenarios en la versión actual y en la versión unificada, en orden alternado. En cada versión indica la cuota mensual y el costo total de un escenario en ambas pantallas y si considera que las cifras coinciden. |
| Scale | Prueba piloto propuesta con cinco compradores de primera vivienda, con diseño intra-sujeto. |
| Success Criteria | Con la versión unificada, como máximo un participante percibe diferencias, menos que con la versión actual, y la consistencia percibida promedio es de 4 o más. |
| Evidence | Respuestas de verificación, observaciones, capturas de ambas versiones y cuestionario de consistencia. |

**Estado:** Pendiente de ejecución. Requiere preparar la versión de prueba con el formato monetario unificado.

<div style="page-break-after: always;"></div>

#### Experiment Card E09: Reactivación de solicitudes descartadas

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E09 |
| Question ID | ERQ-08 |
| Question Type | Belief-led |
| Segmento objetivo | Asesores inmobiliarios |
| Question | ¿La posibilidad de reactivar solicitudes descartadas facilita el seguimiento comercial de los asesores inmobiliarios? |
| Why | En la entrevista de validación, Selene Carhuayo destacó la importancia de retomar el contacto con compradores previamente descartados. Hoy el estado `Discarded` funciona como un cierre: un comprador que desistió por no contar con la cuota inicial puede volver a calificar meses después, y el asesor no dispone de una acción explícita para retomar su seguimiento conservando el historial. |
| Hypothesis | Al menos dos de tres asesores reactivan una solicitud descartada sin asistencia en un minuto o menos y califican la utilidad de la función con 4 o más en una escala de 1 a 5. |
| What (SUT) | Un prototipo navegable de la ficha del lead con la acción "Reactivar seguimiento", que devuelve la solicitud al estado `InContact`, solicita una nota con el motivo y conserva el historial de estados. La API no se modifica antes de obtener evidencia. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Tasa de finalización de la tarea, tiempo de ejecución, solicitudes de ayuda, utilidad percibida en una escala de 1 a 5 y situaciones de uso mencionadas por los asesores. |
| Conditions | Cada asesor recibe una solicitud ficticia en estado descartado y la indicación de retomar su seguimiento, sin explicación sobre la ubicación de la acción. Al terminar, describe en qué casos utilizaría la función. |
| Scale | Prueba piloto propuesta con tres asesores inmobiliarios. |
| Success Criteria | Al menos dos de los tres asesores completan la reactivación sin asistencia en un minuto o menos y califican la utilidad con 4 o más. |
| Evidence | Grabación de la sesión, tiempos de ejecución, capturas del prototipo y respuestas de la entrevista breve. |

**Estado:** Cuenta con evidencia cualitativa preliminar obtenida en la entrevista de validación de Selene Carhuayo (Capítulo VI). Pendiente de prueba con prototipo.

<div style="page-break-after: always;"></div>

#### Experiment Card E10: Gestión de solicitudes desde el móvil

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E10 |
| Question ID | ERQ-09 |
| Question Type | Belief-led |
| Segmento objetivo | Asesores inmobiliarios |
| Question | ¿Una interfaz adaptada a dispositivos móviles facilita la consulta y el seguimiento de solicitudes por parte de los asesores inmobiliarios? |
| Why | Las entrevistas del Capítulo II muestran que los asesores gestionan a sus clientes principalmente desde el celular y por WhatsApp, y en la validación Selene Carhuayo mostró interés en el acceso móvil. Es necesario saber si el portal responsivo actual basta para trabajar desde el teléfono o si se requiere una adaptación específica. |
| Hypothesis | Al menos dos de tres asesores completan desde un smartphone la consulta y la actualización de una solicitud en tres minutos o menos sin asistencia, y califican la facilidad de uso móvil con 4 o más en una escala de 1 a 5. |
| What (SUT) | El portal web del asesor publicado en Vercel, abierto desde el navegador del smartphone de cada participante, sin desarrollar una aplicación nativa. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Tasa de finalización, tiempo de ejecución, errores, solicitudes de ayuda, facilidad de uso móvil en una escala de 1 a 5 y pantallas con dificultades (desplazamiento horizontal, controles pequeños o texto truncado). |
| Conditions | Los participantes realizan las mismas tareas de E05 desde su teléfono con la cuenta de asesor de demostración: localizar una solicitud ficticia, consultar su información financiera, actualizar su estado y registrar una nota. Si el participante también realizó E05, se utiliza una solicitud distinta. |
| Scale | Prueba piloto propuesta con tres asesores inmobiliarios. |
| Success Criteria | Al menos dos de los tres asesores completan las tareas desde el smartphone en tres minutos o menos sin asistencia y califican la facilidad de uso móvil con 4 o más. |
| Evidence | Grabación de la pantalla del teléfono, tiempos de ejecución, capturas y entrevista breve. |

**Estado:** Cuenta con evidencia cualitativa preliminar (entrevistas de los Capítulos II y VI). Pendiente de medición experimental.

<div style="page-break-after: always;"></div>

#### Experiment Card E11: Periodo de gracia y envío a inmobiliarias

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E11 |
| Question ID | ERQ-10 |
| Question Type | Belief-led |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿Qué proporción de las simulaciones completadas usa periodo de gracia, y las simulaciones con gracia terminan más veces en un envío a una inmobiliaria? |
| Why | El periodo de gracia (US03) se incorporó en el Sprint 3 para los compradores cuyas primeras cuotas no caben en su presupuesto. Si casi nadie lo utiliza, o si las simulaciones con gracia conducen a menos envíos a inmobiliarias, conviene reducir su protagonismo en el formulario; si se usa y acompaña el envío, merece mayor visibilidad. |
| Hypothesis | Al menos el 15 % de las simulaciones completadas en la aplicación móvil usa periodo de gracia, y la tasa de envío a inmobiliarias de las simulaciones con gracia es igual o mayor que la de las simulaciones sin gracia. |
| What (SUT) | El selector de periodo de gracia del formulario de simulación de la aplicación móvil, implementado en el Sprint 3. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Proporción de eventos `simulation_completed` con `graceType` distinto de `none`, y tasa de envío (eventos `lead_sent` entre eventos `simulation_completed`) separada por simulaciones con y sin gracia. |
| Conditions | Uso libre de la aplicación distribuida por Firebase App Distribution durante dos semanas. Solo se consideran eventos con origen `mobile`, porque el simulador del Landing Page no ofrece periodo de gracia. Se excluyen las cuentas de demostración y las sesiones del equipo. |
| Scale | Mínimo de 30 simulaciones completadas en la aplicación móvil durante el periodo. Si no se alcanza, el resultado se reporta como exploratorio. |
| Success Criteria | Se cumplen las dos condiciones de la hipótesis. |
| Evidence | Eventos `simulation_completed` y `lead_sent` con sus propiedades de gracia, procesados con `tools/compute_kpis.py`. |

**Estado:** Pendiente de ejecución y análisis de eventos.

<div style="page-break-after: always;"></div>

#### Experiment Card E12: Conversión de la simulación a contacto

**Lado frontal**

| Campo | Descripción |
|---|---|
| Experiment ID | E12 |
| Question ID | ERQ-12 |
| Question Type | Belief-led |
| Segmento objetivo | Compradores de primera vivienda |
| Question | ¿Qué proporción de las sesiones con una simulación completada termina en un mensaje de contacto en el Landing Page o en un envío consentido a una inmobiliaria en la aplicación? |
| Why | La hipótesis H1 del Capítulo I sostiene que un simulador transparente lleva a más compradores a buscar contacto después de simular. Esta conversión sustenta la propuesta de valor para las inmobiliarias: si los compradores no comparten su simulación, el portal del asesor no recibe leads. |
| Hypothesis | Al menos el 10 % de las sesiones con una simulación completada termina en un mensaje de contacto (`contact_message_sent`) o en un envío consentido a una inmobiliaria (`lead_sent`) dentro de la misma sesión. |
| What (SUT) | El formulario de contacto del Landing Page y la opción de envío a una inmobiliaria desde la pantalla de resultados de la aplicación móvil, ya implementados. |

**Lado posterior**

| Campo | Descripción |
|---|---|
| Measures | Sesiones con `contact_message_sent` o `lead_sent` posteriores a un `simulation_completed`, respecto del total de sesiones con simulación completada, reportadas en total y por origen (`landing` y `mobile`). |
| Conditions | Uso libre durante dos semanas, sin pedir a los participantes que se contacten ni que envíen su simulación. Se excluyen las cuentas de demostración y las sesiones del equipo. El mensaje de contacto del Landing Page se considera un indicador indirecto, porque se dirige al equipo de HipoSim y no a una inmobiliaria. |
| Scale | Mínimo de 30 sesiones con simulación completada, sumando ambos productos. Si no se alcanza, el resultado se reporta como exploratorio. |
| Success Criteria | La proporción global de sesiones con contacto alcanza el 10 %. |
| Evidence | Eventos `simulation_completed`, `contact_message_sent` y `lead_sent` por sesión, procesados con `tools/compute_kpis.py`. |

**Estado:** Pendiente de ejecución y análisis de eventos.

<div style="page-break-after: always;"></div>

#### Resumen de experimentos

| ID | Pregunta | Segmento | Funcionalidad | Estado |
|---|---|---|---|---|
| E01 | ERQ-01 | Compradores | Simulación hipotecaria | Planificado |
| E02 | ERQ-02 | Compradores | Comprensión financiera | Planificado |
| E03 | ERQ-03 | Compradores | Comparación de escenarios | Evidencia técnica preliminar |
| E04 | ERQ-04 | Compradores | Exportación de reportes PDF | Planificado |
| E05 | ERQ-05 | Inmobiliarias | Gestión de leads | Evidencia cualitativa preliminar |
| E06 | ERQ-11 | Compradores | Guardado de escenarios y retorno | Planificado |
| E07 | ERQ-06 | Compradores | Distribución visual de la comparación | Planificado |
| E08 | ERQ-07 | Compradores | Precisión monetaria uniforme | Planificado |
| E09 | ERQ-08 | Inmobiliarias | Reactivación de solicitudes descartadas | Evidencia cualitativa preliminar |
| E10 | ERQ-09 | Inmobiliarias | Gestión de solicitudes desde el móvil | Evidencia cualitativa preliminar |
| E11 | ERQ-10 | Compradores | Periodo de gracia y envío a inmobiliarias | Planificado |
| E12 | ERQ-12 | Compradores | Conversión de la simulación a contacto | Planificado |

Las doce tarjetas establecen una base para la fase de Experiment Design. Las escalas propuestas corresponden a pruebas piloto exploratorias de alcance reducido y no permiten generalizar los resultados a toda la población objetivo.

Las hipótesis, medidas, condiciones, escalas y métodos de evaluación se desarrollan en la sección 8.2. Las preguntas ERQ-10 y ERQ-12 se miden con los mismos eventos de uso como indicadores de seguimiento (sección 8.2.7), sin una tarjeta propia en esta iteración.

#### Evidencia preliminar de experimentación

Como parte de las actividades de validación de HipoSim, se realizaron sesiones con dos profesionales del sector inmobiliario, quienes interactuaron con la plataforma de asesores y conocieron las funcionalidades de la aplicación móvil dirigida a compradores.

| Participante | Organización | Segmento | Fecha | Entorno | Evidencia |
|---|---|---|---|---|---|
| Carlos Pebe | Interbank | Inmobiliarias | Pendiente de confirmar | Ejecución local | [Entrevista de validación](https://drive.google.com/file/d/1lBARHJ5aXndSZkgL7pgg14L03eFD84jq/view?usp=drive_link) |
| Selene Carhuayo | RE/MAX | Inmobiliarias | Pendiente de confirmar | Ejecución local | [Entrevista de validación](https://drive.google.com/file/d/1cDnaxrUroIwLSk7pDJxnPiv8eSgKwPRx/view?usp=sharing) |

**Actividades realizadas**

- Exploración del dashboard de asesores inmobiliarios.
- Consulta de la bandeja de leads.
- Revisión de información financiera de potenciales compradores.
- Actualización de estados de solicitudes.
- Revisión de las funcionalidades de seguimiento comercial.
- Pruebas de envío de informes.
- Demostración de la aplicación móvil para compradores y del proceso de simulación hipotecaria.

**Hallazgos preliminares**

| Hallazgo | Pregunta relacionada |
|---|---|
| Valoración favorable de la facilidad de navegación y gestión de solicitudes. | ERQ-05 |
| Utilidad de la información financiera para conocer las necesidades del comprador. | ERQ-05 |
| Interés en retomar solicitudes previamente descartadas. | ERQ-08 |
| Interés en acceder a la plataforma desde dispositivos móviles. | ERQ-09 |
| Valoración favorable de la aplicación móvil para compradores durante su demostración. | ERQ-01, como evidencia indirecta |

Las actividades realizadas proporcionan evidencia cualitativa preliminar relacionada principalmente con el experimento E05. Asimismo, permiten identificar oportunidades de mejora que podrán evaluarse en futuras iteraciones.

Estas sesiones no sustituyen las mediciones experimentales planificadas, debido a que no se cuenta con registros específicos de tiempos de ejecución ni resultados cuantitativos obtenidos bajo las condiciones definidas en las tarjetas de experimentos.

La demostración de la aplicación móvil tampoco constituye una prueba de usabilidad realizada con compradores de primera vivienda, dado que los participantes pertenecen al segmento inmobiliario.

Las grabaciones, capturas y resúmenes completos se encuentran documentados en la sección 6.3.2. Registro de entrevistas del Capítulo VI. Las fechas de las sesiones están pendientes de confirmación y no se cuenta con evidencia de pruebas del Landing Page en estas sesiones.

<div style="page-break-after: always;"></div>

## **8.2. Experiment Design**

### **8.2.1. Hypotheses**

| Experimento | Hipótesis nula (H0) | Hipótesis alternativa (H1) |
|---|---|---|
| E01 | Menos del 80 % de los compradores participantes completa una simulación sin asistencia. | Al menos el 80 % de los compradores participantes completa una simulación sin asistencia. |
| E02 | Menos del 80 % de los participantes responde correctamente cinco o más de las seis preguntas de comprensión financiera. | Al menos el 80 % de los participantes responde correctamente cinco o más de las seis preguntas. |
| E03 | Menos del 80 % de los participantes identifica correctamente los escenarios de menor cuota y de menor costo total. | Al menos el 80 % de los participantes identifica correctamente ambos escenarios. |
| E04 | No aplica: la pregunta es exploratoria. Se describe la proporción de sesiones con exportación y sus motivos. | No aplica. |
| E05 | Al menos uno de los dos asesores no completa la consulta y actualización de una solicitud en tres minutos sin asistencia. | Ambos asesores completan la consulta y actualización en tres minutos o menos sin asistencia. |
| E06 | Menos del 25 % de las sesiones con simulación guarda un escenario, o menos del 20 % de los compradores con escenarios los guarda en días distintos. | Al menos el 25 % de las sesiones con simulación guarda un escenario y al menos el 20 % de los compradores con escenarios los guarda en dos o más días distintos. |
| E07 | Con la precisión unificada, dos o más de los cinco participantes siguen percibiendo diferencias entre las cifras de un mismo escenario, ese número no disminuye respecto de la versión actual, o la consistencia percibida promedio es menor que 4. | Con la precisión unificada, como máximo uno de los cinco participantes percibe diferencias entre las cifras de un mismo escenario, menos que con la versión actual, y la consistencia percibida promedio es de 4 o más. |
| E08 | Con la precisión unificada, dos o más de los cinco participantes siguen percibiendo diferencias entre las cifras de un mismo escenario, ese número no disminuye respecto de la versión actual, o la consistencia percibida promedio es menor que 4. | Con la precisión unificada, como máximo uno de los cinco participantes percibe diferencias entre las cifras de un mismo escenario, menos que con la versión actual, y la consistencia percibida promedio es de 4 o más. |
| E09 | Menos de dos de los tres asesores reactivan una solicitud descartada sin asistencia en un minuto o menos y califican la utilidad de la función con 4 o más. | Al menos dos de los tres asesores reactivan una solicitud descartada sin asistencia en un minuto o menos y califican la utilidad de la función con 4 o más. |
| E10 | Menos de dos de los tres asesores completan desde un smartphone la consulta y la actualización de una solicitud en tres minutos o menos sin asistencia y califican la facilidad de uso móvil con 4 o más. | Al menos dos de los tres asesores completan desde un smartphone la consulta y la actualización de una solicitud en tres minutos o menos sin asistencia y califican la facilidad de uso móvil con 4 o más. |
| E11 | Menos del 15 % de las simulaciones completadas en la aplicación móvil usa periodo de gracia, o la tasa de envío a inmobiliarias de las simulaciones con gracia es menor que la de las simulaciones sin gracia. | Al menos el 15 % de las simulaciones completadas en la aplicación móvil usa periodo de gracia, y la tasa de envío a inmobiliarias de las simulaciones con gracia es igual o mayor que la de las simulaciones sin gracia. |
| E12 | Menos del 10 % de las sesiones con una simulación completada termina en un mensaje de contacto o en un envío consentido a una inmobiliaria. | Al menos el 10 % de las sesiones con una simulación completada termina en un mensaje de contacto o en un envío consentido a una inmobiliaria. |

### **8.2.2. Domain Business Metrics**

| Métrica | Definición | Relación con el negocio | Experimentos |
|---|---|---|---|
| Tasa de finalización de la simulación | Simulaciones completadas entre simulaciones iniciadas | Indica si la herramienta es comprensible para un comprador sin experiencia (H2). | E01 |
| Nivel de comprensión financiera | Participantes con cinco o más respuestas correctas entre participantes | Mide si la transparencia del simulador se traduce en comprensión. | E02 |
| Exactitud en la comparación | Participantes que identifican ambos escenarios correctos entre participantes | Mide el valor de la comparación para decidir (H3). | E03 |
| Uso del reporte PDF | Sesiones con `pdf_exported` entre sesiones móviles con simulación completada | Indica si el comprador lleva su resultado fuera de la aplicación. | E04 |
| Eficiencia del asesor | Tiempo y éxito al consultar y actualizar una solicitud | Mide el valor del producto para las inmobiliarias. | E05 |
| Guardado y retorno | Sesiones con escenario guardado y compradores que vuelven en días distintos | Mide la retención (H4). | E06 |
| Conversión a contacto | Sesiones con contacto o lead enviado entre sesiones con simulación completada | Mide el valor del simulador como canal hacia las inmobiliarias (H1). | Seguimiento (ERQ-12) |

### **8.2.3. Measurements**

| Medida | Fuente | Cálculo |
|---|---|---|
| Simulaciones iniciadas y completadas | Eventos de uso | Número de `simulation_started` y `simulation_completed` por producto (`source`) |
| Tareas completadas sin asistencia | Observación de las pruebas piloto | Participantes que terminan la tarea sin pedir ayuda |
| Tiempo de ejecución | Observación de las pruebas piloto | Segundos desde la indicación de la tarea hasta su término |
| Respuestas correctas | Cuestionario de comprensión de E02 y tareas de E03 | Número de respuestas correctas por participante |
| Exportaciones de PDF | Eventos de uso | Sesiones con `pdf_exported` después de un `simulation_completed` en la misma sesión |
| Escenarios guardados | Eventos de uso | Sesiones con `scenario_saved` entre sesiones con `simulation_completed` |
| Retorno | Base de datos de la API | Días distintos de `created_at` en la tabla `scenarios` por Comprador |
| Uso del periodo de gracia | Eventos de uso | Simulaciones con `graceType` distinto de `none` (seguimiento de ERQ-10) |
| Contacto | Eventos de uso | Sesiones con `contact_message_sent` o `lead_sent` (seguimiento de ERQ-12) |

Los indicadores basados en eventos se calculan con `tools/compute_kpis.py` sobre el CSV que exporta `tools/export_usage_events.py`, con la configuración `tools/kpi_config.json` del repositorio de la API.

### **8.2.4. Conditions**

- **Productos:** Landing Page publicado, aplicación Android distribuida por Firebase App Distribution y portal web del asesor en Vercel, todos conectados a la API desplegada en Render.
- **Pruebas piloto (E01, E02, E03 y E05):** cinco compradores de primera vivienda y dos asesores inmobiliarios reales. Todos reciben los mismos datos de referencia y las mismas indicaciones, sin explicación sobre el uso de la interfaz durante la tarea.
- **Medición por eventos (E04, E06 y seguimiento):** uso libre durante dos semanas desde la publicación de la versión 0.1.0 (110). No se pide a los participantes que usen una función concreta.
- **Exclusiones:** las cuentas de demostración (`@hiposim.test`) y las sesiones de prueba del equipo se excluyen por cuenta, por identificador de sesión y por fecha.
- **Privacidad:** los eventos no contienen nombre, correo, teléfono, DNI ni el nombre del escenario. La API rechaza propiedades con nombres de datos personales, y el pie legal de las aplicaciones informa el registro anónimo.
- **Estabilidad:** las funciones medidas no cambian durante el periodo de experimentación.

### **8.2.5. Scale Calculations and Decisions**

| Experimento | Escala | Decisión si se cumple | Decisión si no se cumple |
|---|---|---|---|
| E01 | 5 compradores en prueba piloto, más las sesiones registradas por eventos | Mantener el flujo de simulación sin registro. | Rediseñar el paso del formulario con más abandono o más solicitudes de ayuda y volver a medir. |
| E02 | 5 compradores | Mantener la presentación actual de indicadores. | Incorporar explicaciones breves de TCEA, VAN y TIR (idea ID-01). |
| E03 | 5 compradores | Mantener la comparación y el resaltado de valores mínimos. | Aplicar las ideas ID-02 e ID-03 y repetir la prueba. |
| E04 | Sesiones móviles con simulación completada durante dos semanas | Describir la frecuencia y los motivos; si es alta, mejorar el diseño del reporte. | Reducir su protagonismo en Resultados. |
| E05 | 2 asesores | Mantener el flujo de la bandeja y la ficha del lead. | Simplificar la actualización de estado y revisar las ideas ID-04 e ID-05. |
| E06 | Mínimo de 15 sesiones móviles con simulación completada | Agregar recordatorios para volver a los escenarios guardados (Sprint 4). | Reforzar la invitación a guardar desde Resultados y volver a medir. |
| E07 | 5 compradores, con diseño intra-sujeto | Implementar la distribución mejorada en la aplicación y cerrar el problema #3 de la evaluación heurística. | Probar otra alternativa, como presentar los escenarios en filas, antes de modificar la aplicación. |
| E08 | 5 compradores, con diseño intra-sujeto | Aplicar el formato de dos decimales en Mis escenarios y cerrar el problema #4 de la evaluación heurística. | Revisar si las diferencias percibidas provienen de otros elementos de la pantalla, como etiquetas o el redondeo de la TCEA, antes de cambiar el formato. |
| E09 | 3 asesores | Agregar la acción "Reactivar seguimiento" al portal y permitir en la API la transición de `Discarded` a `InContact`. | Mantener los estados actuales y registrar la reactivación como nota de seguimiento. |
| E10 | 3 asesores | Mantener el portal responsivo y priorizar las notificaciones de nuevos interesados en el móvil. | Adaptar la bandeja y la ficha al móvil, con tarjetas en lugar de tabla y acciones fijas, y volver a medir. |
| E11 | Mínimo de 30 simulaciones completadas en la aplicación móvil | Dar mayor visibilidad a la gracia en el formulario y explicar su efecto sobre el costo total. | Mover la gracia a una opción avanzada del formulario. |
| E12 | Mínimo de 30 sesiones con simulación completada | Mantener el flujo actual y ampliar la oferta de inmobiliarias disponibles. | Hacer más visible el envío a inmobiliarias en Resultados, agregar un acceso a la aplicación desde los resultados del Landing Page y volver a medir. |


Con cinco participantes por prueba piloto los resultados son exploratorios: permiten detectar problemas de uso, pero no generalizar a toda la población objetivo. Si los experimentos por eventos no alcanzan su escala mínima, se reportan como exploratorios y se complementan con las entrevistas de validación.

### **8.2.6. Methods Selection**

- **Pruebas de usabilidad moderadas** con tareas y observación, para E01, E02, E03 y E05.
- **Cuestionario de comprensión** de seis preguntas, para E02.
- **Análisis de embudo** con los eventos de uso, para E01 y el seguimiento de ERQ-12.
- **Análisis descriptivo** de proporciones, para E04 y el seguimiento de ERQ-10.
- **Análisis de cohortes** por Comprador con las fechas de los escenarios guardados, para E06.
- **Entrevistas breves** posteriores a cada prueba, para explicar los resultados (sección 8.3.4).

### **8.2.7. Data Analytics: Goals, KPIs and Metrics Selection**

| Objetivo | KPI | Meta | Experimento |
|---|---|---|---|
| Que el comprador termine su simulación | Tasa de finalización de la simulación | 80 % en la prueba piloto y 60 % o más en los eventos | E01 |
| Que el comprador entienda su crédito | Participantes con cinco o más respuestas correctas | 80 % o más | E02 |
| Que el comprador compare alternativas correctamente | Participantes que identifican ambos escenarios | 80 % o más | E03 |
| Que el comprador lleve su resultado al banco | Sesiones con exportación de PDF | Indicador exploratorio, sin meta | E04 |
| Que el asesor gestione sus leads con rapidez | Tiempo de consulta y actualización | 3 minutos o menos | E05 |
| Que el comprador vuelva | Sesiones con escenario guardado y compradores que vuelven | 25 % y 20 % | E06 |
| Que la simulación genere contacto | Conversión a contacto | 10 % o más (seguimiento) | ERQ-12 |
| Que la gracia sea útil | Simulaciones con gracia | 15 % o más (seguimiento) | ERQ-10 |

### **8.2.8. Web and Mobile Tracking Plan**

| Evento | Landing Page | Aplicación móvil | Cuándo se envía | Propiedades |
|---|:---:|:---:|---|---|
| `page_viewed` | Sí | No | Al cargar la página | Idioma |
| `app_opened` | No | Sí | Al abrir la aplicación | Versión e idioma |
| `simulation_started` | Sí | Sí | Al primer cambio del formulario o al primer envío | Ninguna |
| `simulation_completed` | Sí | Sí | Al recibir un resultado | Plazo, tipo y meses de gracia, bono y porcentaje de cuota inicial |
| `schedule_opened` | Sí | Sí | Al abrir el cronograma completo | Plazo y tipo de gracia |
| `language_changed` | Sí | No | Al cambiar de idioma | Idioma elegido |
| `contact_message_sent` | Sí | No | Al registrarse el mensaje de contacto | Ninguna |
| `scenario_saved` | No | Sí | Al guardar un escenario | Plazo y tipo de gracia |
| `scenarios_compared` | No | Sí | Al abrir una comparación | Número de escenarios |
| `pdf_exported` | No | Sí | Al descargar el reporte PDF | Plazo y tipo de gracia |
| `lead_sent` | No | Sí | Al enviar la simulación a una inmobiliaria con consentimiento | Plazo y tipo de gracia |

Cada evento lleva un identificador de sesión aleatorio, que se crea al abrir el Landing o la aplicación, y el producto de origen (`landing` o `mobile`). Los eventos se envían en segundo plano: si el envío falla, se descartan sin afectar al usuario. El portal web del asesor no envía eventos; E05 se mide por observación.

<div style="page-break-after: always;"></div>

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
