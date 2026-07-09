📄 Transformación del Modelo de Despliegue
Framework Corporativo DevSecOps con GitLab Ultimate
1. Resumen Ejecutivo

La institución plantea una transformación del modelo actual de entrega de software hacia un enfoque DevSecOps automatizado, gobernado y auditable, soportado en GitLab Ultimate.

El objetivo principal es modernizar el ciclo de vida del software, eliminando dependencias manuales, reduciendo riesgos operativos y garantizando cumplimiento regulatorio (PCI DSS).

✅ Beneficios esperados

El modelo permitirá:

Reducir tiempos asociados al ciclo de entrega de soluciones.
Disminuir riesgos derivados de actividades manuales.
Fortalecer la seguridad mediante controles integrados desde el desarrollo.
Generar evidencias automáticas para auditoría y cumplimiento.
Mantener la segregación de funciones sin afectar la automatización.
Estandarizar procesos de despliegue entre equipos y plataformas.
2. Problema Actual

Actualmente, el proceso de despliegue presenta:

Alta dependencia de actividades manuales.
Intervención secuencial de múltiples áreas.
Tiempos elevados de liberación.
Riesgo de errores humanos.
Dificultad para generar evidencias de auditoría.
Falta de estandarización en pipelines y controles.

👉 Esto impacta directamente en:

velocidad de entrega
riesgo operativo
cumplimiento regulatorio
3. Modelo Propuesto

El nuevo modelo se basa en:

✅ Automatización del pipeline (CI/CD)
 ✅ Gobierno por políticas (Policy as Code)
 ✅ Validaciones previas al despliegue (no durante)
 ✅ Auditoría continua (evidencia automática)

🔑 Principio clave

“Las áreas no intervienen durante el despliegue;
 sus decisiones están integradas previamente como validaciones automatizadas.”

4. Áreas Involucradas

El modelo mantiene la participación de todas las áreas, pero cambia la forma de interacción.

Área	Rol en el nuevo modeloSeguridad	Define políticas y controles automáticos
Infraestructura	Administra plataformas y disponibilidad
Redes	Define conectividad y controles de red
Operaciones	Gestiona ventanas, monitoreo y operación
Procesos	Administra gestión del cambio (ITSM)
Aplicaciones	Valida funcionalidad
Arquitectura	Define estándares y patrones corporativos

👉 Todas las áreas participan antes del pipeline, no durante.

5. Fases del Proceso
Modelo de ciclo de vida
Idea → Desarrollo → Validación → Seguridad → Cumplimiento → Release → Deploy → Operación


Cada fase incluye:

controles automáticos
evidencia
validaciones
6. Flujo de Despliegue
🔵 6.1 Antes del despliegue (Gobierno previo)
Solicitud de cambio (RFC)
↓
Evaluación Arquitectura
↓
Evaluación Seguridad
↓
Evaluación Infraestructura
↓
Evaluación Redes
↓
Evaluación Operaciones
↓
Aprobación del cambio


✅ Resultado:

Cambio aprobado
Condiciones definidas
Evidencias registradas
🟡 6.2 Durante el despliegue (Automatización)
Pipeline GitLab
↓
Validación automática:
- Cambio aprobado
- Ventana abierta
- Políticas de seguridad
- Controles PCI DSS
↓
Deploy automático


🚫 No hay intervención humana.

🟢 6.3 Después del despliegue (Control y auditoría)
Generación automática de evidencias
↓
Monitoreo
↓
Alertas
↓
Auditoría continua
↓
Cierre automático del cambio

7. Plan de Acción para Implementación
🔷 Fase 1 – Fundación
Implementación base de GitLab Ultimate
Definición del modelo de gobierno
Gestión de roles y accesos
Estándares corporativos
🔷 Fase 2 – Automatización
Implementación de pipelines CI/CD
Integración con AWS y Azure
Implementación de controles de seguridad automatizados
🔷 Fase 3 – Cumplimiento Continuo
Generación automática de evidencias
Validaciones PCI DSS
Integración con gestión del cambio (ITSM)
🔷 Fase 4 – Evolución
Incorporación de OpenShift
Optimización de procesos
Nuevas capacidades DevSecOps
8. Impacto del Modelo
⏱️ Tiempo
Reducción significativa del “time to market”
Eliminación de tiempos de espera entre áreas
🛡️ Riesgo
Eliminación de errores manuales
Validación automática en cada despliegue
🔐 Seguridad
Integración de controles desde el desarrollo
Security by Design
📊 Auditoría
Evidencias automáticas
Trazabilidad completa
⚙️ Operación
Procesos estandarizados
Menor fricción entre equipos
9. Diferenciador del Modelo
Antes
Proceso manual
Aprobaciones durante despliegue
Dependencias operativas
Evidencias manuales
Después
Pipeline automatizado
Aprobaciones antes del despliegue
Validaciones automáticas
Auditoría continua
10. Riesgos y Mitigación
Riesgo	MitigaciónResistencia al cambio	Capacitación y acompañamiento
Falta de adopción	Estándares obligatorios
Complejidad inicial	Implementación por fases
Integraciones	Uso de APIs y arquitectura desacoplada
