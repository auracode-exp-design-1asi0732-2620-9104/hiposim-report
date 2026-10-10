# **Conclusions**

## **Conclusions and recommendations**

### Conclusions

<p style="text-align: justify;">
  <b>1. Validación de la problemática y pertinencia de HipoSim.</b> El proceso de investigación de los Capítulos I y II nos permitió reconocer una dificultad recurrente entre los compradores de primera vivienda: la información hipotecaria se encuentra dispersa entre simuladores de distintas entidades y suele resultar compleja de comparar. Las entrevistas mostraron interés por conocer el costo real del financiamiento, comprender la TCEA y evaluar beneficios estatales antes de iniciar una solicitud formal. Consideramos que esta evidencia cualitativa respalda la pertinencia de una herramienta independiente, aunque no constituye por sí sola una validación estadística del mercado.
</p>

<p style="text-align: justify;">
  <b>2. Diferenciación de segmentos y responsabilidades de acceso.</b> La definición del Comprador de primera vivienda y del Asesor de inmobiliaria como usuarios con objetivos diferentes permitió delimitar los flujos del producto. Mientras el comprador necesita simular, comprender y decidir si comparte sus resultados, el asesor requiere consultar exclusivamente los interesados autorizados y registrar su seguimiento. Distinguimos además al Administrador de la plataforma como un rol interno de mantenimiento de parámetros, sin confundirlo con el segmento comercial de inmobiliarias. Esta separación orientó las historias US21 a US25 y las decisiones de autorización y privacidad.
</p>

<p style="text-align: justify;">
  <b>3. Priorización del valor para el usuario.</b> Las User Stories, el Product Backlog y el Impact Mapping nos ayudaron a estructurar una evolución progresiva del producto. El simulador básico de la Landing Page, publicado en GitHub Pages, permite acercar la propuesta de valor a los visitantes antes de exigir una cuenta. La aplicación Android, el portal web del asesor y la API RESTful amplían el alcance hacia un flujo de simulación y contacto autorizado; sin embargo, su integración completa no puede considerarse verificada únicamente por la existencia de pantallas, repositorios o contratos de servicio.
</p>

<p style="text-align: justify;">
  <b>4. Exactitud y transparencia de la información financiera.</b> Identificamos que la confiabilidad de HipoSim depende de mantener consistentes el método de amortización francés, la conversión de tasas, los indicadores VAN, TIR y TCEA, los seguros y la aplicación del Bono del Buen Pagador. Las diferencias de tasas y supuestos entre el simulador público, la aplicación móvil y la API evidenciaron la necesidad de un contrato financiero común. Asimismo, reconocemos que la TEA no representa necesariamente el costo total del crédito y que la TCEA debe contemplar los cargos aplicables. Una estimación educativa no reemplaza una evaluación crediticia ni una oferta contractual de una entidad financiera.
</p>

<p style="text-align: justify;">
  <b>5. Arquitectura y mantenibilidad de la solución.</b> La separación entre Landing Page, frontend web, aplicación Android, API ASP.NET Core y PostgreSQL favorece la asignación de responsabilidades y la evolución de cada producto. La organización por componentes permite aislar el motor financiero, los servicios de autenticación y la gestión de leads respecto de las interfaces de usuario. El uso de repositorios, GitFlow, Pull Requests y convenciones de código contribuye a mantener trazabilidad de los cambios y a disminuir el riesgo de incompatibilidades durante la integración.
</p>

<p style="text-align: justify;">
  <b>6. Verificación y validación del producto.</b> La estrategia desarrollada en el Capítulo VI relaciona las reglas financieras con pruebas unitarias, los servicios y contratos REST con pruebas de integración, los criterios de aceptación con escenarios BDD y los recorridos comprador–asesor con pruebas de sistema. El informe registra para Android 35 pruebas unitarias y 4 pruebas de interfaz en emulador; esta evidencia no equivale a una aprobación integral de todos los productos. Las pruebas del backend, la persistencia y el flujo completo de consentimiento deben sustentarse con resultados de ejecución propios antes de afirmar la validación de extremo a extremo.
</p>

<p style="text-align: justify;">
  <b>7. Prácticas de integración, entrega y despliegue.</b> En el Capítulo VII definimos componentes de Continuous Integration, Continuous Delivery y Continuous Deployment para las distintas tecnologías de HipoSim. La publicación de la Landing Page y el flujo de integración continua documentado para Android constituyen avances concretos. Por el contrario, el informe no acredita todavía URLs productivas de la API y del portal del asesor ni una automatización de despliegue continuo integral. Esta distinción nos permite evaluar los avances con rigor y evita confundir una arquitectura propuesta con un despliegue efectivamente completado.
</p>

<p style="text-align: justify;">
  <b>8. Responsabilidad ética y protección de datos personales.</b> La interacción con inmobiliarias introduce obligaciones específicas respecto del tratamiento de información financiera y de contacto. Por ello, el consentimiento explícito, la autenticación, el aislamiento de leads por inmobiliaria y la limitación de accesos no son funcionalidades accesorias: son condiciones para una implementación responsable. Estas decisiones se relacionan con la Ley N.° 29733 y con el Student Outcome 4, al exigir que el equipo considere consecuencias sociales, profesionales y económicas de los errores de software.
</p>

<p style="text-align: justify;">
  <b>9. Alcance de las hipótesis y aprendizaje obtenido.</b> Las hipótesis Lean UX H1–H4 plantean efectos esperados sobre finalización de simulaciones, conversión, comparación de escenarios y retorno de usuarios. En esta etapa contamos con investigación inicial, criterios de aceptación y avances funcionales, pero no con resultados experimentales suficientes para aceptar o rechazar tales hipótesis. Por lo tanto, nuestro aprendizaje más importante consiste en reconocer qué comportamientos debemos medir y qué funcionalidades necesitan pruebas reales antes de sostener conclusiones sobre su impacto en el negocio.
</p>

<p style="text-align: justify;">
  <b>10. Balance del avance del proyecto.</b> El desarrollo de HipoSim ha permitido conectar la investigación de usuarios con decisiones de arquitectura, implementación, pruebas y prácticas DevOps. El trabajo colaborativo ha hecho posible delimitar responsabilidades técnicas y documentales, identificar dependencias entre historias y establecer criterios de calidad verificables. Concluimos que el avance es consistente con una solución en evolución, cuyo principal reto pendiente es demostrar el funcionamiento integrado de sus productos y validar sus efectos mediante evidencia medible, sin perder de vista la transparencia financiera y la protección del usuario.
</p>

### Recommendations

<p style="text-align: justify;">
  <b>1.</b> Unificar el contrato financiero entre la Landing Page, Android y la API, definiendo una misma TEA de referencia, las reglas de redondeo, los conceptos de seguro y gastos, y el cálculo separado de la TCEA. Los cambios en tasas y beneficios deben depender de parámetros identificables y actualizables, no de valores divergentes codificados en cada cliente.
</p>

<p style="text-align: justify;">
  <b>2.</b> Priorizar la integración completa de US01, US04, US05 y US02 con <code>POST /api/simulations</code>, verificando los importes y el cronograma mensual mediante casos reproducibles y comparación con el motor financiero de referencia.
</p>

<p style="text-align: justify;">
  <b>3.</b> Completar el flujo de autenticación, selección de inmobiliaria y creación de leads con consentimiento explícito (US13, US26, US21 y TS08), comprobando que un asesor solo pueda acceder a los contactos de su organización y que ninguna simulación se comparta por omisión.
</p>

<p style="text-align: justify;">
  <b>4.</b> Ejecutar y registrar las pruebas automatizadas de la API y las pruebas de integración con PostgreSQL, complementándolas con escenarios Gherkin y pruebas de sistema sobre el recorrido comprador–asesor. Los reportes deben asociarse al commit y a la versión evaluada para conservar trazabilidad.
</p>

<p style="text-align: justify;">
  <b>5.</b> Consolidar el pipeline con verificaciones de compilación, análisis estático, pruebas y controles de seguridad. Separar los entornos de desarrollo y producción, proteger secretos y aplicar migraciones de base de datos de forma controlada antes de habilitar un despliegue automatizado de los componentes transaccionales.
</p>

<p style="text-align: justify;">
  <b>6.</b> Realizar sesiones de validación con usuarios de ambos segmentos una vez habilitado el flujo funcional, registrando resultados de tareas, errores, comprensión de indicadores y percepción de privacidad. Estas mediciones permitirán evaluar las hipótesis Lean UX sin extrapolar indebidamente los hallazgos de las entrevistas exploratorias.
</p>

<p style="text-align: justify;">
  <b>7.</b> Mantener la advertencia de carácter referencial de las simulaciones, la explicación visible de costos y beneficios, los términos del servicio y los mecanismos de consentimiento y revocación que correspondan. La protección de datos y la claridad financiera deben comprobarse tanto en el frontend como en la API.
</p>

<p style="text-align: justify;">
  <b>8.</b> Conservar el registro de versiones, los commits, las revisiones de Pull Requests y la relación entre historias, pruebas y evidencias como parte del informe. Las conclusiones futuras deben actualizarse a partir de resultados observados y no únicamente de funcionalidades planificadas.
</p>
