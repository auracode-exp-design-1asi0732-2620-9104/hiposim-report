# **Chapter IV: Product Design**

Este capítulo presenta la propuesta de Software Architecture & Design de HipoSim, traduciendo las User Stories y el Impact Map identificados en el Capítulo III en decisiones concretas de diseño: el sistema de estilo visual compartido por todos los productos, la arquitectura de información que organiza el contenido para cada rol, el diseño UX/UI del Landing Page, la Web Application y la Mobile Application, y el diseño técnico de la solución: Domain-Driven Software Architecture, Object-Oriented Design y Database Design.

## **4.1. Style Guidelines**

Esta sección establece un lenguaje visual compartido y centralizado para todos los productos de HipoSim (el Landing Page, la Web Application y la Native Mobile Application), de modo que los assets, las fuentes, los colores y el tono se mantengan consistentes sin importar la plataforma desde la que el usuario o visitante acceda. Conforme a las restricciones técnicas del curso, el equipo adopta **Material Design** como sistema de diseño base, adaptado mediante **PrimeVue** para la web y trasladado de forma nativa a iOS y Android en móvil.

### **4.1.1. General Style Guidelines**

**Branding.** El nombre del producto, HipoSim, comunica directamente sus dos rasgos definitorios: "Hipo-" (hipotecario) indica el dominio, y "-Sim" indica la naturaleza de la herramienta: un simulador, no un banco. El logo y el wordmark (ver Capítulo II, análisis competitivo) evitan cualquier asociación visual con una entidad financiera específica, reforzando la propuesta de valor central del producto: la independencia frente a cualquier banco.

**Tono de comunicación.** Debido a que HipoSim aborda una decisión financiera de alto impacto para personas con poca o ninguna experiencia previa en créditos, el tono se calibra deliberadamente para generar confianza sin intimidar al usuario:

| Dimensión | Posición adoptada | Justificación |
|---|---|---|
| Divertido ↔ Serio | Tiende a **Serio**, con lenguaje cercano | Los términos hipotecarios (TCEA, periodo de gracia, amortización) son inherentemente técnicos; el tono no debe trivializar un compromiso financiero de 15 a 20 años. |
| Formal ↔ Casual | **Semiformal** | Lo bastante formal para transmitir credibilidad en las cifras financieras, y lo bastante casual para no sonar como texto legal bancario. |
| Respetuoso ↔ Irreverente | **Respetuoso** | El usuario está tomando por primera vez una decisión de alta ansiedad; no hay espacio para la ironía ni el sarcasmo en los textos. |
| Entusiasta ↔ Sereno | Tiende a **Sereno** | El diferenciador del producto es la transparencia y la claridad tranquila, no el entusiasmo ni la persuasión basada en urgencia. |

**Tipografía.** La escala tipográfica sigue los type tokens de Material Design 3 (Display, Headline, Title, Body, Label), utilizando una única familia sans-serif humanista (Roboto, la tipografía por defecto incluida en el tema Material de PrimeVue) en todos los productos, para mantener legibles en pantallas pequeñas los datos numéricos (tasas de interés, montos en moneda, porcentajes de TCEA).

**Colores.** La paleta separa el color de marca del color semántico o de estado, en línea con los roles de color de Material Design:

| Rol | Uso |
|---|---|
| Primary | Navegación, CTAs principales ("Simular ahora", "Guardar simulación") |
| Secondary / Accent | Elementos destacados dentro de la vista de resultados (por ejemplo, el resaltado del TCEA) |
| Success | Estados de confirmación (el beneficio aplica, simulación guardada) |
| Warning | Alertas no bloqueantes (por ejemplo, TCEA por encima de un umbral configurado, según la notificación in-app definida en el Capítulo I) |
| Error | Errores de validación de formularios |
| Neutral / Surface | Fondos, tarjetas, divisores |

Las combinaciones de color para texto y elementos interactivos deben cumplir las **relaciones de contraste WCAG AA**, en línea con el requisito de Accesibilidad (a11y) descrito más adelante en este capítulo.

**Espaciado.** Se utiliza una cuadrícula base de 8px (estándar de Material Design) para todas las decisiones de espaciado, padding y dimensionamiento de componentes, a fin de mantener la alineación consistente entre los archivos de diseño en Figma y las implementaciones en PrimeVue y nativas.

### **4.1.2. Web Style Guidelines**

La Web Application y el Landing Page siguen **Responsive Web Design**, con tres breakpoints: móvil (< 768px), tablet (768px-1024px) y escritorio (> 1024px), sobre una cuadrícula fluida de 12 columnas.

Los componentes de UI de la Web Application provienen de **PrimeVue** (tema Material) para garantizar consistencia y reducir el CSS personalizado: componentes stepper/wizard para el formulario de simulación de varios pasos (datos del cliente → datos de la vivienda → parámetros del crédito → resultados), tablas de datos para el cronograma de amortización y el historial de simulaciones, tarjetas para la comparación de escenarios, y componentes toast/banner para la notificación in-app de umbral.

El Landing Page, construido con HTML5/CSS3/JavaScript puro, replica los mismos tokens de color, tipografía y espaciado que la Web Application (documentados como variables CSS compartidas) aunque no dependa de PrimeVue, de modo que el Visitante no perciba una discontinuidad visual al pasar del Landing Page al producto registrado.

### **4.1.3. Mobile Style Guidelines**

Ambas plataformas móviles comparten los mismos tokens de marca (color, proporciones de la escala tipográfica, iconografía) definidos en 4.1.1, pero cada una adapta sus patrones de navegación e interacción a las convenciones que sus usuarios ya esperan de las aplicaciones nativas.

#### **4.1.3.1. iOS Mobile Style Guidelines**

En iOS, la estructura y las convenciones de gestos siguen las Human Interface Guidelines de Apple (barra de pestañas inferior para la navegación principal, layouts que respetan las safe areas, navegación con swipe hacia atrás, hojas modales nativas para los pasos del asistente de simulación), mientras que el estilo visual (color, elevación, tipografía) se mantiene alineado con el sistema basado en Material definido para el producto, y no con el estilo visual por defecto de iOS, en coherencia con el único Design System aplicado en web y móvil.

#### **4.1.3.2. Android Mobile Style Guidelines**

En Android, tanto la estructura como el estilo visual siguen de forma nativa las guías de Material Design: barra de navegación inferior, un Floating Action Button (FAB) para la acción principal "Nueva simulación" desde la pantalla de historial, y las convenciones de elevación y sombras de Material para las tarjetas (comparación de escenarios) y la hoja de resultados.

## **4.2. Information Architecture**

Esta sección define cómo se organiza el contenido en el Landing Page, la Web Application y la Mobile Application, de modo que los Visitantes, Compradores y Administradores encuentren lo que necesitan con el mínimo esfuerzo, respaldando directamente el alcance de tres roles definido en el Capítulo I.

### **4.2.1. Organization Systems**

- **La organización jerárquica** se aplica al Landing Page (Inicio → Producto → Beneficios → Nosotros/Términos) y a la pantalla de configuración del Administrador (Parámetros base → Métricas de uso), ya que ambos agrupan el contenido por importancia temática y no por secuencia.
- **La organización secuencial (paso a paso)** se aplica al flujo de simulación, la tarea central del producto: datos del cliente → datos de la vivienda → parámetros del crédito (monto, TEA/TNA, plazo, periodo de gracia) → resultados (cronograma de amortización, VAN/TIR/TCEA, beneficios estatales aplicables). Esto refleja cómo se realiza una evaluación hipotecaria real y evita abrumar a un usuario primerizo con todos los campos a la vez.
- **La organización matricial** se aplica al comparador de escenarios, donde 2 o 3 simulaciones guardadas se disponen lado a lado frente al mismo conjunto de indicadores financieros (filas), de modo que el Comprador pueda comparar en igualdad de condiciones.

El contenido se categoriza principalmente **por audiencia** (contenido del Visitante en el Landing Page frente al contenido del Comprador tras iniciar sesión y el del Administrador en el panel de configuración), y secundariamente **por tópicos** dentro del Landing Page (visión general del producto, explicación de beneficios estatales, propuesta de independencia frente a los competidores, Términos y Condiciones).

### **4.2.2. Labeling Systems**

Las etiquetas de navegación son cortas, en lenguaje sencillo y consistentes entre web y móvil:

| Etiqueta | Hace referencia a |
|---|---|
| Simular | Iniciar o continuar una nueva simulación de crédito |
| Comparar | Comparador de escenarios (2 a 3 simulaciones guardadas) |
| Historial | Lista de simulaciones guardadas previamente |
| Beneficios | Explicación del Bono del Buen Pagador / Mivivienda y los requisitos para acceder |
| Exportar / Compartir | Exportación a PDF y enlace de solo lectura para compartir una simulación |
| Configuración | Pantalla de parámetros base del Administrador (tasas, % del BBP, rangos Mivivienda) |

Las etiquetas evitan intencionalmente términos internos o técnicos (por ejemplo, "TCEA" siempre va acompañado de una breve explicación en lenguaje sencillo la primera vez que aparece en una pantalla) para que un comprador primerizo sin formación financiera no se pierda en una jerga de dominio que, según las entrevistas del Capítulo II, los usuarios no comprenden con claridad.

### **4.2.3. SEO Tags and Meta Tags**

| Página | Title | Meta Description | Keywords | Author |
|---|---|---|---|---|
| Landing: Inicio | HipoSim \| Simulador Independiente de Crédito Hipotecario en Perú | Simula tu crédito hipotecario gratis, compara condiciones reales y descubre beneficios estatales como el Bono del Buen Pagador antes de hablar con un banco. | simulador hipotecario Perú, crédito hipotecario, TCEA, Bono del Buen Pagador, Mivivienda | HipoSim / AuraCode |
| Landing: Beneficios | HipoSim \| Bono del Buen Pagador y Nuevo Crédito Mivivienda Explicados | Descubre si calificas para los beneficios estatales hipotecarios y cuánto reducen el costo real de tu crédito. | Bono del Buen Pagador, Nuevo Crédito Mivivienda, subsidio vivienda Perú | HipoSim / AuraCode |
| Web App: Simulador | HipoSim \| Inicia tu Simulación Hipotecaria | Ingresa tus ingresos y la vivienda que deseas comprar para ver el costo real de tu hipoteca, el cronograma de amortización y el TCEA. | simulador hipotecario, cuota hipotecaria, amortización francesa | HipoSim / AuraCode |

### **4.2.4. Searching Systems**

Dado el conjunto intencionalmente pequeño de datos que maneja un Comprador (un puñado de simulaciones guardadas, conforme al alcance "un poco más de alcance" definido en el Capítulo I), HipoSim no implementa una búsqueda de texto completo de propósito general. En su lugar, ofrece **filtros** ligeros donde aportan valor real:

- **Historial**: filtro por rango de fechas y por tipo de vivienda, para que un usuario que vuelve a la herramienta tras varias semanas pueda encontrar una simulación específica sin desplazarse por toda la lista.
- **Comparador**: la selección se realiza eligiendo directamente de la lista (ya corta) de simulaciones guardadas, no mediante búsqueda.

Esta decisión mantiene al producto alineado con el principio "Simplest Useful Thing" referenciado para la fase de experimentación del curso (Capítulo VIII), evitando invertir en un sistema de búsqueda que el segmento no necesita a esta escala.

### **4.2.5. Navigation Systems**

- **Landing Page (Visitante)**: barra de navegación superior persistente (Inicio, Producto, Beneficios, Términos) más un llamado a la acción persistente "Simular ahora" que permite al Visitante probar el simulador básico sin registrarse, en coherencia con el rol de Visitante definido en el Capítulo I.
- **Web Application (Comprador)**: navegación lateral (escritorio) que colapsa en un menú desplegable superior (web móvil) con Simular, Historial y Comparar como destinos principales; un indicador de pasos tipo breadcrumb dentro del asistente de simulación muestra el progreso a lo largo de sus cuatro pasos.
- **Native Mobile Application**: barra de pestañas inferior con los mismos destinos principales (Simular, Historial, Comparar, Perfil), siguiendo la convención propia de cada plataforma descrita en 4.1.3.
- **Administrador**: un único punto de entrada de configuración, separado (no expuesto a los Compradores), accesible tras el inicio de sesión del Administrador, que contiene la pantalla de parámetros y el panel básico de métricas de uso.

## **4.3. Landing Page UI Design**
### **4.3.1. Landing Page Wireframe**
### **4.3.2. Landing Page Mock-up**
## **4.4. Mobile Applications UX/UI Design**
### **4.4.1. Mobile Applications Wireframes**
### **4.4.2. Mobile Applications Wireflow Diagrams**
### **4.4.3. Mobile Applications Mock-ups**
### **4.4.4. Mobile Applications User Flow Diagrams**
## **4.5. Mobile Applications Prototyping**
### **4.5.1. Android Mobile Applications Prototyping**
### **4.5.2. iOS Mobile Applications Prototyping**
## **4.6. Web Applications UX/UI Design**
### **4.6.1. Web Applications Wireframes**
### **4.6.2. Web Applications Wireflow Diagrams**
### **4.6.3. Web Applications Mock-ups**
### **4.6.4. Web Applications User Flow Diagrams**
## **4.7. Web Applications Prototyping**
## **4.8. Domain-Driven Software Architecture**

Esta sección propone la arquitectura de software de HipoSim utilizando el **Modelo C4** (Context, Container, Component), construida sobre las User Stories y el Impact Map del Capítulo III y sobre el alcance del checklist definido en el Capítulo I. Los diagramas a continuación fueron generados a partir de fuentes Diagram-as-Code (guardadas junto a las imágenes en `assets/08-chapter-4/domain-driven-software-architecture/`) como borrador de trabajo; el equipo formalizará las versiones finales en **Structurizr** (Modelo C4), conforme a las restricciones tecnológicas del curso, antes de la siguiente entrega.

### **4.8.1. Software Architecture Context Diagram**

A nivel de contexto, tres actores interactúan con un único sistema de software, **HipoSim Platform**, sin integración con sistemas externos reales en el alcance actual (sin integración bancaria real ni pasarela de pagos real, en coherencia con lo que está explícitamente fuera de alcance según el Capítulo I):

<div align="center">
  <img src="../assets/08-chapter-4/domain-driven-software-architecture/context-diagram.png" alt="Diagrama de contexto del sistema HipoSim" width="800">
</div>

### **4.8.2. Software Architecture Container Diagrams**

A nivel de contenedores, la plataforma se descompone en los productos definidos en el checklist de alcance técnico del Capítulo I: un Landing Page estático, una Web Application basada en Vue, una Native Mobile Application, una única RESTful API compartida y una base de datos relacional.

<div align="center">
  <img src="../assets/08-chapter-4/domain-driven-software-architecture/container-diagram.png" alt="Diagrama de contenedores de HipoSim" width="700">
</div>

### **4.8.3. Software Architecture Components Diagrams**

Dentro del contenedor RESTful Web API, los componentes se organizan por responsabilidad, manteniendo la lógica del dominio financiero aislada de las preocupaciones de transporte y persistencia:

| Componente | Responsabilidad |
|---|---|
| `AuthController` / `AuthService` | Registro e inicio de sesión de Comprador y Administrador; autorización basada en roles |
| `SimulationController` / `SimulationService` | Orquesta una solicitud de simulación: valida los datos de entrada, invoca al Financial Engine y al Benefits Engine, y persiste los resultados |
| `ScenarioController` / `ScenarioService` | Guarda, recupera y agrupa simulaciones en comparaciones de escenarios de 2 a 3 elementos |
| `ReportController` / `ReportGenerationService` | Genera el PDF exportable y el enlace de solo lectura para compartir una simulación |
| `AdminController` / `AdminParameterService` | CRUD de los parámetros base (tasas de referencia, % del Bono del Buen Pagador, rangos Mivivienda) y expone las métricas básicas de uso |
| `FinancialEngine` | Lógica de dominio portada del proyecto original AutoFinance Pro: método de amortización francés, conversión de tasas, periodos de gracia, cálculo de VAN/TIR/TCEA |
| `BenefitsEngine` | Evalúa la elegibilidad al Bono del Buen Pagador / Nuevo Crédito Mivivienda y su efecto en la simulación, según los parámetros configurados por el Administrador |
| `Repositories` (por agregado) | Acceso de persistencia a PostgreSQL mediante Entity Framework Core |

<div align="center">
  <img src="../assets/08-chapter-4/domain-driven-software-architecture/components-diagram.png" alt="Diagrama de componentes de la RESTful API de HipoSim" width="750">
</div>

## **4.9. Software Object-Oriented Design**

### **4.9.1. Class Diagrams**

El diseño de clases a continuación refleja las entidades centrales del dominio que se desprenden del alcance del producto en el Capítulo I (datos del cliente, datos de la vivienda, parámetros de simulación, resultados financieros, beneficios estatales, comparación de escenarios, parámetros de administración), independientemente de cualquier tecnología de persistencia específica. Este diagrama fue generado a partir de una fuente Diagram-as-Code (guardada junto a la imagen en `assets/08-chapter-4/software-object-oriented-design/`) como borrador de trabajo; el equipo lo formalizará en **LucidChart**, conforme a las restricciones tecnológicas del curso.

<div align="center">
  <img src="../assets/08-chapter-4/software-object-oriented-design/class-diagram.png" alt="Diagrama de clases de HipoSim" width="900">
</div>

### **4.9.2. Class Dictionary**

| Clase | Atributos principales | Métodos principales | Descripción |
|---|---|---|---|
| `User` | Id, FullName, Email, PasswordHash, Role | Register(), Login() | Cuenta base compartida por Buyer y Administrator, diferenciada por rol según lo definido en el Capítulo I. |
| `Buyer` | MonthlyIncome, AvailableSavings | Ninguno | Comprador de primera vivienda registrado; puede ser propietario de Simulations y ScenarioComparisons. |
| `Administrator` | Ninguno | UpdateBaseParameters(), ViewUsageMetrics() | Miembro interno del equipo que mantiene los valores de AdminParameter y monitorea las métricas básicas de uso. |
| `Property` | Price, Currency, Type | Ninguno | La vivienda evaluada en una Simulation (precio, moneda, tipo de vivienda). |
| `Simulation` | LoanAmount, AnnualRate, RateType, TermInMonths, GracePeriodMonths, GraceType | Calculate() | Encapsula los parámetros de entrada de una simulación de crédito y dispara el cálculo por método francés portado de AutoFinance Pro. |
| `AmortizationEntry` | Period, Installment, Interest, Amortization, RemainingBalance | Ninguno | Una fila del cronograma de amortización francés producido por una Simulation. |
| `FinancialIndicatorResult` | Npv, Irr, Tcea | Ninguno | Los indicadores VAN, TIR y TCEA calculados para una Simulation. |
| `StateBenefit` | Name, DiscountPercentage, MinPropertyPrice, MaxPropertyPrice | EvaluateEligibility() | Representa el Bono del Buen Pagador o el Nuevo Crédito Mivivienda, y si una Simulation dada califica. |
| `ScenarioComparison` | CreatedAt | AddSimulation() | Agrupa de 2 a 3 Simulations del mismo Buyer para su comparación lado a lado. |
| `SimulationReport` | ShareableLinkToken | GeneratePdf() | Produce el PDF exportable y el enlace de solo lectura para compartir una Simulation. |
| `AdminParameter` | Key, Value, UpdatedAt | Ninguno | Un parámetro base configurable (tasa de referencia, % del Bono del Buen Pagador, rango Mivivienda) mantenido por un Administrator. |

## **4.10. Database Design**

### **4.10.1. Relational/Non-Relational Database Diagram**

Se propone un modelo relacional (PostgreSQL), consistente con el diseño de clases de 4.9 y con la base de datos del proyecto original AutoFinance Pro. Este diagrama fue generado a partir de una fuente Diagram-as-Code (guardada junto a la imagen en `assets/08-chapter-4/database-design/`) como borrador de trabajo; el equipo lo formalizará en **LucidChart / Vertabelo**, conforme a las restricciones tecnológicas del curso.

<div align="center">
  <img src="../assets/08-chapter-4/database-design/er-diagram.png" alt="Diagrama de base de datos relacional de HipoSim" width="900">
</div>
