# **Capítulo VII: DevOps Practices**

Nuestra estrategia DevOps articula el control de versiones, la compilación, la ejecución de pruebas, la preparación de versiones y su publicación. HipoSim se desarrolla mediante repositorios separados para el Landing Page, el portal web, la aplicación Android y la API RESTful, con GitHub como plataforma común de colaboración y Jira como sistema de seguimiento de historias y tareas. El objetivo es reducir errores de integración y conservar trazabilidad entre los requisitos, los cambios de código y las versiones entregadas.

Organizamos el trabajo con **GitFlow**: `main` representa la línea estable; `develop`, la integración cotidiana; `feature/*`, el desarrollo de funcionalidades; `release/*`, la estabilización previa a la entrega; y `hotfix/*`, las correcciones urgentes. Complementamos esta estructura con **Conventional Commits**, revisiones mediante Pull Request y versionado semántico `MAYOR.MENOR.PARCHE`. Diferenciamos claramente tres conceptos: la integración continua comprueba cambios, la entrega continua prepara una versión apta para publicarse y el despliegue continuo publica automáticamente una versión aprobada cuando se cumplen las condiciones definidas.

| Producto | Repositorio o canal documentado | Situación de partida |
|---|---|---|
| Landing Page | [hiposim-LandingPage](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-LandingPage) | Publicada mediante GitHub Pages |
| Portal web del asesor | [hiposim-webApp](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-webApp) | Implementación local con datos de ejemplo; sin despliegue productivo documentado |
| Aplicación Android | [hiposim-app-mobile](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-app-mobile) | Desarrollo en `develop`; PR n.° 1 documentado; pruebas y CI móvil reportadas |
| API RESTful y PostgreSQL | Contrato y componentes definidos en el informe | Repositorio público, ejecución del pipeline y despliegue no acreditados |

<div style="page-break-after: always;"></div>

## **7.1. Continuous Integration**

La integración continua nos permite revisar cada cambio antes de incorporarlo a una versión compartida. En lugar de depender exclusivamente de pruebas manuales posteriores al desarrollo, definimos controles sobre la sintaxis, la construcción de los productos, el comportamiento funcional y la compatibilidad entre componentes. De esta forma, cada historia de usuario puede relacionarse con un cambio identificable y con los resultados de verificación correspondientes.

### **7.1.1. Tools and Practices**

Utilizamos **Git y GitHub** para el historial del código, las ramas GitFlow y las revisiones colaborativas. **GitHub Actions** es el mecanismo de automatización documentado para la aplicación Android. **Jira** conserva la relación entre las tareas y las historias; **Gradle**, el sistema de construcción del proyecto Kotlin; **npm y Vite**, las dependencias y el empaquetado del portal Vue; y **.NET SDK**, la restauración de dependencias, compilación y ejecución de pruebas de la API. La documentación de contratos de servicios se apoya en **OpenAPI/Swagger** y en la verificación de peticiones mediante **Postman**, según el entorno de trabajo establecido en el Capítulo V.

Aplicamos los siguientes acuerdos de integración:

1. Desarrollamos cada funcionalidad en una rama `feature/*` creada desde `develop`, vinculada con una historia o tarea de Jira.
2. Registramos cambios con mensajes Conventional Commits, como `test(financial-engine): add amortization validation cases` y `fix(auth): reject invalid credentials`.
3. Integramos los cambios mediante Pull Requests revisados por otro integrante, evitando modificaciones directas sobre `main`.
4. Comprobamos que la construcción, el análisis estático y las pruebas correspondientes al componente no presenten fallas antes de aceptar una integración.
5. Mantenemos la configuración sensible fuera del repositorio. Las contraseñas, cadenas de conexión, claves de firma y tokens se administran mediante variables de entorno o secretos del servicio de automatización.
6. Preservamos la separación entre datos de demostración y datos reales, especialmente cuando se manejan ingresos, ahorros, simulaciones hipotecarias o datos de contacto.

La aplicación Android aporta la evidencia más concreta de automatización en la versión revisada: el informe consigna **GitHub Actions, 35 pruebas unitarias, 4 pruebas de interfaz y ejecución satisfactoria de `ktlint` y lint**. Para los demás repositorios se encuentran definidos los procesos de compilación y verificación, pero no se documentan ejecuciones automáticas concluidas equivalentes. Esto determina el nivel de madurez de nuestra integración continua por producto y evita generalizar los resultados del móvil a toda la plataforma.

<div style="page-break-after: always;"></div>

### **7.1.2. Build & Test Suite Pipeline Components**

Definimos los componentes del pipeline según la tecnología de cada producto, manteniendo un criterio común: un cambio no es apto para integrarse si no supera las verificaciones pertinentes a su alcance. El flujo técnico comprende la obtención del código, la preparación del entorno, la restauración de dependencias, la compilación, el análisis estático, las pruebas y el registro de resultados.

| Componente del pipeline | Landing Page | Portal Vue | Aplicación Android | API ASP.NET Core |
|---|---|---|---|---|
| Recuperación del código | Checkout del commit | Checkout del commit | Checkout del commit | Checkout del commit |
| Preparación del entorno | Validadores web y navegador | Node.js y npm | JDK, Android SDK y Gradle | .NET SDK |
| Dependencias | Recursos de HTML/CSS/JS | `npm ci` | Resolución de dependencias Gradle | `dotnet restore` |
| Construcción | Verificación de archivos y recursos estáticos | `npm run build` | `assembleDebug` | `dotnet build --configuration Release` |
| Análisis estático | Revisión de HTML, CSS, JavaScript y accesibilidad | Reglas de estilo de JavaScript/Vue | `ktlint` y Android Lint | Advertencias del compilador y convenciones C# |
| Pruebas | Cálculo básico, navegación e idiomas | Validación de formularios y estados del portal | Pruebas unitarias e interfaz instrumentada | `dotnet test` para suites unitarias y de integración |
| Resultado de ejecución | Validación del sitio estático | Construcción del directorio `dist` | Reportes Gradle y compilación Android | Reportes de pruebas y artefacto publicable |

Para la aplicación web, `npm ci` permite instalar versiones de dependencias consistentes con el archivo de bloqueo, mientras que `npm run build` produce los recursos optimizados en `dist`. En la API, `dotnet restore`, `dotnet build` y `dotnet test` establecen una secuencia reproducible de restauración, compilación y pruebas. En Android, Gradle concentra los controles de construcción y el análisis de calidad. Estas órdenes representan el contrato de ejecución de cada tecnología; su inclusión no equivale a afirmar que todas las tareas estén configuradas actualmente en GitHub Actions.

La integración debe impedir que una modificación en el motor financiero altere silenciosamente los valores de la cuota, el TCEA o el cronograma. Por ello priorizamos las pruebas de regresión relacionadas con las historias US01, US02, US04, US05 y el port validado en SP02. En paralelo, los cambios sobre autenticación y leads requieren verificar los códigos de respuesta definidos para TS07 y TS08 y el rechazo de accesos no autorizados.

Nuestro criterio de aceptación del pipeline consiste en obtener una compilación reproducible, sin defectos bloqueantes conocidos, con las pruebas aplicables superadas y con un registro asociado al commit examinado. Esta verificación es especialmente importante al integrar cambios en `develop` y preparar una rama `release/*`, porque permite detectar problemas antes de trasladarlos a una versión pública.

<div style="page-break-after: always;"></div>

## **7.2. Continuous Delivery**

La entrega continua organiza el paso desde una versión integrada hasta un artefacto que pueda publicarse de forma controlada. En HipoSim distinguimos la disponibilidad de código fuente, la preparación del paquete y la liberación efectiva al usuario. Una compilación exitosa no demuestra por sí misma que el producto funciona en un entorno operativo: también deben verificarse configuración, dependencias, permisos, integridad de datos y comportamiento de las rutas principales.

### **7.2.1. Tools and Practices**

Aplicamos el versionado semántico y las ramas `release/*` para delimitar las versiones candidatas. GitHub conserva la trazabilidad entre los commits, los Pull Requests y las versiones; la construcción se adapta a cada tecnología, y la revisión del producto se organiza mediante las historias y criterios de aceptación registrados en Jira.

La **Landing Page** dispone de una publicación en GitHub Pages y constituye el producto con una URL operativa documentada. En el **portal web**, la entrega debe producir el directorio `dist`, configurado para consumir la API del entorno correspondiente. En la **API**, el artefacto de publicación de .NET depende de una configuración protegida de PostgreSQL y de migraciones de Entity Framework Core. Para **Android**, la construcción debe diferenciar el paquete de desarrollo del paquete firmado destinado a distribución interna o publicación; el informe acredita la existencia del flujo de CI, pero no una distribución productiva mediante tienda o servicio de pruebas.

Nuestro proceso de entrega adopta cuatro controles esenciales. Primero, preservamos la integridad del artefacto respecto del commit de origen. Segundo, separamos las variables de configuración por entorno para impedir que una versión de desarrollo apunte involuntariamente a recursos productivos. Tercero, verificamos permisos, HTTPS y el tratamiento del consentimiento antes de exponer datos personales. Por último, mantenemos un mecanismo de recuperación a una versión estable y un registro de los cambios incluidos en la liberación.

<div style="page-break-after: always;"></div>

### **7.2.2. Stages Deployment Pipeline Components**

El pipeline de entrega se estructura por etapas que introducen controles antes de habilitar una publicación. El mismo criterio se aplica a los distintos productos, aunque el contenido del artefacto y sus verificaciones específicas varían.

| Etapa | Actividad | Condición para continuar |
|---|---|---|
| 1. Integración de cambios | Revisión del Pull Request y fusión de la funcionalidad aprobada | Código trazable y revisión concluida |
| 2. Construcción | Generación de archivos web, aplicación Android o publicación .NET | Artefacto reproducible desde el commit |
| 3. Verificación técnica | Compilación, análisis estático y ejecución de pruebas aplicables | Sin fallas bloqueantes en la suite correspondiente |
| 4. Preparación de configuración | Selección del entorno, variables, credenciales y URL de API | Recursos configurados sin secretos en el repositorio |
| 5. Validación de candidato | Comprobación de simulación, autenticación, consentimiento y accesos | Criterios funcionales y de privacidad satisfechos |
| 6. Aprobación de liberación | Revisión del alcance y etiquetado de versión semántica | Versión candidata autorizada |
| 7. Publicación controlada | Transferencia al servicio web o distribución de compilación móvil | Artefacto identificable y disponible en el destino |
| 8. Comprobación posterior | Verificación de HTTPS, rutas, respuesta del servicio y escenarios críticos | Funcionamiento confirmado en el entorno publicado |

En el sitio estático, la publicación se relaciona con la rama principal y el servicio GitHub Pages; su verificación prioriza enlaces, recursos, formularios, contenidos legales y compatibilidad de visualización. En el portal Vue, validamos la configuración de la URL de la API y el acceso a las rutas pertinentes. Para ASP.NET Core, la publicación debe coordinar la conexión PostgreSQL, las migraciones y las comprobaciones del endpoint `/health` y del contrato OpenAPI. Para Android, la liberación considera la construcción firmada, la compatibilidad con dispositivos y las condiciones de distribución establecidas para la plataforma.

La documentación actual acredita la publicación del Landing Page, pero no identifica un entorno de *staging* ya desplegado para la API o el portal, ni registra aprobaciones de releases productivas de esos componentes. En consecuencia, las etapas anteriores describen nuestro flujo de entrega y sus condiciones de aceptación, mientras que su ejecución integral permanece vinculada a la conclusión de la integración del Sprint 2.

<div style="page-break-after: always;"></div>

## **7.3. Continuous deployment**

El despliegue continuo representa el nivel en el que una versión que ha superado las verificaciones y controles de liberación llega automáticamente a su entorno de operación. Para HipoSim establecemos una política diferenciada por riesgo: los recursos estáticos pueden publicarse con un procedimiento simple y reversible, mientras que los servicios que procesan simulaciones y datos personales requieren comprobaciones adicionales de integridad, autorización y disponibilidad.

### **7.3.1. Tools and Practices**

Nuestro punto de partida operativo es **GitHub Pages**, donde se encuentra publicada la Landing Page de HipoSim. Esta disponibilidad pública demuestra que el sitio puede ser servido por HTTPS a partir del repositorio, pero la documentación no detalla el disparador exacto de publicación ni acredita que cada integración en `main` genere automáticamente un nuevo despliegue sin intervención humana. Por tanto, diferenciamos la publicación existente de una automatización de despliegue continuo plenamente comprobada.

Para el portal web y la API contemplamos la entrega a servicios que permitan gestionar variables de entorno, TLS/HTTPS, registros de aplicación y versiones. La API requiere configuración segura de PostgreSQL, aplicación controlada de migraciones y restricciones CORS conforme al origen de los clientes. No atribuimos estos productos a un proveedor cloud específico porque el Capítulo V no define uno ni proporciona enlaces de despliegue. La aplicación Android tampoco cuenta todavía con una distribución pública documentada: su compilación y sus pruebas se mantienen separadas del proceso de publicación en tiendas.

Como principios de despliegue adoptamos la separación de entornos, el uso de credenciales protegidas, la posibilidad de revertir una versión y las comprobaciones posteriores a la publicación. Los cambios que afectan cálculos hipotecarios o permisos de acceso se consideran de mayor criticidad, ya que un fallo podría presentar importes engañosos o divulgar datos de un comprador sin autorización.

<div style="page-break-after: always;"></div>

### **7.3.2. Production Deployment Pipeline Components**

Definimos los componentes productivos de acuerdo con el comportamiento y las dependencias reales de HipoSim. Para cada producto diferenciamos el mecanismo de publicación, las verificaciones indispensables y su estado dentro de la versión del proyecto documentada.

| Producto | Componente de despliegue | Verificaciones de producción | Estado documentado |
|---|---|---|---|
| Landing Page | Publicación de recursos estáticos en GitHub Pages | HTTPS, navegación, simulación básica, selector ES/EN, política de privacidad y diseño responsivo | Sitio publicado |
| Portal web del asesor | Distribución de `dist` y configuración de la URL de la API | Inicio de sesión, bandeja, ficha, autorización y actualización de leads | Sin despliegue productivo registrado |
| API RESTful | Publicación de ASP.NET Core y configuración de servicios | `/health`, contratos OpenAPI, autenticación, simulación, consentimiento y CORS | Sin despliegue productivo registrado |
| Base de datos | PostgreSQL con migraciones de Entity Framework Core | Conectividad protegida, consistencia de datos, migraciones y control de acceso | Sin infraestructura productiva registrada |
| Android | Paquete firmado y distribución de versión | Compatibilidad, autenticación, simulación y consentimiento | Sin distribución productiva registrada |

La comprobación posterior al despliegue no se limita a que el servicio responda. Para el Landing Page implica que un visitante pueda iniciar y completar una simulación sin una cuenta. Para la API supone obtener resultados financieros consistentes ante entradas válidas, rechazar cuotas iniciales insuficientes y proteger los datos personales. Para el portal del asesor exige la consulta de leads dentro de su ámbito autorizado. En Android requiere que las respuestas se presenten correctamente en la interfaz y que el envío a inmobiliarias no se habilite sin el consentimiento del comprador.

La ruta pública actualmente identificada es **https://auracode-exp-design-1asi0732-2620-9104.github.io/hiposim-LandingPage/**. La ausencia de direcciones productivas de la API y del portal web delimita el estado actual de despliegue: contamos con una publicación pública para el producto estático y con una arquitectura de entrega y producción definida para los productos transaccionales. No presentamos estos últimos como desplegados hasta contar con una versión operativa y verificable.

Nuestra práctica DevOps, por tanto, vincula calidad, colaboración y seguridad con la evolución del producto. La automatización móvil consignada, la publicación del Landing Page, los contratos REST y las reglas de GitFlow establecen la base de trabajo; la integración efectiva y el despliegue verificable de los servicios completarán el recorrido hasta una plataforma donde el comprador pueda simular y compartir voluntariamente sus resultados y el asesor pueda atenderlos sin comprometer su privacidad.
