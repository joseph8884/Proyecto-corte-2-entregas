# 📚 Referencias - Entrega 4: Infraestructura y Diagnóstico Técnico

**Taller 4 - Arquitectura Empresarial - Financiera Juriscoop S.A.**

---

## 🔖 Contexto

Entrega 4 del Proyecto Corte 2 - Análisis de infraestructura tecnológica del proceso CF-JUR-PRO-002 (Embargo y Desembargo).

---

## 📚 Referencias Utilizadas

### Arquitectura y Patrones de Sistemas

1. The Open Group. *The TOGAF® Standard, Version 9.2*. 2018. Disponible en: https://www.opengroup.org/togaf
   - Referencia principal para modelado de arquitectura AS-IS y TO-BE

2. C4 Model - Context, Container, Component, Class. Simon Brown. https://c4model.com
   - Utilizado para visualizar topología de red y contexto de sistemas

3. NATO Architecture Framework (NAF) & Zachman Framework. Extended Enterprise Architecture. 
   - Referencias para análisis de capas de infraestructura

### Buenas Prácticas de Infraestructura

4. Amazon Web Services (AWS). *Well-Architected Framework*. 2023. https://aws.amazon.com/architecture/well-architected/
   - Pilares: excelencia operativa, seguridad, confiabilidad, eficiencia de desempeño, optimización de costos

5. Microsoft Azure. *Cloud Adoption Framework (CAF)*. 2024. https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/
   - Estrategia híbrida, migración on-premise-to-cloud

6. British Standard BS 7799 (ISO/IEC 27001:2022). *Information Security Management System*. 
   - Disponibilidad, redundancia, recuperación ante desastres

### Modelos de Resiliencia y Continuidad

7. National Institute of Standards and Technology (NIST). *Cybersecurity Framework 1.1*. 2022. https://www.nist.gov/cyberframework
   - RTO (Recovery Time Objective), RPO (Recovery Point Objective)
   - Estrategias de backup y disaster recovery

8. ITIL v4 - Information Technology Infrastructure Library. Axelos. 
   - Service Design, Operational Excellence
   - Change Management, Incident Response

### Tecnologías Específicas Referenciadas

9. Oracle/Sun Microsystems. *BankVisión - Enterprise Banking System*. Documentation.
   - Sistema core mencionado; lecciones de centralización de datos

10. REST API Best Practices & OpenAPI/Swagger 3.0. https://swagger.io/
    - Integración con APIs (Banco Agrario, sistemas terceros)

11. Database Replication & High Availability. PostgreSQL, MySQL, SQL Server Documentation.
    - Backup incremental, replicación sincrónica/asincrónica

### Escalabilidad y Microservicios

12. Newman, S. *Building Microservices*. O'Reilly Media, 2015.
    - Patrón de descomposición de monolitos para escalar

13. Docker & Kubernetes Documentation. https://www.docker.com/, https://kubernetes.io/
    - Containerización, orquestación de servicios (aunque probablemente no aplicable on-premise actual)

### Monitoreo y Observabilidad

14. Observability Engineering. Honeycomb / New Relic. https://www.honeycomb.io/
    - Metrics, logs, traces; SLOs y alertas

15. ELK Stack (Elasticsearch, Logstash, Kibana). https://www.elastic.co/
    - Centralización de logs (aplicable en propuesta MVP)

### Metodología de Análisis de Brechas

16. GAP Analysis Framework. APQC (American Productivity & Quality Center). https://www.apqc.org/
    - Metodología de identificación de diferencias AS-IS vs TO-BE

17. MIT Sloan. *Digital Transformation and Infrastructure*. 2023.
    - Estrategias de transición tecnológica sin disrupciones operacionales

### Sector Financiero - Buenas Prácticas

18. Superintendencia Financiera de Colombia (SFC). *Circular Externa 053/2015*. 
    - Gestión de riesgos operacionales, infraestructura resiliente

19. Bank of International Settlements (BIS). *BCBS 14*. 2005 (Updated 2020).
    - Operational resilience in banking, infrastructure standards

20. SWIFT Standards. *Customer Security Programme (CSP)*. 2024.
    - High availability, seguridad en integraciones payment

### Mitigación de Cuellos de Botella

21. Goldratt, E. *The Goal: A Process of Ongoing Improvement*. North River Press, 2014.
    - Teoría de Constraints (TOC); identificación y optimización de cuellos de botella

22. Lean Six Sigma. DMAIC Methodology. American Society for Quality (ASQ). https://asq.org/
    - Process optimization, variance reduction

---

## 📌 Recomendaciones de Lectura por Rol

### Para CTO / Director de TI
- TOGAF v9.2 (referencia 1)
- AWS Well-Architected Framework (referencia 4)
- NIST Cyber Framework (referencia 7)

### Para Arquitecto de Soluciones
- C4 Model (referencia 2)
- Microservices Architecture (referencia 12)
- ITIL v4 Change Management (referencia 8)

### Para Equipo Operativo
- Disaster Recovery + RTO/RPO (NIST, referencia 7)
- Monitoreo y Observabilidad (referencia 14)
- SLA y KPIs (referencia 4)

### Para Analistas de Negocio
- GAP Analysis Framework (referencia 16)
- Teoría de Constraints (referencia 21)
- Transformación Digital (referencia 17)

---

## 🔗 Recursos En Línea Útiles

- TOGAF Official: https://www.opengroup.org/togaf
- C4 Model Interactive: https://c4model.com
- AWS Architecture Center: https://aws.amazon.com/architecture/
- NIST Cybersecurity Framework: https://www.nist.gov/cyberframework
- SFC Circulares: https://www.superfinanciera.gov.co/

---

## 📝 Fuente Asistida por IA

Este documento ha sido asistido por Claude Haiku, julio 2025, para sintetizar mejores prácticas de infraestructura y arquitectura empresarial.

---

_Este archivo forma parte de la entrega académica del curso Arquitectura Empresarial - Universidad de La Sabana._
