# 🏛️ ENTREGA 8: Simulación de Comité de Arquitectura — Informe Final
## Financiera Juriscoop S.A. — Proceso CF-JUR-PRO-002 (Embargo y Desembargo)

---

> **Equipo:** Jose Guzman · Juan David Abril · Bryam Diaz
> **Curso:** Arquitectura Empresarial — Universidad de La Sabana
> **Fecha:** Mayo 2026
> **Clasificación:** Uso Académico — Confidencial
> **Marco de referencia:** TOGAF 9.2 · ISO/IEC 27001:2022 · STRIDE · ArchiMate 3.1 · BPMN 2.0

---

## 1. Resumen Ejecutivo

Financiera Juriscoop S.A. Compañía de Financiamiento opera el proceso CF-JUR-PRO-002 de Embargo y Desembargo bajo condiciones de exposición regulatoria activa. El proceso recibe aproximadamente **400 oficios judiciales diarios** y está sujeto a un SLA legal de **3 días hábiles** establecido en el Código General del Proceso (CGP), artículos 593 y 594, con supervisión directa de la Superintendencia Financiera de Colombia (SFC).

El diagnóstico arquitectónico desarrollado a lo largo de este proyecto ha identificado que la arquitectura AS-IS del proceso presenta **vulnerabilidades estructurales en cinco dominios** (negocio, datos, aplicaciones, infraestructura y seguridad) que configuran una exposición regulatoria, operacional y reputacional de carácter crítico. El registro central del proceso en un archivo Excel sin auditoría, la ausencia de un motor de inembargabilidad automatizado, la comunicación inter-áreas por correo corporativo sin trazabilidad sistémica, y la dependencia de BankVisión como punto único de falla constituyen las manifestaciones más críticas de esta vulnerabilidad estructural.

La propuesta arquitectónica documentada en las Entregas 4 a 7 define un **MVP (Minimum Viable Product) de automatización** que aborda estas vulnerabilidades mediante: un módulo de captura estructurada de oficios, un motor de inembargabilidad parametrizado con reglas SFC, una base de datos transaccional con auditoría completa, integración automatizada con BankVisión, y un notificador de SLA con alertas escalonadas. Este MVP se despliega en un modelo **on-premise híbrido** con principios de seguridad Zero Trust, RBAC y cifrado en tránsito y en reposo.

La implementación del MVP transforma el proceso de un modelo de **resiliencia frágil** (basado en el esfuerzo individual de las personas) a un modelo de **resiliencia estructural** (basado en sistemas redundantes, datos persistentes y procesos automatizados), reduciendo el riesgo de incumplimiento regulatorio y habilitando la escalabilidad del proceso ante el crecimiento del volumen de oficios.

---

## 2. Coherencia entre Vistas Arquitectónicas

### 2.1 Articulación de las Cinco Vistas

La solución arquitectónica desarrollada para Juriscoop está documentada en cinco vistas complementarias que se articulan de manera coherente y se validan mutuamente.

**Vista de Negocio (BPMN):** Define el flujo operacional del proceso CF-JUR-PRO-002 en estado AS-IS y TO-BE. Es la vista conductora de toda la arquitectura: cada componente del sistema existe para soportar un paso específico del proceso. La Vista de Negocio conecta directamente con la Vista de Aplicaciones (cada actividad del proceso tiene su contraparte en un componente del MVP) y con la Vista de Información (las entidades de datos son los objetos que el proceso manipula).

**Vista de Información (ERD):** Define las entidades de datos fundamentales: Cliente, ProductoAhorro, OficioMedida, CalculoInembargabilidad, DepositoJudicial y LogAuditoria. Este modelo de datos es la materialización técnica de los objetos de negocio del proceso y es el fundamento sobre el que se construyen los controles de seguridad de datos. La entidad `LogAuditoria` es particularmente relevante: no es un elemento técnico autónomo sino la consecuencia de un requisito que atraviesa tres vistas simultáneamente (Negocio: trazabilidad del proceso; Seguridad: control de Repudiation; Cumplimiento: evidencia ante la SFC).

**Vista de Aplicaciones (C4):** Describe el ecosistema de actores y sistemas (C4 Nivel 1) y los componentes internos del MVP (C4 Nivel 3). Esta vista traduce los requisitos del proceso de negocio en capacidades sistémicas concretas y define las interfaces entre el MVP y los sistemas externos (BankVisión, Banco Agrario). La elección de un Motor de Inembargabilidad como microservicio independiente (ADR-02) se justifica en esta vista por su necesidad de actualización independiente ante cambios normativos.

**Vista de Infraestructura:** Define la topología de despliegue on-premise híbrido, las zonas de red (DMZ, Zona de Aplicaciones, Zona de Datos, Zona Cloud), y los parámetros de disponibilidad (RTO < 4h, RPO < 1h, disponibilidad 99.5%). Esta vista es la consecuencia directa de dos restricciones: la regulatoria (soberanía de datos financieros bajo supervisión SFC) y la arquitectónica (necesidad de modo degradado ante indisponibilidad de BankVisión).

**Vista de Seguridad (STRIDE):** Identifica y clasifica las amenazas por componente (17 amenazas en seis categorías) y define los controles de mitigación. Esta vista valida las decisiones tomadas en las otras cuatro vistas desde la perspectiva de seguridad: confirma que la arquitectura de red (DMZ, WAF) responde a amenazas de DoS; que el RBAC y MFA responden a amenazas de Spoofing y Escalada de Privilegios; y que los logs inmutables responden a amenazas de Tampering y Repudiation.

### 2.2 Vínculos de Coherencia entre Vistas

| Relación entre Vistas | Mecanismo de Coherencia | Ejemplo Concreto |
|----------------------|------------------------|-----------------|
| Negocio → Aplicaciones | Cada actividad del proceso tiene un componente del MVP | "Calcular inembargabilidad" → Motor de Inembargabilidad |
| Aplicaciones → Datos | Cada componente opera sobre entidades definidas en el ERD | Motor de Inembargabilidad → entidad `CalculoInembargabilidad` |
| Datos → Seguridad | Los datos clasificados como PII activan controles específicos | `Cliente.num_doc` → cifrado en reposo + RBAC |
| Infraestructura → Seguridad | La topología de red implementa el perímetro de seguridad | Zona DMZ → control de DoS (WAF + Rate Limiting) |
| Negocio → Seguridad | El SLA legal condiciona la criticidad de los controles | 3 días hábiles → alerta de Repudiation + expediente inmutable |

---

## 3. Conexión con Objetivos Estratégicos del Cliente

### 3.1 Objetivos Estratégicos de Juriscoop

| Objetivo Estratégico | Vista Arquitectónica que lo Soporta | Entregable de Evidencia |
|---------------------|-------------------------------------|------------------------|
| **Cumplimiento del SLA regulatorio (3 días hábiles)** | Negocio TO-BE, Aplicaciones (Notificador SLA) | E4: Infraestructura propuesta; E7: Vista de Negocio |
| **Reducción de riesgo operacional por error humano** | Aplicaciones (Motor de Inembargabilidad), Negocio TO-BE | E4: Diagnóstico; Análisis de Riesgos: R-01, R-02 |
| **Cumplimiento normativo ante SFC y Ley 1581** | Seguridad, Datos (LogAuditoria) | E5: STRIDE; E6: Checklist normativo |
| **Trazabilidad completa del proceso judicial** | Datos (ERD + LogAuditoria), Seguridad (Repudiation) | E7: Vista de Información; Análisis de Riesgos: R-06 |
| **Protección de datos personales de clientes** | Seguridad (cifrado, RBAC), Datos (PII) | E5: STRIDE; E6: Ley 1581 |
| **Continuidad operacional ante incidentes** | Infraestructura (modo degradado, RPO/RTO) | E4: Infraestructura; Análisis de Riesgos: R-08 |
| **Escalabilidad del proceso sin escalar personal** | Aplicaciones (automatización), Infraestructura | E4: MVP; Análisis de Riesgos: R-11 |

### 3.2 Impacto Esperado por la Implementación del MVP

| KPI | Estado AS-IS | Meta TO-BE (MVP) | Reducción de Riesgo |
|-----|-------------|-----------------|---------------------|
| Tasa de cumplimiento SLA (3 días) | ~85% | 100% | R-01: Crítico → Residual |
| Precisión cálculo inembargabilidad | ~95% (manual) | 100% (algorítmico) | R-02: Crítico → Residual |
| Disponibilidad del proceso | ~98% | 99.5% | R-08: Crítico → Alto |
| Tiempo de validación por oficio | Variable (horas) | < 5 minutos (automatizado) | R-11: Alto → Bajo |
| Cumplimiento Ley 1581/2012 | 35% | > 85% | R-07, R-16: Crítico → Medio |
| Incidentes de seguridad documentados | No medido | < 2/año | R-05, R-06: Crítico → Residual |

---

## 4. Suficiencia Técnica y Argumentación de Decisiones

### 4.1 Justificación del Modelo de Despliegue On-Premise Híbrido

La elección de un modelo on-premise para los componentes críticos del MVP (Base de Datos Transaccional, Motor de Inembargabilidad, Middleware BankVisión) responde a dos restricciones no negociables: la regulatoria y la arquitectónica.

Desde la perspectiva regulatoria, la SFC ejerce supervisión sobre la gestión de datos financieros y exige que las entidades financieras mantengan control directo sobre los datos sensibles de sus clientes. La externalización completa a la nube de datos de embargos que incluyen PII financiera y judicial introduciría complejidades de cumplimiento con la Ley 1581 y las circulares de la SFC que superan los beneficios operacionales de una arquitectura cloud-first para el volumen de datos del proceso CF-JUR-PRO-002.

Desde la perspectiva arquitectónica, la integración con BankVisión —que opera on-premise sin APIs cloud-native— requiere conectividad de red interna de baja latencia que es más eficiente de implementar en infraestructura local. Un MVP completamente cloud requeriría un túnel VPN de alta disponibilidad hacia el core bancario, introduciendo una dependencia de red adicional que puede comprometer el SLA del proceso.

Los servicios de monitoreo externo y notificaciones push se ubicaron en la nube precisamente porque no tienen acceso a datos sensibles y se benefician de la elasticidad y disponibilidad de los proveedores cloud sin introducir riesgos regulatorios.

### 4.2 Justificación del Motor de Inembargabilidad como Microservicio

La decisión de implementar el Motor de Inembargabilidad como un microservicio REST independiente (en lugar de integrar esta lógica en el módulo principal del MVP) responde al principio arquitectónico de **separación de responsabilidades** y a la naturaleza cambiante de las reglas normativas.

Las circulares de la SFC que establecen los montos de inembargabilidad (UVT, límites por tipo de producto) se actualizan con una frecuencia que puede ser superior a los ciclos de despliegue del sistema. Si la lógica de inembargabilidad estuviera embebida en el MVP monolítico, cada actualización normativa requeriría un ciclo completo de desarrollo, pruebas y despliegue del sistema. Al implementarla como microservicio con reglas parametrizables, la actualización normativa se convierte en un cambio de configuración que puede ser validado jurídicamente e implementado en producción sin afectar al resto del sistema.

Esta decisión tiene también implicaciones en la Vista de Seguridad: el microservicio puede ser auditado de manera independiente, su superficie de ataque es menor que la del sistema completo, y sus pruebas de regresión pueden ejecutarse de manera aislada ante cada cambio de parámetro normativo.

### 4.3 Justificación del Principio Zero Trust

La adopción del principio Zero Trust como modelo de seguridad del MVP contrasta directamente con el modelo de confianza implícita de la arquitectura AS-IS, donde cualquier usuario con credenciales básicas tiene acceso amplio a BankVisión y al Excel de la Base Embargos.

Zero Trust no implica desconfianza hacia los usuarios legítimos; implica verificación continua de la identidad y los permisos antes de cada acceso, independientemente de si el usuario está dentro o fuera de la red corporativa. En el contexto del proceso CF-JUR-PRO-002, este principio es especialmente relevante porque el proceso involucra datos de alta sensibilidad (PII financiera y judicial) accesibles por múltiples roles con responsabilidades diferentes. La posibilidad de que las credenciales de un usuario operativo sean comprometidas (Spoofing), o de que un usuario interno acceda a funciones que exceden su rol (Escalada de Privilegios), justifica plenamente la implementación de MFA universal, RBAC estricto y verificación en cada transición de estado del proceso.

### 4.4 Justificación del Modelo Human-in-the-Loop

El diseño del MVP preserva deliberadamente al Analista Jurídico como aprobador final de cada respuesta oficial a un oficio de embargo, a pesar de que técnicamente el sistema podría automatizar también ese paso.

Esta decisión responde a la naturaleza jurídica del proceso: una respuesta a un oficio de embargo es un acto con consecuencias directas sobre los derechos económicos de un ciudadano y puede generar responsabilidad institucional ante el juzgado emisor. La delegación completa de este acto a un algoritmo, sin supervisión humana calificada, introduciría riesgos legales que exceden los beneficios operacionales de la automatización total.

El MVP está diseñado para que la intervención del Analista Jurídico sea eficiente: el sistema le presenta un expediente pre-procesado con el resultado del Motor de Inembargabilidad, el histórico del cliente, los documentos del oficio y una recomendación de acción. El analista revisa, valida y aprueba en un flujo de trabajo optimizado, sin necesidad de consultar BankVisión manualmente ni calcular montos. Esta arquitectura convierte la supervisión humana en un control de calidad de alto valor, no en un cuello de botella operacional.

---

## 5. Matriz de Riesgos Arquitectónicos

El análisis de riesgos desarrollado en el marco del proyecto identificó **17 riesgos** distribuidos en seis dominios de arquitectura empresarial. La matriz a continuación reproduce la totalidad de los riesgos con su evaluación de probabilidad, impacto y prioridad de mitigación.

| # | Riesgo | Causa Raíz | Probabilidad | Impacto | Criticidad | Dominio | Prioridad |
|---|--------|------------|-------------|---------|------------|---------|-----------|
| R-01 | Incumplimiento SLA legal 3 días hábiles | Seguimiento manual sin alertas automáticas | Alta | Crítico | **Crítico** | Procesos / Negocio | **Inmediata** |
| R-02 | Error en cálculo de inembargabilidad | Cálculo manual sin validación algorítmica | Alta | Crítico | **Crítico** | Negocio / Procesos / Datos | **Inmediata** |
| R-03 | Pérdida o corrupción de la Base Embargos (Excel) | Repositorio frágil sin integridad de datos | Media | Crítico | **Crítico** | Datos / Infraestructura | **Inmediata** |
| R-04 | Falsificación de oficios judiciales (Spoofing) | Ausencia de verificación criptográfica | Baja | Alto | **Alto** | Seguridad / Negocio | **Urgente** |
| R-05 | Manipulación de registros en Excel (Tampering) | Sin control de versiones ni logs de auditoría | Alta | Crítico | **Crítico** | Seguridad / Datos | **Inmediata** |
| R-06 | Repudio de acciones ante entes reguladores | Ausencia de evidencia digital irrefutable | Alta | Crítico | **Crítico** | Gobierno TI / Seguridad | **Inmediata** |
| R-07 | Exposición de PII financiera y judicial | Transmisión de datos sensibles por correo no cifrado | Alta | Crítico | **Crítico** | Seguridad / Datos | **Inmediata** |
| R-08 | Indisponibilidad de BankVisión (SPOF) | Arquitectura on-premise sin redundancia | Media | Crítico | **Crítico** | Infraestructura / Procesos | **Urgente** |
| R-09 | Escalada de privilegios en BankVisión y Excel | Ausencia de RBAC estricto y segregación de funciones | Media | Alto | **Alto** | Seguridad / Gobierno TI | **Urgente** |
| R-10 | Dependencia de conocimiento tácito del equipo | Ausencia de sistematización del proceso | Alta | Alto | **Alto** | Negocio / Gobierno TI | **Urgente** |
| R-11 | Saturación operacional en picos de demanda | Proceso manual sin capacidad de escala automática | Alta | Alto | **Alto** | Procesos / Infraestructura | **Urgente** |
| R-12 | Ausencia de gobierno de cambios regulatorios | Sin proceso formal de actualización ante nuevas circulares SFC | Media | Alto | **Alto** | Gobierno TI / Cumplimiento | **Estratégico** |
| R-13 | Duplicidad y silos de información inter-áreas | Múltiples repositorios no integrados; correo como canal de datos | Alta | Alto | **Alto** | Datos / Procesos | **Urgente** |
| R-14 | Falta de observabilidad del proceso | Sin dashboards, métricas ni alertas en tiempo real | Alta | Medio | **Medio** | Gobierno TI / Infraestructura | **Estratégico** |
| R-15 | Vendor lock-in y obsolescencia del core BankVisión | Arquitectura legacy sin APIs estándar | Baja | Medio | **Medio** | Aplicaciones / Estrategia | **Estratégico** |
| R-16 | Incumplimiento de Ley 1581 por gestión sin consentimiento | Ausencia de gestión sistematizada de consentimientos y derechos ARCO | Media | Alto | **Alto** | Cumplimiento / Datos | **Urgente** |
| R-17 | Denegación de servicio por volumen inusual de oficios | Ausencia de mecanismo de gestión de carga | Media | Alto | **Alto** | Infraestructura / Procesos | **Urgente** |

### 5.1 Distribución de Riesgos por Criticidad

| Criticidad | Cantidad | Riesgos |
|-----------|----------|---------|
| 🔴 **Crítico** | 6 | R-01, R-02, R-03, R-05, R-06, R-07 |
| 🟠 **Alto** | 9 | R-04, R-08, R-09, R-10, R-11, R-12, R-13, R-16, R-17 |
| 🟡 **Medio** | 2 | R-14, R-15 |

### 5.2 Mitigaciones por Prioridad

**Prioridad Inmediata (R-01, R-02, R-03, R-05, R-06, R-07):**
Estos seis riesgos combinan alta probabilidad con criticidad máxima y exposición regulatoria directa. Son la condición mínima de puesta en producción del MVP. Sin resolver estos riesgos, el sistema no reduce sustancialmente la exposición actual de la entidad.

- R-01/R-02: Motor de Inembargabilidad + Notificador SLA automatizados
- R-03/R-05: Base de datos transaccional reemplaza el Excel
- R-06: Logs inmutables con timestamping + SIEM
- R-07: Cifrado TLS + cifrado en reposo + RBAC

**Prioridad Urgente (R-04, R-08, R-09, R-10, R-11, R-13, R-16, R-17):**
Deben resolverse en las primeras semanas posteriores al despliegue del MVP. No bloquean el go-live pero representan vulnerabilidades activas que deben cerrarse en el corto plazo.

**Prioridad Estratégica (R-12, R-14, R-15):**
Configuran la hoja de ruta de madurez arquitectónica a mediano plazo: gobierno de cambios normativos, observabilidad avanzada y desacoplamiento del core bancario.

---

## 6. Vistas Arquitectónicas Finales

La documentación completa de las vistas arquitectónicas de la solución se encuentra en la **Entrega 7: Integración de Vistas de Arquitectura**, que constituye el repositorio canónico de los diagramas y narrativas de cada vista.

### 6.1 Resumen de Vistas por Dominio

| Vista | Diagrama Principal | Herramienta | Estado |
|-------|-------------------|-------------|--------|
| **Negocio AS-IS** | BPMN — Flujo CF-JUR-PRO-002 actual | BPMN 2.0 / Mermaid | Documentado en E7 |
| **Negocio TO-BE** | BPMN — Flujo MVP automatizado | BPMN 2.0 / Mermaid | Documentado en E7 |
| **Información** | ERD — Modelo de datos | Mermaid erDiagram | Documentado en E7 |
| **Aplicaciones C4-L1** | C4 Contexto — Ecosistema del sistema | C4 Model / Mermaid | Documentado en E7; imagen en E4 |
| **Aplicaciones C4-L3** | C4 Componentes — Módulos del MVP | C4 Model / Mermaid | Documentado en E7; imagen en E4 |
| **Infraestructura** | Topología on-premise híbrida | Mermaid flowchart | Documentado en E7; imagen en E4 |
| **Seguridad** | Mapa STRIDE por componente | STRIDE / Mermaid | Documentado en E7; modelo en E5 |

### 6.2 Repositorio de Artefactos del Proyecto

| Entregable | Contenido | Ubicación |
|-----------|-----------|-----------|
| **Entrega 4** | Infraestructura AS-IS, C4 Contexto, C4 Componentes, Red | `/Entrega 4/Informe.md` + imágenes |
| **Entrega 5** | Análisis STRIDE completo, 17 amenazas, plan de mitigación | `/Entrega 5/Informe.md` |
| **Entrega 6** | Checklist normativo: Ley 1581, ISO 27001, CGP, SFC | `/Entrega 6/Informe.md` |
| **Entrega 7** | Integración de 5 vistas con diagramas y narrativa | `/Entrega 7/Informe.md` |
| **Análisis de Riesgos** | Matriz de 17 riesgos, Gap Analysis, arquitectura de mitigación | `/Analisisi de riesgos/Informe.md` |
| **Entrega 8** | Informe final de comité de arquitectura (este documento) | `/Entrega 8/Informe.md` |

---

## 7. Reflexiones Individuales

### 7.1 José Guzman

El desarrollo de este proyecto ha representado una transformación en la manera en que comprendo el rol de la tecnología dentro de una organización. Antes de abordar la arquitectura empresarial como disciplina, tendía a pensar en los sistemas de información como soluciones técnicas a problemas técnicos. Trabajar con el caso de Juriscoop y el proceso CF-JUR-PRO-002 me permitió entender que la tecnología es, fundamentalmente, una respuesta a una necesidad organizacional con implicaciones regulatorias, operacionales y humanas. El ejercicio de construir las vistas de infraestructura y aplicaciones me resultó especialmente revelador: cada decisión de diseño —dónde ubicar el servidor, cómo integrar con BankVisión, qué motor de base de datos usar— no era una decisión técnica aislada, sino una decisión con consecuencias en la seguridad de los datos de los clientes, en el cumplimiento de la SFC y en la sostenibilidad operacional del proceso. Llevo de este proceso el aprendizaje de que documentar una arquitectura es, en esencia, documentar las razones de cada decisión: el diagrama no es el objetivo; es el lenguaje mediante el cual se hace explícito el razonamiento que de otro modo permanecería tácito.

### 7.2 Juan David Abril

Mi mayor aprendizaje en este proyecto fue comprender la dimensión normativa de la arquitectura empresarial. Cuando empezamos a revisar el proceso de Juriscoop, la cantidad de regulaciones aplicables —Ley 1581, Código General del Proceso, Circulares de la SFC, ISO 27001— me pareció abrumadora. Con el tiempo, sin embargo, fui entendiendo que esas regulaciones no son restricciones externas al diseño arquitectónico: son requisitos funcionales del sistema. El SLA de 3 días hábiles no es una opción de diseño; es una obligación legal que define la urgencia del Notificador SLA. El cálculo de inembargabilidad no es una funcionalidad adicional; es el core del servicio que Juriscoop debe prestar ante el sistema judicial. Esta comprensión cambió completamente mi lectura de los checklists normativos de la Entrega 6: detrás de cada brecha identificada no había un problema de cumplimiento burocrático, sino una vulnerabilidad real en la experiencia de un cliente en situación de vulnerabilidad financiera. Ese reconocimiento le dio a cada decisión de diseño un peso que no había tenido antes.

### 7.3 Bryam Diaz

El análisis de seguridad con STRIDE fue el componente del proyecto que más impacto tuvo en mi formación. Antes de este ejercicio, asociaba la seguridad de sistemas principalmente con firewalls y antivirus. El modelo STRIDE me mostró que la seguridad es, ante todo, una disciplina de razonamiento sistemático sobre las formas en que un sistema puede fallar: no solo ante atacantes externos, sino ante errores internos, comportamientos inesperados de los usuarios y decisiones de diseño inadecuadas. Aplicar STRIDE al proceso de Juriscoop me permitió ver que la mayor amenaza no era necesariamente un ciberataque sofisticado, sino algo tan cotidiano como un archivo Excel sin control de acceso o un correo electrónico con información de clientes enviado a la dirección equivocada. El concepto de Zero Trust me pareció especialmente valioso porque sintetiza una postura de diseño: no asumir que el contexto es seguro, sino verificar continuamente. Esa postura, aplicada no solo a sistemas sino al diseño de procesos, es una de las ideas más prácticas que me llevo de esta materia.

---

## 📚 Referencias

Véase archivo `referencias.md` para las fuentes sobre TOGAF, ISO 27001, normativa SFC, STRIDE y marcos de arquitectura empresarial utilizados en este informe.

---

*Documento preparado con base en los entregables del proyecto de Arquitectura Empresarial para Financiera Juriscoop S.A., Proceso CF-JUR-PRO-002. Universidad de La Sabana, Mayo 2026.*
