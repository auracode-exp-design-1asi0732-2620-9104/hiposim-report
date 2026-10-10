# **Capítulo VI: Product Verification & Validation**

## **6.1. Testing Suites & Validation**

Para garantizar la confiabilidad de HipoSim, estructuramos nuestra estrategia de verificación y validación alrededor de las funcionalidades que aportan mayor valor al comprador de primera vivienda y al asesor inmobiliario: el cálculo del crédito hipotecario, la presentación de sus indicadores financieros, la aplicación de beneficios estatales y el intercambio de simulaciones exclusivamente mediante consentimiento. Nuestro criterio central es comprobar tanto la exactitud de los resultados como la integridad de los datos personales utilizados durante estos procesos.

Distinguimos cuatro niveles de prueba complementarios. Las **pruebas unitarias** se concentran en reglas y componentes aislados; las **pruebas de integración** examinan la comunicación entre capas y productos; los escenarios de **Behavior-Driven Development (BDD)** traducen los criterios de aceptación en comportamientos verificables; y las **pruebas de sistema** evalúan los recorridos completos que experimentan los usuarios. Este enfoque mantiene la trazabilidad con las historias de usuario y las historias técnicas del Capítulo III, la arquitectura del Capítulo IV y los avances de implementación del Capítulo V.

La solución abarca una Landing Page desarrollada con HTML5, CSS3 y JavaScript; el portal web del asesor, desarrollado con Vue 3, Vite, PrimeVue, Pinia y axios; una aplicación Android nativa con Kotlin, Jetpack Compose, Hilt, Navigation Compose y ViewModel con StateFlow; y una API diseñada con ASP.NET Core, Entity Framework Core y PostgreSQL. El Landing Page ya está publicado en GitHub Pages y ejecuta un simulador básico en el navegador. El portal web utiliza datos de ejemplo, mientras que la integración del móvil y de la web con la API forma parte del Sprint 2.

<div style="page-break-after: always;"></div>

| Nivel de verificación | Componentes y procesos prioritarios | Historias relacionadas | Criterio de aceptación |
|---|---|---|---|
| Unit Testing | Método francés, conversión de tasas, cálculo de indicadores, validación de entradas y elegibilidad al BBP | US01, US02, US04, US05, US15, SP02 | Reglas matemáticas y de negocio correctas de manera aislada |
| Integration Testing | Autenticación, servicio de simulación, persistencia, consentimiento, API y clientes web/móvil | TS02, TS06, TS07, TS08, US21–US25 | Intercambio de datos coherente y aplicación de permisos entre componentes |
| Behavior-Driven Development | Simulación sin registro, validación de cuota inicial, aplicación del BBP y gestión autorizada de leads | US01, US05, US15, US21, US23–US25 | Cumplimiento de escenarios expresados en lenguaje del dominio |
| System Testing | Navegación del sitio, resultados hipotecarios, acceso móvil y recorrido comprador–asesor | US14–US20, US13, US26, US21–US25 | Recorridos funcionales y seguros, con manejo comprensible de errores |

El registro técnico disponible consigna **35 pruebas unitarias, 4 pruebas de interfaz ejecutadas en emulador y un flujo de integración continua mediante GitHub Actions para la aplicación Android**, junto con verificaciones de `ktlint` y Android Lint. Para la API y la integración completa con PostgreSQL contamos con el alcance funcional y los contratos previstos, pero no con un registro de ejecución que permita declarar sus pruebas aprobadas. Por ello presentamos sus casos y resultados esperados como especificación verificable, sin confundirlos con resultados obtenidos.

<div style="page-break-after: always;"></div>

### **6.1.1. Core Entities Unit Tests**

Organizamos las pruebas unitarias alrededor de las entidades y servicios de mayor criticidad financiera: `Property`, `Simulation`, `AmortizationEntry`, `FinancialIndicatorResult`, `StateBenefit` y `AdminParameter`, así como los componentes de cálculo `FinancialEngine` y `BenefitsEngine`. El aislamiento de estas reglas impide que errores de interfaz, comunicación o almacenamiento oculten defectos de cálculo. En el cliente Android, las pruebas de lógica y estado se separan de las pruebas de interfaz para comprobar los cambios de estado del `ViewModel` sin depender de la navegación completa.

La principal regla de simulación corresponde al método de amortización francés, con cuotas periódicas calculadas a partir del capital financiado, la tasa efectiva periódica y el plazo. Usamos la siguiente expresión como referencia de consistencia del motor financiero:

\[
C=P\frac{i(1+i)^n}{(1+i)^n-1}
\]

Donde `C` es la cuota periódica, `P` representa el capital financiado, `i` es la tasa efectiva del periodo y `n` corresponde al número de cuotas. Para convertir una tasa efectiva anual (`TEA`) a una tasa mensual efectiva, aplicamos:

\[
i=(1+TEA)^{1/12}-1\]

La fórmula supone un escenario de amortización regular, sin gracia ni cargos adicionales integrados en la cuota. Los seguros, comisiones y otros cargos se consideran por separado en el cálculo del costo efectivo total cuando corresponden. La TCEA no debe tratarse como equivalente a la TEA si existen costos adicionales.

<div style="page-break-after: always;"></div>

**Matriz de casos unitarios del núcleo funcional**

| ID | Clase o componente | Comportamiento bajo prueba | Datos y condición | Resultado esperado | Referencia |
|---|---|---|---|---|---|
| UT-01 | `Property` / validación de entrada | Validar el valor de la vivienda | Precio igual a cero o negativo | Rechazo del dato de entrada; no se inicia el cálculo | US01, TS06 |
| UT-02 | `Simulation` | Verificar la cuota inicial mínima | Cuota inicial inferior al 10 % del precio | Error de validación que informa el mínimo permitido | US01, TS06 |
| UT-03 | `Simulation` | Aceptar el límite de cuota inicial | Cuota inicial exactamente del 10 % | Entrada aceptada cuando los restantes datos son válidos | US01 |
| UT-04 | `FinancialEngine` | Convertir TEA a tasa efectiva mensual | TEA positiva expresada en forma decimal | Resultado consistente con `(1 + TEA)^(1/12) - 1` | US01, SP02 |
| UT-05 | `FinancialEngine` | Obtener la cuota francesa sin periodo de gracia | Capital positivo, tasa válida y 240 cuotas | Cuota positiva y consistente con el cálculo de referencia | US01, SP02 |
| UT-06 | `AmortizationEntry` | Distribuir capital e intereses | Primera cuota de un cronograma regular | Interés calculado sobre el saldo inicial y amortización igual a cuota menos interés | US02 |
| UT-07 | `Simulation` | Liquidar el préstamo al final del plazo | Cronograma completo del crédito | Saldo final igual a cero, considerando el ajuste de redondeo de la última cuota | US02 |
| UT-08 | `StateBenefit` / `BenefitsEngine` | Aplicar el Bono del Buen Pagador | Vivienda elegible y bono activado | Reducción del capital financiado y recálculo de la cuota | US05, US15 |
| UT-09 | `StateBenefit` / `BenefitsEngine` | Rechazar beneficio fuera de rango | Vivienda que no cumple el rango configurado | No se aplica el bono ni se altera el préstamo original | US05 |
| UT-10 | `FinancialIndicatorResult` | Comprobar coherencia de indicadores | Escenario válido con costos financieros | VAN, TIR y TCEA generados a partir de flujos consistentes | US04 |
| UT-11 | `Simulation` / `FinancialEngine` | Calcular gracia parcial | Tres meses de gracia parcial | Pago de intereses durante los tres primeros meses y cuota posterior recalculada | US03 |
| UT-12 | `Simulation` / `FinancialEngine` | Calcular gracia total | Tres meses de gracia total | Ausencia de pagos iniciales y capitalización de intereses | US03 |
| UT-13 | Lógica de autorización y consentimiento | Impedir la creación de un lead no autorizado | Consentimiento ausente o falso | No se habilita el envío ni se genera un lead | US21, TS08 |
| UT-14 | Estado de sesión Android | Restringir una operación de usuario registrado | Comprador sin sesión activa | Se solicita autenticación antes de compartir una simulación | US13, US21, US26 |

Para establecer un caso de referencia reproducible empleamos los datos de simulación definidos en la documentación de la API: vivienda de **S/ 280 000**, cuota inicial de **S/ 42 000**, TEA de **8,5 %**, plazo de **240 meses** y ausencia de periodo de gracia. El capital inicial, antes de cualquier subsidio, es **S/ 238 000**. Si el escenario es elegible y el beneficio aplicado asciende a **S/ 18 200**, el capital pasa a **S/ 219 800**. Estas igualdades constituyen verificaciones determinísticas del cálculo del principal; la cuota, los indicadores y el cronograma deben contrastarse con el motor de referencia y con la definición efectiva de seguros y redondeos.

También utilizamos pruebas de límites: cuota inicial exactamente igual al mínimo, precio de vivienda en los extremos de un rango de beneficio, tasas válidas muy bajas, plazos en sus valores extremos admitidos y redondeo de centavos. En las verificaciones del cronograma comprobamos las invariantes `cuota = interés + amortización`, `saldo final = saldo inicial - amortización` y la conservación del capital amortizado. La comparación con el proyecto de referencia **AutoFinance Pro** forma parte de la historia técnica SP02 y permite detectar diferencias introducidas al portar las fórmulas financieras a C#.

En la aplicación Android, el Capítulo V documenta 35 pruebas unitarias, además de verificaciones de estilo y análisis estático. Esa cifra describe el conjunto de pruebas informado para dicho producto; no la extendemos al backend, al portal web ni a la Landing Page sin los respectivos registros de ejecución.

<div style="page-break-after: always;"></div>

### **6.1.2. Core Integration Tests**

Definimos nuestras pruebas de integración a partir de las dependencias entre el motor de cálculo, los servicios de aplicación, los controladores REST, el acceso a PostgreSQL y los clientes que consumen los endpoints. El objetivo es detectar discrepancias que no son visibles durante las pruebas unitarias, tales como transformaciones incorrectas de datos, pérdida de consentimiento, problemas de autenticación, filtrado insuficiente de leads o respuestas incompatibles con los modelos del frontend.

El contrato REST diseñado en la sección 5.2.6 constituye la base de las verificaciones. Las peticiones de simulación utilizan `POST /api/simulations`; el registro y el inicio de sesión utilizan `POST /api/auth/register` y `POST /api/auth/login`; mientras que el flujo comercial utiliza `POST /api/leads`, `GET /api/leads`, `GET /api/leads/{id}` y `PATCH /api/leads/{id}/status`.

| ID | Integración | Solicitud o evento | Verificación esperada | Historias |
|---|---|---|---|---|
| IT-01 | Controlador de simulación → motor financiero | `POST /api/simulations` con datos válidos | HTTP 200 y respuesta con cuota, indicadores y cronograma consistentes | US01, US02, US04, TS06 |
| IT-02 | Validación → API | Cuota inicial inferior al 10 % o campos obligatorios ausentes | HTTP 400 con información de validación; no se persiste una simulación inválida | US01, TS06 |
| IT-03 | Registro → servicio de usuarios → base de datos | `POST /api/auth/register` con usuario nuevo | HTTP 201 y usuario disponible para autenticación | US13, TS07 |
| IT-04 | Restricción de unicidad → base de datos | Registro de correo electrónico ya existente | HTTP 409; no se duplica el usuario | TS07 |
| IT-05 | Autenticación → emisión de token | Credenciales correctas e incorrectas | HTTP 200 con JWT válido o HTTP 401, según el caso | US22, US26, TS07 |
| IT-06 | Comprador → API de leads → persistencia | `POST /api/leads` con consentimiento expreso | HTTP 201, lead generado y consentimiento asociado a la operación | US21, TS08 |
| IT-07 | Validación de privacidad → API de leads | Solicitud de envío sin consentimiento | HTTP 400 y ausencia de lead registrado | US21, TS08 |
| IT-08 | Asesor → API de leads → autorización | `GET /api/leads` con token del asesor | HTTP 200 y solamente los leads permitidos para su inmobiliaria | US23, TS08 |
| IT-09 | Middleware de autenticación → API | Consulta de leads sin token | HTTP 401 y ausencia de datos personales en la respuesta | US23, TS08 |
| IT-10 | Portal Vue → API | Apertura de bandeja, ficha y actualización de estado | Datos mostrados y actualizados de acuerdo con la respuesta del servicio | US23, US24, US25 |
| IT-11 | Aplicación Android → API | Simulación autenticada o anónima, según la operación | Estado del `ViewModel` y resultados compatibles con el contrato REST | US01, US04, US26 |
| IT-12 | Entity Framework Core → PostgreSQL | Escritura y lectura de una simulación o lead | Persistencia y recuperación sin alterar importes, propietarios ni permisos | TS02, TS08 |

**Contrato representativo de simulación**

```json
{
  "propertyPrice": 280000.00,
  "downPayment": 42000.00,
  "annualEffectiveRate": 0.085,
  "termInMonths": 240,
  "gracePeriodMonths": 0,
  "graceType": "none",
  "applyGoodPayerBonus": true
}
```

La respuesta satisfactoria debe identificar la simulación, informar el capital financiado y la cuota, devolver los indicadores de evaluación y proporcionar el cronograma correspondiente. El resultado no puede considerarse correcto solamente por recibir HTTP 200: los importes deben conservar sus relaciones matemáticas, la elegibilidad al beneficio debe respetar los parámetros vigentes y la estructura del JSON debe resultar compatible con la interfaz consumidora.

El flujo de integración más importante combina el envío voluntario de una simulación por parte del Comprador con la consulta posterior del Asesor. Verificamos este contrato en dos sentidos: un consentimiento válido habilita la creación del lead y su visualización dentro del ámbito autorizado; la ausencia de consentimiento impide el registro y la divulgación. Asimismo, una inmobiliaria no debe acceder a contactos pertenecientes a otra organización mediante el cambio de identificadores o la modificación de parámetros en la solicitud.

Durante esta versión, el simulador básico del Landing Page realiza sus operaciones en JavaScript dentro del navegador; no corresponde presentarlo como un cliente de la API desplegada. De igual forma, el portal del asesor todavía utiliza datos de ejemplo y la conexión efectiva con los servicios se encuentra comprendida en el Sprint 2. Las verificaciones IT-01 a IT-12 establecen criterios de integración para esa etapa, pero su aprobación depende de la disponibilidad de la API, de la base de datos y de los clientes conectados.

<div style="page-break-after: always;"></div>

### **6.1.3. Core Behavior-Driven Development**

Adoptamos BDD como mecanismo de comunicación entre requisitos, implementación y verificación. Cada escenario describe un comportamiento observable por el usuario o por el consumidor del servicio, sin incorporar detalles internos del código ni decisiones particulares de diseño de pantallas. La nomenclatura y el formato Gherkin permiten relacionar directamente las especificaciones con las historias de usuario del Product Backlog.

Los escenarios siguientes expresan las reglas principales de HipoSim con la estructura **Dado–Cuando–Entonces**. El texto es compatible con el dialecto español de Gherkin y mantiene los identificadores funcionales utilizados en el informe.

**Simulación hipotecaria sin registro — US01, US15 y TS06**

```gherkin
# language: es
@US01 @US15 @TS06 @simulation
Característica: Simulación hipotecaria básica
  Como comprador de primera vivienda
  Quiero calcular el costo estimado de mi crédito
  Para evaluar una alternativa antes de registrarme

  Escenario: Simulación válida sin cuenta de usuario
    Dado que el comprador no ha iniciado sesión
    Y que el precio de la vivienda es S/ 280000
    Y que la cuota inicial es S/ 42000
    Y que el plazo es de 240 meses
    Cuando solicita la simulación hipotecaria
    Entonces el sistema genera un cronograma de amortización
    Y presenta una cuota mensual estimada
    Y no exige el registro de una cuenta

  Escenario: Cuota inicial inferior al mínimo permitido
    Dado que el precio de la vivienda es S/ 280000
    Y que la cuota inicial es S/ 20000
    Cuando el comprador solicita la simulación
    Entonces el sistema rechaza los parámetros ingresados
    Y comunica que la cuota inicial mínima es del 10 por ciento
```
<div style="page-break-after: always;"></div>

**Bono del Buen Pagador — US05 y US15**

```gherkin
# language: es
@US05 @US15 @benefits
Característica: Evaluación del Bono del Buen Pagador
  Como comprador de primera vivienda
  Quiero evaluar el beneficio estatal aplicable
  Para conocer cómo afecta al monto financiado

  Escenario: Aplicación de un bono a una vivienda elegible
    Dado que la vivienda cumple los rangos vigentes del beneficio
    Y que el comprador solicita aplicar el Bono del Buen Pagador
    Cuando el sistema procesa la simulación
    Entonces el monto financiado disminuye según el bono aplicable
    Y la cuota mensual se recalcula con el nuevo capital

  Escenario: Vivienda fuera del rango admitido
    Dado que la vivienda no cumple los rangos vigentes del beneficio
    Cuando el comprador solicita aplicar el Bono del Buen Pagador
    Entonces el sistema informa que la vivienda no es elegible
    Y conserva el monto financiado sin subsidio
```

**Consentimiento para compartir la simulación — US21 y TS08**

```gherkin
# language: es
@US21 @TS08 @privacy
Característica: Intercambio autorizado de simulaciones
  Como comprador registrado
  Quiero decidir si comparto mi simulación con una inmobiliaria
  Para recibir contacto comercial solamente cuando lo autorice

  Escenario: Envío voluntario de la simulación
    Dado que el comprador tiene una sesión válida
    Y que dispone de una simulación completada
    Y que autoriza expresamente compartirla con una inmobiliaria
    Cuando solicita el envío de su simulación
    Entonces el sistema registra el consentimiento asociado al envío
    Y crea el lead para la inmobiliaria autorizada

  Escenario: Envío sin consentimiento
    Dado que el comprador tiene una simulación completada
    Y que no autoriza compartir sus datos
    Cuando intenta enviar su simulación a una inmobiliaria
    Entonces el sistema rechaza el envío
    Y no crea un lead
    Y no revela información financiera del comprador
```
<div style="page-break-after: always;"></div>

**Acceso y seguimiento de leads — US22, US23, US24, US25 y TS08**

```gherkin
# language: es
@US22 @US23 @US24 @US25 @TS08 @leads
Característica: Gestión segura de interesados inmobiliarios
  Como asesor de inmobiliaria
  Quiero consultar y dar seguimiento a los interesados autorizados
  Para atender sus solicitudes manteniendo la confidencialidad

  Escenario: Consulta de leads de la inmobiliaria autorizada
    Dado que el asesor ha iniciado sesión correctamente
    Y que existen leads autorizados para su inmobiliaria
    Cuando consulta su bandeja de interesados
    Entonces el sistema presenta los leads de su inmobiliaria
    Y no muestra los leads asociados a otras inmobiliarias

  Escenario: Actualización de seguimiento de un lead propio
    Dado que el asesor ha iniciado sesión correctamente
    Y que el lead pertenece a su inmobiliaria
    Cuando actualiza el estado de seguimiento del lead
    Entonces el sistema conserva el nuevo estado
    Y permite consultar el cambio realizado

  Escenario: Consulta sin autenticación
    Dado que el asesor no dispone de una sesión válida
    Cuando solicita la bandeja de interesados
    Entonces el sistema deniega el acceso
    Y no expone datos personales ni financieros
```

Para enlazar estos escenarios con la automatización, distinguimos la **especificación funcional** (archivo `.feature`), su **implementación ejecutable** (definiciones de pasos) y el **reporte de resultados**. Los escenarios aquí redactados constituyen especificaciones de aceptación; el informe actual no acredita todavía definiciones de pasos ejecutadas contra la API para cada uno de ellos. Esta distinción evita equiparar una historia redactada en Gherkin con una prueba automatizada que haya superado su ejecución.

Las reglas de privacidad se consideran transversales: el consentimiento tiene que ser explícito, la identidad del comprador debe estar autenticada para compartir y el asesor solamente puede acceder a los leads para los que posee autorización. Así preservamos la finalidad informativa de HipoSim y el tratamiento responsable de los datos personales descrito en la Ley N.° 29733.

<div style="page-break-after: always;"></div>

### **6.1.4. Core System Tests**

Las pruebas de sistema abarcan el comportamiento completo de los productos digitales y los recorridos que conectan al visitante, al comprador registrado y al asesor. Evaluamos la navegación, la validación de formularios, la visualización financiera, los permisos, la experiencia responsiva y la comunicación con servicios externos al cliente. Priorizamos las rutas que afectan directamente una decisión económica o que pueden exponer información personal.

| ID | Producto o recorrido | Procedimiento funcional | Resultado esperado | Alcance documentado |
|---|---|---|---|---|
| ST-01 | Landing Page | Acceder al sitio publicado y recorrer Inicio, Producto, Beneficios y Preguntas | Navegación disponible mediante HTTPS, enlaces operativos y contenido responsivo | Landing Page publicada |
| ST-02 | Landing Page | Ejecutar una simulación básica sin registrarse | Presentación de cuota, préstamo neto y TCEA referencial sin solicitar cuenta | Función descrita en Sprint 1 |
| ST-03 | Landing Page | Cambiar entre español e inglés y navegar por las secciones | Traducciones visibles y conservación de la preferencia mediante `localStorage` | Función descrita en Sprint 1 |
| ST-04 | Landing Page | Enviar datos incompletos al formulario de contacto | Validación del formulario sin atribuirle envío a un backend real | Envío simulado documentado |
| ST-05 | Android | Consultar resultados y abrir el registro contextual | Estados y navegación coherentes, incluso con sesión simulada | Pantallas implementadas en Sprint 1 |
| ST-06 | Android + API | Registrarse, autenticarse y simular desde el móvil | Sesión real, cálculo devuelto por la API y resultados consistentes | Integración del Sprint 2 |
| ST-07 | Android + API | Compartir una simulación tras aceptar el consentimiento | Lead generado solamente después de la autorización expresa | Integración del Sprint 2 |
| ST-08 | Portal web + API | Iniciar sesión como asesor y consultar bandeja y ficha | Visualización de leads autorizados provenientes de la API | Integración del Sprint 2 |
| ST-09 | Portal web + API | Actualizar el estado de un lead y consultar el seguimiento | Cambio persistente sin afectar leads de otras inmobiliarias | Integración del Sprint 2 |
| ST-10 | Recorrido transversal | Intentar compartir sin consentimiento o consultar leads sin token | Operaciones rechazadas y ausencia de exposición de datos | Criterio de seguridad transversal |
| ST-11 | Web y Android | Interrumpir o hacer fallar una solicitud de servicio | Error comprensible y estado de interfaz coherente, sin confirmar una operación fallida | Criterio de robustez |
| ST-12 | Android | Ejecutar pruebas automatizadas de interfaz en emulador | Verificación de los flujos de interfaz incluidos en la suite móvil | Cuatro pruebas de interfaz consignadas |
