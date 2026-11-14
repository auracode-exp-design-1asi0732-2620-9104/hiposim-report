# **Chapter VIII: Experiment-Driven Development**

En este capítulo planificamos y diseñamos los experimentos con los que validamos las hipótesis de negocio del Capítulo I sobre el producto ya implementado. Partimos de lo que HipoSim hace hoy (sección 8.1.1), convertimos los supuestos y vacíos de conocimiento en preguntas que un experimento puede responder (secciones 8.1.2 a 8.1.5) y definimos para cada experimento la hipótesis, las métricas, las condiciones y el plan de registro de datos (sección 8.2). La ejecución, el análisis de resultados y el aprendizaje (secciones 8.3 a 8.6) se documentan en la entrega final.

<div style="page-break-after: always;"></div>

## **8.1. Experiment Planning**

### **8.1.1. As-Is Summary**

Al cierre del Sprint 3, HipoSim cuenta con cuatro productos publicados que comparten una misma API:

| Producto | Usuario | Funciones disponibles | Publicación |
|---|---|---|---|
| Landing Page | Visitante | Propuesta de valor, simulación sin registro con Bono del Buen Pagador y cronograma completo, beneficios, FAQ, Términos y Privacidad, contacto y selector ES/EN | GitHub Pages |
| Aplicación Android | Comprador | Registro e inicio de sesión, simulación con periodo de gracia, indicadores TCEA, VAN y TIR, cronograma, guardado y comparación de escenarios, reporte PDF y envío consentido a una inmobiliaria | Firebase App Distribution |
| Portal web | Asesor | Bandeja y ficha de leads, estados y notas de seguimiento | Vercel |
| API RESTful | Todos | Autenticación, motor financiero, leads, escenarios, reporte PDF, contacto y eventos de uso | Render |

Para los experimentos ya existe la recolección de datos: el Landing Page y la aplicación móvil envían eventos de uso anónimos a `POST /api/events`, que los guarda en la tabla `usage_events` con un identificador de sesión aleatorio, el producto de origen, el nombre del evento, la fecha y propiedades sin datos personales. Además, la API guarda las simulaciones, los escenarios y los leads de cada Comprador, y el equipo cuenta con herramientas para exportar los eventos a CSV y calcular indicadores (tarea EXP2). Lo que todavía no sabemos es si estas funciones cambian el comportamiento de los compradores, que es lo que buscan responder los experimentos.

### **8.1.2. Raw Material: Assumptions, Knowledge Gaps, Ideas, Claims**

| Tipo | Contenido | Origen |
|---|---|---|
| Supuesto | El comprador primerizo desconfía de los simuladores de los bancos y prefiere una herramienta independiente y transparente. | Entrevistas del Capítulo II |
| Supuesto | Ver la TCEA y el cronograma completo antes de ir al banco aumenta la intención de solicitar un crédito. | Hipótesis H1 |
| Supuesto | Una decisión hipotecaria se toma en varias sesiones, comparando alternativas de plazo, cuota inicial y gracia. | Hipótesis H3 y H4 |
| Vacío de conocimiento | No sabemos qué porcentaje de quienes empiezan una simulación la terminan, ni en qué paso abandonan. | Métrica de abandono del Capítulo I |
| Vacío de conocimiento | No sabemos si los compradores usan el periodo de gracia ni cómo cambia su elección. | US03 |
| Vacío de conocimiento | No sabemos si el comprador acepta compartir su simulación con una inmobiliaria cuando se le pide consentimiento explícito. | US21 y Ley 29733 |
| Idea | Sugerir guardar el escenario justo después de ver los resultados aumentaría las comparaciones. | Equipo |
| Idea | Mostrar la diferencia de cuota y de total a pagar entre escenarios ayudaría a decidir. | US07 |
| Afirmación | El simulador del Landing Page, sin registro, es la puerta de entrada principal del producto. | Estrategia del Capítulo I |

### **8.1.3. Experiment-Ready Questions**

| ID | Pregunta | Origen |
|---|---|---|
| Q1 | ¿Qué porcentaje de las simulaciones iniciadas en el Landing Page y en la aplicación móvil se completan? | Métrica de abandono del Capítulo I |
| Q2 | ¿Los compradores que guardan dos o más escenarios completan más simulaciones por sesión que los que no guardan ninguno? | H3 |
| Q3 | ¿Qué porcentaje de las sesiones con una simulación completada termina en una solicitud de contacto: mensaje en el Landing Page o envío consentido a una inmobiliaria en la aplicación? | H1 |
| Q4 | ¿Los compradores que guardan escenarios vuelven a usar la aplicación en días distintos? | H4 |
| Q5 | ¿Cuánto tiempo tarda un visitante, desde que entra, en completar su primera simulación? | H2 |
| Q6 | ¿Qué parte de los compradores descarga el reporte PDF de su simulación? | US08 |
| Q7 | ¿Qué porcentaje de las simulaciones completadas usa periodo de gracia, y las simulaciones con gracia terminan más veces en un envío a una inmobiliaria? | US03 |
| Q8 | ¿Qué porcentaje de las simulaciones completadas en el Landing Page lleva a abrir el cronograma completo? | US15 y US02 |
| Q9 | ¿Las sesiones del Landing Page que cambian a inglés completan la simulación en la misma proporción que las que se quedan en español? | US20 |
| Q10 | ¿Qué porcentaje de las sesiones de la aplicación con una simulación completada guarda al menos un escenario? | US06 y H4 |
| Q11 | ¿Los compradores que comparan escenarios envían su simulación a una inmobiliaria en mayor proporción que los que no comparan? | US07 y H1 |
| Q12 | ¿Qué porcentaje de cuota inicial eligen los compradores y qué parte aplica el Bono del Buen Pagador? | US05 y segmento objetivo |

### **8.1.4. Question Backlog**

Priorizamos las preguntas por su impacto en las hipótesis de negocio y por la facilidad de medirlas con los eventos que ya se registran (escala de 1 a 5). La prioridad resulta del producto de ambas puntuaciones; ante un empate, va primero la pregunta ligada a una hipótesis del Capítulo I.

| Prioridad | Pregunta | Hipótesis o historia | Impacto | Facilidad | Puntaje | Datos disponibles |
|---:|---|---|---:|---:|---:|---|
| 1 | Q1. Tasa de finalización de la simulación | H2 | 5 | 5 | 25 | `simulation_started` y `simulation_completed` del Landing y del móvil |
| 2 | Q3. Conversión a contacto | H1 | 5 | 4 | 20 | `simulation_completed`, `contact_message_sent` y `lead_sent` |
| 3 | Q10. Guardado de escenarios tras simular | US06 y H4 | 4 | 5 | 20 | `simulation_completed` y `scenario_saved` del móvil |
| 4 | Q2. Escenarios y simulaciones por sesión | H3 | 4 | 4 | 16 | `scenario_saved`, `scenarios_compared` y `simulation_completed` |
| 5 | Q7. Uso del periodo de gracia | US03 | 4 | 4 | 16 | Propiedades `graceType` y `graceMonths` de `simulation_completed` y `lead_sent` |
| 6 | Q5. Tiempo hasta la primera simulación | H2 | 3 | 5 | 15 | `page_viewed` o `app_opened` y `simulation_completed` |
| 7 | Q8. Apertura del cronograma completo en el Landing | US15 | 3 | 5 | 15 | `simulation_completed` y `schedule_opened` con `source` igual a `landing` |
| 8 | Q11. Comparación y envío a inmobiliarias | US07 y H1 | 4 | 3 | 12 | `scenarios_compared` y `lead_sent` por sesión |
| 9 | Q12. Cuota inicial y Bono del Buen Pagador | US05 | 3 | 4 | 12 | Propiedades `downPaymentPercent` y `goodPayerBonus` de `simulation_completed` |
| 10 | Q6. Descargas del reporte PDF | US08 | 2 | 5 | 10 | `pdf_exported` |
| 11 | Q4. Retorno de compradores con escenarios | H4 | 4 | 2 | 8 | Fechas de los escenarios guardados por Comprador en la API |
| 12 | Q9. Idioma y finalización en el Landing | US20 | 2 | 4 | 8 | `language_changed` y `simulation_completed` por sesión |

### **8.1.5. Experiment Cards**

Agrupamos las preguntas del backlog en seis experimentos. Cada tarjeta indica qué creemos, qué hacemos para comprobarlo, qué medimos y cuál es el criterio para darlo por válido.

**EXP-A: Finalización de la simulación y conversión a contacto**

| Campo | Contenido |
|---|---|
| Creemos que | Un simulador transparente, que muestra TCEA, bono y cronograma sin pedir registro, hace que los compradores terminen su simulación y luego busquen contacto (H1 y H2). |
| Preguntas | Q1, Q3 y Q5 |
| Para comprobarlo | Medimos el embudo de la simulación sin registro del Landing y de la aplicación, desde que se inicia hasta el contacto o el envío a una inmobiliaria. |
| Medimos | Tasa de finalización, conversión a contacto y mediana del tiempo hasta la primera simulación. |
| Es válido si | Al menos el 60 % de las simulaciones iniciadas se completan y al menos el 10 % de las sesiones con simulación completada termina en contacto. |

**EXP-B: Comparación de escenarios**

| Campo | Contenido |
|---|---|
| Creemos que | Guardar y comparar dos o tres escenarios lado a lado hace que el comprador explore más alternativas (H3). |
| Preguntas | Q2 y Q11 |
| Para comprobarlo | Comparamos las sesiones de compradores que guardan dos o más escenarios con las que no guardan ninguno, y las sesiones que usan la comparación con las que no la usan. |
| Medimos | Simulaciones completadas por sesión y porcentaje de sesiones con `lead_sent`. |
| Es válido si | Las sesiones con dos o más escenarios guardados completan en promedio al menos 1,5 veces más simulaciones que las demás. |

**EXP-C: Periodo de gracia**

| Campo | Contenido |
|---|---|
| Creemos que | Ofrecer gracia parcial o total ayuda a los compradores cuyas primeras cuotas no caben en su presupuesto, y por eso las simulaciones con gracia terminan más veces en un envío a una inmobiliaria (US03). |
| Preguntas | Q7 |
| Para comprobarlo | Segmentamos las simulaciones completadas del móvil por tipo de gracia (ninguna, parcial y total) y seguimos cuáles de esas sesiones envían su simulación. |
| Medimos | Porcentaje de simulaciones con gracia y porcentaje de sesiones con `lead_sent` en cada segmento. |
| Es válido si | Al menos el 15 % de las simulaciones completadas usa gracia y su tasa de envío no es menor que la de las simulaciones sin gracia. |

**EXP-D: Cronograma y reporte como apoyo a la decisión**

| Campo | Contenido |
|---|---|
| Creemos que | Ver el cronograma completo y llevarse el reporte PDF son parte de cómo el comprador decide, no un detalle técnico (US02, US08 y US15). |
| Preguntas | Q8 y Q6 |
| Para comprobarlo | Medimos qué parte de las simulaciones completadas abre el cronograma completo, en el Landing y en la aplicación, y qué parte de los compradores descarga el PDF. |
| Medimos | `schedule_opened` entre `simulation_completed` por producto, y `pdf_exported` entre las sesiones con simulación completada del móvil. |
| Es válido si | Al menos el 30 % de las simulaciones completadas abre el cronograma y al menos el 10 % de las sesiones del móvil con simulación descarga el PDF. |

**EXP-E: Escenarios guardados y retorno**

| Campo | Contenido |
|---|---|
| Creemos que | Una decisión hipotecaria toma varias sesiones, y guardar escenarios hace que el comprador vuelva a la aplicación (H4). |
| Preguntas | Q10 y Q4 |
| Para comprobarlo | Medimos qué parte de las sesiones con simulación guarda un escenario y, para los compradores con escenarios, en cuántos días distintos los guardaron. |
| Medimos | `scenario_saved` entre sesiones con `simulation_completed`, y días distintos de `created_at` en la tabla `scenarios` por Comprador. |
| Es válido si | Al menos el 25 % de las sesiones con simulación guarda un escenario y al menos el 20 % de los compradores con escenarios los guarda en dos o más días distintos. |

**EXP-F: Perfil de la simulación y accesibilidad del idioma**

| Campo | Contenido |
|---|---|
| Creemos que | El segmento objetivo simula con cuotas iniciales cercanas al mínimo y aplica el Bono del Buen Pagador, y ofrecer el sitio en inglés no reduce la finalización (US05 y US20). |
| Preguntas | Q12 y Q9 |
| Para comprobarlo | Describimos la distribución del porcentaje de cuota inicial y el uso del bono en las simulaciones completadas, y comparamos la tasa de finalización del Landing entre sesiones con y sin cambio a inglés. |
| Medimos | Mediana de `downPaymentPercent`, porcentaje con `goodPayerBonus` y tasa de finalización por idioma. |
| Es válido si | La mediana de la cuota inicial está entre 10 % y 20 %, al menos la mitad de las simulaciones aplica el bono y la tasa de finalización en inglés no es menor en más de 10 puntos que en español. |


<div style="page-break-after: always;"></div>

## **8.2. Experiment Design**

### **8.2.1. Hypotheses**

| ID | Hipótesis nula (H0) | Hipótesis alternativa (H1) |
|---|---|---|
| EXP-A | Ver la simulación completa con TCEA, bono y cronograma no se asocia con el contacto: menos del 10 % de las sesiones con simulación completada termina en contacto. | Al menos el 10 % de las sesiones con simulación completada termina en un mensaje de contacto o en un envío consentido a una inmobiliaria. |
| EXP-B | Las sesiones con dos o más escenarios guardados completan en promedio el mismo número de simulaciones que las que no guardan escenarios. | Las sesiones con dos o más escenarios guardados completan en promedio al menos 1,5 veces más simulaciones. |
| EXP-C | Menos del 15 % de las simulaciones usa gracia, o las simulaciones con gracia terminan en un envío a una inmobiliaria menos veces que las simulaciones sin gracia. | Al menos el 15 % de las simulaciones usa gracia y su tasa de envío es igual o mayor que la de las simulaciones sin gracia. |
| EXP-D | Menos del 30 % de las simulaciones completadas abre el cronograma completo y menos del 10 % de las sesiones del móvil descarga el PDF. | Al menos el 30 % abre el cronograma y al menos el 10 % descarga el PDF. |
| EXP-E | Menos del 25 % de las sesiones con simulación guarda un escenario, o menos del 20 % de los compradores con escenarios los guarda en días distintos. | Al menos el 25 % guarda un escenario y al menos el 20 % de los compradores con escenarios los guarda en dos o más días distintos. |
| EXP-F | La finalización en inglés es más de 10 puntos menor que en español. | La finalización en inglés no es menor en más de 10 puntos que en español; la cuota inicial y el uso del bono se describen sin hipótesis de comparación. |

### **8.2.2. Domain Business Metrics**

| Métrica | Definición | Relación con el negocio |
|---|---|---|
| Tasa de finalización de la simulación | Simulaciones completadas entre simulaciones iniciadas | Indica si la herramienta es comprensible para un comprador sin experiencia (H2). |
| Conversión a contacto | Sesiones con contacto o lead enviado entre sesiones con una simulación completada | Mide el valor del simulador para las inmobiliarias (H1). |
| Simulaciones por sesión | Promedio de simulaciones completadas en cada sesión | Mide la exploración de alternativas (H3). |
| Retorno de compradores | Compradores con escenarios guardados en dos o más días distintos entre compradores con escenarios | Mide la retención (H4). |
| Tiempo hasta la primera simulación | Mediana de segundos entre la entrada y la primera simulación completada | Mide la facilidad de uso. |

### **8.2.3. Measurements**

| Medida | Cálculo con los datos registrados |
|---|---|
| Simulaciones iniciadas | Número de eventos `simulation_started` por producto (`source`) |
| Simulaciones completadas | Número de eventos `simulation_completed` por producto |
| Sesiones con simulación completada | Sesiones (`session_id`) con al menos un `simulation_completed` |
| Sesiones con contacto | Sesiones con `contact_message_sent` (Landing) o `lead_sent` (móvil) |
| Escenarios por sesión | Número de `scenario_saved` por sesión |
| Comparaciones | Número de `scenarios_compared` |
| Tiempo hasta la primera simulación | Segundos entre el primer evento de la sesión y su primer `simulation_completed` |
| Retorno | Días distintos de `created_at` en la tabla `scenarios` por Comprador |

Los indicadores se calculan con `tools/compute_kpis.py` sobre el CSV que exporta `tools/export_usage_events.py`, con la configuración `tools/kpi_config.json` del repositorio de la API.

### **8.2.4. Conditions**

- **Productos:** Landing Page publicado y versión 0.1.0 (110) de la aplicación Android, conectados a la API desplegada en Render.
- **Participantes:** solo personas reales. Cada integrante invita al menos a dos personas y anota quién, cuándo y qué hizo (EXP1). Las cuentas y pruebas del equipo se excluyen del análisis por su identificador de sesión y por la fecha.
- **Privacidad:** los eventos no contienen nombre, correo, teléfono, DNI ni el nombre del escenario. La API rechaza propiedades con nombres de datos personales y el pie legal de las aplicaciones informa el registro anónimo.
- **Periodo:** dos semanas desde la publicación de la versión, sin cambiar las funciones medidas durante ese tiempo.
- **Exclusiones:** sesiones con un solo evento `page_viewed` o `app_opened` cuentan como visitas, pero no entran en las tasas de finalización.

### **8.2.5. Scale Calculations and Decisions**

| Experimento | Muestra mínima | Decisión si se cumple | Decisión si no se cumple |
|---|---|---|---|
| EXP-A | 30 sesiones con una simulación iniciada | Mantener el flujo y priorizar mejoras en el envío a inmobiliarias (Sprint 4). | Revisar el formulario: el paso con más abandono se rediseña y se vuelve a medir. |
| EXP-B | 10 compradores registrados con al menos un escenario | Promover el guardado desde Resultados y mantener la comparación. | Evaluar con entrevistas si la comparación se entiende antes de seguir invirtiendo en ella. |
| EXP-C | 30 simulaciones completadas en el móvil | Destacar la gracia en el formulario y explicar su costo en Resultados. | Revisar si el selector de gracia se entiende; si no, simplificarlo o moverlo a una opción avanzada. |
| EXP-D | 30 simulaciones completadas | Mantener el cronograma y el PDF como funciones principales y mejorar su presentación. | Reducir su protagonismo en la pantalla y priorizar otras funciones del backlog. |
| EXP-E | 15 sesiones del móvil con simulación completada | Agregar recordatorios para volver a los escenarios guardados (Sprint 4). | Reforzar la invitación a guardar desde Resultados y volver a medir. |
| EXP-F | 30 sesiones del Landing con simulación iniciada | Mantener los valores por defecto del formulario y el sitio bilingüe. | Ajustar los valores por defecto del formulario y revisar las traducciones del simulador. |

Con un equipo de seis integrantes y al menos dos personas por integrante, esperamos entre 12 y 20 participantes directos además del tráfico del Landing. Si no se alcanza la muestra mínima, los resultados se reportan como exploratorios y se complementan con las entrevistas de validación.

### **8.2.6. Methods Selection**

- **Análisis de embudo** con los eventos de uso, para EXP-A y EXP-D.
- **Comparación de grupos** (sesiones con y sin escenarios guardados, con y sin gracia, en español y en inglés), para EXP-B, EXP-C y EXP-F, con la diferencia de proporciones o de medias y su intervalo de confianza si la muestra lo permite.
- **Análisis de cohortes** por Comprador con las fechas de los escenarios guardados, para EXP-E.
- **Estadística descriptiva** (mediana y distribución) del porcentaje de cuota inicial y del uso del bono, para EXP-F.
- **Entrevistas cortas** con algunos participantes, para explicar los resultados del embudo (sección 8.3.4).

### **8.2.7. Data Analytics: Goals, KPIs and Metrics Selection**

| Objetivo | KPI | Meta |
|---|---|---|
| Que el comprador termine su simulación | Tasa de finalización de la simulación | 60 % o más |
| Que la simulación genere contacto | Conversión a contacto | 10 % o más |
| Que el comprador compare alternativas | Simulaciones por sesión con dos o más escenarios guardados frente a sin escenarios | 1,5 veces o más |
| Que el producto sea fácil de usar | Mediana del tiempo hasta la primera simulación | 120 segundos o menos |
| Que el comprador lleve su resultado al banco | Descargas del reporte PDF | Indicador de seguimiento, sin meta |

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

Cada evento lleva un identificador de sesión aleatorio, que se crea al abrir el Landing o la aplicación, y el producto de origen (`landing` o `mobile`). Los eventos se envían en segundo plano: si el envío falla, se descartan sin afectar al usuario.

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
