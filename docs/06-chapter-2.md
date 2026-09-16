# **Chapter II: Requirements Elicitation & Analysis**
## **2.1. Competitors**
Conocer el entorno competitivo es fundamental para identificar las fortalezas y debilidades de HipoSim frente a las alternativas que hoy utilizan los compradores de primera vivienda en Perú para estimar el costo real de un crédito hipotecario. Este análisis permite entender cómo cada entidad expone su información de simulación, con o sin independencia frente al propio banco que la ofrece, y qué limitaciones presentan sus herramientas actuales.

En esta etapa se analizan distintos tipos de competidores con el objetivo de comprender sus fortalezas, debilidades y enfoque de mercado, y así posicionar a HipoSim como una propuesta que responda de manera más efectiva a la necesidad real del comprador primerizo: comparar condiciones reales de forma independiente antes de comprometerse con un banco.

### **2.1.1. Competitive Analysis**

Para desarrollar una solución realmente útil, es fundamental comprender las alternativas que actualmente utiliza un comprador de primera vivienda en Perú para simular un crédito hipotecario. Este análisis permite identificar no solo cómo se informan hoy los usuarios, sino también las principales limitaciones de las herramientas existentes.

A continuación, se presenta una comparación de los principales competidores considerando su propuesta de valor, mercado objetivo y características generales. Este análisis evidencia que, mientras las soluciones existentes están integradas dentro del canal comercial de una entidad específica —ya sea un banco privado o el propio Fondo Mivivienda— HipoSim se posiciona como una alternativa independiente, centrada en mostrar el costo efectivo real (TCEA) y los beneficios estatales aplicables en un solo lugar, sin sesgo comercial hacia ninguna entidad.

<table border="1" cellpadding="10" cellspacing="0" style="margin-left: auto; margin-right: auto; font-family: sans-serif;">
<tr>
<th colspan="6">Panorama del análisis competitivo</th>
</tr>
<tr>
<td colspan="2" rowspan="2"><b>¿Por qué llevar a cabo este análisis?</b></td>
<td colspan="4">¿Cómo se posiciona HipoSim frente a sus competidores en cuanto a fortalezas, debilidades, oportunidades y su propuesta de valor dentro del proceso de simulación de crédito hipotecario en Perú?</td>
</tr>
<tr>
<td colspan="4">Es una propuesta que posiciona a HipoSim como un simulador independiente de crédito hipotecario, sin afiliación a ninguna entidad financiera, que integra el método de amortización francés, la conversión de tasas, los periodos de gracia y los indicadores TCEA, VAN y TIR, junto con la visibilidad de beneficios estatales, frente a herramientas que hoy están confinadas al canal comercial de cada banco o programa estatal.</td>
</tr>
<tr>
<td colspan="2" style="text-align: center;"><b>Competidores</b></td>
<td style="text-align: center; vertical-align: middle;">
<b>HipoSim</b>

<img src="../assets/img/chapter-ii/hiposim-logo.png" alt="HipoSim" width="150" height="80"/>
</td>
<td style="text-align: center; vertical-align: middle;">
<b>Simulador BCP (ViaBCP)</b>

<img src="../assets/img/chapter-ii/bcp-logo.png" alt="BCP" width="150"/>
</td>
<td style="text-align: center; vertical-align: middle;">
<b>Simulador Interbank</b>

<img src="../assets/img/chapter-ii/interbank-logo.png" alt="Interbank" width="150"/>
</td>
<td style="text-align: center; vertical-align: middle;">
<b>Simulador Fondo Mivivienda</b>

<img src="../assets/img/chapter-ii/mivivienda-logo.png" alt="Fondo Mivivienda" width="150"/>
</td>
</tr>
<tr>
<td rowspan="2"><b>Perfil</b></td>
<td>Overview</td>
<td>Simulador web y móvil independiente de crédito hipotecario para compradores de primera vivienda en Perú, que modela el método de amortización francés, la conversión de tasas y los indicadores TCEA, VAN y TIR.</td>
<td>Calculadora hipotecaria integrada dentro del canal digital ViaBCP, que estima la cuota mensual según el valor de la vivienda, el porcentaje de cuota inicial y el plazo elegido.</td>
<td>Calculadora hipotecaria del canal digital de Interbank, que permite simular créditos convencionales y bajo la modalidad Nuevo Crédito Mivivienda, ajustando el tipo de cuota.</td>
<td>Herramienta oficial del Fondo Mivivienda para estimar el crédito bajo el programa Nuevo Crédito Mivivienda, aplicando las fórmulas normativas de Tasa de Costo Efectivo (TCED) y el subsidio del Bono del Buen Pagador (BBP).</td>
</tr>
<tr>
<td>Ventaja competitiva</td>
<td>Independencia frente a cualquier entidad financiera, visualización comparativa del TCEA y beneficios estatales, comparador de escenarios y reporte exportable en PDF.</td>
<td>Marca líder del sistema financiero peruano e integración directa con el proceso real de solicitud del propio banco.</td>
<td>Tasa competitiva dentro del mercado privado y opción integrada de modalidad Mivivienda dentro del mismo canal digital del banco.</td>
<td>Único canal oficial autorizado para calcular con exactitud el subsidio estatal (BBP) y el Nuevo Crédito Mivivienda conforme a la normativa vigente.</td>
</tr>
<tr>
<td rowspan="2"><b>Perfil de Marketing</b></td>
<td>Mercado objetivo</td>
<td>Compradores de primera vivienda de 25 a 40 años en Perú, con empleo formal estable y sin experiencia previa comparando créditos.</td>
<td>Clientes actuales y potenciales de BCP interesados en un crédito hipotecario propio del banco.</td>
<td>Clientes actuales y potenciales de Interbank, incluyendo quienes califican para el Nuevo Crédito Mivivienda a través de este banco.</td>
<td>Familias peruanas elegibles para el subsidio estatal, dentro de los rangos de precio de vivienda establecidos por el programa.</td>
</tr>
<tr>
<td>Estrategias de marketing</td>
<td>Posicionamiento como comparador independiente y educativo, enfocado en la transparencia del costo real (TCEA) y en la difusión de beneficios estatales.</td>
<td>Captación de clientes hipotecarios dentro del ecosistema propio del banco a través del canal digital ViaBCP.</td>
<td>Comunicación de tasas competitivas y facilidad para acceder a Mivivienda dentro del mismo flujo digital del banco.</td>
<td>Comunicación institucional del Estado sobre el Bono del Buen Pagador y los rangos de precios del Nuevo Crédito Mivivienda.</td>
</tr>
<tr>
<td rowspan="3"><b>Perfil de Producto</b></td>
<td>Productos & Servicios</td>
<td>Simulador con método francés, cálculo de TCEA/VAN/TIR, periodos de gracia, comparador de escenarios, historial de simulaciones, toggle de beneficios estatales y reporte exportable en PDF.</td>
<td>Calculadora de cuota mensual según plazo y porcentaje de cuota inicial, con acceso al detalle del crédito hipotecario del banco.</td>
<td>Calculadora de cuota con selección de tipo de cuota y modalidad Mivivienda.</td>
<td>Cálculo del monto de crédito, cuota y cronograma bajo las fórmulas oficiales del programa, incluyendo el Bono del Buen Pagador.</td>
</tr>
<tr>
<td>Precios & Costos</td>
<td>Acceso gratuito; producto digital independiente sin cobro directo al usuario final.</td>
<td>Sin costo de uso del simulador; el costo real depende de la tasa y condiciones del crédito otorgado por el banco.</td>
<td>Sin costo de uso del simulador; costo real sujeto a la evaluación crediticia del banco.</td>
<td>Sin costo de uso del simulador oficial; el subsidio (BBP) reduce el costo real del crédito para quienes califican.</td>
</tr>
<tr>
<td>Canales de distribución</td>
<td>Web y aplicación móvil propia.</td>
<td>Sitio web ViaBCP.</td>
<td>Sitio web y aplicación móvil de Interbank.</td>
<td>Sitio web oficial del Fondo Mivivienda y bancos participantes del programa.</td>
</tr>
<tr>
<td rowspan="5"><b>Análisis SWOT</b></td>
</tr>
<tr>
<td>Fortalezas</td>
<td>Independencia de cualquier banco, visualización comparativa del TCEA y los beneficios estatales en un solo lugar, comparador de escenarios y reporte compartible.</td>
<td>Marca líder y confianza del sistema financiero, integración directa con el proceso real de solicitud.</td>
<td>Tasa competitiva dentro del mercado privado e integración de la modalidad Mivivienda en el mismo flujo.</td>
<td>Único canal oficial válido para el cálculo exacto del subsidio estatal, con normativa clara y verificable.</td>
</tr>
<tr>
<td>Debilidades</td>
<td>Producto nuevo sin reconocimiento de marca, sin relación comercial directa con bancos ni otorgamiento de créditos, dependiente de la actualización manual de tasas y parámetros.</td>
<td>Muestra únicamente la oferta propia del banco, sin comparación con otras entidades ni con los beneficios estatales de forma integrada.</td>
<td>Misma limitación de mostrar solo su propia oferta; la información puede percibirse como comercialmente sesgada.</td>
<td>Solo aplica al Nuevo Crédito Mivivienda (no a créditos hipotecarios convencionales); su cálculo formal (TCED iterativo) resulta poco intuitivo para un usuario sin conocimientos financieros.</td>
</tr>
<tr>
<td>Oportunidades</td>
<td>Bajo conocimiento del TCEA real y de los beneficios estatales entre compradores primerizos, y creciente investigación informal previa a la compra.</td>
<td>Ampliar su simulador con mayor transparencia del costo total para reducir el uso de herramientas externas.</td>
<td>Reforzar la integración de Mivivienda como diferenciador frente a otros bancos.</td>
<td>Mayor difusión digital del programa hacia compradores primerizos.</td>
</tr>
<tr>
<td>Amenazas</td>
<td>Mejora de los simuladores propios de cada banco, desconfianza inicial del usuario al ingresar datos financieros en una plataforma independiente, y posible entrada de fintechs comparadoras similares.</td>
<td>Pérdida de clientes que comparan condiciones fuera de su canal antes de decidir.</td>
<td>Clientes que comparan condiciones en herramientas independientes antes de acercarse al banco.</td>
<td>Bajo conocimiento del programa entre la población objetivo, lo que limita su alcance real.</td>
</tr>
</table>

A partir del análisis comparativo, se identifican las siguientes diferencias clave:

- Frente a los simuladores de BCP e Interbank, HipoSim no depende de ninguna entidad financiera y no muestra únicamente la oferta de un solo banco, sino que permite comparar condiciones de forma independiente antes de iniciar un proceso comercial.
- A diferencia del simulador oficial del Fondo Mivivienda, que se enfoca exclusivamente en el cálculo normativo del Nuevo Crédito Mivivienda mediante fórmulas poco accesibles para un usuario sin formación financiera, HipoSim traduce ese mismo tipo de beneficio estatal en una visualización simple y comparable junto con créditos hipotecarios convencionales.
- En los tres casos, los simuladores existentes están confinados al canal comercial de la entidad que los ofrece, lo cual coincide directamente con el problema de negocio identificado en el Capítulo I: no existe hoy un producto independiente que permita a un comprador primerizo explorar y comparar escenarios reales de crédito hipotecario por su cuenta.

En conjunto, este análisis permite concluir que HipoSim no compite como un producto bancario ni reemplaza al canal oficial del Fondo Mivivienda, sino que ocupa un espacio diferenciado: el de una herramienta independiente que traduce información dispersa y entidad-específica en una simulación transparente y comparable, dirigida específicamente al comprador de primera vivienda en la etapa previa a su acercamiento formal a un banco.

### **2.1.2. Strategies and Tactics Against Competitors**

Una vez identificados los actores del mercado y las principales diferencias entre las alternativas existentes, resulta necesario definir cómo HipoSim puede fortalecer su posicionamiento competitivo frente a simuladores bancarios ya consolidados y al canal oficial del Fondo Mivivienda.

Con este objetivo, se emplea la Matriz CAME, la cual permite transformar el análisis FODA en estrategias y acciones concretas. A través de esta herramienta se plantean tácticas orientadas a potenciar las fortalezas diferenciales de HipoSim —su independencia, la visualización comparativa del TCEA y de los beneficios estatales— así como a mitigar las debilidades propias de un producto nuevo sin relación comercial directa con las entidades financieras.

Las estrategias definidas buscan:
* Aprovechar el bajo conocimiento del TCEA real y de los beneficios estatales entre los compradores primerizos para posicionar a HipoSim como fuente de información clara.
* Comunicar el valor de la independencia y la transparencia frente a simuladores confinados al canal comercial de una sola entidad.
* Reducir la desconfianza inicial del usuario al ingresar datos financieros personales mediante una experiencia simple y sin barreras de entrada.
* Posicionar a HipoSim como el punto de referencia informativo antes de que el comprador primerizo se acerque a un banco.

Matriz CAME para el desarrollo de estrategias basadas en el análisis FODA.

| **Análisis FODA cruzado** | **Oportunidades** | **Amenazas** |
|---------------------------|------------------|--------------|
| **Fortalezas (F)**<br>1. Independencia frente a cualquier entidad financiera.<br>2. Visualización comparativa del TCEA y de los beneficios estatales.<br>3. Comparador de escenarios e historial de simulaciones para usuarios registrados.<br>4. Acceso web y móvil, sin necesidad de crear cuenta para ver un primer resultado.<br>5. Reporte de simulación exportable y compartible en PDF. | **Estrategia (FO) — Estrategias Ofensivas**<br>1. Posicionar a HipoSim como el único comparador independiente que muestra el TCEA real y los beneficios estatales en un solo lugar.<br>2. Aprovechar el bajo conocimiento del TCEA para educar al usuario mediante visualizaciones claras y comparativas.<br>3. Difundir el comparador de escenarios y el reporte PDF como herramienta para discutir la decisión en familia o con un asesor.<br>4. Dirigir campañas hacia compradores primerizos que investigan informalmente antes de acercarse a un banco. | **Estrategia (FA) — Estrategias Defensivas**<br>1. Reforzar la transparencia e independencia frente a los simuladores bancarios como principal diferenciador de marca.<br>2. Mantener una actualización rigurosa y frecuente de tasas y parámetros (rol Administrador) para sostener la confianza del usuario.<br>3. Comunicar explícitamente las políticas de privacidad y limitar la solicitud de datos sensibles al mínimo necesario.<br>4. Monitorear los simuladores bancarios y posibles fintechs comparadoras para anticipar mejoras funcionales. |
| **Debilidades (D)**<br>1. Producto nuevo sin reconocimiento de marca.<br>2. Sin relación comercial directa con bancos ni otorgamiento de créditos.<br>3. Dependencia de la actualización manual de tasas y parámetros.<br>4. Alcance inicial limitado al segmento comprador primerizo. | **Estrategia (DO) — Reorientación**<br>1. Priorizar el MVP con la visualización comparativa de TCEA y beneficios (H2) antes de invertir en el comparador y el historial.<br>2. Aprovechar la tendencia de digitalización financiera para ganar visibilidad pese a ser un producto nuevo.<br>3. Usar el acceso sin barrera de entrada al primer resultado para impulsar la adopción progresiva.<br>4. Explorar la actualización semiautomatizada de tasas y beneficios estatales para reducir la dependencia manual del Administrador. | **Estrategia (DA) — Supervivencia**<br>1. Mantener el alcance acotado al comprador primerizo mientras se valida el modelo, sin competir directamente con bancos o el canal oficial de Mivivienda.<br>2. Simplificar el ingreso de datos personales al mínimo indispensable para reducir la fricción y la desconfianza inicial.<br>3. Evaluar una futura alianza informativa (no comercial) con el Fondo Mivivienda para validar la exactitud de los beneficios mostrados.<br>4. Priorizar el mantenimiento actualizado de las tasas de los bancos de referencia (BCP, Interbank) antes de expandir a más entidades. |

## **2.2. Interviews**

Las entrevistas son clave para la metodología de diseño centrado en el usuario, al permitir recolectar información cualitativa directamente del comprador de primera vivienda: cómo investiga hoy, qué tan bien entiende el costo real de un crédito hipotecario y qué fricciones enfrenta antes de acercarse a un banco.

### **2.2.1. Interview Design**

## Segmento 1: Comprador de Primera Vivienda:

Preguntas Personales  

1. ¿Cuál es su nombre, edad y distrito de residencia?

2. ¿Cuál es su ocupación actual y hace cuánto tiene un empleo formal estable?

3. ¿Está actualmente evaluando la compra de su primera vivienda?

4. ¿Qué dispositivo utiliza con más frecuencia para informarse sobre temas financieros?

5. ¿Qué canal usa normalmente para informarse: bancos, redes sociales, recomendaciones u otro?

6. ¿Qué parte de este proceso le genera mayor dificultad o frustración?

Preguntas Específicas

1. ¿Sabe qué es el TCEA y cómo se calcula?

2. ¿Ha usado algún simulador de crédito hipotecario? ¿De qué banco?

3. ¿Confía en que ese simulador es objetivo e independiente? ¿Por qué?

4. ¿Ha comparado las condiciones de más de un banco antes de decidir? ¿Cómo?

5. ¿Conocía el Bono del Buen Pagador o el Nuevo Crédito Mivivienda?

6. ¿Qué información necesita para sentirse seguro antes de acercarse a un banco?

7. ¿Ingresaría sus datos financieros (ingresos, ahorro, precio de vivienda) en una herramienta independiente para simular? ¿Por qué?

8. ¿Le interesaría guardar, comparar o exportar sus simulaciones?

## Segmento 2: Administrador de producto:

Preguntas personales

1. ¿Cuál es su nombre, edad y cargo dentro del equipo o la organización?

2. ¿Cuál sería su rol respecto al mantenimiento de tasas y parámetros del producto?

3. ¿Qué fuentes usa hoy para obtener esa información: SBS, bancos, Fondo Mivivienda u otra?

4. ¿Con qué frecuencia necesitaría actualizar estos datos?

5. ¿Qué herramienta o dispositivo usa con más frecuencia para esta tarea?

6. ¿Qué parte de este proceso le genera mayor dificultad?

Preguntas Específicas

1. ¿Qué parámetros necesita mantener actualizados: tasas referenciales, porcentaje del Bono del Buen Pagador, rangos Mivivienda u otros?

2. ¿Qué tan seguido cambian estos valores y qué tan rápido deberían reflejarse en el sistema?

3. ¿Qué riesgo representa que un valor quede desactualizado?

4. ¿Qué tan simple le resultaría actualizar estos valores desde un panel de administración?

5. ¿Qué métricas de uso le interesaría monitorear, como simulaciones realizadas o tasa de conversión?

6. ¿Qué nivel de acceso o permisos considera necesario para realizar estas tareas de forma segura?

7. ¿Confía en que los cambios que realice se reflejarán correctamente y a tiempo en el simulador?

8. ¿Qué funcionalidad le facilitaría esta tarea, como alertas de cambio de tasas o un historial de modificaciones?


### **2.2.2. Interview Recording**

<table>
    <colgroup></colgroup>
    <thead>
        <tr>
            <th colspan="2">Entrevista #1<br></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Nombre</td>
            <td></td>
        </tr>
        <tr>
            <td>Apellidos</td>
            <td></td>
        </tr>
        <tr>
            <td>Edad</td>
            <td></td>
        </tr>
        <tr>
            <td>Distrito</td>
            <td></td>
        </tr>
        <tr>
            <td>Evidencia</td>
            <td style="text-align: left;">
                <div align="center"><img src="../assets/img/chapter-ii/[nombre-entrevistado].png" width="700"></div>
            </td>
        </tr>
        <tr>
            <td>Link</td>
            <td>
                <a href="#" target="_blank">
                [pendiente]
            </a>
            </td>
        </tr>
        <tr>
            <td>Timing donde inicia la entrevista<br></td>
            <td></td>
        </tr>
        <tr>
            <td>Duración de la entrevista<br></td>
            <td></td>
        </tr>
        <tr>
            <td>Resumen</td>
            <td></td>
        </tr>
    </tbody>
</table>

<table>
    <colgroup></colgroup>
    <thead>
        <tr>
            <th colspan="2">Entrevista #2<br></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Nombre</td>
            <td></td>
        </tr>
        <tr>
            <td>Apellidos</td>
            <td></td>
        </tr>
        <tr>
            <td>Edad</td>
            <td></td>
        </tr>
        <tr>
            <td>Distrito</td>
            <td></td>
        </tr>
        <tr>
            <td>Evidencia</td>
            <td style="text-align: left;">
                <div align="center"><img src="../assets/img/chapter-ii/[nombre-entrevistado].png" width="700"></div>
            </td>
        </tr>
        <tr>
            <td>Link</td>
            <td>
                <a href="#" target="_blank">
                [pendiente]
            </a>
            </td>
        </tr>
        <tr>
            <td>Timing donde inicia la entrevista<br></td>
            <td></td>
        </tr>
        <tr>
            <td>Duración de la entrevista<br></td>
            <td></td>
        </tr>
        <tr>
            <td>Resumen</td>
            <td></td>
        </tr>
    </tbody>
</table>

<table>
    <colgroup></colgroup>
    <thead>
        <tr>
            <th colspan="2">Entrevista #3<br></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Nombre</td>
            <td></td>
        </tr>
        <tr>
            <td>Apellidos</td>
            <td></td>
        </tr>
        <tr>
            <td>Edad</td>
            <td></td>
        </tr>
        <tr>
            <td>Distrito</td>
            <td></td>
        </tr>
        <tr>
            <td>Evidencia</td>
            <td style="text-align: left;">
                <div align="center"><img src="../assets/img/chapter-ii/[nombre-entrevistado].png" width="700"></div>
            </td>
        </tr>
        <tr>
            <td>Link</td>
            <td>
                <a href="#" target="_blank">
                [pendiente]
            </a>
            </td>
        </tr>
        <tr>
            <td>Timing donde inicia la entrevista<br></td>
            <td></td>
        </tr>
        <tr>
            <td>Duración de la entrevista<br></td>
            <td></td>
        </tr>
        <tr>
            <td>Resumen</td>
            <td></td>
        </tr>
    </tbody>
</table>

### **2.2.3. Interview Analysis**
## **2.3. Needfinding**
### **2.3.1. User Personas**
### **2.3.2. User Task Matrix**
### **2.3.3. User Journey Mapping**
### **2.3.4. Empathy Mapping**
### **2.3.5. As-is Scenario Mapping**
## **2.4. Ubiquitous Language**
