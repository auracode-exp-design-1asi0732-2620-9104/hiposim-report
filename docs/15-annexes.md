# **Annexes**

## **Annex A. Repositorios y publicación de productos digitales**

| Producto | Recurso | Vinculación con el informe |
|---|---|---|
| Landing Page | [Repositorio de código fuente](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-LandingPage) | 5.1.2 y 5.2.2; presentación del servicio, simulador básico, beneficios, FAQ e internacionalización |
| Landing Page | [Sitio publicado en GitHub Pages](https://auracode-exp-design-1asi0732-2620-9104.github.io/hiposim-LandingPage/) | 5.1.4 y 5.2.2; publicación web con acceso HTTPS |
| Aplicación web del asesor | [Repositorio hiposim-webApp](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-webApp) | 5.2.3; autenticación, bandeja, ficha y seguimiento de leads |
| Aplicación móvil Android | [Repositorio hiposim-app-mobile](https://github.com/auracode-exp-design-1asi0732-2620-9104/hiposim-app-mobile) | 5.2.4; registro contextual, simulación y resultados móviles |


## **Annex B. Registro audiovisual de entrevistas de investigación**

<p style="text-align: justify;">
  Las entrevistas de la sección 2.2.2 constituyen la evidencia primaria del proceso de Needfinding. Se organizan por segmento para conservar la correspondencia entre los testimonios, el análisis de necesidades y las decisiones de diseño. Los enlaces corresponden a los registrados en el informe del proyecto.
</p>

### Segmento 1. Comprador de primera vivienda

| Entrevista | Participante | Duración | Evidencia audiovisual |
|---|---|---|---|
| 1 | Vitaly Baca Arturo | 08:13 | [Ver entrevista](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202315890_upc_edu_pe/IQAF5AyST2rQSp1Vf_9zuk_9AaycEdJysPCj3KbCrMCFYoU?e=wSeJ4W) |
| 2 | Alberto Román | 06:13 | [Ver entrevista](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202315890_upc_edu_pe/IQAdCnl85yvhSrk9QQ9Lem4JAZkundmLCncxIt0ueEJ-jlw?e=UDoIg6) |
| 3 | Jack Daga | 09:49 | [Ver entrevista](https://drive.google.com/file/d/1pg9zZ18wrHPP4SKXrtPEQ-oGWhUn8r4F/view?usp=share_link) |

### Segmento 2. Inmobiliarias

| Entrevista | Participante | Duración | Evidencia audiovisual |
|---|---|---|---|
| 1 | Juliana Paucan Alburqueque | 25:05 | [Ver entrevista](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202315890_upc_edu_pe/IQC7z6bBUthnRZMrOohhLHtrATYp7gnwS0OgZz87q1-F__k?e=weynr2) |
| 2 | Ricardo Huamán Torres | 15:17 | [Ver entrevista](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202315890_upc_edu_pe/IQC3XxibKa8FRYeFW8RdpwIJAbsCVOepUYkQBw9wABSRVFg?e=GWH2fC) |
| 3 | Jakelin Gutiérrez Flores | 06:07 | [Ver entrevista](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202323319_upc_edu_pe/IQBxlDKkWL6ZRb-3Xr0whyq-Aa-yvKwN0Denn3JxVq112X0?e=UdOlvc) |

<p style="text-align: justify;">
  En el segmento comprador, las entrevistas aportan información sobre comparación de bancos, comprensión de la TCEA, beneficios estatales y necesidad de guardar simulaciones. En el segmento inmobiliario, abordan la calificación inicial de interesados, el uso de WhatsApp o registros manuales, la gestión del seguimiento y el valor de recibir leads con consentimiento. Estos hallazgos son cualitativos y no se presentan como estimaciones representativas de toda la población.
</p>

<div style="page-break-after: always;"></div>

## **Annex C. Trazabilidad entre requisitos, componentes y verificación**

| Identificador | Funcionalidad o componente | Producto involucrado | Relación documental |
|---|---|---|---|
| US01 / TS06 | Simulación de crédito y validación de cuota inicial mínima | Android / API | 3.2; 5.2.4–5.2.6; 6.1.1–6.1.4 |
| US02 | Cronograma mensual de amortización | Android / API | 3.2; 5.2.4–5.2.6; 6.1.1 y 6.1.4 |
| US04 | Visualización de TCEA, VAN y TIR | Android / API | 3.2; 5.2.4–5.2.6; 6.1.1 y 6.1.4 |
| US05 | Aplicación del Bono del Buen Pagador | Android / API | 3.2; 5.2.4–5.2.6; 6.1.1 y 6.1.3 |
| US13 / US26 / TS07 | Registro, inicio de sesión y autorización | Android / API | 3.2; 5.2.4–5.2.6; 6.1.2 y 6.1.3 |
| US21 / TS08 | Envío de simulación a inmobiliaria con consentimiento | Android / API | 3.2; 5.2.4–5.2.6; 6.1.2–6.1.4 |
| US22–US25 | Autenticación y seguimiento de leads | Web del asesor / API | 3.2; 5.2.3–5.2.6; 6.1.2–6.1.4 |
| TS05 | Documentación REST mediante OpenAPI y Swagger | API | 5.2.6; 6.1.2 |
| TS04 / US14–US20 | Sitio institucional y simulador básico | Landing Page | 5.2.2; 6.1.4; 7.3.2 |

<div style="page-break-after: always;"></div>

## **Annex D. Contrato de referencia para la simulación hipotecaria**

<p style="text-align: justify;">
  El Capítulo V define el recurso <code>POST /api/simulations</code> como entrada principal al motor financiero. La siguiente solicitud reproduce el escenario representativo del contrato documentado y permite identificar las reglas de entrada que deben mantenerse consistentes entre clientes. Los importes y tasas pertenecen al caso ilustrativo del proyecto, no a una cotización bancaria vigente.
</p>

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

| Parámetro o comprobación | Valor del caso | Interpretación |
|---|---:|---|
| Valor de vivienda | S/ 280 000,00 | Precio de la propiedad evaluada |
| Cuota inicial | S/ 42 000,00 | Corresponde al 15 % del valor de vivienda |
| Capital antes del beneficio | S/ 238 000,00 | Vivienda menos cuota inicial |
| TEA enviada a la API | 8,5 % | Tasa de entrada consignada en el ejemplo del Capítulo V |
| Plazo | 240 meses | Financiamiento de 20 años |
| Bono ilustrativo mencionado en la respuesta | S/ 18 200,00 | Monto de ejemplo del contrato, sujeto a elegibilidad y parámetros vigentes |
| Capital con beneficio ilustrativo | S/ 219 800,00 | Capital inicial menos el bono de ejemplo |

<p style="text-align: justify;">
  El contrato de referencia utiliza una TEA de 8,5 %, mientras que el simulador de la Landing Page presenta una tasa referencial de 8,85 % en la versión documentada. La homologación de tasas, seguros, cargos y criterios de redondeo es necesaria antes de comparar directamente las cuotas entre productos. La TCEA se diferencia de la TEA porque incorpora los costos aplicables al crédito; no debe mostrarse como sinónimo de la tasa base.
</p>

<div style="page-break-after: always;"></div>

## **Annex E. Inventario de servicios REST del flujo principal**

| Método | Recurso | Propósito funcional | Referencia |
|---|---|---|---|
| `POST` | `/api/auth/register` | Registrar al comprador | US13, TS07 |
| `POST` | `/api/auth/login` | Autenticar comprador o asesor | US22, US26, TS07 |
| `POST` | `/api/simulations` | Calcular simulación y resultados | US01, US04, US05, TS06 |
| `GET` | `/api/simulations/{id}` | Recuperar el detalle de una simulación autorizada | US02, US06 |
| `POST` | `/api/leads` | Compartir la simulación con consentimiento | US21, TS08 |
| `GET` | `/api/leads` | Consultar los leads de la inmobiliaria | US23, TS08 |
| `GET` | `/api/leads/{id}` | Consultar la ficha de un lead | US24 |
| `PATCH` | `/api/leads/{id}/status` | Actualizar el estado del seguimiento | US25, TS08 |
| `POST` | `/api/leads/{id}/notes` | Registrar notas sobre el contacto | US25 |
| `GET` | `/health` | Consultar el estado operativo del servicio | TS02 |


## **Annex F. Estado de las evidencias de calidad y despliegue**

| Área | Evidencia consignada en el informe | Alcance verificable |
|---|---|---|
| Landing Page | Repositorio y URL pública en GitHub Pages | Publicación del sitio estático |
| Aplicación Android | 35 pruebas unitarias y 4 pruebas de interfaz en emulador | Pruebas registradas para el producto móvil |
| Integración continua Android | Flujo de GitHub Actions, ktlint y Android Lint | Automatización documentada para Android |
| Aplicación web del asesor | Pantallas con datos de ejemplo y repositorio propio | Implementación de interfaz; integración real descrita como objetivo del Sprint 2 |
| API RESTful y PostgreSQL | Componentes, diseño de endpoints y estrategia de despliegue | Contrato y arquitectura, sin reporte completo de ejecución o URL productiva en el informe |
| Entrega y despliegue continuo | Etapas, controles y criterios de liberación del Capítulo VII | Proceso definido; no equivale a operación productiva automatizada de toda la plataforma |
