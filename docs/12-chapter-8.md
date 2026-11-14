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
### **8.1.4. Question Backlog**
### **8.1.5. Experiment Cards**
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
