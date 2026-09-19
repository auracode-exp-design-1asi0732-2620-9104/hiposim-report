# **Chapter III: Requirements Specification**
## **3.1. To-Be Scenario Mapping**

<p style="text-align: justify; line-height: 1.6;">
  El To-Be Scenario Mapping describe la experiencia futura e ideal de los usuarios al utilizar HipoSim. A diferencia del escenario actual (As-Is), en el que predomina la frustración causada por la desinformación y el trabajo manual, este nuevo recorrido refleja un proceso fluido, centralizado y transparente.
</p>

**Segmento 1: Comprador de Primera Vivienda (Hernesto)**

<div align="center" style="margin: 16px 0 24px 0; page-break-inside: avoid;">
  <img src="../assets/07-chapter-3/to-be-scenario-mapping/scenario-map-segmento-1.png" width="90%" style="max-width: 100%; height: auto;" alt="To-Be Scenario Map del comprador de primera vivienda">
  <p style="text-align: center; margin-top: 8px;"><em>Figura 1. To-Be Scenario Map del comprador de primera vivienda.</em></p>
</div>

**Segmento 2: Administrador de Producto (Daniel)**

<div align="center" style="margin: 16px 0 24px 0; page-break-inside: avoid;">
  <img src="../assets/07-chapter-3/to-be-scenario-mapping/scenario-map-segmento-2.png" width="90%" style="max-width: 100%; height: auto;" alt="To-Be Scenario Map del administrador de producto">
  <p style="text-align: center; margin-top: 8px;"><em>Figura 2. To-Be Scenario Map del administrador de producto.</em></p>
</div>

## **3.2. User Stories**

<p style="text-align: justify; line-height: 1.6;">
  Las User Stories se organizan en épicas y se redactan con el formato "Como... quiero... para...". Cada historia incluye criterios de aceptación escritos en Gherkin (Dado que, Cuando, Entonces), en tiempo presente y sin referencias a la interfaz de usuario. Se incluyen historias para los roles Visitante (Landing Page), Comprador y Usuario Registrado, Asesor de inmobiliaria y Administrador, además de Technical Stories para el rol Developer y Spike Stories para reducir la incertidumbre técnica. La prioridad se expresa como Alta, Media o Baja según el valor para el negocio.
</p>

<p style="text-align: justify; line-height: 1.6;">
  El alcance se mantiene acotado: la conexión con inmobiliarias es una función opcional que el Comprador autoriza de forma explícita, y la gestión de parámetros del Administrador queda con prioridad baja para una etapa posterior.
</p>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0 22px 0; font-size: 8pt; page-break-inside: auto; table-layout: fixed;">
  <thead style="display: table-header-group;">
    <tr style="page-break-inside: avoid;">
      <th style="width: 6%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">ID</th>
      <th style="width: 9%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Usuario</th>
      <th style="width: 7%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Prioridad</th>
      <th style="width: 6%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Épica</th>
      <th style="width: 14%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Título</th>
      <th style="width: 25%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Descripción</th>
      <th style="width: 33%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Criterios de aceptación</th>
    </tr>
  </thead>
  <tbody style="page-break-inside: auto;">
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>EP01</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">N/A</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Motor de Simulación Base</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como usuario de la plataforma, quiero calcular las cuotas de un crédito hipotecario, para conocer el costo mensual según el método de amortización francés.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Se completa cuando se cumplen las historias US01, US02 y US03.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>EP02</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">N/A</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Costo Efectivo y Beneficios Estatales</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como usuario de la plataforma, quiero visualizar el TCEA, el VAN y la TIR y aplicar subsidios estatales, para conocer el costo real total de la operación financiera.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Se completa cuando se cumplen las historias US04 y US05.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>EP03</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Usuario Registrado</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">N/A</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Gestión de Escenarios</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como usuario registrado, quiero guardar, comparar y exportar simulaciones, para discutir las opciones con mi familia sin perder los cálculos.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Se completa cuando se cumplen las historias US06, US07 y US08.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>EP04</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Administrador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Baja</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">N/A</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Panel de Administración</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero gestionar tasas, rangos y beneficios estatales, para mantener el simulador actualizado según la normativa oficial de forma segura.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Se completa cuando se cumplen las historias US09, US10, US11 y US12.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>EP05</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador y Asesor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">N/A</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Autenticación y Perfiles</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como usuario, quiero registrarme e iniciar sesión, para acceder de forma segura a las funciones que requieren una cuenta.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Se completa cuando se cumplen las historias US13 y US22.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>EP06</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">N/A</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Arquitectura y Tecnología</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como equipo de desarrollo, queremos implementar el backend, el frontend y la base de datos, para garantizar el correcto funcionamiento, la seguridad y el despliegue del sistema.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Se completa cuando se cumplen las historias TS01 a TS08 y los spikes SP01 a SP03.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>EP07</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visitante</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">N/A</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Landing Page</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero conocer la propuesta de HipoSim y probar un simulador básico sin registrarme, para decidir si la herramienta me ayuda a entender el costo real de mi crédito.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Se completa cuando se cumplen las historias US14 a US20 y TS04.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>EP08</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador y Asesor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">N/A</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Conexión con Inmobiliarias</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero compartir mi simulación con inmobiliarias solo si yo lo autorizo, para recibir información de proyectos en mi rango presupuestal, y como Asesor, quiero gestionar los interesados que llegan, para darles seguimiento.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Se completa cuando se cumplen las historias US21 y US23 a US25.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US01</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP01</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Simular crédito base</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero simular un crédito ingresando el precio de la vivienda y la cuota inicial, para ver mi cuota mensual sin tener que registrarme primero.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Simulación exitosa.</strong> Dado que el Comprador ingresa un valor de vivienda mayor a cero y una cuota inicial de al menos 10%; Cuando solicita la simulación; Entonces el sistema genera el cronograma de pagos bajo el método francés y muestra la cuota mensual.<br><br><strong>Escenario 2: Cuota inicial insuficiente.</strong> Dado que el Comprador ingresa una cuota inicial menor al 10%; Cuando solicita la simulación; Entonces el sistema rechaza la solicitud e informa que la cuota inicial mínima es del 10%.<br><br><strong>Escenario 3: Simulación sin cuenta.</strong> Dado que el Comprador no ha iniciado sesión; Cuando solicita la simulación; Entonces el sistema muestra el resultado sin solicitar datos personales.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US02</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP01</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Ver cronograma de pagos</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero visualizar el cronograma de pagos detallado, para entender cómo se distribuye mi cuota entre capital e intereses mes a mes.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Cronograma detallado.</strong> Dado que se completó una simulación; Cuando el Comprador solicita el detalle del cronograma; Entonces el sistema muestra, por cada mes, el saldo inicial, la amortización, el interés y el saldo final.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US03</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP01</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Aplicar periodo de gracia</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero añadir un periodo de gracia, total o parcial, a mi simulación, para ver cómo afecta el pago de mis primeras cuotas y el costo total.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Gracia parcial.</strong> Dado que el Comprador selecciona una gracia parcial de 3 meses; Cuando solicita la simulación; Entonces el cronograma muestra únicamente el pago de intereses durante los primeros 3 meses y recalcula la cuota desde el mes 4.<br><br><strong>Escenario 2: Gracia total.</strong> Dado que el Comprador selecciona una gracia total de 3 meses; Cuando solicita la simulación; Entonces el cronograma no registra pagos durante esos 3 meses y los intereses se capitalizan al saldo.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US04</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP02</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visualizar TCEA, VAN y TIR</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero ver el cálculo automático del TCEA, el VAN y la TIR de mi simulación, para conocer el costo real efectivo más allá de la tasa nominal.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Indicadores calculados.</strong> Dado que la simulación es exitosa; Cuando el sistema presenta los resultados; Entonces se muestran el TCEA, calculado con el seguro de desgravamen y los seguros estimados, junto con el VAN y la TIR.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US05</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP02</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Aplicar Bono del Buen Pagador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero aplicar el Bono del Buen Pagador a mi simulación, para ver automáticamente cómo se reduce el monto a financiar si califico.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Bono aplicado.</strong> Dado que el valor de la vivienda está dentro del rango vigente del bono; Cuando el Comprador solicita aplicar el bono; Entonces el sistema descuenta el subsidio del monto a financiar y recalcula la cuota.<br><br><strong>Escenario 2: Vivienda fuera de rango.</strong> Dado que el valor de la vivienda está fuera del rango vigente del bono; Cuando el Comprador solicita aplicar el bono; Entonces el sistema informa que la vivienda no califica y no modifica el monto a financiar.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US06</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Usuario Registrado</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP03</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Guardar escenario de simulación</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Usuario Registrado, quiero guardar un escenario de simulación en mi perfil, para no tener que volver a ingresar los datos en futuras sesiones.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Guardado exitoso.</strong> Dado que el usuario ha iniciado sesión y tiene una simulación completada; Cuando solicita guardarla asignándole un nombre; Entonces el sistema la almacena en su historial personal.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US07</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Usuario Registrado</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP03</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comparar escenarios guardados</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Usuario Registrado, quiero comparar entre dos y tres escenarios guardados lado a lado, para decidir qué configuración, por ejemplo el plazo o la cuota inicial, me conviene más.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Comparación de escenarios.</strong> Dado que el usuario tiene al menos dos escenarios guardados; Cuando selecciona entre dos y tres escenarios para compararlos; Entonces el sistema presenta los indicadores en paralelo, resaltando las diferencias en cuota, TCEA y pago total.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US08</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Usuario Registrado</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP03</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Exportar reporte en PDF</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Usuario Registrado, quiero descargar un reporte en PDF de mis simulaciones o comparativas, para enviárselo a mi pareja o llevarlo al banco.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Descarga exitosa.</strong> Dado que el usuario visualiza el resultado de una simulación; Cuando solicita exportar el reporte; Entonces el sistema genera un archivo PDF con el resumen, los indicadores y el cronograma.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US09</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Administrador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Baja</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP04</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Actualizar tasas referenciales</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero actualizar las tasas de interés referenciales (TEA) del sistema, para que las nuevas simulaciones reflejen las condiciones actuales del mercado.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Actualización exitosa.</strong> Dado que el Administrador ingresa una TEA válida; Cuando confirma la actualización; Entonces el sistema guarda el nuevo valor con su fecha de vigencia y lo utiliza en las nuevas simulaciones.<br><br><strong>Escenario 2: Valor inválido.</strong> Dado que el Administrador ingresa una TEA negativa o igual a cero; Cuando confirma la actualización; Entonces el sistema rechaza el valor y mantiene el vigente.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US10</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Administrador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Baja</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP04</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Configurar rangos Mivivienda</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero actualizar los topes y valores del programa Mivivienda y del Bono del Buen Pagador, para mantener la exactitud legal de los subsidios estatales calculados.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Modificación de tramos.</strong> Dado que la normativa cambia; Cuando el Administrador ajusta los rangos de precio mínimo y máximo y los montos del bono; Entonces el simulador evalúa la elegibilidad con los nuevos tramos.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US11</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Administrador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Baja</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP04</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Previsualizar impacto de parámetros</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero previsualizar cómo afectará un cambio de tasa a una simulación estándar antes de publicarlo, para evitar errores de digitación que afecten al simulador.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Vista previa.</strong> Dado que el Administrador modifica un valor; Cuando solicita una previsualización; Entonces el sistema muestra la cuota anterior y la cuota nueva de una simulación estándar sin publicar el cambio.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US12</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Administrador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Baja</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP04</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Historial de auditoría de parámetros</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero ver un historial completo de quién cambió cada parámetro y cuándo, para mantener la trazabilidad frente a auditorías normativas.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Historial consultado.</strong> Dado que el Administrador selecciona un parámetro; Cuando consulta su historial; Entonces el sistema muestra las versiones anteriores, el responsable, la fecha y el documento de respaldo de cada cambio.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US13</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP05</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Registrarse como Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero registrarme con mi correo electrónico y una contraseña, para acceder a las funciones de guardado, comparación y exportación.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Registro exitoso.</strong> Dado que el Comprador ingresa nombre, correo, celular y contraseña válidos y acepta los Términos y la autorización de tratamiento de datos personales (Ley N° 29733); Cuando envía el registro; Entonces el sistema crea la cuenta y emite un token JWT de sesión.<br><br><strong>Escenario 2: Correo ya registrado.</strong> Dado que el correo ingresado ya tiene una cuenta; Cuando envía el registro; Entonces el sistema rechaza la solicitud e informa que el correo ya está registrado.<br><br><strong>Escenario 3: Términos no aceptados.</strong> Dado que el Comprador no acepta los Términos; Cuando envía el registro; Entonces el sistema no crea la cuenta.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS01</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Configurar entorno de frontend</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero configurar el entorno de desarrollo con Vue y PrimeVue (tema Material), para asegurar una interfaz modular y responsiva alineada con el Design System definido.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Configuración inicial.</strong> Dado que el proyecto se inicializa; Cuando se ejecuta el servidor de desarrollo; Entonces la aplicación carga la estructura base de componentes con PrimeVue en el navegador.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS02</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Implementar backend y base de datos</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero configurar el backend con ASP.NET Core (C#) y las migraciones en PostgreSQL mediante Entity Framework Core, para asegurar una persistencia robusta y escalable.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Migración exitosa.</strong> Dado que los modelos de datos están definidos; Cuando se ejecutan las migraciones; Entonces las tablas se crean en PostgreSQL respetando las relaciones y los tipos definidos en el diseño de base de datos.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS03</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Generar reportes PDF desde la API</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero implementar en la API un servicio que genere el reporte de una simulación en PDF, para que las aplicaciones web y móvil descarguen el mismo documento.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Reporte generado.</strong> Dado el identificador de una simulación existente; Cuando el cliente solicita el reporte; Entonces la API responde con código 200 y un archivo PDF con el resumen y el cronograma.<br><br><strong>Escenario 2: Simulación inexistente.</strong> Dado un identificador que no corresponde a ninguna simulación; Cuando el cliente solicita el reporte; Entonces la API responde con código 404.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US14</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visitante</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP07</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Ver propuesta de valor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero ver en la página de inicio qué es HipoSim y en qué se diferencia de los simuladores bancarios, para entender su propuesta antes de simular.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Propuesta de valor visible.</strong> Dado que el Visitante accede al Landing Page; Cuando se carga la página de inicio; Entonces el sistema presenta la propuesta de valor de HipoSim, su comparación con los simuladores bancarios tradicionales y la invitación a simular.<br><br><strong>Escenario 2: Navegación por secciones.</strong> Dado que el Visitante se encuentra en cualquier sección del sitio; Cuando utiliza la navegación principal; Entonces accede a las secciones Inicio, Producto, Beneficios y Términos.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US15</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visitante</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP07</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Simular crédito sin registro desde el Landing Page</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero probar un simulador básico indicando el valor de la vivienda, la cuota inicial y el plazo, para obtener una cuota mensual y un TCEA estimados sin registrarme.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Estimación sin registro.</strong> Dado que el Visitante ingresa un valor de vivienda entre S/ 120,000 y S/ 800,000, una cuota inicial entre 10% y 40% y un plazo entre 5 y 30 años; Cuando el sistema calcula la simulación; Entonces muestra la cuota mensual proyectada, el TCEA estimado y el préstamo neto sin solicitar datos personales.<br><br><strong>Escenario 2: Bono aplicado.</strong> Dado que el Visitante ingresa un valor de vivienda dentro del rango vigente del Bono del Buen Pagador; Cuando solicita aplicar el bono; Entonces el préstamo neto se reduce en el monto del subsidio y la cuota se recalcula.<br><br><strong>Escenario 3: Cronograma completo.</strong> Dado que el Visitante obtuvo una estimación; Cuando solicita el cronograma completo; Entonces el sistema muestra el detalle mensual calculado con el método francés.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US16</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visitante</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP07</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Conocer beneficios estatales</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero conocer el Bono del Buen Pagador, el Bono Mivivienda Sostenible y el Nuevo Crédito Mivivienda, para saber a qué subsidios podría acceder.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Beneficios descritos.</strong> Dado que el Visitante accede a la sección de beneficios; Cuando se carga el contenido; Entonces el sistema describe cada beneficio con sus condiciones y montos referenciales.<br><br><strong>Escenario 2: Verificación de elegibilidad.</strong> Dado que el Visitante desea saber si califica a un bono; Cuando solicita verificarlo; Entonces el sistema lo dirige al simulador con la opción del bono disponible.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US17</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visitante</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP07</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Consultar Términos y Condiciones y Privacidad</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero consultar los Términos y Condiciones y la política de privacidad, para conocer mis derechos y cómo se tratan mis datos personales.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Términos y privacidad accesibles.</strong> Dado que el Visitante se encuentra en cualquier página del Landing Page; Cuando solicita los Términos y Condiciones; Entonces el sistema muestra el acuerdo de servicio y la política de privacidad conforme a la Ley N° 29733.<br><br><strong>Escenario 2: Acceso desde las aplicaciones.</strong> Dado que el usuario utiliza la aplicación web o móvil; Cuando busca los Términos y Condiciones; Entonces los encuentra accesibles desde el pie de la aplicación.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US18</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visitante</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP07</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Consultar preguntas frecuentes</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero consultar preguntas frecuentes sobre el simulador, el TCEA y los beneficios estatales, para resolver mis dudas sin contactar al equipo.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Respuesta a una pregunta.</strong> Dado que el Visitante accede a las preguntas frecuentes; Cuando selecciona una pregunta; Entonces el sistema muestra su respuesta.<br><br><strong>Escenario 2: Temas cubiertos.</strong> Dado que el Visitante consulta las preguntas frecuentes; Cuando revisa el listado; Entonces las preguntas cubren el uso del simulador, el TCEA y los beneficios estatales.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US19</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visitante</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP07</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Contactar al equipo de HipoSim</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero enviar una consulta al equipo de HipoSim, para resolver dudas que no encontré en el sitio.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Consulta enviada.</strong> Dado que el Visitante ingresa nombre, correo y mensaje válidos; Cuando envía la consulta; Entonces el sistema registra la consulta y confirma su recepción.<br><br><strong>Escenario 2: Datos incompletos.</strong> Dado que el Visitante omite un campo obligatorio; Cuando envía la consulta; Entonces el sistema indica el campo faltante y no envía la consulta.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US20</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visitante</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP07</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Cambiar el idioma del sitio</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero cambiar el idioma del sitio entre español (es_419) e inglés (en_US), para usarlo en el idioma que prefiero.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Idioma por defecto.</strong> Dado que el Visitante accede por primera vez sin haber elegido un idioma; Cuando se carga el sitio; Entonces los textos se muestran en el idioma por defecto definido para el producto.<br><br><strong>Escenario 2: Cambio de idioma.</strong> Dado que el Visitante selecciona el idioma inglés o el español; Cuando el sitio se actualiza; Entonces todos los textos del Landing Page se muestran en el idioma elegido.<br><br><strong>Escenario 3: Idioma conservado.</strong> Dado que el Visitante eligió un idioma; Cuando navega a otra sección; Entonces el sitio mantiene el idioma elegido.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US21</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP08</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Enviar mi simulación a inmobiliarias con mi consentimiento</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero elegir enviar mi simulación a inmobiliarias verificadas, para recibir información de proyectos en mi rango presupuestal solo si yo lo autorizo.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Envío autorizado.</strong> Dado que el Comprador ha iniciado sesión y tiene una simulación completada; Cuando autoriza de forma expresa compartir su simulación y su contacto; Entonces el sistema registra la solicitud, la pone a disposición de las inmobiliarias y confirma el envío al Comprador.<br><br><strong>Escenario 2: Sesión requerida.</strong> Dado que el Comprador no ha iniciado sesión; Cuando solicita enviar su simulación; Entonces el sistema le pide registrarse o iniciar sesión antes de continuar y no comparte ningún dato.<br><br><strong>Escenario 3: Sin autorización.</strong> Dado que el Comprador no otorga la autorización; Cuando finaliza el proceso; Entonces el sistema no comparte ninguno de sus datos.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US22</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Asesor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP05</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Iniciar sesión como Asesor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Asesor de inmobiliaria, quiero iniciar sesión con mis credenciales, para acceder a los interesados de mi inmobiliaria.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Inicio de sesión exitoso.</strong> Dado que el Asesor ingresa credenciales válidas; Cuando inicia sesión; Entonces el sistema emite un token JWT y le da acceso únicamente a los leads de su inmobiliaria.<br><br><strong>Escenario 2: Credenciales inválidas.</strong> Dado que el Asesor ingresa credenciales inválidas; Cuando inicia sesión; Entonces el sistema rechaza el acceso sin indicar cuál de los datos es incorrecto.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US23</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Asesor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP08</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Ver bandeja de leads</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Asesor de inmobiliaria, quiero ver la bandeja de leads que autorizaron compartir su simulación, para priorizar a quién contactar.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Bandeja de leads.</strong> Dado que el Asesor ha iniciado sesión; Cuando consulta su bandeja; Entonces el sistema lista los leads de su inmobiliaria con nombre, inmueble simulado, cuota estimada, TCEA, estado y fecha de recepción.<br><br><strong>Escenario 2: Filtro por estado.</strong> Dado que el Asesor aplica un filtro por estado; Cuando consulta su bandeja; Entonces el sistema muestra únicamente los leads que se encuentran en ese estado.<br><br><strong>Escenario 3: Solo leads autorizados.</strong> Dado que un Comprador no autorizó compartir su simulación; Cuando el Asesor consulta su bandeja; Entonces el sistema no muestra a ese Comprador.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US24</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Asesor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP08</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Ver ficha del lead</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Asesor de inmobiliaria, quiero ver la ficha de un lead con su simulación, para conocer su capacidad de compra antes de contactarlo.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Ficha del lead.</strong> Dado que el Asesor selecciona un lead de su bandeja; Cuando abre su ficha; Entonces el sistema muestra los datos de contacto del Comprador, la simulación compartida (valor del inmueble, cuota inicial, bono aplicado, monto financiado, plazo, cuota y TCEA) y el historial de seguimiento.<br><br><strong>Escenario 2: Contacto directo.</strong> Dado que el Asesor consulta la ficha de un lead; Cuando solicita contactarlo por WhatsApp o por llamada; Entonces el sistema abre el canal con el número que el Comprador autorizó.<br><br><strong>Escenario 3: Lead de otra inmobiliaria.</strong> Dado que el lead pertenece a otra inmobiliaria; Cuando el Asesor intenta acceder a su ficha; Entonces el sistema deniega el acceso.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US25</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Asesor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP08</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Gestionar estado y seguimiento del lead</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Asesor de inmobiliaria, quiero cambiar el estado de un lead y registrar notas de mis contactos, para llevar el control de su atención.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Cambio de estado.</strong> Dado que el Asesor abre la ficha de un lead; Cuando cambia su estado a Nuevo, En contacto, Cita agendada, Cerrado o Descartado; Entonces el sistema actualiza el estado y registra la fecha y el responsable del cambio.<br><br><strong>Escenario 2: Nota de seguimiento.</strong> Dado que el Asesor abre la ficha de un lead; Cuando registra una nota; Entonces el sistema la agrega al historial con su fecha y su autor.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS04</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP07</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Configurar y publicar el Landing Page</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero desarrollar el Landing Page con HTML5, CSS3 y JavaScript y publicarlo en GitHub Pages con atributos ARIA, para que el sitio esté disponible y sea accesible.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Sitio publicado.</strong> Dado que el código del Landing Page está en su repositorio; Cuando se publica en GitHub Pages; Entonces el sitio es accesible desde su URL pública.<br><br><strong>Escenario 2: Accesibilidad.</strong> Dado que el sitio está publicado; Cuando se evalúa con una herramienta de accesibilidad; Entonces las secciones principales y los elementos interactivos tienen atributos ARIA y los colores cumplen el contraste WCAG AA.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS05</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Documentar la API con OpenAPI/Swagger</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero documentar la API con OpenAPI mediante Swagger, para que los equipos de web y móvil conozcan los contratos de cada endpoint.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Documentación disponible.</strong> Dado que la API está en ejecución; Cuando se accede a la documentación de Swagger; Entonces se listan todos los endpoints con sus esquemas de solicitud y de respuesta.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS06</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Exponer endpoint de simulación</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero exponer un endpoint REST para calcular una simulación hipotecaria, para que el Landing Page, la web y el móvil compartan el mismo motor de cálculo.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Simulación calculada.</strong> Dado que una solicitud POST a /api/simulations con valor de vivienda, cuota inicial, plazo, tasa y gracia válidos; Cuando la API procesa la solicitud; Entonces responde con código 200 y la cuota mensual, el TCEA, el VAN, la TIR y el cronograma.<br><br><strong>Escenario 2: Cuota inicial insuficiente.</strong> Dado que una solicitud con una cuota inicial menor al 10%; Cuando la API procesa la solicitud; Entonces responde con código 400 y un mensaje de validación.<br><br><strong>Escenario 3: Datos incompletos.</strong> Dado que una solicitud con campos obligatorios faltantes; Cuando la API procesa la solicitud; Entonces responde con código 400 y la lista de campos con error.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS07</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Exponer endpoints de autenticación</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero exponer los endpoints de registro e inicio de sesión con JWT, para autenticar a Compradores y Asesores de forma segura.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Registro exitoso.</strong> Dado que una solicitud POST a /api/auth/register con datos válidos; Cuando la API procesa la solicitud; Entonces responde con código 201 y los datos del usuario creado.<br><br><strong>Escenario 2: Correo duplicado.</strong> Dado que una solicitud de registro con un correo ya existente; Cuando la API procesa la solicitud; Entonces responde con código 409.<br><br><strong>Escenario 3: Inicio de sesión.</strong> Dado que una solicitud POST a /api/auth/login con credenciales válidas; Cuando la API procesa la solicitud; Entonces responde con código 200 y un token JWT.<br><br><strong>Escenario 4: Credenciales inválidas.</strong> Dado que una solicitud de inicio de sesión con credenciales inválidas; Cuando la API procesa la solicitud; Entonces responde con código 401.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS08</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Exponer endpoints de leads</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero exponer los endpoints para enviar y gestionar leads, para que el Comprador comparta su simulación y el Asesor le dé seguimiento.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Lead creado con consentimiento.</strong> Dado que una solicitud POST a /api/leads de un Comprador autenticado con la autorización expresa registrada; Cuando la API procesa la solicitud; Entonces responde con código 201 y el identificador del lead.<br><br><strong>Escenario 2: Lead sin consentimiento.</strong> Dado que una solicitud POST a /api/leads sin la autorización del Comprador; Cuando la API procesa la solicitud; Entonces responde con código 400 y no registra el lead.<br><br><strong>Escenario 3: Bandeja del Asesor.</strong> Dado que una solicitud GET a /api/leads con el token de un Asesor; Cuando la API procesa la solicitud; Entonces responde con código 200 y solo los leads de su inmobiliaria.<br><br><strong>Escenario 4: Acceso sin token.</strong> Dado que una solicitud GET a /api/leads sin token; Cuando la API procesa la solicitud; Entonces responde con código 401.<br><br><strong>Escenario 5: Cambio de estado.</strong> Dado que una solicitud PATCH a /api/leads/{id}/status con un estado permitido; Cuando la API procesa la solicitud; Entonces responde con código 200 y el estado actualizado.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>SP01</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Media</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Investigar bibliotecas de generación de PDF en C#</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero investigar bibliotecas de generación de PDF para ASP.NET Core, para determinar cuál es la más adecuada para el reporte de simulación.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Recomendación documentada.</strong> Dado que se investigan las bibliotecas disponibles; Cuando se evalúan criterios de licencia, calidad de salida y facilidad de integración; Entonces se presenta un documento con la recomendación y un prototipo mínimo que genera el cronograma en PDF.</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>SP02</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Validar el port del motor financiero a C#</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero validar el port del motor financiero (método francés, VAN, TIR y TCEA) de Python a C#, para asegurar que los resultados coinciden con los del proyecto original.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Resultados validados.</strong> Dado que se cuenta con los casos de prueba documentados de AutoFinance Pro; Cuando se ejecutan contra la implementación en C#; Entonces se documentan la diferencia máxima observada, las reglas de redondeo y un prototipo mínimo del cálculo.</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>SP03</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Desarrollador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Alta</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">EP06</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Definir la tecnología de la app móvil nativa</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero comparar las opciones de desarrollo móvil nativo, para elegir la tecnología de la aplicación con el menor riesgo para el tiempo disponible.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>Escenario 1: Tecnología recomendada.</strong> Dado que se comparan las opciones para Android y iOS; Cuando se evalúan curva de aprendizaje, tiempo de desarrollo y consumo de la API; Entonces se presenta un documento con la recomendación y un prototipo mínimo de una pantalla conectada a la API.</td>
    </tr>
  </tbody>
</table>

## **3.3. Product Backlog**

<p style="text-align: justify; line-height: 1.6;">
  El Product Backlog ordena las historias según su valor para el negocio. Las historias del Landing Page se ubican al inicio porque forman parte del primer Sprint, seguidas de las bases técnicas y del simulador; las historias de autenticación y de conexión con inmobiliarias se ubican después de que el simulador entrega valor, y las del Administrador quedan al final. La estimación utiliza la escala de Story Points 1, 2, 3, 5 y 8.
</p>

<table style="width: 100%; border-collapse: collapse; margin: 16px 0 22px 0; font-size: 9pt; page-break-inside: auto; table-layout: fixed;">
  <thead style="display: table-header-group;">
    <tr style="page-break-inside: avoid;">
      <th style="width: 6%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Orden</th>
      <th style="width: 10%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">User Story ID</th>
      <th style="width: 18%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Título</th>
      <th style="width: 56%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Descripción</th>
      <th style="width: 10%; background-color: #0E5C63; color: #FFFFFF; border: 1px solid #64748B; padding: 7px; text-align: center; vertical-align: middle; overflow-wrap: anywhere;">Story Points</th>
    </tr>
  </thead>
  <tbody style="page-break-inside: auto;">
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">1</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS04</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Configurar y publicar el Landing Page</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero desarrollar el Landing Page con HTML5, CSS3 y JavaScript y publicarlo en GitHub Pages con atributos ARIA, para que el sitio esté disponible y sea accesible.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US14</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Ver propuesta de valor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero ver en la página de inicio qué es HipoSim y en qué se diferencia de los simuladores bancarios, para entender su propuesta antes de simular.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US15</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Simular crédito sin registro desde el Landing Page</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero probar un simulador básico indicando el valor de la vivienda, la cuota inicial y el plazo, para obtener una cuota mensual y un TCEA estimados sin registrarme.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">4</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US16</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Conocer beneficios estatales</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero conocer el Bono del Buen Pagador, el Bono Mivivienda Sostenible y el Nuevo Crédito Mivivienda, para saber a qué subsidios podría acceder.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US17</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Consultar Términos y Condiciones y Privacidad</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero consultar los Términos y Condiciones y la política de privacidad, para conocer mis derechos y cómo se tratan mis datos personales.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">6</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US18</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Consultar preguntas frecuentes</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero consultar preguntas frecuentes sobre el simulador, el TCEA y los beneficios estatales, para resolver mis dudas sin contactar al equipo.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">7</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US19</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Contactar al equipo de HipoSim</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero enviar una consulta al equipo de HipoSim, para resolver dudas que no encontré en el sitio.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">8</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US20</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Cambiar el idioma del sitio</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Visitante, quiero cambiar el idioma del sitio entre español (es_419) e inglés (en_US), para usarlo en el idioma que prefiero.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">9</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS01</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Configurar entorno de frontend</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero configurar el entorno de desarrollo con Vue y PrimeVue (tema Material), para asegurar una interfaz modular y responsiva alineada con el Design System definido.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">10</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>SP03</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Definir la tecnología de la app móvil nativa</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero comparar las opciones de desarrollo móvil nativo, para elegir la tecnología de la aplicación con el menor riesgo para el tiempo disponible.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">11</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>SP02</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Validar el port del motor financiero a C#</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero validar el port del motor financiero (método francés, VAN, TIR y TCEA) de Python a C#, para asegurar que los resultados coinciden con los del proyecto original.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">12</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS02</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Implementar backend y base de datos</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero configurar el backend con ASP.NET Core (C#) y las migraciones en PostgreSQL mediante Entity Framework Core, para asegurar una persistencia robusta y escalable.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">13</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS06</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Exponer endpoint de simulación</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero exponer un endpoint REST para calcular una simulación hipotecaria, para que el Landing Page, la web y el móvil compartan el mismo motor de cálculo.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">14</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS05</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Documentar la API con OpenAPI/Swagger</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero documentar la API con OpenAPI mediante Swagger, para que los equipos de web y móvil conozcan los contratos de cada endpoint.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">15</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US01</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Simular crédito base</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero simular un crédito ingresando el precio de la vivienda y la cuota inicial, para ver mi cuota mensual sin tener que registrarme primero.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">16</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US04</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Visualizar TCEA, VAN y TIR</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero ver el cálculo automático del TCEA, el VAN y la TIR de mi simulación, para conocer el costo real efectivo más allá de la tasa nominal.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">8</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">17</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US05</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Aplicar Bono del Buen Pagador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero aplicar el Bono del Buen Pagador a mi simulación, para ver automáticamente cómo se reduce el monto a financiar si califico.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">18</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US02</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Ver cronograma de pagos</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero visualizar el cronograma de pagos detallado, para entender cómo se distribuye mi cuota entre capital e intereses mes a mes.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">19</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US13</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Registrarse como Comprador</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero registrarme con mi correo electrónico y una contraseña, para acceder a las funciones de guardado, comparación y exportación.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">20</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS07</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Exponer endpoints de autenticación</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero exponer los endpoints de registro e inicio de sesión con JWT, para autenticar a Compradores y Asesores de forma segura.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">21</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US06</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Guardar escenario de simulación</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Usuario Registrado, quiero guardar un escenario de simulación en mi perfil, para no tener que volver a ingresar los datos en futuras sesiones.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">22</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US07</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Comparar escenarios guardados</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Usuario Registrado, quiero comparar entre dos y tres escenarios guardados lado a lado, para decidir qué configuración, por ejemplo el plazo o la cuota inicial, me conviene más.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">23</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>SP01</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Investigar bibliotecas de generación de PDF en C#</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero investigar bibliotecas de generación de PDF para ASP.NET Core, para determinar cuál es la más adecuada para el reporte de simulación.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">2</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">24</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS03</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Generar reportes PDF desde la API</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero implementar en la API un servicio que genere el reporte de una simulación en PDF, para que las aplicaciones web y móvil descarguen el mismo documento.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">25</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US08</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Exportar reporte en PDF</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Usuario Registrado, quiero descargar un reporte en PDF de mis simulaciones o comparativas, para enviárselo a mi pareja o llevarlo al banco.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">26</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US21</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Enviar mi simulación a inmobiliarias con mi consentimiento</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero elegir enviar mi simulación a inmobiliarias verificadas, para recibir información de proyectos en mi rango presupuestal solo si yo lo autorizo.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">27</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US22</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Iniciar sesión como Asesor</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Asesor de inmobiliaria, quiero iniciar sesión con mis credenciales, para acceder a los interesados de mi inmobiliaria.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">28</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>TS08</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Exponer endpoints de leads</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como desarrollador, quiero exponer los endpoints para enviar y gestionar leads, para que el Comprador comparta su simulación y el Asesor le dé seguimiento.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">29</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US23</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Ver bandeja de leads</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Asesor de inmobiliaria, quiero ver la bandeja de leads que autorizaron compartir su simulación, para priorizar a quién contactar.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">30</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US24</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Ver ficha del lead</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Asesor de inmobiliaria, quiero ver la ficha de un lead con su simulación, para conocer su capacidad de compra antes de contactarlo.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">31</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US25</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Gestionar estado y seguimiento del lead</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Asesor de inmobiliaria, quiero cambiar el estado de un lead y registrar notas de mis contactos, para llevar el control de su atención.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">32</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US03</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Aplicar periodo de gracia</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Comprador, quiero añadir un periodo de gracia, total o parcial, a mi simulación, para ver cómo afecta el pago de mis primeras cuotas y el costo total.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">33</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US09</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Actualizar tasas referenciales</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero actualizar las tasas de interés referenciales (TEA) del sistema, para que las nuevas simulaciones reflejen las condiciones actuales del mercado.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">34</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US10</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Configurar rangos Mivivienda</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero actualizar los topes y valores del programa Mivivienda y del Bono del Buen Pagador, para mantener la exactitud legal de los subsidios estatales calculados.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
    <tr style="page-break-inside: avoid;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">35</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US11</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Previsualizar impacto de parámetros</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero previsualizar cómo afectará un cambio de tasa a una simulación estándar antes de publicarlo, para evitar errores de digitación que afecten al simulador.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">3</td>
    </tr>
    <tr style="page-break-inside: avoid; background-color: #F8FAFC;">
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">36</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;"><strong>US12</strong></td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Historial de auditoría de parámetros</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: justify; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">Como Administrador, quiero ver un historial completo de quién cambió cada parámetro y cuándo, para mantener la trazabilidad frente a auditorías normativas.</td>
      <td style="border: 1px solid #94A3B8; padding: 7px; text-align: center; vertical-align: top; line-height: 1.35; overflow-wrap: anywhere;">5</td>
    </tr>
  </tbody>
</table>

<div style="margin: 16px 0; padding: 12px 16px; background-color: #F8FAFC; border-left: 5px solid #0E5C63; page-break-inside: avoid;">
  <strong>Product Backlog en Jira</strong>
  <p style="text-align: justify; margin: 8px 0 4px 0;">Captura del Product Backlog en Jira: <em>pendiente de agregar</em> (<code>../assets/07-chapter-3/product-backlog-jira.png</code>).</p>
  <p style="text-align: justify; margin: 4px 0;">URL pública del Product Backlog: <em>pendiente de agregar</em>.</p>
</div>

## **3.4. Impact Mapping**

<p style="text-align: justify; line-height: 1.6;">
  El Impact Mapping vincula los objetivos principales del negocio con el cambio de comportamiento esperado en nuestros segmentos de usuarios y con las funcionalidades (entregables) necesarias para lograrlo.
</p>

**Impact Map - Segmento 1: Comprador de Primera Vivienda**

<div align="center" style="margin: 16px 0 24px 0; page-break-inside: avoid;">
  <img src="../assets/07-chapter-3/impact-mapping/impact-map-segmento-1.png" width="90%" style="max-width: 100%; height: auto;" alt="Impact Map del comprador de primera vivienda">
  <p style="text-align: center; margin-top: 8px;"><em>Figura 3. Impact Map del comprador de primera vivienda.</em></p>
</div>

**Impact Map - Segmento 2: Administrador de Producto**

<div align="center" style="margin: 16px 0 24px 0; page-break-inside: avoid;">
  <img src="../assets/07-chapter-3/impact-mapping/impact-map-segmento-2.png" width="90%" style="max-width: 100%; height: auto;" alt="Impact Map del administrador de producto">
  <p style="text-align: center; margin-top: 8px;"><em>Figura 4. Impact Map del administrador de producto.</em></p>
</div>
