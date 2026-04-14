# ⚖️ ENTREGA 6: Evaluación de Cumplimiento Normativo
## Financiera Juriscoop S.A. - Proceso CF-JUR-PRO-002 (Embargo y Desembargo)

---

## 📋 Objetivo

Verificar los aspectos legales, normativos y de cumplimiento que aplican al sistema de Embargo y Desembargo de Financiera Juriscoop S.A., utilizando listas de control basadas en marcos como:
- **ISO/IEC 27001:** Gestión de seguridad de la información
- **Ley 1581/2012:** Protección de datos personales en Colombia (Habeas Data)
- **Dirección de Impuestos y Aduanas Nacionales (DIAN):** Normativa tributaria
- **Superintendencia Financiera de Colombia (SFC):** Circulares y decretos regulatorios
- **Código General del Proceso (CGP):** Artículos 593/594 sobre embargos
- **Resolución 1530/2022 (SFC):** Sobre gestión de riesgos operacionales

---

## 1. Contexto Normativo Aplicable

### 1.1 Normativa por Jurisdicción

| Normativa | Aplicabilidad | Áreas del Proceso |
|-----------|---------------|-------------------|
| **Ley 1581/2012** | 🔴 CRÍTICA | Protección datos personales (DNI clientes) |
| **Decreto 1377/2013** | 🔴 CRÍTICA | Reglamento Ley 1581 (consentimiento, derecho acceso) |
| **Código General del Proceso (Art. 593/594)** | 🔴 CRÍTICA | Procedimiento legal embargo/desembargo |
| **Circular Externa 022/2014 (SFC)** | 🔴 CRÍTICA | Montos inembargables por tipo de producto |
| **Resolución 1530/2022 (SFC)** | 🟡 CRÍTICA | Gestión de riesgos operacionales |
| **Decreto 1074/2015** | 🟡 ALTA | Código de comercio, operaciones financieras |
| **Resolución 1406/2007 (MinTIC)** | 🟡 MEDIA | Seguridad de la información |
| **Norma ISO/IEC 27001:2022** | 🟡 MEDIA | Certificación sistemas información |
| **Habeas Data (jurisprudencia)** | 🟡 ALTA | Derechos sobre datos personales |

### 1.2 Autoridades Fiscalizadoras
- **SFC:** Supervisa cumplimiento de circulares sobre inembargabilidad
- **Superintendencia de Vigilancia y Seguridad Privada (SVSP):** Datos personales en sistemas transaccionales
- **Juzgados:** Validan legitimidad de respuestas a oficios
- **Defensoría del Consumidor Financiero:** Quejas sobre retenciones indebidas

---

## 2. Checklist de Cumplimiento Normativo

### 2.1 Ley 1581/2012 - Protección de Datos Personales

#### 2.1.1 Consentimiento y Legitimidad

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Consentimiento previo del cliente** | No documentado sistémicamente | ❌ NO | Alta | Política explícita en contrato apertura cuenta: "autorizo embargo según procedimiento legal" | 1 mes |
| **Aviso de tratamiento de datos** | Genérico en contrato | ⚠️ PARCIAL | Media | Especificar propósito de embargo, base legal (CGP), duración retención | 2 sem |
| **Claridad en finalidad del procesamiento** | Vago ("procesos judiciales") | ⚠️ PARCIAL | Media | Detallar: "Procesar embargo conforme CGP Art 593, retener hasta desembargo judicial" | 2 sem |
| **Base legal para procesamiento** | Mencionada implícitamente | ⚠️ PARCIAL | Media | Documentar explícitamente: Ley 1581, CGP, Circular SFC como base legal | Inmediato |

#### 2.1.2 Derechos del Titular

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Derecho de acceso a datos** | Manual, lento (3-5 días) | ❌ NO | Alta | Crear portal web donde cliente vea sus embargos activos en tiempo real | 1 mes |
| **Derecho de rectificación** | No hay proceso definido | ❌ NO | Alta | Protocolo: cliente reporta error → validación → corrección en BD | 2 sem |
| **Derecho de supresión** | No aplica (dato permanente hasta desembargo) | ✅ N/A | Baja | Documentar excepción legal: retención obligatoria por CGP | Inmediato |
| **Derecho a no ser perfilado** | No aplicable (sin ML actualmente) | ✅ N/A | Baja | Si implementan ML futuro, revisar normativa | A futuro |
| **Derecho a presentar reclamaciones** | Por formulario físico (lento) | ⚠️ PARCIAL | Media | Crear buzón digital, responder en máximo 10 días (SLA legal) | 1 mes |

#### 2.1.3 Responsabilidades del Responsable (Juriscoop)

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Política de Privacidad** | Existe pero no específica para embargos | ⚠️ PARCIAL | Media | Actualizar con procedimiento de embargo, retención y desembargo | 2 sem |
| **Registro de actividades de procesamiento** | No existe registro formal | ❌ NO | Alta | Crear Base de Datos de Tratamientos (BDTA): qué datos, para qué, dónde | 1 mes |
| **Medidas de seguridad (Anexo 1 Decreto 1377)** | Parciales (sin cifrado sistemático) | ⚠️ PARCIAL | Alta | Implementar: cifrado datos en reposo, TLS en tránsito, auditoría, MFA | 2 meses |
| **Respuesta a requerimientos de autoridades** | Manual, variable en tiempo | ⚠️ PARCIAL | Media | Protocolo: máximo 5 días para requerimientossyper visor | 1 mes |
| **Incident Response Plan** | No documentado | ❌ NO | Media | Plan escrito: cómo responder ante brecha de datos en máximo 72 horas | 2 sem |

---

### 2.2 ISO/IEC 27001:2022 - Gestión de Seguridad de la Información

#### 2.2.1 Organización de Seguridad

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Comité de Seguridad de la Información** | No existe formalmente | ❌ NO | Alta | Constituir comité: CIO, Legal, Ops, Audit, Compliance | 1 mes |
| **Política de Seguridad de la Información** | Genérica, no auditable | ⚠️ PARCIAL | Media | Política específica: objetivos SMART, roles, ciclo de revisión anual | 2 sem |
| **Roles y responsabilidades (RACI)** | Implícitos, no documentados | ❌ NO | Alta | Matriz RACI: quién es accountable, responsible, consulted, informed | 2 sem |
| **Comunicación de seguridad al personal** | Entrenamientos anuales genéricos | ⚠️ PARCIAL | Media | Entrenamientos trimestrales específicos STRIDE, MFA, phishing | 1 mes |

#### 2.2.2 Control de Acceso (ISO 27001 A.8)

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Autenticación MFA** | Solo usuario/password | ❌ NO | Crítica | MFA obligatorio en BankVisión, MVP, Correo corporativo | 2 sem |
| **Control de acceso basado en roles (RBAC)** | Parcial en BankVisión | ⚠️ PARCIAL | Alta | Revisar y enforcer RBAC: Jurídica solo aprueba, Ops solo consulta | 2 sem |
| **Revisión periódica de accesos** | Ocasional, ad-hoc | ❌ NO | Alta | Audit trimestral: quién tiene qué permisos, validar necesidad | 1 mes |
| **Revocar acceso al retiro de empleado** | Manual, variable | ⚠️ PARCIAL | Media | Automatizar: RRHH -> AD disable en 2 horas | 1 mes |

#### 2.2.3 Criptografía (ISO 27001 A.10)

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Cifrado en tránsito (TLS)** | HTTP en algunas conexiones | ❌ NO | Crítica | Enforcar TLS 1.2+ en todas las APIs: MVP ↔ BankVisión | 2 sem |
| **Cifrado en reposo (BD)** | No implementado en Base Embargos | ❌ NO | Alta | Cifrado de DB de embargos (datos personales de clientes) | 1 mes |
| **Gestión de claves (PKI)** | No formalizada | ❌ NO | Alta | Política: rotación de keys cada 90 días, almacenamiento secure (HSM) | 1 mes |
| **Firma digital certificados** | Manual en correos | ⚠️ PARCIAL | Media | Firma digital reconocida por MinTIC en oficios críticos | 2 meses |

#### 2.2.4 Operaciones y Disponibilidad (ISO 27001 A.17)

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Backup y recuperación** | Diario, pero no testado | ⚠️ PARCIAL | Media | Plan de recuperación: RTO <1h, RPO <15min; test trimestral | 1 mes |
| **Control de cambios** | Manual, sin documentación | ❌ NO | Alta | Sistema de tickets: cambios autorizados, testeados, documentados | 2 sem |
| **Monitoreo y logging** | Básico, sin SIEM | ⚠️ PARCIAL | Media | Implementar ELK o Splunk: logs centralizados, alertas en tiempo real | 2 meses |
| **Continuidad del negocio** | Documentada pero no actualizada | ⚠️ PARCIAL | Media | Revisar BCP: incluir MVP, test de failover anual | 1 mes |

---

### 2.3 CGP Art. 593/594 - Procedimiento Embargo y Desembargo

#### 2.3.1 Legitimidad de la Medida

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Validación de autoridad emisora** | Manual, solo revisión visual | ❌ NO | Crítica | Cross-check DB juzgados: verificar radicado válido en OVJUD | Inmediato |
| **Verificación de cliente embargado** | Por DNI en BankVisión | ✅ SÍ | Baja | Mantener, asegurar que DNI sea exacto en BD | Continuo |
| **Monto judicialmente válido** | Revisión abogado | ⚠️ PARCIAL | Media | Validación automática en MVP: monto >0, <=saldo total cliente | 2 sem |

#### 2.3.2 Cumplimiento de Tiempos

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Respuesta en 3 días hábiles** | Frecuentemente incumplido | ❌ NO | Crítica | MVP con alertas automáticas + notificador SLA | 1 mes |
| **Documentación de respuesta** | Formulario manual Banco Agrario | ⚠️ PARCIAL | Media | Template automatizado en MVP, pre-llenado con datos validados | 2 sem |
| **Comunicación a autoridad** | Manual por correo | ⚠️ PARCIAL | Media | Integración API Banco Agrario (Fase 2), confirmación de entrega digital | 2 meses |

#### 2.3.3 Inembargabilidad (SFC)

| Elemento | Estado ACTUAL | Cumplimiento | Brecha | Acción Correctiva | Plazo |
|----------|---------------|--------------|--------|------------------|-------|
| **Cálculo de límites SFC** | Manual por abogado (calculadora) | ❌ NO | Crítica | Motor de reglas: parametriza límites según Circular SFC (ej. UVT) | 2 sem |
| **Actualización de límites** | Cambios manuales anuales | ⚠️ PARCIAL | Media | Automatizar: UVT actualiza anualmente, sistema recalcula automáticamente | 1 mes |
| **Auditoría de decisiones** | No hay trazabilidad | ❌ NO | Alta | Todas las decisiones de inembargabilidad quedan registradas con justificación | 2 sem |

---

### 2.4 Circular SFC 022/2014 - Montos Inembargables

#### Aplicabilidad al Proceso

| Aplicativo | Límite Inembargable | Validación ACTUAL | Cumplimiento | Acción |
|------------|-------------------| --|--------|---------|
| **Cuenta de Ahorros** | Min(saldo, 5 UVT) | Manual | ❌ NO | Motor de reglas: lógica: embargo = saldo - UVT_vigente * 5 |
| **Cuenta Corriente** | Min(saldo, 5 UVT) | Manual | ❌ NO | Igual como arriba |  
| **CDT/Inversiones** | Parcialmente embargable (depende contrato) | Manual | ⚠️ | Consulta con Jurídica, MVP genera alerta "Revisar CDD" |
| **Pensiones/Cesantías** | 100% inembargable (Art. 593 CGP) | Manual | ⚠️ PARCIAL | Motor: detecta tipo producto, bloquea embargo automáticamente |

---

### 2.5 Resolución 1530/2022 (SFC) - Gestión de Riesgos Operacionales

#### 2.5.1 Eventos de Riesgo Operacional

| Tipo de Evento | Escenario | ACTUAL | Cumplimiento | Acción |
|----------------|-----------|--------|--------------|--------|
| **Riesgo de procesos** | Embargo incorrecto (SLA vencido) | Frecuente | ❌ NO | MVP alertas SLA, reduce a <1% |
| **Riesgo de personas** | Error humano cálculo inembargabilidad | Frecuente | ❌ NO | Motor de reglas automatizado, auditoría |
| **Riesgo de tecnología** | Base Embargos corrompida (Excel) | Ocasional | ❌ NO | BD transaccional con backup diario |
| **Riesgo de cumplimiento** | Incumplimiento normativa SFC | Ocasional | ❌ NO | Validaciones automáticas, auditoría de cumplimiento |
| **Riesgo externo** | Falsificación oficio judicial | Raro | ⚠️ | Verificación callback + firma digital |

#### 2.5.2 Indicadores de Cumplimiento (KPIs Operacionales)

| KPI | Meta | ACTUAL | Brecha | Target |
|-----|------|--------|--------|--------|
| **Tasa de embargos respondidos en SLA** | 100% | ~85% | -15% | 100% en 3 meses con MVP |
| **Tasa de inembargabilidades calculadas correctamente** | 100% | ~95% (manuales) | -5% | 100% con motor de reglas |
| **Disponibilidad del sistema** | 99.5% | ~98% (BankVisión) | -1.5% | 99.5% con redundancia |
| **Incidents de seguridad**: | <2/año | Data no clara | Desconocida | 0 con MFA + cifrado |
| **Reclamaciones por retenciones indebidas** | <5/año | Desconocida | Desconocida | Medir con MVP |

---

### 2.6 Habeas Data y Legislación Complementaria

#### Jurisprudencia Constitucional (Sentencias CC)

| Sentencia | Principio | ACTUAL | Cumplimiento | Acción |
|-----------|-----------|--------|--------------|--------|
| **T-414/1992** | Derecho acceso a datos personal | Lento (3-5 días) | ⚠️ PARCIAL | Portal web: acceso inmediato a embargos propios |
| **T-729/2002** | Veracidad y actualidad de datos | BD Excel no auditada | ❌ NO | BD relacional con versionamiento |
| **T-747/2003** | Derecho al olvido (excepto casos justificados) | No aplica por CGP | ✅ N/A | Documentar excepción legal |
| **T-284/2017** | Protección de datos menores | N/A (embargados son mayores) | ✅ N/A | Revisar si aplica en caso de menores |

---

## 3. Matriz de Cumplimiento Consolidada

| Área Normativa | Cumplimiento % | Estado | Brecha Crítica | Brecha Alta | Brecha Media | Plazo Regularización |
|---|---|---|---|---|---|---|
| **Ley 1581/2012** | 35% | 🔴 CRÍTICO | 3 | 4 | 3 | 2 meses |
| **ISO 27001** | 25% | 🔴 CRÍTICO | 2 | 6 | 4 | 3 meses |
| **CGP Art. 593/594** | 45% | 🟠 GRAVE | 2 | 3 | 1 | 1 mes |
| **SFC Circular 022/2014** | 30% | 🔴 CRÍTICO | 1 | 2 | 0 | 2 sem |
| **Resolución 1530/2022 (SFC)** | 20% | 🔴 CRÍTICO | 2 | 1 | 2 | 2 meses |
| **TOTAL** | **31%** | 🔴 CRÍTICO | **10 Brechas** | **16 Brechas** | **10 Brechas** | **3 meses** |

---

## 4. Plan de Acción por Normativa

### 4.1 Ley 1581/2012 - URGENT (Semana 1-4)

**Brecha Crítica #1:** Sin consentimiento documentado del cliente
- Acción: Actualizar contrato de apertura incluir cláusula explícita embargo
- Responsabilidad: Legal + Comercial
- Plazo: 2 semanas

**Brecha Crítica #2:** Sin medidas de seguridad sistematicas
- Acción: Implementar encriptación, MFA, auditoría (ver ISO 27001)
- Responsabilidad: TI + Seguridad
- Plazo: 2 meses

**Brecha Crítica #3:** Sin derechos de datos efectivos
- Acción: Portal web auto-servicio cliente, buzón reclamaciones digital
- Responsabilidad: Producto + TI
- Plazo: 1 mes

### 4.2ISO 27001 - URGENT (Mes 1-3)

**Brecha Crítica #1:** Sin MFA en accesos a datos sensibles
- Acción: MFA en BankVisión, MVP, Correo corporativo
- Responsabilidad: TI Seguridad
- Plazo: 2 semanas

**Brecha Crítica #2:** Sin cifrado de datos personales
- Acción: Cifrado BD Embargos + TLS APIs
- Responsabilidad: TI Infraestructura + Desarrollo
- Plazo: 1 mes

**Brecha Alta #1:** Sin SIEM/auditoría centralizada
- Acción: Implementar ELK/Splunk para logs centralizados
- Responsabilidad: TI
- Plazo: 2 meses

### 4.3 CGP + SFC - IMMEDIATE (Semana 1)

**Brecha Crítica:** Motor de inembargabilidad no automatizado
- Acción: Parametrizar cálculo en MVP antes de go-live
- Responsabilidad: Desarrollo + Legal
- Plazo: 2 semanas

**Brecha Alta:** SLA de 3 días sin monitoreo
- Acción: Notificador automático, alertas antes de vencimiento
- Responsabilidad: Producto + Operaciones
- Plazo: 1 mes

---

## 5. Recomendaciones de Gobernanza

### 5.1 Comité de Cumplimiento
**Frecuencia:** Mensual (escalación semanal si hay incidentes)
**Miembros:** CIO, Director Legal, Director Operaciones, DPO (Data Protection Officer), Auditoría Interna
**Agenda:**
- Estado de brechas normativas
- Auditoría de controles implementados
- Cambios normativos de SFC/DIAN por implementar
- Incidents de seguridad y lecciones aprendidas

### 5.2 Data Protection Officer (DPO) / Officer Compliance
**Rol:** Designadamente responsable de cumplimiento Ley 1581
**Responsabilidades:**
- Auditoría Data Protection Impact Assessments (DPIA)
- Gestión derechos de datos (acceso, rectificación, supresión)
- Respuesta a requerimientos de autoridades
- Capacitaciones sobre privacidad

### 5.3 Ciclo de Auditoría
- **Trimestral:** Accesos RBAC, logs de cambios en BD
- **Semestral:** Cifrado keys, certificados TLS, backups
- **Anual:** Penetration test, auditoría externa ISO 27001, DPIA actualizada

---

## 6. Investigación: Normativa del Sector Financiero en Colombia

### 6.1 Autoridades Regulatorias

| Autoridad | Competencia | Relevancia para Juriscoop |
|-----------|-------------|--------------------------|
| **SFC** | Supervisa entidades financieras, circulares sobre operaciones | CRÍTICA: inembargabilidad, riesgos operacionales |
| **DIAN** | Tributación | ALTA: derechos impuestos del deudor no embargables |
| **MinTIC** | Seguridad de información | MEDIA: estándares cifrado, certificados digitales |
| **Superintendencia Superintendencia de Vigilancia** | Protección datos | MEDIA: cumplimiento LSSVP |
| **Procuraduría General** | Vigilancia entidades públicas | BAJA: solo si embargo involucra entidad pública |
| **Juzgados Civiles** | Validación embargos | CRÍTICA: verificar radicados válidos |

### 6.2 Circulares SFC Relevantes

| Circular | Tema | Impacto en Proceso |
|----------|------|-------------------|
| **053/2015** | Gestión de riesgos operacionales | KPIs, riesgo personas/procesos |
| **022/2014** | Montos inembargables | Motor de reglas, cálculos |
| **093/2014** | Gestión de crisis y continuidad | BCP, RTO/RPO |
| **048/2013** | Administración de personal | Segregación funciones |
| **001/2021** | Transformación digital | Recomendación automatización |

### 6.3 Tendencias Normativas 2024-2025

✅ **Enfoque Zero Trust:** SFC incentiva arquitectura "verificar siempre"
✅ **Automatización:** SFC promueve procesos sistematizados para reducir error humano
✅ **Transparencia:** GDPR global influye hacia mayor documentación de decisiones
✅ **Blockchain:** Exploración en cobros judiciales (inmutabilidad de registros)

---

## 7. Conclusiones y Recomendaciones

### Hallazgo Principal
**Juriscoop tiene cumplimiento normativo del 31%.** La brecha más crítica está en:
1. 🔴 Protección de datos personales (Ley 1581) - Sin controles criptográficos sistemáticos
2. 🔴 Seguridad de información (ISO 27001) - Sin MFA, sin auditoría centralizada
3. 🔴 Automatización de inembargabilidad (SFC) - Riesgo de cálculos incorrectos

### Recomendación Estratégica
**Implementar MVP con controles de compliance integrados**:
- Captura de oficios con validación de autoridad (CGP)
- Motor de inembargabilidad parametrizado (SFC)
- Auditoría inmutable de decisiones (Ley 1581 + ISO 27001)
- Notificador SLA automático (CGP Art. 593)
- Protección de datos: cifrado + MFA (Ley 1581)

### Timeline de Regularización
- **Semana 1:** Validación officio + motor inembargabilidad
- **Semana 2:** MFA + consentimiento cliente documentado
- **Mes 1:** Datos seguridad, portal cliente, SIEM
- **Mes 2-3:** Certificación ISO 27001, auditoría externa

---

## 📚 Referencias

Véase archivo `referencias.md` para fuentes legales, circulares SFC, jurisprudencia y estándares ISO.
