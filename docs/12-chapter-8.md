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
