# 🛠️ Taller 2: Modelo de Información y Diagrama de Contexto

## 🎯 Objetivo

Modelar las entidades principales del dominio del cliente y los flujos de información entre actores y sistemas, mediante un modelo entidad-relación (ERD) y un diagrama de contexto de negocio.

---

## 🏥 Caso base de referencia: Clínica Salud Viva

Durante este taller, todos los equipos trabajarán en clase con un caso base común antes de aplicarlo a su cliente real.

## 🧠 Contexto

La Clínica Salud Viva gestiona diversos flujos de información relacionados con pacientes, citas, médicos, facturación y servicios médicos. Estos datos están organizados en múltiples sistemas que deben interoperar entre sí, incluyendo un ERP clínico, una base de datos central de pacientes, y sistemas de terceros como aseguradoras. La correcta estructuración de las entidades de información y su contexto de operación es clave para lograr una arquitectura alineada con las necesidades clínicas, administrativas y regulatorias del sector salud.

**Descripción del caso:**
- Clínica Salud Viva ofrece servicios médicos presenciales y virtuales.
- El sistema permite a los pacientes agendar citas, los médicos gestionar su agenda, y el personal validar datos con aseguradoras.

**Elementos para modelar en clase:**
- **Entidades principales:** Paciente, Cita, Médico, Especialidad, Factura
- **Relaciones clave:** Un paciente puede tener muchas citas; cada cita se asocia a un médico y una especialidad.
- **Diagrama de contexto:** Incluye actores (paciente, médico, asistente), sistemas (ERP, agendamiento, notificador), y flujos de datos.

---

## 🧪 Parte 1: Trabajo en Clase

Durante la clase se espera que el equipo:

- Modele un ERD simple con las entidades del caso base y sus relaciones.
- Elabore un primer borrador del diagrama de contexto de negocio.
- Identifique qué información fluye entre actores y qué sistemas intervienen.
- Use herramientas como draw.io o papel para registrar la idea inicial.

---

## 🧠 Parte 2: Aplicación al Cliente Real

Después de la clase, el equipo debe:

- Adaptar el modelo de información al dominio del cliente real asignado.
- Elaborar un modelo ER limpio y un diagrama de contexto ajustado.
- Redactar un informe explicando las decisiones tomadas.
- Complementar con una investigación sobre ERD y contexto en casos reales de la industria.

---

## 📁 Estructura esperada del repositorio

```
taller-02-modelo-informacion/
├── README.md
├── clase/
│   ├── modelo-er-borrador.drawio
│   ├── contexto-borrador.drawio
│   └── notas.md
├── entrega/
│   ├── modelo-final-er.drawio
│   ├── diagrama-contexto-final.drawio
│   ├── informe.md
│   └── referencias.md
```

---

## 📤 Entregables

- Modelo ER final (`modelo-final-er.drawio`)
- Diagrama de contexto final (`diagrama-contexto-final.drawio`)
- Informe técnico (`informe.md`)
- Documento de investigación y referencias (`referencias.md`)

---

## 📊 Rúbrica de Evaluación

| Criterio                            | Excelente (5)                                                        | Aceptable (3) / Insuficiente (1–2)                        |
|-------------------------------------|-----------------------------------------------------------------------|------------------------------------------------------------|
| Modelo ER del caso base             | Diagrama coherente, con relaciones claras y alineado con el caso      | Relaciones poco claras o errores estructurales             |
| Diagrama de contexto funcional      | Conexiones correctas entre actores, sistemas y datos                  | Faltan actores clave o flujos mal definidos                |
| Aplicación al cliente real          | Buena adaptación con diferencias justificadas                         | No refleja el dominio real del cliente                     |
| Investigación complementaria        | Aplica teoría o ejemplos reales para enriquecer la entrega            | Pobremente documentada o sin conexión                      |

---

## ✅ Licencia

Este taller hace parte del curso de Arquitectura Empresarial - Universidad de La Sabana. Uso académico bajo licencia MIT.
