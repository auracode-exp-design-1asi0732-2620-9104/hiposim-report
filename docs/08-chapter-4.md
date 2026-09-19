# **Chapter IV: Product Design**

Este capítulo presenta la propuesta de Software Architecture & Design de HipoSim, traduciendo las User Stories y el Impact Map identificados en el Capítulo III en decisiones concretas de diseño: el sistema de estilo visual compartido por todos los productos, la arquitectura de información que organiza el contenido para cada rol, el diseño UX/UI del Landing Page, la Web Application y la Mobile Application, y el diseño técnico de la solución: Domain-Driven Software Architecture, Object-Oriented Design y Database Design.

## **4.1. Style Guidelines**

Esta sección establece un lenguaje visual compartido y centralizado para todos los productos de HipoSim (el Landing Page, la Web Application y la Native Mobile Application), de modo que los assets, las fuentes, los colores y el tono se mantengan consistentes sin importar la plataforma desde la que el usuario o visitante acceda. Conforme a las restricciones técnicas del curso, el equipo adopta **Material Design** como sistema de diseño base, adaptado mediante **PrimeVue** para la web y trasladado de forma nativa a iOS y Android en móvil.

### **4.1.1. General Style Guidelines**

A continuación se presentan las pautas generales de estilo que guiarán la identidad visual de HipoSim, asegurando coherencia, claridad y una experiencia de navegación fluida para todos los usuarios. Las decisiones se apoyan en los principios de Material Design y buscan transmitir confianza, transparencia y cercanía, atributos clave para un producto que acompaña una decisión financiera de largo plazo.

---

**Colors**

Se ha seleccionado una paleta de cinco colores que representa la identidad de HipoSim. Los colores fueron elegidos para transmitir confianza y estabilidad (propias del ámbito financiero), sin caer en los azules y verdes corporativos que hoy identifican a los bancos que ofrecen simuladores hipotecarios (BCP, Interbank), reforzando así el mensaje de independencia del producto. El ámbar aporta la calidez asociada al hogar y se reserva para los puntos de acción.

| Color | Hex | Rol en la interfaz |
|---|---|---|
| Verde azulado | `#0E5C63` | Color principal. Transmite confianza, estabilidad y seriedad financiera. Se usa en navegación, encabezados y botones primarios. |
| Turquesa | `#3AAFA9` | Color secundario. Complementa al principal aportando frescura y claridad. Se usa en gráficos, iconos y elementos de apoyo. |
| Ámbar | `#F5A524` | Color de acento. Aporta calidez y energía, atrayendo la atención en los puntos clave (por ejemplo, "Simular ahora" y el resaltado del TCEA). |
| Gris pizarra | `#5F6B76` | Color neutro. Se usa en textos secundarios, bordes y elementos deshabilitados, manteniendo el equilibrio visual. |
| Blanco | `#FFFFFF` | Fondo base. Brinda claridad y limpieza, permitiendo que los demás colores destaquen. |

<div align="center">
  <img src="../assets/08-chapter-4/style-guidelines/color-palette.png" alt="Paleta de colores de HipoSim" width="800">
</div>

Como apoyo a la paleta principal, la interfaz utiliza un color de texto principal (`#1F2933`) y colores de estado para los mensajes al usuario:

| Estado | Hex | Uso |
|---|---|---|
| Éxito | `#2E9E6B` | Confirmaciones (simulación guardada, el beneficio estatal aplica). |
| Advertencia | `#F5A524` | Alertas no bloqueantes (por ejemplo, TCEA por encima del umbral configurado). Reutiliza el ámbar de acento. |
| Error | `#D64545` | Errores de validación de formularios. |

Todas las combinaciones de texto y fondo deben cumplir la relación de contraste **WCAG AA** (mínimo 4.5:1 para texto normal). En particular, el texto sobre `#0E5C63` y `#5F6B76` es blanco, mientras que el texto sobre el turquesa `#3AAFA9` y el ámbar `#F5A524` es siempre el color oscuro `#1F2933`.

---

**Branding**

El branding de HipoSim define la identidad visual de la marca con el objetivo de comunicar de forma inmediata su propuesta de valor: ayudar a compradores de primera vivienda a entender, de manera independiente y transparente, cuánto costará realmente su crédito hipotecario antes de acercarse a un banco.

El nombre combina "Hipo-" (hipotecario), que indica el dominio, y "-Sim", que indica la naturaleza de la herramienta: un simulador, no un banco. El logotipo integra dos ideas en un mismo símbolo: una casa, que representa la primera vivienda, y tres barras ascendentes en su interior, que representan la simulación y el cronograma de pagos. La última barra se destaca en ámbar, en referencia al resultado clave que el usuario busca: el costo real de su crédito. El wordmark separa visualmente "Hipo" (verde azulado) y "Sim" (ámbar), y se acompaña del descriptor "Simulador hipotecario" para dejar claro desde el primer contacto qué es el producto.

<div align="center">
  <img src="../assets/08-chapter-4/style-guidelines/logo-hiposim.png" alt="Logotipo de HipoSim" width="500">
</div>

El ícono (sin el wordmark) se utiliza en espacios reducidos como el favicon, el ícono de la aplicación móvil y los avatares.

<div align="center">
  <img src="../assets/08-chapter-4/style-guidelines/logo-icon.png" alt="Ícono de HipoSim" width="120">
</div>

Los archivos fuente del logotipo en formato vectorial (`logo-hiposim.svg` y `logo-icon.svg`) se conservan en `assets/08-chapter-4/style-guidelines/`.

---

**Typography**

La tipografía principal seleccionada para el Landing Page y la Web Application es **Poppins** para encabezados y **Roboto** para el cuerpo de texto. Poppins, una sans-serif geométrica, aporta un carácter moderno y cercano que refuerza el wordmark de la marca; Roboto, la tipografía por defecto del tema Material de PrimeVue, garantiza una lectura clara de párrafos y, sobre todo, de datos numéricos (tasas de interés, montos, porcentajes de TCEA) incluso en pantallas pequeñas.

El tamaño y el peso tipográfico varían según el nivel jerárquico del contenido y el tipo de dispositivo utilizado:

| Elemento | Tipografía | Peso | Tamaño |
|---|---|---|---|
| Encabezado principal (H1) | Poppins | Bold (700) | 40-56 px |
| Subtítulos (H2, H3) | Poppins | SemiBold (600) | 24-32 px |
| Texto destacado | Roboto | Medium (500) | 18-20 px |
| Texto de párrafo / cuerpo | Roboto | Regular (400) | 16-18 px |
| Texto secundario | Roboto | Regular (400) | 14 px |
| Cifras clave (cuota, TCEA) | Poppins | SemiBold (600) | 32-48 px |
| Botón principal | Roboto | Medium (500) | 16 px |
| Botón secundario | Roboto | Medium (500) | 14 px |

---

**Spacing**

El espaciado garantiza armonía visual y legibilidad en todas las secciones de la plataforma. Se utiliza un sistema de espaciado basado en múltiplos de 8 px (8, 16, 24, 32, 40...) para mantener consistencia y orden en todos los componentes, y para que los diseños de Figma coincidan con las implementaciones en PrimeVue y en las aplicaciones nativas.

| Elemento | Escritorio | Móvil |
|---|---|---|
| Separación entre secciones principales | 80-96 px | 48-64 px |
| Separación entre elementos dentro de una sección | 24-40 px | 16-24 px |
| Separación entre campos de un formulario | 16-24 px | 16 px |
| Separación entre tarjetas (por ejemplo, comparador de escenarios) | 24 px | 16 px |
| Separación entre imagen y texto | 24-40 px | 16-24 px |

---

**Tone of Voice**

Los tonos de comunicación definen cómo se dirige HipoSim a cada rol, con el objetivo de generar confianza, transmitir la propuesta de valor con claridad y lograr que los usuarios se sientan acompañados en una decisión financiera importante. En términos generales, el tono es **serio pero cercano**, **semiformal**, **respetuoso** y **sereno**: HipoSim debe sonar como un asesor confiable que explica, no como un vendedor que persigue una conversión.

- **Visitante y Comprador de primera vivienda:** se utiliza un lenguaje claro, sin jerga financiera innecesaria, que explica cada término técnico (como TCEA o periodo de gracia) la primera vez que aparece. El tono es tranquilizador y orientado a la transparencia, ya que estas personas toman por primera vez una decisión de alto impacto y desconfían de la información que muestran los bancos. Se evita la ironía, el sarcasmo y la presión por urgencia.
- **Administrador:** se emplea un lenguaje directo, preciso y funcional, centrado en la tarea de mantener actualizados los parámetros del simulador (tasas de referencia, porcentaje del Bono del Buen Pagador, rangos de Mivivienda). El tono es neutro y orientado a la acción, con mensajes de confirmación y de error explícitos para evitar cambios accidentales sobre valores que afectan a todas las simulaciones.

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

Esta sección presenta el diseño UX/UI del Landing Page, el punto de entrada del Visitante definido en el Capítulo I. Su estructura sigue la organización jerárquica y el sistema de navegación descritos en 4.2 (Inicio, Producto, Beneficios, Términos, más el CTA persistente "Simular ahora"), y aplica los tokens visuales del Style Guide (4.1) sin depender de PrimeVue, ya que el Landing Page se construye con HTML5/CSS3/JavaScript puro.

### **4.3.1. Landing Page Wireframe**

<div align="center">
  <img src="../assets/08-chapter-4/landing-page-ui-design/wireframes/desktop.png" alt="Wireframe del Landing Page (desktop)" width="850">
  &nbsp;&nbsp;
  <img src="../assets/08-chapter-4/landing-page-ui-design/wireframes/mobile.png" alt="Wireframe del Landing Page (mobile)" width="220">
</div>

El wireframe organiza el contenido en siete bloques secuenciales: hero con el simulador interactivo embebido (sin necesidad de registro previo), explicación del flujo en 4 pasos, comparación frente a los simuladores bancarios tradicionales, explicación de los subsidios estatales (BBP y Mivivienda), un bloque de funcionalidades avanzadas que incentiva la creación de cuenta gratuita, el banner de conversión final y el footer con navegación legal y de soporte. En mobile, el simulador interactivo del hero se apila debajo del titular y los pasos pasan de una grilla de 4 columnas a un listado vertical, conforme a los breakpoints definidos en 4.1.2.

### **4.3.2. Landing Page Mock-up**

<div align="center">
  <img src="../assets/08-chapter-4/landing-page-ui-design/mock-ups/desktop.png" alt="Mock-up del Landing Page (desktop)" width="850">
  &nbsp;&nbsp;
  <img src="../assets/08-chapter-4/landing-page-ui-design/mock-ups/mobile.png" alt="Mock-up del Landing Page (mobile)" width="220">
</div>

El mock-up aplica la paleta de marca sobre la estructura validada en el wireframe: el verde azulado (`#0E5C63`) enmarca el widget del simulador y la sección de transparencia frente a bancos, el ámbar (`#F5A524`) se reserva exclusivamente para el CTA principal "Simular ahora" (repetido en el navbar, el hero y el banner final, pero como única acción destacada por pantalla), y el turquesa (`#3AAFA9`) resalta los datos de apoyo (ahorro estimado, badges de confianza "100% Independiente", "Regulación SBS referencial"). El bloque comparativo "HipoSim vs. Simuladores Bancarios Tradicionales" traduce visualmente el análisis competitivo del Capítulo II, usando el color de error (`#D64545`) para las limitaciones de los bancos y el de éxito (`#2E9E6B`) para los diferenciales de HipoSim.
## **4.4. Mobile Applications UX/UI Design**

Esta sección presenta el diseño UX/UI de la aplicación móvil nativa para el Comprador, cubriendo dos pantallas críticas del flujo: el registro contextual que se activa justo después de que el usuario ve el resultado de su simulación (no antes, en coherencia con la regla de acceso sin login definida en el Capítulo I), y la pantalla de resultados que conecta la simulación con las inmobiliarias disponibles.

### **4.4.1. Mobile Applications Wireframes**

Los wireframes de baja fidelidad a continuación validan la estructura y jerarquía de contenido antes de aplicar la marca visual de HipoSim.

<div align="center">
  <img src="../assets/08-chapter-4/mobile-applications-ux-ui-design/wireframes/results-wireframe.png" alt="Wireframe de la pantalla de Resultados del Crédito (mobile)" width="320">
  <img src="../assets/08-chapter-4/mobile-applications-ux-ui-design/wireframes/registration-wireframe.png" alt="Wireframe de la pantalla de Registro Contextual (mobile)" width="320">
</div>

- **Resultados del Crédito**: expone primero la cuota mensual y el TCEA calculados por el motor financiero, seguidos del subsidio estatal aplicado (Bono del Buen Pagador), el desglose de la cuota (capital, interés, seguros) y el cronograma inicial de amortización, antes de ofrecer la conexión con inmobiliarias — reforzando que el valor (la simulación) se entrega primero.
- **Registro Contextual**: se activa desde el botón "Enviar cotización a inmobiliarias" de la pantalla de resultados y mantiene visible un resumen de la cotización ya calculada, para que el usuario entienda por qué se le pide crear una cuenta en ese momento específico.

### **4.4.2. Mobile Applications Wireflow Diagrams**

El wireflow conecta las pantallas del flujo del Comprador diseñadas en 4.4.1 y 4.4.3, mostrando la navegación entre ellas y el punto exacto donde se activa el Registro Contextual.

```mermaid
flowchart LR
    A[Simulador · Datos del cliente] --> B[Simulador · Datos de la vivienda]
    B --> C[Simulador · Parámetros del crédito]
    C --> D[Resultados del Crédito]
    D -->|Enviar cotización a inmobiliarias| E[Registro Contextual]
    D -->|Guardar / Exportar PDF| D
    E -->|Cuenta creada| F[Lista de Inmobiliarias]
    F -->|Seleccionar inmobiliaria| G[Detalle de Inmobiliaria]
    G -->|Enviar mi cotización| H[Confirmación de envío]
    H --> I[Historial de simulaciones y cotizaciones]
```

### **4.4.3. Mobile Applications Mock-ups**

Los mock-ups de alta fidelidad aplican la paleta, tipografía y componentes definidos en 4.1.1 y 4.1.3 sobre la estructura validada en los wireframes.

<div align="center">
  <img src="../assets/08-chapter-4/mobile-applications-ux-ui-design/mock-ups/results-mockup.png" alt="Mock-up de la pantalla de Resultados del Crédito (mobile)" width="320">
  <img src="../assets/08-chapter-4/mobile-applications-ux-ui-design/mock-ups/registration-mockup.png" alt="Mock-up de la pantalla de Registro Contextual (mobile)" width="320">
</div>

En el mock-up de Resultados, el TCEA y la cuota mensual se destacan en ámbar (`#F5A524`), siguiendo la regla de acento único definida en el Style Guide, mientras que el subsidio estatal aplicado se resalta con el color de éxito (`#2E9E6B`) para transmitir un beneficio ya confirmado. El botón "Enviar cotización a inmobiliarias" reutiliza el mismo acento ámbar como único llamado a la acción de la pantalla, coherente con la restricción de un solo uso de ámbar por vista.

### **4.4.4. Mobile Applications User Flow Diagrams**

A diferencia del wireflow, el diagrama de flujo de usuario representa las decisiones del Comprador en abstracto, sin atarse a pantallas específicas — en particular, la regla de acceso definida en el Capítulo I: el simulador es libre y el login solo se pide al intentar enviar una cotización.

```mermaid
flowchart TD
    Start([Visitante abre la app]) --> Sim[Completa el Simulador]
    Sim --> Res[Ve Resultados del Crédito]
    Res --> Dec1{¿Quiere enviar cotización<br/>a inmobiliarias?}
    Dec1 -- No --> End1([Guarda / Exporta PDF y sale])
    Dec1 -- Sí --> Dec2{¿Tiene sesión iniciada?}
    Dec2 -- Sí --> List[Ve lista de Inmobiliarias]
    Dec2 -- No --> Reg[Registro Contextual]
    Reg --> Dec3{¿Registro exitoso?}
    Dec3 -- No --> Reg
    Dec3 -- Sí --> List
    List --> Sel[Selecciona una Inmobiliaria]
    Sel --> Send[Envía su cotización]
    Send --> Conf([Confirmación de envío])
    Conf --> Hist[Consulta su Historial de cotizaciones]
```
## **4.5. Mobile Applications Prototyping**
### **4.5.1. Android Mobile Applications Prototyping**
### **4.5.2. iOS Mobile Applications Prototyping**
## **4.6. Web Applications UX/UI Design**

Esta sección presenta el diseño UX/UI de la Web Application para el rol Inmobiliaria (cliente principal de la plataforma), cubriendo la Bandeja de Leads e Interesados y la Ficha de Detalle de un Lead — las dos pantallas centrales de su flujo de trabajo diario.

### **4.6.1. Web Applications Wireframes**

<div align="center">
  <img src="../assets/08-chapter-4/web-applications-ux-ui-design/wireframes/leads-inbox-wireframe.png" alt="Wireframe de la Bandeja de Leads e Interesados (desktop)" width="900">
</div>

<div align="center">
  <img src="../assets/08-chapter-4/web-applications-ux-ui-design/wireframes/lead-detail-wireframe.png" alt="Wireframe de la Ficha de Detalle de un Lead (desktop)" width="900">
</div>

- **Bandeja de Leads e Interesados**: organiza el contenido en tres niveles, de arriba hacia abajo: KPIs operativos (leads nuevos, en contacto, calificados a BBP, pipeline proyectado), filtros de búsqueda (nombre/DNI, estado, distrito, solo con Bono BBP) y la tabla de prospectos, siguiendo la organización jerárquica definida en 4.2.1.
- **Ficha de Detalle de un Lead**: agrupa los datos del solicitante, su capacidad financiera y ratios de aprobación, la simulación certificada por HipoSim (cuota, TCEA, composición de la cuota inicial), el match de inventario de la inmobiliaria y la bitácora de interacciones tipo CRM, de modo que el asesor comercial pueda evaluar y contactar al prospecto sin salir de la pantalla.

### **4.6.2. Web Applications Wireflow Diagrams**

El wireflow conecta las pantallas del panel de Inmobiliaria diseñadas en 4.6.1 y 4.6.3, incluyendo las pantallas complementarias del checklist de navegación definido en 4.2.5 (Dashboard, Mi Inmobiliaria, Notificaciones, Configuración).

```mermaid
flowchart LR
    A[Login Inmobiliaria] --> B[Dashboard]
    B --> C[Bandeja de Leads e Interesados]
    C -->|Ver Ficha| D[Detalle del Lead]
    D -->|Contactar WhatsApp / Llamar| D
    D -->|Cambiar estado| D
    D -->|Presentar propiedad a Lead| D
    D -->|Reasignar Lead Comercial| C
    B --> E[Mi Inmobiliaria]
    B --> F[Notificaciones]
    F -->|Atender ahora| D
    B --> G[Configuración]
```

### **4.6.3. Web Applications Mock-ups**

<div align="center">
  <img src="../assets/08-chapter-4/web-applications-ux-ui-design/mock-ups/leads-inbox-mockup.png" alt="Mock-up de la Bandeja de Leads e Interesados (desktop)" width="900">
</div>

<div align="center">
  <img src="../assets/08-chapter-4/web-applications-ux-ui-design/mock-ups/lead-detail-mockup.png" alt="Mock-up de la Ficha de Detalle de un Lead (desktop)" width="900">
</div>

Los mock-ups aplican el sistema de componentes de PrimeVue sobre la estructura validada en los wireframes: el verde azulado (`#0E5C63`) organiza la navegación y la tarjeta de simulación certificada, el turquesa (`#3AAFA9`) resalta el TCEA y los indicadores secundarios, y el ámbar (`#F5A524`) se reserva para las alertas de leads nuevos sin atender y el botón "Nueva Propuesta" — sin reutilizarse en ningún otro elemento de la pantalla, conforme a la regla de acento único.

### **4.6.4. Web Applications User Flow Diagrams**

El diagrama de flujo de usuario representa el ciclo de decisión diario de la Inmobiliaria frente a un lead, desde que revisa el Dashboard hasta que actualiza el estado del prospecto.

```mermaid
flowchart TD
    Start([Inmobiliaria inicia sesión]) --> Dash[Revisa Dashboard]
    Dash --> Notif{¿Hay leads nuevos<br/>sin atender?}
    Notif -- Sí --> Open[Abre Bandeja de Leads]
    Notif -- No --> Wait[Espera notificación]
    Open --> Sel[Selecciona un Lead]
    Sel --> View[Revisa Ficha del Lead:<br/>capacidad financiera + simulación]
    View --> Dec{¿Califica y hay match<br/>de inventario disponible?}
    Dec -- Sí --> Contact[Contacta al Lead<br/>WhatsApp / Llamada]
    Dec -- No --> Reassign[Reasigna o descarta el Lead]
    Contact --> Update[Actualiza el estado del Lead]
    Update --> Close{¿Se concretó la venta?}
    Close -- Sí --> Closed([Estado: Cerrado / Separación])
    Close -- No --> Open
```
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
