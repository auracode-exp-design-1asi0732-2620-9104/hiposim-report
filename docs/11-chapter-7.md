# **Capítulo VII: DevOps Practices**

Nuestra estrategia DevOps articula el control de versiones, la compilación, la ejecución de pruebas, la preparación de versiones, su publicación y el monitoreo de los servicios en operación. HipoSim se desarrolla en repositorios separados para el Landing Page, el portal web del asesor, la aplicación Android y la API RESTful, con GitHub como plataforma común de colaboración y Jira como sistema de seguimiento de historias y tareas. El objetivo es reducir errores de integración y conservar la trazabilidad entre los requisitos, los cambios de código y las versiones entregadas.

Organizamos el trabajo con **GitFlow**: `main` representa la línea estable; `develop`, la integración cotidiana; `feature/*`, el desarrollo de funcionalidades; y `hotfix/*`, las correcciones urgentes. Complementamos esta estructura con **Conventional Commits**, revisiones mediante Pull Request y versionado semántico `MAYOR.MENOR.PARCHE`. Diferenciamos tres conceptos: la integración continua comprueba cada cambio, la entrega continua prepara una versión apta para publicarse y el despliegue continuo publica automáticamente una versión aprobada cuando se cumplen las condiciones definidas.

| Producto | Repositorio | Automatización vigente | Publicación |
|---|---|---|---|
| Landing Page | [hiposim-LandingPage](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-LandingPage) | Publicación automática de GitHub Pages desde `main` | [GitHub Pages](https://auracode-exp-design-1asi0732-2620-9104.github.io/hiposim-LandingPage/) |
| Portal web del asesor | [hiposim-webApp](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-webApp) | Flujo `CI` de GitHub Actions: lint, verificación de tipos, pruebas y construcción | [Vercel](https://hiposim-web.vercel.app) |
| Aplicación Android | [hiposim-app-mobile](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-app-mobile) | Flujos `CI` (ktlint, Android lint, pruebas y APK) y `Distribute` (APK firmado a Firebase App Distribution) | Firebase App Distribution, grupo de probadores `equipo-hiposim` |
| API RESTful y PostgreSQL | [hiposim-backEnd](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-backEnd) | Pruebas con `dotnet test`, Blueprint `render.yaml` y flujo `Monitoring` cada 10 minutos | [Render](https://hiposim-api.onrender.com/swagger), con PostgreSQL 18 administrado |

<div style="page-break-after: always;"></div>

## **7.1. Continuous Integration**

La integración continua nos permite revisar cada cambio antes de incorporarlo a una versión compartida. Definimos controles sobre el estilo del código, la construcción de los productos, el comportamiento funcional y el contrato entre componentes, de modo que cada historia de usuario se relaciona con un Pull Request identificable y con los resultados de verificación correspondientes.

### **7.1.1. Tools and Practices**

Utilizamos **Git y GitHub** para el historial del código, las ramas GitFlow y las revisiones colaborativas, y **GitHub Actions** para ejecutar las verificaciones en cada Pull Request. **Jira** conserva la relación entre las tareas y las historias; **Gradle**, la construcción del proyecto Kotlin; **npm y Vite**, las dependencias y el empaquetado del portal Vue; y el **.NET SDK**, la restauración, compilación y pruebas de la API. El contrato de servicios se documenta con **OpenAPI/Swagger** y lo verifican pruebas de conformidad dentro de la propia suite de la API.

Aplicamos los siguientes acuerdos de integración:

1. Desarrollamos cada funcionalidad en una rama `feature/*` creada desde `develop`, vinculada con una historia o tarea de Jira.
2. Registramos los cambios con Conventional Commits, por ejemplo `feat(us06): save the simulation as a named scenario` o `fix(us07): preserve cents in scenario comparisons`.
3. Integramos los cambios mediante Pull Requests y no modificamos `main` directamente; `main` solo recibe la integración de `develop` mediante un Pull Request de versión.
4. No integramos un Pull Request cuyo flujo de CI falle. En la aplicación móvil y en el portal web, el resultado de GitHub Actions aparece en cada Pull Request.
5. Mantenemos la configuración sensible fuera del repositorio: contraseñas, cadenas de conexión, claves de firma y tokens se administran como variables de entorno de Render o como secretos de GitHub Actions.
6. Separamos los datos de demostración de los datos reales. Las aplicaciones tienen una variante de demostración con una API en memoria, que cumple el mismo contrato, para desarrollar y probar sin tocar el servicio desplegado.

<div style="page-break-after: always;"></div>

### **7.1.2. Build & Test Suite Pipeline Components**

Definimos los componentes del pipeline según la tecnología de cada producto, con un criterio común: un cambio no es apto para integrarse si no supera las verificaciones de su alcance.

| Componente del pipeline | Portal Vue (`ci.yml`) | Aplicación Android (`ci.yml`) | API ASP.NET Core |
|---|---|---|---|
| Disparador | `push` y `pull_request` sobre `main` y `develop` | `push` sobre `main` y `develop` y todo `pull_request` | Ejecución local antes de cada Pull Request |
| Preparación del entorno | Node.js 22 con caché de npm | JDK 21 (Temurin) y Gradle | .NET SDK 9 |
| Dependencias | `npm ci` | Resolución de dependencias de Gradle | `dotnet restore` |
| Análisis estático | `npm run lint` y `npm run type-check` | `ktlintCheck` y `lintDebug` | Advertencias del compilador tratadas como defectos |
| Pruebas | `npm test` (unitarias y de componentes) | `testDebugUnitTest` | `dotnet test`: motor financiero, simulaciones y API |
| Construcción | `npm run build-only` | `assembleDebug` | `dotnet publish` dentro de la imagen Docker |
| Resultado ante falla | El Pull Request queda en rojo | El Pull Request queda en rojo y se suben los reportes como artefacto | Se corrige antes de abrir el Pull Request |

Al cierre del Sprint 3, la suite de la aplicación Android tiene **292 pruebas unitarias** y la de la API **303 pruebas** (109 del motor financiero, 118 de simulaciones y reportes, y 76 de los endpoints y del contrato OpenAPI), todas en verde. Además, la API cuenta con escenarios BDD en Gherkin y con un análisis estático documentado en su repositorio (`docs/bdd-and-static-analysis.md`).

Priorizamos las pruebas de regresión que impiden que un cambio altere silenciosamente la cuota, la TCEA o el cronograma. Por ejemplo, los casos de gracia parcial y total (US03) fijan la cuota esperada en el contrato, y las pruebas de conformidad comparan cada respuesta de la API con el esquema OpenAPI. Los cambios sobre autenticación, leads y escenarios verifican también el rechazo de accesos no autorizados (401, 403 y 404).

La API todavía no ejecuta su suite en GitHub Actions: hoy la ejecuta cada integrante antes de abrir el Pull Request. Agregar ese flujo (tarea DO1) queda como mejora para el Sprint 4.

<div style="page-break-after: always;"></div>

## **7.2. Continuous Delivery**

La entrega continua organiza el paso desde una versión integrada hasta un artefacto que se puede publicar de forma controlada. En HipoSim distinguimos la disponibilidad del código fuente, la preparación del paquete y la liberación efectiva al usuario.

### **7.2.1. Tools and Practices**

Usamos el versionado semántico para identificar las versiones y Pull Requests de `develop` a `main` para delimitar cada liberación. Cada producto genera su artefacto de forma reproducible a partir de un commit:

- **Landing Page:** el sitio estático de la rama `main`, servido por GitHub Pages.
- **Portal web:** el directorio `dist` generado por Vite, con la URL de la API definida por la variable `VITE_API_URL` del entorno de Vercel.
- **API:** una imagen Docker construida desde el `Dockerfile` del repositorio. Render la define con el Blueprint `render.yaml`, que declara el servicio web, la base PostgreSQL y las variables de entorno (`DATABASE_URL`, `Database__AutoMigrate`, `Seed__Enabled` y los orígenes CORS).
- **Aplicación Android:** dos variantes de APK firmado. La variante `api` apunta a la API desplegada; la variante `demo` usa la API en memoria. La firma se toma de un archivo de propiedades fuera del repositorio o de los secretos de GitHub Actions, nunca del código.

Aplicamos cuatro controles de entrega:

1. El artefacto se construye desde un commit identificado; el APK, por ejemplo, lleva un `versionCode` creciente.
2. La configuración se separa por entorno, para que una versión de desarrollo no apunte por error al servicio desplegado.
3. Verificamos HTTPS, permisos y consentimiento antes de exponer datos personales.
4. Conservamos la versión anterior para poder volver a ella: Render mantiene los deploys previos y Firebase App Distribution conserva cada versión del APK.

<div style="page-break-after: always;"></div>

### **7.2.2. Stages Deployment Pipeline Components**

| Etapa | Actividad | Condición para continuar |
|---|---|---|
| 1. Integración de cambios | Revisión y merge del Pull Request de la funcionalidad en `develop` | CI en verde y revisión concluida |
| 2. Construcción | APK firmado, directorio `dist` de Vite o imagen Docker de la API | Artefacto reproducible desde el commit |
| 3. Verificación técnica | Análisis estático y suites de pruebas de cada producto | Sin fallas en la suite correspondiente |
| 4. Preparación de configuración | URL de la API, orígenes CORS, cadena de conexión y claves de firma | Secretos fuera del repositorio |
| 5. Validación del candidato | Recorrido de simulación, registro, guardado de escenarios, envío consentido y reporte PDF | Criterios de aceptación de las historias satisfechos |
| 6. Aprobación de la liberación | Pull Request de `develop` a `main` | Alcance revisado por el equipo |
| 7. Publicación | GitHub Pages, Vercel, Render o Firebase App Distribution | Artefacto disponible en su destino |
| 8. Comprobación posterior | `/health`, Swagger, Landing Page y flujo principal en la app | Funcionamiento confirmado en el entorno publicado |

En la aplicación Android, las etapas 2 a 7 están automatizadas en el flujo `distribute.yml`. En cada `push` a `develop`, compila el APK `api` firmado con un `versionCode` igual al número de ejecución más 100 y lo sube a Firebase App Distribution para el grupo `equipo-hiposim`, que recibe un correo con cada versión. El flujo necesita cinco secretos del repositorio (el keystore en Base64, sus dos contraseñas, el alias y la cuenta de servicio de Firebase); mientras no estén cargados, termina con un aviso sin publicar nada. Por eso la versión 0.1.0 (10) del Sprint 3 se firmó y distribuyó manualmente con Firebase CLI.

<div style="page-break-after: always;"></div>

## **7.3. Continuous Deployment**

El despliegue continuo es el nivel en el que una versión que superó las verificaciones llega automáticamente a su entorno de operación. Aplicamos una política diferenciada por riesgo: los recursos estáticos se publican con un procedimiento simple y reversible, mientras que la API, que procesa simulaciones y datos personales, pasa además por la comprobación de su estado después de cada despliegue.

### **7.3.1. Tools and Practices**

- **GitHub Pages** publica el Landing Page en cada merge a `main`.
- **Vercel** publica el portal web del asesor desde su repositorio y expone la versión en `https://hiposim-web.vercel.app`.
- **Render** ejecuta la API a partir del Blueprint `render.yaml`, en un servicio web Docker con plan gratuito y una base PostgreSQL administrada. Al arrancar, la API aplica las migraciones pendientes de Entity Framework Core (`Database__AutoMigrate=true`) y crea la inmobiliaria y el asesor de demostración (`Seed__Enabled=true`). Hoy el despliegue se dispara con **Manual Deploy** sobre el último commit de `main`; conectar el deploy hook de Render al merge en `main` (tarea DO2) queda para el Sprint 4.
- **Firebase App Distribution** publica la aplicación Android para los probadores, sin pasar por una tienda.

Adoptamos como principios la separación de entornos, el uso de credenciales protegidas, la posibilidad de revertir una versión y la comprobación posterior a cada publicación. Los cambios que afectan cálculos hipotecarios o permisos de acceso se consideran de mayor criticidad, porque un fallo podría mostrar importes engañosos o divulgar datos de un comprador sin autorización.

<div style="page-break-after: always;"></div>

### **7.3.2. Production Deployment Pipeline Components**

| Producto | Componente de despliegue | Verificaciones de producción | Estado |
|---|---|---|---|
| Landing Page | GitHub Pages desde `main` | HTTPS, simulación sin cuenta, selector ES/EN, formulario de contacto y eventos de uso | Publicado |
| Portal web del asesor | Vercel, con la URL de la API como variable de entorno | Inicio de sesión del asesor, bandeja y ficha de leads, estados y notas | Publicado |
| API RESTful | Imagen Docker en Render desde `main` | `/health`, Swagger, autenticación, simulación, escenarios, reporte PDF, eventos y CORS | Publicada |
| Base de datos | PostgreSQL 18 administrado por Render, con migraciones de EF Core | Conexión interna, migraciones aplicadas y datos semilla | Operativa |
| Aplicación Android | APK firmado en Firebase App Distribution | Registro, simulación con gracia, guardado y comparación de escenarios, PDF y envío consentido | Distribuida, versión 0.1.0 (10) |

La comprobación posterior al despliegue no se limita a que el servicio responda: para la API supone obtener resultados financieros consistentes ante entradas válidas (por ejemplo, la cuota de S/ 1 959,21 con gracia total de 3 meses en el caso de referencia del contrato), rechazar accesos sin sesión y aceptar eventos de uso anónimos.

<div style="page-break-after: always;"></div>

## **7.4. Continuous Monitoring**

El monitoreo continuo nos permite saber si los productos publicados siguen disponibles sin esperar a que un usuario reporte el problema. En esta entrega lo concentramos en la disponibilidad de la API y del Landing Page, que son los puntos de entrada de los compradores y la fuente de los datos de los experimentos del Capítulo VIII.

### **7.4.1. Tools and Practices**

- **GitHub Actions (`monitoring.yml`, tarea DO4):** un flujo programado en el repositorio de la API que cada 10 minutos consulta `/health` y la página principal del Landing Page.
- **Render:** registra los eventos del servicio (deploys, instancias que fallan y recuperaciones), los logs de la aplicación y envía correos de alerta ante fallas del servidor.
- **Endpoint `/health`:** responde `{"status":"Healthy"}` cuando la API está operativa.
- **Eventos de uso (`POST /api/events`):** el Landing Page y la aplicación móvil registran eventos anónimos en la tabla `usage_events`. Esos eventos alimentan las métricas de los experimentos y muestran si los productos se usan después de cada versión.

### **7.4.2. Monitoring Pipeline Components**

| Componente | Qué observa | Frecuencia | Criterio de éxito |
|---|---|---|---|
| Paso `API health` | `GET https://hiposim-api.onrender.com/health` | Cada 10 minutos | HTTP 200 y cuerpo con `Healthy`, con hasta 3 reintentos de 15 segundos para tolerar el arranque del plan gratuito |
| Paso `Landing Page` | Página principal en GitHub Pages | Cada 10 minutos | HTTP 200, con hasta 2 reintentos |
| Paso `Summary` | Resultado y tiempo de respuesta de ambos | En cada ejecución | Tabla en el resumen de la ejecución de GitHub Actions |
| Eventos de Render | Instancias fallidas, deploys y recuperaciones | Continuo | Ninguna instancia en estado fallido después del último deploy |
| Logs de la aplicación | Consultas a la base de datos y errores de ASP.NET Core | Continuo | Sin excepciones no controladas |

Como efecto secundario, la consulta cada 10 minutos evita que Render suspenda la API por inactividad, ya que el plan gratuito la duerme tras 15 minutos sin solicitudes.

### **7.4.3. Alerting Pipeline Components**

| Condición | Origen | Alerta |
|---|---|---|
| `/health` no responde 200 con `Healthy` | Flujo `Monitoring` | La ejecución termina en estado fallido |
| El Landing Page no responde 200 | Flujo `Monitoring` | La ejecución termina en estado fallido |
| Una instancia de la API termina inesperadamente | Render | Evento "Instance failed" y correo "Server failure detected" |
| Falla un deploy | Render | Evento "Deploy failed" en el panel del servicio |

**Incidente registrado.** El 14 de noviembre de 2026, la base PostgreSQL gratuita de Render caducó a los 30 días de su creación y quedó suspendida. Las instancias de la API se reiniciaron en bucle (código de salida 139) y Render envió las alertas por correo. Lo resolvimos creando una base nueva, actualizando `DATABASE_URL` en el servicio y volviendo a desplegar; las migraciones y los datos semilla se aplicaron solos al arrancar. Desde ese despliegue, la instancia en servicio no registra fallas. Como acción preventiva, anotamos la fecha de caducidad de la base gratuita para recrearla antes de las siguientes entregas.

### **7.4.4. Notification Pipeline Components**

| Canal | Destinatarios | Contenido |
|---|---|---|
| Notificaciones de GitHub Actions | Integrantes que siguen el repositorio de la API | Aviso de ejecución fallida del flujo `Monitoring`, con el enlace al resumen |
| Correo de Render | Propietario del servicio | Instancia fallida, código de salida y enlace a los logs |
| Correo de Firebase App Distribution | Grupo `equipo-hiposim` | Disponibilidad de una nueva versión del APK y sus notas |
| Grupo del equipo | Todo el equipo | Coordinación de la respuesta: quién revisa los logs y quién despliega la corrección |

Nuestra práctica DevOps vincula calidad, colaboración y seguridad con la evolución del producto. Los cuatro productos están publicados, la integración continua cubre la aplicación móvil y el portal web, y el monitoreo detecta caídas de la API y del Landing Page. Para el Sprint 4 quedan como mejoras la integración continua de la API en GitHub Actions (DO1), el despliegue automático en Render al integrar en `main` (DO2) y la carga de los secretos que activan la distribución automática del APK.
