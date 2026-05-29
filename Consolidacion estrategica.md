## 📋 Paso 1 : Kit de Diagnóstico (Adopción inicial)

* **Matriz de Brecha Operativa (Gap Analysis):** Medirá la distancia entre cómo operan hoy (procesos manuales, acuerdos de palabra, hilos de correo) y el estado ideal en Jira/Confluence.
* **Inventario de Dispersión de Información:** Una plantilla para mapear dónde vive la información hoy (los "Excels infinitos", tableros de Trello personales, grupos de WhatsApp, minutas en Word locales) para planificar la migración y centralización.
* **Guía de Entrevistas de "Dolor de Usuario":** Enfocada en descubrir las frustraciones del día a día (ej. *"Pierdo dos horas buscando el último requerimiento"*, *"No sé en qué está trabajando el equipo de QA"*). Usaremos estos dolores para demostrarle al equipo el valor de Jira desde el día uno.
* **Checklist de Prerrequisitos Técnicos y de Infraestructura:** Validación de los cimientos para la instalación (existencia de proveedores de identidad/SSO como Active Directory, volumen estimado de usuarios para el licenciamiento, y estado de los repositorios de código actuales como GitHub/Azure DevOps para futuras integraciones).

---

---

# PARTE 1: Herramientas de Diagnóstico (Fase 0)

Para pasar de un levantamiento cualitativo a datos duros que la gerencia pueda entender, estructuraremos las herramientas con criterios de cuantificación numérica y plantillas técnicas de recopilación.

### 1.1 Modelo de Puntuación para la Matriz de Brecha Operativa

Para medir el estado actual antes de instalar Jira/Confluence, utilizaremos una escala de **Nivel de Fricción Operativa (1 al 5)**, donde 1 es "Flujo Automatizado" y 5 es "Bloqueo Total/Caos".

| Proceso Crítico | Criterio de Evaluación Actual | Indicador de Fricción (1-5) | Impacto Financiero / Operativo |
| --- | --- | --- | --- |
| **Pase a Producción (Deployment)** | ¿Cómo se entera Operaciones de lo que hay que desplegar? Si es por un Word/Excel enviado por correo a última hora, la fricción es máxima. | **5** (Crítico) | Riesgo de caídas en producción por falta de documentación clara (*Runbooks*) y trazabilidad del código. |
| **Control de Calidad (QA)** | ¿Dónde se registran los bugs encontrados? Si se envían capturas por Teams o WhatsApp sin un formato estándar. | **4** (Alto) | Fuga de defectos a producción (*Defect Leakage*) y discusiones sobre si un bug fue reportado o no. |
| **Priorización de Negocio** | ¿Cómo decide el equipo técnico qué desarrollar mañana? Si depende del último correo de la gerencia o del stakeholder que grite más fuerte. | **4** (Alto) | Desalineación estratégica. El equipo trabaja en tareas de bajo valor percibido por el negocio. |

---

### 1.2 Plantilla Técnica: Inventario de Dispersión de Información

Este formato extendido permite planificar la migración de datos hacia Confluence y la creación de campos personalizados en Jira.

* **Campo "Criticidad de Migración":** **Alta** (No se puede iniciar el día uno sin esto), **Media** (Puede migrarse durante el piloto), **Baja** (Se archiva o se limpia).

```markdown
[ÁREA: Arquitectura y Desarrollo]
- Artefacto: Registro de Decisiones de Arquitectura (ADRs)
  - Ubicación actual: Notas personales en OneNote del Tech Lead.
  - Formato: Texto plano sin estructura.
  - Criticidad de Migración: Alta.
  - Acción en Ecosistema: Crear Espacio "ARQ" en Confluence y configurar la plantilla nativa de ADR.

[ÁREA: Product Owners / Negocio]
- Artefacto: Roadmap de Lanzamientos Anuales
  - Ubicación actual: Archivo PowerPoint en OneDrive compartido con permisos mixtos.
  - Formato: Línea de tiempo visual estática.
  - Criticidad de Migración: Media.
  - Acción en Ecosistema: Implementar "Jira Product Discovery" o "Advanced Roadmaps" conectado a las Épicas.

```

---

### 1.3 Matriz de Síntesis de "Dolores de Usuario"

Las respuestas de las entrevistas se procesan mediante esta plantilla para traducirlas directamente en requerimientos de configuración de las herramientas:

> 🗣️ **Frustración Detectada:** *"El negocio me cambia las prioridades a mitad de semana y mi equipo pierde el enfoque."* (Reportado por: Tech Lead).
> * **Causa Raíz:** Falta de un contenedor formal de requerimientos y un proceso de aprobación.
> * **Solución en el Ecosistema:** Configurar un flujo de *Backlog Refinement* en Jira. Implementar el estado **"Ready for Development"** con restricciones de transición: nadie puede mover un ticket ahí sin la aprobación del Product Owner.
> 
> 

---

### 1.4 Checklist Avanzado de Prerrequisitos Técnicos

Antes de adquirir las licencias Cloud, el equipo de Infraestructura y Seguridad debe validar estos tres bloques técnicos de manera estricta:

* [ ] **Políticas de Retención de Datos y Cumplimiento (Compliance):** Determinar si por regulaciones locales o de auditoría la organización requiere que los datos residan en una región geográfica específica (Data Residency en Jira Cloud Premium).
* [ ] **Mapeo de Herramientas Legadas para Integración Técnica:** Identificar las herramientas activas que deberán conectarse mediante API o Webhooks a Jira (ej. SonarQube para calidad de código, Service Desk actual para escalamiento de incidentes).
* [ ] **Estrategia de User Provisioning:** Confirmar si el Directorio Activo permite la sincronización automática de usuarios (SCIM) a través de Atlassian Access para automatizar altas y bajas de personal.

---

---

## 📊 Herramienta 2: Inventario de Dispersión de Información

El objetivo de este inventario es mapear todos los "silos" de datos actuales. Esto servirá para estructurar la migración de contenido hacia Confluence y la creación de tipos de tiquetes en Jira.

* **Instrucciones de aplicación:** El equipo consultor o líder de la iniciativa debe auditar a cada área funcional y completar este registro.

| Tipo de Artefacto / Documento | ¿Dónde vive hoy? (Herramienta actual) | ¿Quién lo actualiza? | Destino Final en el Ecosistema |
| --- | --- | --- | --- |
| Requerimientos / Historias de Usuario | Word locales, correos o minutas de Teams. | Product Owner / Analista | **Jira**: Product Backlog (Epics / User Stories). |
| Documentación de Arquitectura (ADRs) | No se documenta formalmente o está en blocs de notas. | Arquitecto de Software / Tech Lead | **Confluence**: Espacio de Arquitectura (Plantilla ADR). |
| Plan de Proyecto / Cronograma | Microsoft Project o Excel compartido. | Project Manager | **Jira**: Advanced Roadmaps / Tableros de Portafolio. |
| Casos de Prueba / Evidencia de QA | Hojas de cálculo de Excel. | QA Lead / Tester | **Jira**: Integración con herramienta de QA o workflows específicos. |
| Manuales Operativos y Runbooks | PDFs en carpetas de red de acceso restringido. | Infraestructura / Soporte | **Confluence**: Espacio de Operaciones (Runbooks estandarizados). |

---

## 🗣️ Herramienta 3: Guía de Entrevistas de "Dolor de Usuario"

Para mitigar la resistencia al cambio, las entrevistas no deben sonar como una auditoría de control, sino como una sesión de escucha activa. El enfoque es: *"Dime qué te duele hoy, para asegurarme de que Jira/Confluence te lo resuelva mañana"*.

### Cuestionario por Roles Clave

> 💡 **Para Líderes de Negocio y Product Owners:**
> 1. ¿Cómo te aseguras hoy de que el equipo de desarrollo está trabajando en tu prioridad número uno?
> 2. ¿Qué tan fácil es para ti saber la fecha estimada de entrega de una nueva funcionalidad sin tener que programar una reunión?
> 3. ¿Cuáles son los principales malentendidos que ocurren cuando transmites un requerimiento al equipo técnico?
> 
> 

> 💻 **Para Tech Leads y Desarrolladores:**
> 1. ¿Cuánto tiempo a la semana pierdes buscando la última versión de un requerimiento o esperando aprobaciones?
> 2. Cuando ocurre un error en producción, ¿qué tan fácil es rastrear qué se cambió, quién lo aprobó y por qué?
> 3. ¿Qué procesos administrativos (reportar horas, actualizar estados) te generan más frustración en tu día a día?
> 
> 

> 🚀 **Para Project Managers y Operaciones:**
> 1. ¿Cómo identificas actualmente que un proyecto está bloqueado por dependencias de otra área (ej. Seguridad o Infraestructura)?
> 2. ¿Cuánto tiempo te toma consolidar el estado de avance del portafolio para la gerencia ejecutiva?
> 
> 

---

## 🔒 Herramienta 4: Checklist de Prerrequisitos Técnicos de Infraestructura

Al implementar desde cero, debemos asegurar que los cimientos técnicos estén listos para evitar retrasos en el aprovisionamiento de las herramientas.

* [ ] **Gestión de Identidades (Identity Management / SSO):**
* Definir si se utilizará el proveedor corporativo (ej. Azure Active Directory / Entra ID) para el aprovisionamiento de usuarios de Jira/Confluence.
* Mapear los grupos de seguridad actuales que heredarán los permisos de administración.


* [ ] **Dimensionamiento de Licenciamiento (Tiering):**
* Censo preliminar de usuarios activos desglosado por roles: Usuarios con permisos de edición completa (Jira Software), usuarios solo de lectura/documentación (Confluence) y stakeholders externos.


* [ ] **Ecosistema de Código Actual:**
* Identificar las plataformas de repositorios vigentes (ej. Azure DevOps, GitHub, GitLab) y verificar si se cuenta con accesos de administrador para configurar los webhooks y las integraciones nativas de desarrollo con Jira.


* [ ] **Políticas de Seguridad e Información:**
* Validar restricciones de red (VPN, IPs permitidas) si la organización requiere un esquema de acceso controlado para herramientas Cloud.




---

# PARTE 2: Diseño del Framework Metodológico (Fase 1)

Con la radiografía del estado actual clara, diseñamos el **Modelo Operativo Híbrido** de la organización. Este framework establece las reglas del juego antes de abrir la consola de configuración de Jira.

## 2.1 Criterios de Selección Metodológica (Gobernanza Adaptativa)

No todos los proyectos se gestionan igual. Implementaremos un árbol de decisión basado en dos variables principales: **Incertidumbre del Requerimiento** y **Complejidad Técnica**.

1. **Evaluación de Estabilidad del Alcance:** Paso Inicial.
Analizar si los requerimientos son altamente cambiantes o si están definidos por regulaciones externas inamovibles. Si el alcance es fijo y regulado, se preselecciona un enfoque predictivo.


2. **Medición de Complejidad e Integración Técnica:** Paso Técnico.
Evaluar la cantidad de áreas involucradas y dependencias tecnológicas (ej. bases de datos legadas, proveedores externos). A mayor cantidad de dependencias cross-team, se requiere mayor robustez en la gestión de riesgos.


3. **Clasificación y Asignación del Framework:** Decisión Final.
Aplicar la matriz de asignación del portafolio:

* **Proyectos de Software Core / Innovación:** Scrum (Sprints de 2 semanas).
* **Proyectos de Infraestructura y Migraciones Cloud:** Híbrido (Roadmap Waterfall para hitos macro + Tableros Kanban para la ejecución técnica).
* **Soporte, Mantenimiento Evolutivo y QA Continuo:** Kanban Puro (Gestión por flujo continuo y límites WIP).


---

## 2.2 Roles, Responsabilidades y su Reflejo en las Herramientas

Para evitar conflictos de autoridad entre los roles tradicionales y los ágiles, definimos la responsabilidad metodológica y su **dueño operativo** dentro de la plataforma.

| Rol Metodológico | Responsabilidad Principal | Rol / Permiso en Jira y Confluence |
| --- | --- | --- |
| **Product Owner (PO)** | Maximizar el valor del producto. Dueño absoluto de la priorización del Backlog de negocio. | **Jira:** *Project Admin / Board Administrator*. Único rol con permisos para reordenar el Product Backlog. |
| **Scrum Master / PM** | Eliminar impedimentos, asegurar la salud del flujo y la adopción del método. | **Jira:** Propietario de la configuración de reportes y dashboards. Gestiona el estado "Blocked" y las alertas de cuello de botella. |
| **Tech Lead** | Garantizar la calidad técnica, arquitectura y viabilidad de la solución. | **Jira/Git:** Configura los *Quality Gates*. Su aprobación es requerida en Jira para transicionar tickets de "Code Review" a "QA". |
| **Equipo de Desarrollo / QA** | Construir el incremento de software con calidad y probarlo. | **Jira:** Permisos de ejecución (*Collaborators*). Responsables de actualizar sus tickets diariamente y adjuntar evidencias. |

---

## 2.3 Procesos, Ceremonias y Estandarización Documental

Las ceremonias ágiles e hitos de control del proyecto deben dejar un rastro digital exacto. Aquí establecemos cómo interactúan los rituales del equipo con la documentación centralizada:

### A. El Ciclo de Ceremonias y su Soporte Digital

* **Sprint Planning:** Se realiza sobre el Backlog depurado en Jira. Al finalizar la sesión, el Sprint debe quedar formalmente iniciado en la herramienta con un **Sprint Goal** redactado en el dashboard del equipo.
* **Daily Standup:** No se realiza de memoria. El equipo se reúne proyectando el **Tablero Scrum/Kanban de Jira**, revisando estrictamente el flujo de derecha a izquierda (enfocándose en cerrar tareas antes de abrir nuevas).
* **Sprint Review & Retrospective:** Los resultados de negocio se muestran desde el reporte de Jira. Los compromisos de mejora del equipo se documentan en una **página de Retrospectiva en Confluence**, y los planes de acción se convierten en tickets de mejora en el Backlog del siguiente Sprint.

### B. Estándares de Calidad Operativa: DoR y DoD

Para que un requerimiento fluya sin fricciones, implementamos dos acuerdos de equipo (*Working Agreements*) obligatorios que parametrizaremos en el flujo de Jira:

> 📝 **Definition of Ready (DoR) - Para empezar a trabajar:**
> Un ticket solo puede pasar a "To Do" o planificarse en un Sprint si cumple con:
> 1. Historia de Usuario redactada bajo el formato estándar (*Como [rol], quiero [acción], para [beneficio]*).
> 2. Criterios de Aceptación claros y validados por el PO (formato *Dado que / Cuando / Entonces*).
> 3. Estimación técnica preliminar asignada (Story Points o T-Shirt sizes).
> 4. Dependencias técnicas externas identificadas y desbloqueadas.
> 
> 

> 🏁 **Definition of Done (DoD) - Para considerar terminado:**
> Una iniciativa solo se mueve al estado "Done" si cumple con:
> 1. Código fuente integrado en la rama principal sin conflictos de merge.
> 2. Code Review aprobado por al menos un par técnico o Tech Lead.
> 3. Pruebas de QA ejecutadas con 0 defectos críticos abiertos.
> 4. Documentación técnica actualizada en Confluence (Diagrama de arquitectura o API endpoints registrados).
> 5. Despliegue exitoso en el ambiente de pruebas (UAT o Stage).
> 
> 

---
# PARTE 3: Blueprint Técnico y Configuración del Ecosistema (Jira + Confluence) (FASE 2).
## 🛠️ 1. Blueprint Técnico de Jira Software

Para soportar proyectos Ágiles (Scrum/Kanban) y el enfoque **Lean** (detección de *Muda* o desperdicios), diseñaremos un esquema unificado pero parametrizable.

### 1.1 Configuración del Flujo de Trabajo (Workflow) Lean-Agile

El flujo de Jira no debe ser una cárcel de tickets, sino un mapa del flujo de valor (*Value Stream Map*). Configuraremos un workflow estándar con **Límites de Trabajo en Progreso (WIP Limits)** en columnas clave para evitar la sobrecarga y el desperdicio por cambio de contexto.

```
[Backlog] ➔ [Selected for Development] ➔ [In Progress (WIP: Max 3)] ➔ [Code Review] ➔ [QA Testing (WIP: Max 2)] ➔ [UAT] ➔ [Done]

```

* **Estado: Selected for Development (El "Pull System" de Lean):** Los desarrolladores *halan* el trabajo solo cuando tienen capacidad, en lugar de recibir asignaciones automáticas de manera masiva.
* **Regla de Transición Automatizada (Eliminación de Desperdicio):** Al abrir un *Pull Request* en GitHub/Azure DevOps, el ticket en Jira pasa automáticamente de `In Progress` a `Code Review`. Si el PR es rechazado, regresa a `In Progress` con una bandera de alerta.

### 1.2 Automatizaciones Clave en Jira (Enfoque Lean)

Para reducir las tareas administrativas manuales (desperdicio de procesamiento), implementaremos las siguientes reglas globales:

* **Alerta de Ticket Estancado (Kaizen Trigger):** Si un ticket pasa más de 3 días en el estado `In Progress` o `Blocked`, Jira añade automáticamente un comentario etiquetando al Scrum Master/PM y cambia el color de la tarjeta a rojo en el tablero.
* **Cierre de Cascada Eficiente:** Cuando una Épica cambia a estado `Done`, todas las Historias de Usuario e incidentes asociados que sigan abiertos se mueven automáticamente a `Done` (previo check de aprobación técnica) o se devuelven al Backlog general.

---

## 📄 2. Blueprint Técnico de Confluence (Base de Conocimiento)

Confluence funcionará como la memoria centralizada de la organización. Para evitar el desorden estructural, se implementará una arquitectura basada en **Espacios** y **Plantillas Lean**.

### 2.1 Estructura Global de Espacios

* **Espacio de Producto (PROD):** Gestionado por los Product Owners. Contiene los Lean Canvas, Roadmaps y especificaciones funcionales globales.
* **Espacio de Ingeniería y Arquitectura (ENG):** Documentación técnica de sistemas, diagramas de arquitectura y el registro de decisiones críticas (ADRs).
* **Espacio de Operaciones y DevOps (OPS):** Runbooks de despliegue, planes de contingencia frente a incidentes y lecciones aprendidas de Post-Mortems.

### 2.2 Plantilla Destacada: Lean Canvas de Iniciativa

Antes de crear tareas en Jira, cada nuevo proyecto debe defender su valor mediante esta plantilla simplificada en Confluence:

> **[Nombre de la Iniciativa] - Lean Canvas**
> * **Problema Actual:** ¿Qué fricción u ineficiencia estamos resolviendo?
> * **Solución Propuesta:** Descripción del MVP (Producto Mínimo Viable).
> * **Métricas de Éxito:** ¿Cómo mediremos que funcionó? (Ej: Reducción del 15% en el tiempo de procesamiento).
> * **Desperdicios Eliminados:** ¿Qué pasos manuales, duplicidades o aprobaciones burocráticas elimina esta iniciativa?
> 
> 

---

## 🎮 3. Estrategia de Gamificación Operativa (Gamification Blueprint)

La gamificación se utilizará para **premiar comportamientos saludables** (como documentar o mantener Jira actualizado) y nunca para penalizar o generar competencia tóxica entre los equipos.

### 3.1 El Sistema de Puntos y "Badges" Atlassian

Utilizaremos campos personalizados ocultos en Jira y automatizaciones de Confluence para calcular los logros del equipo al final de cada Sprint o mes.

| Logro / Medalla | Criterio de Activación (Trigger en Jira/Confluence) | Comportamiento Cultural que Incentiva |
| --- | --- | --- |
| 🛡️ **Defensor del Flujo** | Cerrar un Sprint habiendo respetado el límite WIP y con 0 tickets acumulados en la última semana. | Planificación realista y predictibilidad (Lean). |
| ✍️ **Escriba del Conocimiento** | Crear al menos 2 páginas de documentación técnica útiles (ADRs o Runbooks) en Confluence durante el mes. | Evitar los silos de información y fomentar la transferencia técnica. |
| 🪓 **Cazador de Desperdicio** | Identificar y marcar como "Depreciado/Duplicado" más de 5 tickets obsoletos en el Backlog. | Mantenimiento y limpieza del Product Backlog (*Backlog Grooming*). |
| 🚀 **Clean Code Champion** | Pasar 3 Sprints seguidos con una tasa de defectos rechazados en QA menor al 5%. | Calidad integrada en el origen (*Build Quality In*). |

### 3.2 Visualización: El "Tablero de Logros Colectivos"

En lugar de un ranking individual de desarrolladores (que destruye el trabajo en equipo), se configurará un **Dashboard Ejecutivo en Jira** que muestre el progreso de los equipos completos:

* **Métrica Gamificada de Colaboración:** Porcentaje de tickets bloqueados que fueron resueltos por un miembro del equipo diferente al asignado originalmente (Premio a la colaboración *Cross-functional*).
* **Celebraciones Automatizadas:** Integración con Microsoft Teams o Slack. Cuando un equipo desbloquea un logro importante (ej. *Medalla Clean Code*), el bot de Jira envía un mensaje de felicitación al canal general de la empresa reconociendo el esfuerzo técnico.

---

# PARTE 4: Plan de Gestión del Cambio, Capacitación por Perfiles y Estrategia del Piloto Controlado, integrando esta potente triada metodológica (FASE 3).

Entendido por completo. El verdadero poder de la transformación ocurre cuando no vemos estos marcos como silos excluyentes, sino como un engranaje unificado: **Agile como la filosofía** (colaboración y valor), **Scrum como la estructura y ritmo** (Sprints, ceremonias y roles) y **Lean como el optimizador del flujo** (eliminación de desperdicios, enfoque en la entrega constante y mejora continua).

---

## 📈 1. Plan de Gestión del Cambio (Lean Change Management)

Para una adopción desde cero, los planes de gestión del cambio tradicionales (rígidos y de arriba hacia abajo) suelen fracasar. Aplicaremos un enfoque **Lean-Agile**: el cambio se tratará como un producto interactivo, lanzando **Cambios Mínimos Viables (MVCs)** para medir la respuesta cultural del equipo y pivotar si es necesario.

### 1.1 Ciclo de Adopción del Cambio

Cada nueva práctica en Jira/Confluence pasará por tres estados antes de volverse obligatoria:

1. **Insights (Fase 0):** Identificar el dolor (ej. *"Perdemos tiempo en reuniones de estatus"*).
2. **Opciones:** Proponer la solución conjunta (ej. *"Usemos el tablero Kanban de Jira en el Daily"*).
3. **Experimentos:** Probar la solución con el equipo piloto durante 2 Sprints antes de estandarizarla.

### 1.2 Mitigación de la Resistencia mediante la Triada (Agile-Scrum-Lean)

* **El Dolor de la "Burocracia" (Anti-Jira):** El equipo técnico suele temer que Jira sea una herramienta de microgestión.
* **La Respuesta Lean-Agile:** Demostrarles que al implementar límites WIP (Lean) y automatizaciones de Git con Jira, se elimina el desperdicio de reportar horas o estados manualmente. Jira pasa de ser una herramienta de control a un escudo protector de la capacidad del equipo.

---

## 🎓 2. Plan de Capacitación Centrado en el Flujo de Valor

La capacitación no será un monólogo técnico de "cómo dar clic en Jira". Será un entrenamiento vivencial que conectará el marco metodológico con el uso práctico de las herramientas según el rol.

### Matriz de Capacitación por Perfiles

| Perfil | Foco Metodológico (Agile + Scrum + Lean) | Ejecución Práctica en el Ecosistema | Indicador de Éxito de la Capacitación |
| --- | --- | --- | --- |
| **Product Owners & Negocio** | *   Priorización de valor (Agile).<br>

<br>*   Definición de MVP y Épicas (Lean).<br>

<br>*   Refinamiento del Backlog (Scrum). | *   Uso de Confluence para el Lean Canvas.<br>

<br>*   Gestión y ordenamiento del Backlog en Jira.<br>

<br>*   Seguimiento del Roadmap en tiempo real. | Un Backlog en Jira con al menos 2 Sprints de historias que cumplan con el **DoR**. |
| **Scrum Masters & PMs** | *   Facilitación de ceremonias (Scrum).<br>

<br>*   Detección de cuellos de botella y *Muda* (Lean).<br>

<br>*   Protección del Sprint (Agile). | *   Configuración y lectura de gráficos de flujo (CFD, Velocity, Lead Time).<br>

<br>*   Gestión de impedimentos y banderas de bloqueo en Jira. | Dashboards operativos configurados correctamente sin intervención de TI. |
| **Tech Leads, Devs & QA** | *   Entrega técnica incremental (Scrum).<br>

<br>*   Calidad en el origen y límites WIP (Lean).<br>

<br>*   Autoorganización (Agile). | *   Uso del tablero Jira diario.<br>

<br>*   Integración de Jira con repositorios (ramas, PRs).<br>

<br>*   Documentación de ADRs en Confluence. | Transiciones automáticas de tickets mediante triggers de código y 100% de uso de plantillas en Confluence. |

---

## 🚀 3. Estrategia de Piloto Controlado

El lanzamiento desde cero requiere un laboratorio seguro. No abriremos las herramientas para toda la organización a la vez; seleccionaremos un **Equipo Piloto Transversal** (un producto o iniciativa específica que involucre a Negocio, Desarrollo, QA y Operaciones).

### 3.1 Ciclo de Vida del Piloto (Duración: 3 Sprints de 2 semanas)

#### 🔸 Sprint 1: El Arranque Estructural (Enfoque Scrum)

* **Meta:** Estabilizar la cadencia y entender la herramienta.
* **Acciones:** El equipo realiza su primera *Sprint Planning* directamente en Jira. Se definen las subtareas y se inicia el Sprint en la plataforma. Las *Dailies* se guían proyectando el tablero de Jira.
* **Gamificación:** Se activa la medalla *🛡️ Defensor del Flujo* para incentivar la actualización diaria de los estados.

#### 🔸 Sprint 2: Optimización del Flujo (Enfoque Lean)

* **Meta:** Identificar y eliminar desperdicios en el proceso de desarrollo.
* **Acciones:** Se activan estrictamente los **Límites WIP** en las columnas `In Progress` y `QA Testing`. Si una columna se satura, el equipo detiene la entrada de nuevo trabajo (*Stop Starting, Start Finishing*) para resolver el cuello de botella. Se analizan los tickets estancados mediante las alertas automáticas de Jira.

#### 🔸 Sprint 3: Integración y Calidad Total (Enfoque DevOps + Kaizen)

* **Meta:** Consolidar la trazabilidad de punta a punta (*End-to-End*).
* **Acciones:** Se conecta formalmente el repositorio de código. El paso de `In Progress` a `Code Review` y `QA` se realiza mediante automatizaciones nativas. Al final del Sprint, la *Retrospectiva* se realiza usando la plantilla de Confluence, generando planes de acción medibles que se inyectan automáticamente como tareas en el Backlog de Jira para el siguiente ciclo.

### 3.2 Hito de Cierre del Piloto: El Evento Kaizen

Al finalizar el Sprint 3, se realiza una sesión de revisión técnica y metodológica con los líderes del proyecto. Se evalúan las métricas reales del piloto (Lead Time, Cycle Time y tasa de adopción de la herramienta) para ajustar el **Blueprint Técnico** final antes de iniciar el escalamiento masivo al resto del Departamento de Tecnología.

---

Con este plan de adopción y piloto, aseguramos que la teoría ágil se convierta en hábito operativo a través del uso correcto de Jira y Confluence.

---

# PARTE 5: Escalamiento Organizacional, Ecosistema de Dashboards y Métricas Avanzadas(FASE 4).

Una vez validado el piloto, el desafío es expandir el modelo sin generar caos. Aquí la combinación de **Agile** (sincronización de objetivos), **Scrum** (estructuras de coordinación inter-equipos) y **Lean** (gestión del flujo de portafolio y eliminación de dependencias) se vuelve indispensable para consolidar una toma de decisiones 100% basada en datos.

---

## 🏢 1. Escalamiento Organizacional y Gestión de Dependencias

Al pasar de un equipo a múltiples equipos concurrentes, el principal "desperdicio Lean" es la espera por dependencias interdepartamentales (ej. Desarrollo esperando por Seguridad o Infraestructura).

### A. La Estructura de Coordinación (Scrum de Scrums)

Para mantener la agilidad a escala, implementaremos la ceremonia de **Scrum de Scrums (SoS)** dos veces por semana. No es una reunión de estatus político; es una sesión técnica donde los representantes de cada equipo (Scrum Masters / Tech Leads) abren un **Tablero de Dependencias Cruzadas en Jira** para resolver bloqueos en tiempo real.

### B. Gestión Visual del Portafolio en Jira Software

Utilizaremos la funcionalidad de *Advanced Roadmaps* de Jira para consolidar la vista multi-proyecto.

* **Jerarquía Escalada:** Iniciativa Estratégica (Nivel Portafolio) ➔ Épica (Nivel Producto) ➔ Historia de Usuario / Bug (Nivel Equipo).
* **Líneas de Dependencia Automatizadas:** Si el equipo de QA bloquea un ticket del equipo de Core, Jira dibuja automáticamente una línea roja de dependencia en el Roadmap del Portafolio, alertando a la gerencia antes de que afecte la fecha de liberación (*Release Date*).

---

## 📊 2. Arquitectura de Dashboards y Reportabilidad en Tiempo Real

Configuraremos tres niveles de visibilidad en Jira para asegurar que cada rol consuma la información que necesita para actuar, eliminando por completo los reportes manuales en Excel o PowerPoint.

### 📈 Nivel 1: Dashboard Estratégico (Dirección y C-Level)

* **Enfoque:** Entrega de valor macro, predictibilidad del portafolio y eficiencia financiera.
* **Gadgets clave en Jira:**
* *Portafolio Health:* Gráfico de pastel que muestra el % de avance real de las Iniciativas Estratégicas vs. el tiempo transcurrido.
* *Value Delivery Rate:* Gráfico de barras que mide cuántas iniciativas de alto valor de negocio se han completado por trimestre.
* *Strategic Alignment:* Mapeo de inversión de capacidad técnica (ej. 60% Innovación, 20% Soporte/Mantenimiento, 20% Deuda Técnica).



### 🛠️ Nivel 2: Dashboard Operativo / Gerencial (PMs, Product Owners y Gerencia de TI)

* **Enfoque:** Gestión del flujo, cuellos de botella y salud del proceso.
* **Gadgets clave en Jira:**
* *Cumulative Flow Diagram (CFD):* El gráfico Lean por excelencia. Permite ver si el trabajo se está acumulando de forma peligrosa en estados como `QA Testing` o `UAT`.
* *Control Chart (Cycle Time):* Mide la estabilidad del proceso, mostrando cuánto tiempo toma en promedio resolver un requerimiento desde que se inicia.
* *Impediment Radar:* Lista en tiempo real de todos los tickets con la bandera de "Bloqueado" activa, ordenados por los días que llevan estancados.



### 💻 Nivel 3: Dashboard de Ejecución Técnica (Squads, Tech Leads y QA)

* **Enfoque:** El día a día del Sprint y calidad del código.
* **Gadgets clave en Jira:**
* *Sprint Burndown Chart:* Progreso diario del equipo hacia la meta del Sprint.
* *Defect Leakage Counter:* Cantidad de bugs encontrados en producción vs. ambientes de prueba.
* *Git Integration Status:* Panel que muestra *Pull Requests* abiertos, aprobados y despliegues fallidos integrados desde los repositorios.



---

## 📐 3. El Cuadro de Mando Avanzado (Métricas Lean-Agile + DORA)

Para transformar la cultura operativa en una de alto rendimiento técnico, mediremos al departamento bajo dos marcos de métricas líderes en la industria global:

| Tipo de Métrica | Nombre del Indicador | ¿Qué mide exactamente? | Meta Organizacional Mínima |
| --- | --- | --- | --- |
| **Lean-Agile** | **Lead Time** | Tiempo total desde que el negocio solicita una idea hasta que está en producción. | Reducción progresiva del 25% anual. |
| **Lean-Agile** | **Throughput** | Cantidad de Historias de Usuario / Entregables completados por unidad de tiempo (Sprint). | Estabilidad (Predictibilidad de entrega). |
| **Métrica DORA** | **Deployment Frequency** | Qué tan seguido el equipo despliega código exitoso en producción. | Pasar de despliegues mensuales a semanales / diarios. |
| **Métrica DORA** | **Lead Time for Changes** | El tiempo que toma un commit de código en llegar exitosamente a producción. | Menos de 24 horas (Automatización CI/CD). |
| **Métrica DORA** | **Change Failure Rate** | El % de despliegues en producción que requieren un rollback, fix o parche de emergencia. | Menor al 10%. |
| **Métrica DORA** | **Mean Time to Recovery (MTTR)** | Tiempo promedio que le toma al área de tecnología restaurar el servicio cuando ocurre un incidente crítico. | Menor a 1 hora. |

---

## 🎮 4. Gamificación a Escala Inter-Equipos

Al escalar, la gamificación evoluciona para **evitar el aislamiento entre células de trabajo**. Implementaremos la **"Copa Kaizen Corporativa"**.

* **Mecánica Colectiva (The Guild Challenge):** Los puntos no se ganan compitiendo un equipo contra otro, sino alcanzando "Metas Globales de Madurez".
* **Logro Escallado: *The Continuous Delivery Clan*:** Si todos los equipos del departamento logran mantener un *Change Failure Rate* menor al 10% durante dos meses consecutivos, la organización financia una certificación internacional oficial para todos los miembros de los equipos o un evento de integración técnica (*Hackathon* interna). Esto incentiva a que los equipos más maduros ayuden activamente a los equipos que están experimentando problemas de calidad.

---

Con la estructura de escalamiento, dashboards y métricas de ingeniería de software avanzada listas, el modelo operativo está completamente blindado.

---

# PARTE 6: Optimización Continua (Kaizen), Modelo de Madurez Definitivo y Criterios de Aceptación Finales (FASE 5)

Esta sección actúa como el sistema de autolimpieza y evolución del marco. Aquí garantizamos que el ecosistema no se vuelva obsoleto con el tiempo y definimos exactamente qué significa "éxito" para la dirección ejecutiva.

---

## 🔄 1. Modelo de Optimización Continua (Kaizen Operativo)

Para que el ecosistema viva a largo plazo, utilizaremos los datos acumulados en Jira y Confluence para realizar optimizaciones periódicas sin generar fricción en el equipo técnico.

### A. El Ciclo de Inspección y Adaptación Mensual (Value Stream Review)

Cada fin de mes, la gerencia de tecnología y los Scrum Masters utilizarán el *Control Chart* de Jira para auditar el flujo de valor mediante dos acciones específicas:

* **Identificación de Desperdicios Técnicos (*Muda*):** Se analizarán los tickets que pasaron más del 40% de su ciclo de vida en estados de espera (`Blocked`, `Waiting for Deploy`, `UAT`).
* **Ajuste Dinámico de Límites WIP:** Si un equipo demuestra estabilidad en su flujo, el Scrum Master puede proponer reducir el límite WIP en la columna `In Progress` para forzar la resolución rápida de tareas y acelerar el *Lead Time*.

### B. El Repositorio Viviente de Lecciones Aprendidas

Las retrospectivas no se quedarán en el olvido. Configuraremos un espacio en Confluence indexado automáticamente. Cada vez que un equipo identifique una acción de mejora técnica, esta se etiquetará como `#Kaizen-Action` en Jira. Si el experimento funciona, se actualiza inmediatamente el *Blueprint Técnico* global en Confluence, permitiendo que un aprendizaje de la Célula A optimice la operación de las Células B y C de forma inmediata.

---

## 📊 2. El Modelo de Madurez Definitivo (5 Niveles Integrados)

Para medir el avance de la transformación de manera objetiva, estructuramos los niveles de madurez combinando la adopción de herramientas con la madurez metodológica (Agile + Scrum + Lean).

| Nivel de Madurez | Componente Metodológico | Uso del Ecosistema (Jira + Confluence) | Indicador Clave de Nivel |
| --- | --- | --- | --- |
| **Nivel 1: Inicial (Reactivo)** | Operación ad-hoc. Priorización verbal. Ritmo impredecible. | Herramientas dispersas (Excels, correos). Jira y Confluence no se utilizan o están vacíos. | Caos operativo. El trabajo es invisible. |
| **Nivel 2: Estandarizado** | Ceremonias básicas de Scrum activas. Roles definidos en papel. | Tickets creados en Jira de forma manual. Flujos de trabajo lineales sin automatización. | Visibilidad básica. El Backlog existe pero es inestable. |
| **Nivel 3: Gestionado (Lean)** | Aplicación estricta de Límites WIP. Enfoque en eliminar bloqueos. | Uso diario del tablero. Alertas automáticas de estancamiento configuradas. Confluence como Wiki. | Predictibilidad. Reducción medible de la fricción operativa. |
| **Nivel 4: Integrado (DevOps)** | Sincronización multi-equipo (SoS). Calidad en el origen. | Integración nativa con Git/CI-CD. Transiciones automáticas de tickets. Métricas DORA activas. | Trazabilidad End-to-End. Despliegues frecuentes con baja tasa de fallo. |
| **Nivel 5: Optimizado** | Cultura Kaizen basada en datos. Alta autonomía operativa. | Dashboards ejecutivos en tiempo real. Gamificación corporativa consolidada. | Innovación continua. Toma de decisiones 100% basada en datos. |

---

## 🎯 3. Criterios de Aceptación Finales del Programa de Transformación

El programa de implementación de este marco se considerará formalmente exitoso y finalizado cuando cumpla con los siguientes criterios de aceptación cuantitativos en producción:

> 🟩 **Criterio 1: Adopción Activa de Herramientas**
> * El **100%** de los proyectos tecnológicos vigentes del portafolio deben estar registrados y gestionados activamente dentro de Jira Software.
> * El **100%** de las iniciativas activas deben contar con su especificación técnica, criterios de aceptación y arquitectura documentados en Confluence antes de iniciar desarrollo.
> 
> 

> 🟩 **Criterio 2: Eficiencia del Flujo (Métricas Lean-Agile)**
> * Reducción comprobada de al menos un **20% del Cycle Time** promedio en los equipos que alcanzaron el Nivel 3 de madurez.
> * Cero tickets en estado "En progreso" que violen los límites WIP establecidos por más de un Sprint sin una bandera de bloqueo formalmente justificada.
> 
> 

> 🟩 **Criterio 3: Automatización Operativa**
> * Eliminación total del reporte manual de estatus técnico. La gerencia y los líderes de negocio deben consumir el avance exclusivamente a través de los Dashboards automatizados de Jira.
> * El **80%** de las transiciones de desarrollo (`Code Review` ➔ `QA` ➔ `Done`) deben ser ejecutadas por triggers automáticos del repositorio de código, no por movimiento manual del desarrollador.
> 
> 

---

## 🏆 Cierre de la Consolidación Estratégica

Con esta **estrategia operativa detallada, accionable y de alto nivel de ingeniería**. Tenemos diseñado desde el diagnóstico inicial en frío hasta las métricas DORA y los flujos automatizados que sostendrán el rendimiento del área de tecnología.
