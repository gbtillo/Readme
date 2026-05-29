# 📑 TRANSFORMACIÓN OPERATIVA

## Implementación del Marco Metodológico Unificado (Agile-Scrum-Lean) y Ecosistema Atlassian
---

## 1. El Enfoque Estratégico: La Triada Metodológica

Para evitar el dogmatismo y maximizar la entrega de valor, la organización operará bajo un modelo híbrido unificado, donde cada marco cumple una función específica dentro del flujo de valor:

* **Agile (El Mindset):** Foco absoluto en la colaboración multidisciplinaria y la orientación a resultados de negocio sobre procesos rígidos.
* **Scrum (La Estructura):** Proporciona el ritmo y la cadencia operativa mediante Sprints de 2 semanas, roles claros (PO, SM, Dev) y ceremonias de sincronización.
* **Lean (El Optimisor):** Enfocado en la eliminación sistemática de desperdicios (*Muda*), gestión de cuellos de botella mediante Límites WIP y aceleración del *Time-to-Market*.

```
       [ FILOSOFÍA AGILE: Orientación a Valor ]
                         │
        ┌────────────────┴────────────────┐
        ▼                                 ▼
[ RITMO DE SCRUM ]                [ OPTIMIZACIÓN LEAN ]
Sprints, Roles y Ceremonias       Límites WIP y Flujo Continuo

```

---

## 2. Fase 0: Diagnóstico de Adopción desde Cero (Greenfield)

El punto de partida asume la inexistencia de herramientas centralizadas. El diagnóstico inicial se centrará en levantar la fricción y mapear los prerrequisitos técnicos de infraestructura.

### A. Matriz de Brecha y Captura de Dolores

Se implementarán entrevistas cualitativas basadas en el "dolor del usuario" para traducir frustraciones operativas directas en requerimientos de configuración en Jira Software.

### B. Prerrequisitos de Arquitectura e Infraestructura (Cimientos Técnicos)

Antes del aprovisionamiento de licencias Cloud, se validarán de forma estricta los siguientes puntos:

* Sincronización automatizada de usuarios (SCIM) a través de **Atlassian Access** con el proveedor corporativo de identidad (SSO).
* Mapeo de políticas de **Data Residency** para el cumplimiento de normativas locales de retención de datos.
* Accesos de administrador a repositorios de código vigentes (GitHub, GitLab, Azure DevOps) para el diseño de webhooks.

---

## 3. Blueprint Técnico: Configuración del Ecosistema

### A. Workflow Lean-Agile Unificado en Jira

Diseñado para reflejar el estado real del código y evitar el desperdicio administrativo de actualización manual.

```
[Backlog] ➔ [Selected for Dev] ➔ [In Progress (WIP Max: 3)] ➔ [Code Review] ➔ [QA Testing (WIP Max: 2)] ➔ [UAT] ➔ [Done]

```

* **Trigger Automatizado:** La apertura de un *Pull Request* en el repositorio transiciona automáticamente el ticket de `In Progress` a `Code Review`.
* **Alerta Kaizen:** Notificación automática y bloqueo visual si un ticket permanece más de 3 días estancado en un mismo estado.

### B. Arquitectura de Confluence (Base de Conocimiento Viva)

Estructura global de tres espacios core para centralizar el *know-how* organizacional y erradicar los silos de información:

```
[Espacio PROD: Producto]    ➔ Lean Canvas, Roadmaps y Especificaciones de Negocio.
[Espacio ENG: Ingeniería]   ➔ Diagramas de Arquitectura y ADRs (Architecture Decision Records).
[Espacio OPS: Operaciones]  ➔ Runbooks de Despliegue y Post-Mortems de Incidentes.

```

---

## 4. Gestión del Cambio y Piloto Controlado

### A. Estrategia Lean Change Management

El cambio cultural se abordará mediante **Cambios Mínimos Viables (MVCs)** evaluados en un equipo piloto transversal durante un período cerrado de 3 Sprints (6 semanas).

```
[Sprint 1: Estabilización Scrum]  ➔ Planificación y Daily guiadas 100% sobre Jira.
[Sprint 2: Optimización Lean]      ➔ Activación de Límites WIP y control de cuellos de botella.
[Sprint 3: Integración DevOps]     ➔ Automatización completa desde Git hasta QA.

```

### B. Matriz de Capacitación Orientada al Rol

* **Product Owners:** Foco en gestión y priorización del Backlog en Jira y Lean Canvas en Confluence.
* **Scrum Masters / PMs:** Foco en analítica de tableros, bloqueos y diagramas de flujo acumulado.
* **Equipos Técnicos (Dev/QA):** Foco en actualización automatizada del tablero e ingeniería de calidad.

---

## 5. Ecosistema de Dashboards y Analítica Avanzada

Se eliminan los reportes manuales en hojas de cálculo. La reportabilidad será en tiempo real y segmentada según el perfil del consumidor:

### Cuadro de Mando Integral (Métricas Core)

| Categoría | Métrica Clave | Objetivo Ejecutivo | Fuente de Datos |
| --- | --- | --- | --- |
| **Negocio / Lean** | **Lead Time** | Reducir el tiempo total desde la idea hasta producción. | Jira Software (Control Chart) |
| **DORA (DevOps)** | **Deployment Frequency** | Incrementar la cadencia de lanzamientos al mercado. | Integración Jira + CI/CD |
| **DORA (DevOps)** | **Change Failure Rate** | Mantener la tasa de fallos en producción por debajo del 10%. | Jira Software (Bugs en Producción) |
| **DORA (DevOps)** | **Mean Time to Recovery** | Resolver incidentes críticos en producción en menos de 1 hora. | Jira Service Management / Ops |

---

## 6. Gamificación, Modelo de Madurez y Éxito del Programa

### A. Gamificación Colaborativa

Implementación de medallas digitales colectivas (*The Continuous Delivery Clan*, *Defensor del Flujo*) configuradas en Jira para premiar los comportamientos saludables del equipo (mantener Jira al día, documentar en Confluence) sin generar competitividad tóxica.

### B. Criterios de Aceptación para el Cierre de la Transformación

El programa se considerará formalmente exitoso cuando cumpla con los siguientes tres pilares en producción:

> 🟩 **1. Cobertura del Portafolio:** El 100% de los proyectos tecnológicos gestionados centralizadamente en Jira y Confluence.
> 🟩 **2. Eficiencia Operativa:** Reducción comprobada de al menos el 20% del *Cycle Time* promedio en los equipos piloto.
> 🟩 **3. Automatización de Procesos:** El 80% de las transiciones de estados técnicos ejecutadas por triggers automáticos del repositorio de código, eliminando la carga administrativa manual del desarrollador.

---
