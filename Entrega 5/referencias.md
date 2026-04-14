# 📚 Referencias - Entrega 5: Evaluación de Seguridad con STRIDE

**Taller 5 - Arquitectura Empresarial - Financiera Juriscoop S.A.**

---

## 🔖 Contexto

Entrega 5 del Proyecto Corte 2 - Análisis de seguridad de la información en el proceso CF-JUR-PRO-002 (Embargo y Desembargo) usando el marco STRIDE.

---

## 📚 Referencias Utilizadas

### Marco STRIDE - Fundamentos

1. Shostack, A. *Threat Modeling: Designing for Security*. John Wiley & Sons, 2014.
   - Metodología STRIDE en profundidad; casos de aplicación industrial

2. Microsoft Developer Network (MSDN). *The STRIDE Threat Model*. 2023.
   - Explicación técnica de las 6 categorías de amenazas
   - https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ff648644(v=pandp.10)

3. OWASP (Open Web Application Security Project). *Threat Modeling* Guidelines. 2023.
   - https://owasp.org/www-community/Threat_Modeling
   - Framework compatible con STRIDE

### Seguridad en Sistemas Financieros

4. Superintendencia Financiera de Colombia (SFC). *Circular Externa 053/2015*.
   - Gestión de riesgos operacionales, controles preventivos
   - Documento oficial regulatorio aplicable

5. Basel Committee on Banking Supervision (BCBS). *Guidance on Cyber Resilience*.
   - BIS Papers No. 304, 2018
   - Estándar internacional para seguridad en banca

6. Payment Card Industry Security Standards Council (PCI-DSS). *PCI DSS v3.2.1* (2018).
   - No directamente aplicable (Juriscoop no procesa tarjetas), pero referencia para buenas prácticas

### Criptografía y Autenticación

7. National Institute of Standards and Technology (NIST). *Special Publication 800-63C:
 Authentication and Lifecycle Management*. 2019.
   - Multi-Factor Authentication (MFA) estándares
   - Session management best practices

8. OWASP. *Authentication Cheat Sheet*. 2024.
   - Implementación segura de login, password policies, MFA
   - https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html

9. RFC 5246 - TLS 1.2 Protocol. IETF, 2008.
   - Estándar de cifrado en tránsito
   - https://tools.ietf.org/html/rfc5246

10. RFC 8446 - TLS 1.3 Protocol. IETF, 2018.
    - Versión mejorada de TLS; recomendado para nuevos desarrollos

### Análisis de Amenazas y Riesgos

11. ISO/IEC 31010:2019 *Risk Assessment Techniques*.
    - Metodología formal de análisis de riesgos
    - Matriz probabilidad vs impacto

12. NIST Risk Management Framework (RMF). *SP 800-37*. 2024.
    - Categorización de activos, valoración de riesgos, selección de controles

13. FAIR Institute. *Factor Analysis of Information Risk (FAIR)*.
    - Modelo cuantitativo de risk; estimación de probabilidad y coste de incidentes

### Detección y Respuesta ante Amenazas

14. NIST Cybersecurity Framework (CSF). *Framework v1.1*. 2022.
    - Detect, Identify, Respond, Recover
    - https://www.nist.gov/cyberframework

15. MITRE ATT&CK Framework. *Tactics, Techniques, Knowledge Base*. 2024.
    - Base de conocimiento de tácticas adversarias; mapeo con STRIDE
    - https://attack.mitre.org

16. SANS Institute. *Incident Handler's Handbook*. 
    - Procedimientos de respuesta ante incidentes de seguridad
    - Escalación, notificación, investigación forense

### Frameworks de Seguridad Integral

17. ISO/IEC 27001:2022 *Information Security Management Systems*.
    - Estándar certificable de gestión de seguridad
    - Controles técnicos y organizacionales

18. ISO/IEC 27035:2016 *Information Security Incident Management*.
    - Proceso formal de manejo de incidentes
    - Plan de respuesta a brechas

### Seguridad Aplicada a Procesos Judiciales

19. Colombia, Congreso de la República. *Código General del Proceso (CGP)*.
    - Artículos 593/594: Embargo y desembargo
    - Requisitos regulatorios y legales

20. Colombia, Superintendencia Financiera. *Guía sobre Protección de Datos en Procesos Judiciales*. (2020).
    - Recomendaciones para entidades financieras procesando embargos

### Buenas Prácticas en Sector Financiero

21. Federal Financial Institutions Examination Council (FFIEC). *Information Security IT Examination Handbook*. 2023.
    - Estándares de seguridad examinables por reguladores
    - Aplicables a contexto latinoamericano

22. Banco de la República (Colombia). *Estándares de Seguridad para Transacciones Electrónicas*. 2022.
    - Directrices para sistemas de información financieros en Colombia

### Auditoría y Compliance

23. The Institute of Internal Auditors (IIA). *The Three Lines Model*. 2020.
    - Auditoría interna, riesgos, compliance; segregación de funciones

24. COBIT 2019. *ISACA Framework for Governance and Management of Enterprise IT*. 
    - Mapeo entre riesgos de negocio y controles técnicos

### Protección de Datos Personales

25. Ley 1581 de 2012 (Colombia). *Protección de Datos Personales*.
    - Marco legal aplicable; derechos de titulares

26. Decreto 1377 de 2013 (Colombia). Reglamento Ley 1581.
    - Regulaciones técnicas para protección de datos

27. European Union. *General Data Protection Regulation (GDPR)*. (2018).
    - Referencia internacional para privacidad; influye normativa colombiana

---

## 📊 Matriz de Referencias por Amenaza STRIDE

| Amenaza ID | Categoría | Referencias Principales |
|-----------|-----------|------------------------|
| S-1 | Spoofing | Shostack (1), OWASP Auth (8), CGP (19) |
| S-2 | Spoofing | NIST 800-63 (7), OWASP Auth (8), ISO 27001 (17) |
| T-1 | Tampering | Shostack (1), ISO 31010 (11), NIST 31010 (12) |
| T-2 | Tampering | RFC 5246/8446 (9,10), OWASP (3) |
| T-3 | Tampering | OWASP (3), NIST CSF (14), ISO 27001 (17) |
| R-1 | Repudiation | NIST 27035 (18), SFC 053/2015 (4), IIA 3Lines (23) |
| R-2 | Repudiation | FAIR (13), NIST RMF (12), CGP (19) |
| ID-1 | Information Disclosure | Ley 1581 (25), GDPR (27), SFC (20) |
| ID-2 | Information Disclosure | ISO 27001 (17), COBIT (24), IIA (23) |
| ID-3 | Information Disclosure | OWASP (3), NIST CSF (14), ISO 27035 (18) |
| DoS-1 | Denial of Service | OWASP (3), NIST CSF (14), BCBS (5) |
| DoS-2 | Denial of Service | BCBS (5), Basel (5), NIST RMF (12) |
| DoS-3 | Denial of Service | OWASP (3), RFC 7208 SPF, NIST CSF (14) |
| EoP-1 | EoP | Shostack (1), NIST 800-63 (7), ISO 27001 (17) |
| EoP-2 | EoP | OWASP (3), SANS Handbook (16), Shostack (1) |
| EoP-3 | EoP | NIST 800-63 (7), OWASP (8), Microsoft Security (2) |

---

## 📌 Guías de Implementación por Personal

### Para CISO / Director de Seguridad
- Threat Modeling de Shostack (1)
- NIST Cybersecurity Framework (14)
- BCBS Cyber Resilience (5)
- ISO 27001 (17)

### Para Arquitecto de Seguridad
- STRIDE MSDN (2)
- RFC TLS (9, 10)
- FAIR Risk Quantification (13)
- MITRE ATT&CK (15)

### Para Equipos de Desarrollo MVP
- OWASP Cheat Sheets (8, 3)
- NIST 800-63 (7)
- Incident Handling (16)
- Coding Security (OWASP Top 10)

### Para Auditoría Interna
- Three Lines Model (23)
- COBIT 2019 (24)
- ISO 27035 Incident Management (18)
- SFC 053/2015 (4)

---

## 🔗 Recursos En Línea Útiles

- OWASP Top 10: https://owasp.org/www-project-top-ten
- NIST Cybersecurity Framework: https://www.nist.gov/cyberframework
- MITRE ATT&CK: https://attack.mitre.org
- SFC Normativa: https://www.superfinanciera.gov.co/
- ISO 27001 Oficial: https://www.iso.org/isoiec-27001-information-security-management.html

---

## 📝 Fuente Asistida por IA

Este documento ha sido asistido por Claude Haiku, julio 2025, para sintetizar análisis STRIDE y buenas prácticas de seguridad en sistemas financieros.

---

_Este archivo forma parte de la entrega académica del curso Arquitectura Empresarial - Universidad de La Sabana._
