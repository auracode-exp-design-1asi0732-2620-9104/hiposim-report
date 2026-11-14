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

1. **Q1.** ¿Qué porcentaje de las simulaciones iniciadas en el Landing Page y en la aplicación móvil se completan?
2. **Q2.** ¿Los compradores que guardan dos o más escenarios completan más simulaciones por sesión que los que no guardan ninguno?
3. **Q3.** ¿Qué porcentaje de las sesiones con una simulación completada termina en una solicitud de contacto: mensaje en el Landing Page o envío consentido a una inmobiliaria en la aplicación?
4. **Q4.** ¿Los compradores que guardan escenarios vuelven a usar la aplicación en días distintos?
5. **Q5.** ¿Cuánto tiempo tarda un visitante, desde que entra, en completar su primera simulación?
6. **Q6.** ¿Qué parte de los compradores descarga el reporte PDF de su simulación?

### **8.1.4. Question Backlog**

Priorizamos las preguntas por su impacto en las hipótesis de negocio y por la facilidad de medirlas con los eventos que ya se registran (escala de 1 a 5).

| Prioridad | Pregunta | Hipótesis | Impacto | Facilidad de medición | Datos disponibles |
|---:|---|---|---:|---:|---|
| 1 | Q1. Tasa de finalización de la simulación | H2 | 5 | 5 | `simulation_started` y `simulation_completed` del Landing y del móvil |
| 2 | Q3. Conversión a contacto | H1 | 5 | 4 | `simulation_completed`, `contact_message_sent` y `lead_sent` |
| 3 | Q2. Escenarios y simulaciones por sesión | H3 | 4 | 4 | `scenario_saved`, `scenarios_compared` y `simulation_completed` |
| 4 | Q5. Tiempo hasta la primera simulación | H2 | 3 | 5 | `page_viewed` o `app_opened` y `simulation_completed` |
| 5 | Q4. Retorno de compradores con escenarios | H4 | 4 | 2 | Fechas de los escenarios guardados por Comprador en la API |
| 6 | Q6. Descargas del reporte PDF | Ninguna directa | 2 | 5 | `pdf_exported` |

### **8.1.5. Experiment Cards**

| Campo | EXP-A: Finalización y conversión | EXP-B: Comparación de escenarios |
|---|---|---|
| Hipótesis | H1 y H2 | H3 |
| Pregunta | Q1, Q3 y Q5 | Q2 |
| Qué hacemos | Medimos el embudo de la simulación sin registro del Landing y de la aplicación hasta el contacto o el envío a una inmobiliaria. | Comparamos las sesiones de compradores que guardan dos o más escenarios con las que no guardan ninguno. |
| Qué medimos | Tasa de finalización, conversión a contacto y tiempo hasta la primera simulación. | Simulaciones completadas por sesión y uso de la comparación. |
| Criterio de éxito | Al menos 60 % de las simulaciones iniciadas se completan y al menos 10 % de las sesiones con simulación completada termina en contacto. | Las sesiones con dos o más escenarios guardados completan en promedio al menos 1,5 veces más simulaciones que las demás. |
| Participantes | Personas reales que cada integrante invita a probar el Landing y el APK (EXP1), más el tráfico del Landing publicado. | Compradores registrados en la aplicación móvil. |
| Duración | Dos semanas desde la publicación de la versión 0.1.0 (110). | Dos semanas, en paralelo con EXP-A. |

<div style="page-break-after: always;"></div>

## **8.2. Experiment Design**

### **8.2.1. Hypotheses**

| ID | Hipótesis nula (H0) | Hipótesis alternativa (H1) |
|---|---|---|
| EXP-A | Ver la simulación completa con TCEA, bono y cronograma no se asocia con el contacto: menos del 10 % de las sesiones con simulación completada termina en contacto. | Al menos el 10 % de las sesiones con simulación completada termina en un mensaje de contacto o en un envío consentido a una inmobiliaria. |
| EXP-B | Las sesiones con dos o más escenarios guardados completan en promedio el mismo número de simulaciones que las que no guardan escenarios. | Las sesiones con dos o más escenarios guardados completan en promedio al menos 1,5 veces más simulaciones. |

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

Con un equipo de seis integrantes y al menos dos personas por integrante, esperamos entre 12 y 20 participantes directos además del tráfico del Landing. Si no se alcanza la muestra mínima, los resultados se reportan como exploratorios y se complementan con las entrevistas de validación.

### **8.2.6. Methods Selection**

- **Análisis de embudo** con los eventos de uso, para EXP-A.
- **Comparación de grupos** (sesiones con y sin escenarios guardados), para EXP-B, con la diferencia de medias y su intervalo de confianza si la muestra lo permite.
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
