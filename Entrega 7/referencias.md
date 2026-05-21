# 📚 Referencias — Entrega 7: Integración de Vistas de Arquitectura
## Financiera Juriscoop S.A. — Proceso CF-JUR-PRO-002

---

## 🔖 Contexto

Entrega 7 del Proyecto Corte 2 — Integración de vistas arquitectónicas (Negocio, Información, Aplicaciones, Infraestructura y Seguridad) del proceso de Embargo y Desembargo de Financiera Juriscoop S.A., bajo marcos TOGAF 9.2, ArchiMate 3.1, C4 Model, BPMN 2.0 y STRIDE.

---

## 📚 Referencias Utilizadas

### Marcos de Arquitectura Empresarial

1. **The Open Group. (2018).** *The TOGAF® Standard, Version 9.2.*
   - Architecture Development Method (ADM): Fases B, C, D para vistas de Negocio, SI e Infraestructura
   - Disponible: https://www.opengroup.org/togaf

2. **The Open Group. (2019).** *ArchiMate® 3.1 Specification.*
   - Lenguaje de modelado para vistas integradas de arquitectura empresarial
   - Capas: Negocio, Aplicación, Tecnología
   - Disponible: https://www.opengroup.org/archimate-forum

3. **Zachman, J. A. (1987).** *A Framework for Information Systems Architecture.*
   - IBM Systems Journal, 26(3), 276–292
   - Fundamento del enfoque de vistas múltiples en arquitectura empresarial

4. **Kruchten, P. (1995).** *The 4+1 View Model of Architecture.*
   - IEEE Software, 12(6), 42–50
   - Vistas: Lógica, Implementación, Proceso, Despliegue + Casos de Uso

5. **Ross, J. W., Weill, P., & Robertson, D. C. (2006).** *Enterprise Architecture as Strategy.*
   - Harvard Business School Press
   - Alineación estratégica de la arquitectura con objetivos de negocio

### Documentación de Arquitectura con C4 Model

6. **Brown, S. (2018).** *The C4 Model for Visualising Software Architecture.*
   - Documentación oficial: https://c4model.com
   - Niveles: Context (L1), Container (L2), Component (L3), Code (L4)

7. **Brown, S. (2019).** *Software Architecture for Developers, Volume 2.*
   - Leanpub
   - Guía práctica de diagramas C4 con ejemplos del sector financiero

### Modelado de Procesos de Negocio — BPMN

8. **Object Management Group. (2013).** *Business Process Model and Notation (BPMN) Version 2.0.2.*
   - OMG Document Number: formal/2013-12-09
   - Disponible: https://www.omg.org/spec/BPMN/2.0/

9. **Weske, M. (2019).** *Business Process Management: Concepts, Languages, Architectures.* (3ra ed.)
   - Springer
   - Capítulos 3 y 4: Modelado de procesos AS-IS y TO-BE

### Integración de Vistas en el Sector Financiero

10. **Bancolombia S.A. (2023).** *Informe de Gestión — Transformación Digital.*
    - Referencia a adopción de TOGAF y marcos de arquitectura empresarial para cumplimiento regulatorio
    - Disponible: https://www.bancolombia.com/acerca-de/inversionistas/informes-anuales

11. **BBVA Research. (2022).** *Digital Architecture in Banking: From Monoliths to Microservices.*
    - Whitepaper sobre arquitecturas modernas en el sector financiero latinoamericano
    - Disponible: https://www.bbvaresearch.com/

12. **Superintendencia Financiera de Colombia (SFC). (2022).**
    - Circular Externa 001/2021: Lineamientos de transformación digital para entidades vigiladas
    - Requerimientos de documentación de sistemas de información ante auditorías
    - Disponible: https://www.superfinanciera.gov.co/

### Seguridad en Arquitecturas — STRIDE

13. **Microsoft. (2021).** *The STRIDE Threat Model.*
    - Microsoft Security Documentation
    - Disponible: https://docs.microsoft.com/en-us/security/

14. **Shostack, A. (2014).** *Threat Modeling: Designing for Security.*
    - Wiley
    - Marco STRIDE aplicado a arquitecturas empresariales

15. **NIST. (2018).** *NIST Cybersecurity Framework (CSF) Version 1.1.*
    - National Institute of Standards and Technology
    - Disponible: https://www.nist.gov/cyberframework

### Integración de Vistas y Gobierno

16. **ISO/IEC 42010:2011.** *Systems and Software Engineering — Architecture Description.*
    - Estándar para descripción de arquitecturas de sistemas, incluyendo vistas y puntos de vista
    - Disponible: https://www.iso.org/

17. **Sessions, R. (2007).** *A Comparison of the Top Four Enterprise Architecture Methodologies.*
    - Microsoft Architecture Journal
    - Comparación TOGAF, Zachman, FEA, Gartner EA

18. **Lankhorst, M. (2017).** *Enterprise Architecture at Work: Modelling, Communication and Analysis.* (4ta ed.)
    - Springer
    - Capítulo 5: Integración de vistas y coherencia arquitectónica

### Normativa Regulatoria Aplicada a las Vistas

19. **Congreso de la República de Colombia. (2012).** *Código General del Proceso — Ley 1564.*
    - Artículos 593/594: Procedimiento de embargo y desembargo
    - Condicionante del proceso de negocio (Vista Negocio)
    - Disponible: https://www.funcionpublica.gov.co/

20. **Superintendencia Financiera de Colombia. (2014).** *Circular Externa 022.*
    - Montos de inembargabilidad por tipo de producto financiero
    - Condicionante del Motor de Inembargabilidad (Vista Aplicaciones y Datos)

21. **Congreso de la República de Colombia. (2012).** *Ley 1581 — Protección de Datos Personales.*
    - Condicionante de los controles de seguridad (Vista Seguridad) y del modelo de datos (Vista Información)

### Herramientas y Tecnologías Referenciadas

22. **PostgreSQL Global Development Group. (2024).** *PostgreSQL 16 Documentation.*
    - Sistema gestor de base de datos relacional propuesto para la BD Transaccional
    - Disponible: https://www.postgresql.org/docs/

23. **Kong Inc. (2023).** *Kong Gateway Documentation.*
    - API Gateway propuesto para la capa de acceso del MVP
    - Disponible: https://docs.konghq.com/

24. **OWASP Foundation. (2023).** *OWASP Top 10.*
    - Referencia de vulnerabilidades aplicada en el diseño de seguridad del MVP
    - Disponible: https://owasp.org/www-project-top-ten/

---

## 📊 Mapa de Referencias por Vista

| Vista Arquitectónica | Referencias Clave |
|---------------------|-------------------|
| **Negocio (BPMN)** | (8), (9), (1) ADM Fase B |
| **Información (ERD)** | (1) ADM Fase C, (16), (18) |
| **Aplicaciones (C4)** | (6), (7), (2) ArchiMate |
| **Infraestructura** | (1) ADM Fase D, (22), (23) |
| **Seguridad (STRIDE)** | (13), (14), (15), (24) |
| **Integración de Vistas** | (3), (4), (5), (16), (17), (18) |
| **Sector Financiero** | (10), (11), (12), (19), (20), (21) |

