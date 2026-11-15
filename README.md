# Sistema de Gestión del Taller Automotriz Automatizado

Sistema de gestión y automatización para un taller de **automóviles y motocicletas**. Cubre el ciclo completo de atención: desde que el cliente pide una cita hasta que recibe su factura electrónica validada por la DIAN, con los pasos intermedios automatizados mediante eventos de dominio.

> **Este repositorio contiene el diseño.** El código del backend vive en **[BACKEND-TALLER-AUTOMOTRIZ](https://github.com/camilin0811/BACKEND-TALLER-AUTOMOTRIZ)**.

**Autor:** Andrés Camilo Muñoz Bolaños

---

## Dónde está cada cosa

| | Dónde | Qué encontrarás |
|---|---|---|
| 📐 **Diseño** | [Wiki](https://github.com/camilin0811/TALLER-AUTOMOTRIZ/wiki) | 12 páginas: arquitectura, dominio, API, datos, decisiones y pruebas |
| 📋 **Historias de usuario** | [Issues](https://github.com/camilin0811/TALLER-AUTOMOTRIZ/issues) | Las 20 historias, cada una con su mockup y criterios de aceptación |
| 💻 **Código** | [BACKEND-TALLER-AUTOMOTRIZ](https://github.com/camilin0811/BACKEND-TALLER-AUTOMOTRIZ) | Java 21 · Spring Boot · MongoDB · arquitectura hexagonal |

---

## El problema

Un taller que opera con planillas y llamadas pierde dinero en tres puntos concretos:

| Punto de fuga | Qué ocurre hoy | Qué hace el sistema |
|---|---|---|
| **Aprobación de cotizaciones** | El asesor llama al cliente varias veces; el vehículo espera en bahía sin avanzar | La cotización se envía por WhatsApp y la respuesta del cliente entra como webhook |
| **Control de repuestos** | El stock se descubre agotado cuando el mecánico lo necesita | El consumo descuenta inventario y dispara reposición al llegar al mínimo |
| **Facturación** | Se factura en lote al final del día, con errores de transcripción | El cierre de la orden emite la factura y la envía a validación DIAN |

## Las cinco vistas de arquitectura

| Vista | Pregunta que responde | Notación |
|---|---|---|
| [Contexto](https://github.com/camilin0811/TALLER-AUTOMOTRIZ/wiki/02-Arquitectura#1-vista-de-contexto) | ¿Con quién habla el sistema y qué datos intercambia? | DFD Yourdon-DeMarco |
| [Funcional](https://github.com/camilin0811/TALLER-AUTOMOTRIZ/wiki/02-Arquitectura#2-vista-funcional) | ¿De qué piezas se compone? | Componentes UML |
| [Lógica](https://github.com/camilin0811/TALLER-AUTOMOTRIZ/wiki/02-Arquitectura#3-vista-lógica) | ¿Qué conceptos del negocio existen? | Clases de dominio |
| [Desarrollo](https://github.com/camilin0811/TALLER-AUTOMOTRIZ/wiki/02-Arquitectura#4-vista-de-desarrollo) | ¿Cómo se organiza el código? | Clases de implementación |
| [Despliegue](https://github.com/camilin0811/TALLER-AUTOMOTRIZ/wiki/02-Arquitectura#5-vista-de-despliegue) | ¿Dónde se ejecuta cada artefacto? | Despliegue UML |

Los archivos fuente de Visual Paradigm (`.vpp`) están fuera del control de versiones; las imágenes exportadas están en la wiki.

## Decisiones de un vistazo

| Dimensión | Decisión |
|---|---|
| Backend | Java 21 · Spring Boot · arquitectura hexagonal |
| Persistencia | MongoDB Atlas (servicio administrado) |
| Alcance operativo | Un solo taller, sin sucursales |
| País | Colombia · facturación electrónica DIAN con proveedor tecnológico autorizado |
| Integración con el cliente | WhatsApp bidireccional (envío y recepción de webhooks) |
| Diagnóstico | Escáner OBD-II conectado por un gateway IoT local |

El razonamiento de cada una, con las alternativas descartadas, está en los [10 ADR](https://github.com/camilin0811/TALLER-AUTOMOTRIZ/wiki/09-Decisiones-de-Arquitectura).

## Estado

| Entregable | Estado |
|---|---|
| Diagramas UML (5 vistas) | Completo |
| Wiki de diseño (12 páginas) | Completo |
| Historias de usuario (20) | Completo, con mockups y criterios Gherkin |
| Backend · dominio y aplicación | Completo · 193 pruebas · 96,6 % de cobertura del dominio |
| Backend · API REST | Completo y probado contra MongoDB Atlas |
| Backend · autenticación | **Pendiente** |
| Pruebas de integración y aceptación | **Pendientes** |
| Frontend | **Pendiente** |
