# INFORME FINAL DE AUDITORÍA DE SISTEMAS
## Sistema de Asistente de IA Corporativo - AuditoriaHelpDeskIA

---

## CARÁTULA

**Entidad Auditada:** Corporación ACME - Departamento de Tecnologías de la Información  
**Ubicación:** Lima, Perú  
**Período auditado:** 22/10/2025 - 22/10/2025  
**Equipo Auditor:** 
- Auditor Principal: Mirian Cuadros

- Especialista en Seguridad: Mirian Cuadros

**Fecha del informe:** 22/10/2025

---

## ÍNDICE

1. [Resumen Ejecutivo](#1-resumen-ejecutivo)
2. [Antecedentes](#2-antecedentes)
3. [Objetivos de la Auditoría](#3-objetivos-de-la-auditoría)
4. [Alcance de la Auditoría](#4-alcance-de-la-auditoría)
5. [Normativa y Criterios de Evaluación](#5-normativa-y-criterios-de-evaluación)
6. [Metodología y Enfoque](#6-metodología-y-enfoque)
7. [Hallazgos y Observaciones](#7-hallazgos-y-observaciones)
8. [Análisis de Riesgos](#8-análisis-de-riesgos)
9. [Recomendaciones](#9-recomendaciones)
10. [Conclusiones](#10-conclusiones)
11. [Plan de Acción y Seguimiento](#11-plan-de-acción-y-seguimiento)
12. [Anexos](#12-anexos)

---

## 1. RESUMEN EJECUTIVO

### Propósito de la Auditoría
Se realizó una auditoría integral del sistema de Asistente de IA Corporativo "AuditoriaHelpDeskIA", desarrollado para responder consultas de usuarios basándose en documentación interna y gestionar tickets de soporte técnico.

### Principales Hallazgos
- **CRÍTICO**: Vulnerabilidades en la gestión de base de datos SQLite
- **ALTO**: Falta de autenticación y autorización en endpoints
- **MEDIO**: Ausencia de logging de auditoría
- **MEDIO**: Configuración de seguridad insuficiente en contenedores Docker

### Conclusiones Principales
El sistema presenta una arquitectura sólida con tecnologías modernas (RAG, LangChain, Ollama), pero requiere mejoras significativas en seguridad y gestión de datos para ser considerado apto para producción.

### Recomendaciones Críticas
1. Implementar autenticación robusta
2. Mejorar la gestión de base de datos
3. Establecer logging de auditoría
4. Revisar configuraciones de seguridad

---

## 2. ANTECEDENTES

### Contexto de la Entidad
La Corporación ACME ha implementado un sistema de asistente de IA conversacional para mejorar la eficiencia del soporte técnico interno. El sistema utiliza arquitectura RAG (Retrieval-Augmented Generation) con modelos de lenguaje local.

### Naturaleza del Sistema
- **Tipo**: Sistema de Asistente de IA con capacidades RAG
- **Arquitectura**: Microservicios con Docker
- **Tecnologías**: Python/FastAPI, React/TypeScript, Ollama, ChromaDB
- **Propósito**: Soporte técnico automatizado con base de conocimiento interna

### Antecedentes de Auditorías
Primera auditoría del sistema. No se identificaron auditorías previas de sistemas similares en la entidad.

---

## 3. OBJETIVOS DE LA AUDITORÍA

### Objetivo General
Evaluar la seguridad, integridad y eficacia del sistema de Asistente de IA Corporativo para determinar su idoneidad para uso en producción.

### Objetivos Específicos
1. **Seguridad de la Información**
   - Evaluar controles de acceso y autenticación
   - Revisar cifrado de datos en tránsito y reposo
   - Analizar vulnerabilidades de seguridad

2. **Integridad y Disponibilidad**
   - Verificar integridad de la base de datos
   - Evaluar mecanismos de respaldo
   - Analizar disponibilidad del servicio

3. **Cumplimiento Normativo**
   - Verificar cumplimiento de políticas internas
   - Evaluar protección de datos personales
   - Revisar trazabilidad de operaciones

4. **Gestión de Configuración**
   - Evaluar gestión de cambios
   - Revisar versionado de código
   - Analizar documentación técnica

---

## 4. ALCANCE DE LA AUDITORÍA

### Ámbitos Evaluados
- **Tecnológico**: Arquitectura, código fuente, configuraciones
- **Organizacional**: Procesos de desarrollo y despliegue
- **Normativo**: Cumplimiento de políticas de seguridad

### Sistemas Incluidos
- Backend API (FastAPI)
- Frontend Web (React/TypeScript)
- Base de datos vectorial (ChromaDB)
- Base de datos relacional (SQLite)
- Servicio de IA (Ollama)

### Áreas Auditadas
- Desarrollo y despliegue
- Gestión de datos
- Seguridad de la información
- Continuidad del servicio

### Período Auditado
22 de octubre de 2025 (auditoría puntual)

---

## 5. NORMATIVA Y CRITERIOS DE EVALUACIÓN

### Marcos de Referencia Aplicados
- **ISO/IEC 27001:2022** - Gestión de Seguridad de la Información
- **COBIT 2019** - Gobierno y Gestión de TI
- **NIST Cybersecurity Framework** - Gestión de Ciberseguridad
- **OWASP Top 10** - Vulnerabilidades de Aplicaciones Web

### Normativas Locales
- **Ley de Protección de Datos Personales** (Ley N° 29733)
- **Reglamento de Seguridad de la Información** del Estado Peruano
- **Políticas Internas de TI** de la Corporación ACME

### Criterios de Evaluación
- Seguridad de la información
- Integridad de datos
- Disponibilidad del servicio
- Cumplimiento normativo
- Gestión de riesgos

---

## 6. METODOLOGÍA Y ENFOQUE

### Enfoque Utilizado
**Auditoría basada en riesgos** con énfasis en seguridad y cumplimiento normativo.

### Métodos Aplicados

#### 1. Revisión de Documentación
- Análisis de arquitectura del sistema
- Revisión de código fuente
- Evaluación de configuraciones Docker

#### 2. Pruebas Técnicas
- Análisis de vulnerabilidades en contenedores
- Revisión de configuraciones de seguridad
- Evaluación de gestión de base de datos

#### 3. Entrevistas
- Entrevistas con desarrolladores
- Consultas a administradores de sistemas
- Revisión con responsables de seguridad

#### 4. Herramientas Utilizadas
- Docker Security Scanning
- Análisis de código estático
- Revisión de logs del sistema

---

## 7. HALLAZGOS Y OBSERVACIONES

### HALLAZGO 1: Vulnerabilidades en Gestión de Base de Datos
**Descripción:** El sistema presenta problemas críticos en la gestión de la base de datos SQLite, incluyendo errores de conexión y falta de persistencia adecuada.

**Evidencia Objetiva:**
- Error: `sqlite3.OperationalError: unable to open database file`
- Base de datos no persiste entre reinicios de contenedores
- Falta de respaldo automático

**Grado de Criticidad:** CRÍTICO

**Criterio Vulnerado:** ISO/IEC 27001 - A.12.3.1 (Gestión de respaldos)

**Causa y Efecto:**
- **Causa:** Configuración incorrecta de rutas de base de datos
- **Efecto:** Pérdida de datos de tickets y fallos en el sistema

---

### HALLAZGO 2: Ausencia de Autenticación y Autorización
**Descripción:** Los endpoints de la API no implementan controles de autenticación ni autorización, permitiendo acceso no autorizado.

**Evidencia Objetiva:**
- Endpoint `/ask` accesible sin autenticación
- Falta de middleware de autenticación
- No se implementan tokens de sesión

**Grado de Criticidad:** ALTO

**Criterio Vulnerado:** ISO/IEC 27001 - A.9.1.1 (Política de control de acceso)

**Causa y Efecto:**
- **Causa:** Desarrollo sin consideraciones de seguridad
- **Efecto:** Acceso no autorizado a información corporativa

---

### HALLAZGO 3: Configuración de Seguridad Insuficiente en Contenedores
**Descripción:** Los contenedores Docker no implementan configuraciones de seguridad adecuadas.

**Evidencia Objetiva:**
- Contenedores ejecutándose con privilegios elevados
- Falta de límites de recursos
- No se implementan políticas de red restrictivas

**Grado de Criticidad:** MEDIO

**Criterio Vulnerado:** NIST Cybersecurity Framework - PR.AC-1

**Causa y Efecto:**
- **Causa:** Configuración por defecto de Docker
- **Efecto:** Exposición a ataques de escalación de privilegios

---

### HALLAZGO 4: Ausencia de Logging de Auditoría
**Descripción:** El sistema no implementa logging adecuado para auditoría y monitoreo de seguridad.

**Evidencia Objetiva:**
- Falta de logs de acceso a la API
- No se registran consultas de usuarios
- Ausencia de logs de seguridad

**Grado de Criticidad:** MEDIO

**Criterio Vulnerado:** ISO/IEC 27001 - A.12.4.1 (Registro de eventos)

**Causa y Efecto:**
- **Causa:** No se consideró la trazabilidad en el diseño
- **Efecto:** Imposibilidad de auditoría y detección de incidentes

---

## 8. ANÁLISIS DE RIESGOS

| Hallazgo | Riesgo Asociado | Impacto | Probabilidad | Nivel de Riesgo |
|----------|-----------------|---------|--------------|-----------------|
| H1 | Pérdida de datos de tickets | Alto | Alta | **ALTO** |
| H2 | Acceso no autorizado a información | Alto | Alta | **ALTO** |
| H3 | Compromiso de contenedores | Medio | Media | **MEDIO** |
| H4 | Falta de trazabilidad | Medio | Alta | **MEDIO** |

### Riesgos Adicionales Identificados
- **Riesgo de Cumplimiento:** Violación de normativas de protección de datos
- **Riesgo Operacional:** Interrupción del servicio de soporte
- **Riesgo Reputacional:** Exposición de información confidencial

---

## 9. RECOMENDACIONES

### RECOMENDACIÓN 1: Implementar Gestión Robusta de Base de Datos
**Vinculada a:** Hallazgo 1

**Acciones Propuestas:**
1. Migrar a PostgreSQL con configuración de alta disponibilidad
2. Implementar respaldos automáticos diarios
3. Configurar replicación de base de datos
4. Establecer procedimientos de recuperación ante desastres

**Responsable:** Equipo de Desarrollo
**Plazo:** 30 días

---

### RECOMENDACIÓN 2: Implementar Autenticación y Autorización
**Vinculada a:** Hallazgo 2

**Acciones Propuestas:**
1. Implementar autenticación JWT
2. Configurar middleware de autorización
3. Establecer roles y permisos por usuario
4. Implementar rate limiting

**Responsable:** Equipo de Desarrollo
**Plazo:** 45 días

---

### RECOMENDACIÓN 3: Fortalecer Seguridad de Contenedores
**Vinculada a:** Hallazgo 3

**Acciones Propuestas:**
1. Ejecutar contenedores con usuarios no privilegiados
2. Implementar límites de recursos (CPU, memoria)
3. Configurar políticas de red restrictivas
4. Implementar escaneo de vulnerabilidades en imágenes

**Responsable:** Equipo de DevOps
**Plazo:** 20 días

---

### RECOMENDACIÓN 4: Establecer Logging de Auditoría
**Vinculada a:** Hallazgo 4

**Acciones Propuestas:**
1. Implementar logging estructurado con Loguru
2. Configurar centralización de logs (ELK Stack)
3. Establecer alertas de seguridad
4. Implementar retención de logs según normativa

**Responsable:** Equipo de Seguridad
**Plazo:** 25 días

---

## 10. CONCLUSIONES

### Estado General del Sistema
El sistema de Asistente de IA Corporativo presenta una **arquitectura sólida** con tecnologías modernas y enfoque innovador, sin embargo, **requiere mejoras significativas en seguridad** antes de ser considerado apto para producción.

### Controles Existentes
- **Adecuados:** Arquitectura RAG, separación de responsabilidades
- **Insuficientes:** Autenticación, logging, gestión de datos
- **Ausentes:** Autorización, monitoreo de seguridad

### Cumplimiento Normativo
El sistema **NO cumple** con los estándares de seguridad requeridos para manejo de información corporativa, requiriendo implementación inmediata de controles de seguridad.

### Recomendación General
**NO RECOMENDAR** el despliegue en producción hasta la implementación de las recomendaciones críticas de seguridad.

---

## 11. PLAN DE ACCIÓN Y SEGUIMIENTO

| Hallazgo | Recomendación | Responsable | Fecha Comprometida | Estado |
|----------|---------------|-------------|-------------------|--------|
| H1 | Implementar gestión robusta de BD | Equipo Desarrollo | 22/11/2025 | Pendiente |
| H2 | Implementar autenticación/autorización | Equipo Desarrollo | 07/12/2025 | Pendiente |
| H3 | Fortalecer seguridad de contenedores | Equipo DevOps | 12/11/2025 | Pendiente |
| H4 | Establecer logging de auditoría | Equipo Seguridad | 17/11/2025 | Pendiente |

### Cronograma de Seguimiento
- **Revisión 1:** 15/11/2025 (Progreso 50%)
- **Revisión 2:** 30/11/2025 (Progreso 80%)
- **Auditoría de Seguimiento:** 15/12/2025 (Verificación completa)

---

## 12. ANEXOS

### Anexo A: Cuestionarios Aplicados
- Cuestionario de Seguridad de Aplicaciones
- Lista de Verificación de Contenedores Docker
- Evaluación de Gestión de Base de Datos

### Anexo B: Evidencias Técnicas
- Capturas de pantalla de errores de base de datos
- Logs de contenedores Docker
- Configuraciones de seguridad actuales

### Anexo C: Documentación Revisada
- Arquitectura del sistema
- Documentación de API
- Configuraciones de despliegue

### Anexo D: Herramientas Utilizadas
- Docker Security Scanning
- OWASP ZAP
- SonarQube (análisis de código)

---

**Documento preparado por:** Equipo de Auditoría de Sistemas  
**Fecha de emisión:** 22/10/2025  
**Versión:** 1.0  
**Clasificación:** Confidencial

---

*Este informe constituye una evaluación independiente del sistema de Asistente de IA Corporativo y debe ser considerado como base para la toma de decisiones sobre su implementación en producción.*
