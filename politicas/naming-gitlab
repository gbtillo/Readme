# Política Corporativa de Nomenclatura de Usuarios GitLab

| Campo | Valor |
|---------|---------|
| Código | POL-DEVSECOPS-GL-001 |
| Versión | 1.0 |
| Estado | Vigente |
| Propietario | Área de Tecnología / DevSecOps |
| Aprobador | Gerencia de Tecnología |
| Fecha de Vigencia | DD/MM/AAAA |

---

# 1. Objetivo

Establecer un estándar corporativo para la creación y administración de nombres de usuario (*username*) en GitLab, garantizando:

- Trazabilidad de las acciones realizadas por cada usuario.
- Identificación inequívoca de los colaboradores.
- Uniformidad en todos los proyectos y repositorios.
- Cumplimiento de prácticas de gobierno de plataformas DevSecOps.
- Compatibilidad con procesos de auditoría y cumplimiento normativo.

---

# 2. Alcance

Esta política aplica a:

- Empleados internos.
- Consultores.
- Contratistas.
- Proveedores.
- Cuentas de servicio.
- Integraciones automáticas.
- Bots y automatizaciones CI/CD.
- Ambientes de desarrollo, pruebas, certificación y producción.

---

# 3. Principios Generales

## 3.1 Unicidad

Cada persona deberá disponer de una única cuenta personal.

## 3.2 Trazabilidad

Toda actividad realizada en GitLab debe poder asociarse a una persona o responsable identificado.

## 3.3 No Compartición

Queda prohibido el uso de cuentas compartidas entre varios usuarios.

## 3.4 Consistencia

Los usuarios deberán mantener una nomenclatura alineada al estándar corporativo y, cuando aplique, al directorio corporativo (Active Directory, Entra ID u otro servicio de identidad).

## 3.5 Auditoría

Las cuentas deberán permitir la identificación inmediata del propietario y su tipo de uso.

---

# 4. Convenciones de Nomenclatura

## 4.1 Usuarios Internos

### Formato

```text
nombre.apellido
```

### Ejemplos

```text
jackson.gamboa
karol.moran
mario.perez
```

### Reglas

- Solo letras minúsculas.
- Separación mediante punto (.).
- Sin espacios.
- Sin caracteres especiales.
- Sin acentos.
- Sin la letra ñ.

### Ejemplos de Conversión

```text
José Muñoz → jose.munoz
María Pérez → maria.perez
Ángel Cárdenas → angel.cardenas
```

---

## 4.2 Usuarios Duplicados

Cuando exista más de un usuario con los mismos nombres y apellidos.

### Formato

```text
nombre.apellidoa
nombre.apellidoav
```

### Ejemplos

```text
juan.pereza
juan.perezan
```

La asignación será administrada por el equipo DevSecOps.

---

## 4.3 Contratistas y Consultores

### Formato

```text
ext.nombre.apellido
```

### Ejemplos

```text
ext.carlos.ramirez
ext.maria.lopez
```

---

## 4.4 Proveedores Externos

### Formato

```text
prov.empresa.nombre
```

### Ejemplos

```text
prov.ibm.johnsmith
prov.oracle.mrodriguez
prov.accenture.jmartinez
```

---

## 4.5 Cuentas de Servicio

Las cuentas de servicio serán utilizadas exclusivamente por procesos automatizados.

### Formato

```text
svc-funcion
```

### Ejemplos

```text
svc-ci
svc-cd
svc-sonarqube
svc-deploy
svc-backup
svc-monitoring
svc-securityscan
```

---

## 4.6 Bots e Integraciones

### Formato

```text
bot-funcion
api-sistema
```

### Ejemplos

```text
bot-notificaciones
bot-mergeapproval
api-erp
api-pgo
api-conciliacion
api-merchantpanel
```

---

# 5. Nombres de Usuario Prohibidos

No se permite la creación de usuarios con nombres genéricos o ambiguos.

## Ejemplos No Permitidos

```text
admin
administrator
root
gitlab
usuario
developer
dev
qa
testing
equipo
backend
frontend
app
system
```

Asimismo, quedan prohibidos:

- Alias personales.
- Apodos.
- Identificadores temporales.
- Nombres ofensivos o inapropiados.
- Abreviaciones que impidan identificar al propietario de la cuenta.

---

# 6. Relación con Correo Corporativo

Siempre que sea posible, el identificador GitLab deberá coincidir con la primera parte del correo corporativo.

### Ejemplo
Usuario:
```text
jackson gamboa
```

Correo:

```text
jgamboa@empresa.com
```

Usuario GitLab:

```text
jackson.gamboa
```

---

# 7. Estándar para DevSecOps

Las siguientes cuentas deberán existir de manera diferenciada:

| Categoría | Formato |
|------------|------------|
| CI/CD | svc-ci |
| Deploy | svc-deploy |
| SonarQube | svc-sonarqube |
| SAST | svc-sast |
| DAST | svc-dast |
| Dependency Scan | svc-dependencyscan |
| Container Scan | svc-containerscan |
| IaC Scan | svc-iacscan |
| Terraform | svc-terraform |
| Monitoring | svc-monitoring |
| Backup | svc-backup |

---

# 8. Gestión y Gobierno

## Altas

Las altas de usuarios deberán estar respaldadas por:

- Solicitud formal.
- Aprobación del líder del área.
- Asociación a un proyecto o equipo.

## Modificaciones

Cualquier modificación de usuario deberá:

- Mantener la trazabilidad histórica.
- Ser aprobada por el Administrador GitLab.

## Bajas

Las cuentas de usuarios desvinculados deberán:

- Ser deshabilitadas inmediatamente.
- Mantener la información histórica de auditoría.
- Conservar los registros de contribuciones.

---

# 9. Auditoría y Cumplimiento

El equipo DevSecOps realizará revisiones periódicas para validar:

- Usuarios inactivos.
- Cuentas sin propietario.
- Accesos de proveedores vencidos.
- Cuentas de servicio sin justificación.
- Incumplimientos de nomenclatura.

Las desviaciones detectadas deberán regularizarse siguiendo el proceso de gestión de accesos corporativo.

---

# 10. Excepciones

Toda excepción deberá contar con:

1. Justificación documentada.
2. Evaluación de riesgos.
3. Aprobación del Líder DevSecOps.
4. Registro en el sistema corporativo de gestión de cambios o mesa de servicios.

---

# 11. Estándar Recomendado para la Organización

| Tipo | Formato |
|---------|---------|
| Usuario Interno | `nombre.apellido` |
| Contratista | `ext.nombre.apellido` |
| Proveedor | `proveedor.empresa.nombre` |
| Servicio | `svc-funcion` |
| Bot | `bot-funcion` |
| Integración | `api-sistema` |

### Ejemplos

```text
jackson.gamboa
karol.moran
ext.juan.perez
proveedor.ibm.johnsmith
svc-ci
svc-sonarqube
svc-terraform
api-pgo
api-conciliacion
api-merchantpanel
```

---

# Control de Cambios

| Versión | Fecha | Descripción | Autor |
|----------|--------|-------------|---------|
| 1.0 | DD/MM/AAAA | Creación inicial de la política | Equipo DevSecOps |