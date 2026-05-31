# 🛠️ Taller 1: Modelado de Proceso del Cliente con BPMN

## 🎯 Objetivo

Modelar un proceso de negocio real del cliente utilizando la notación BPMN, identificando eventos, actividades, decisiones, actores involucrados y puntos críticos del flujo.

---

## 🏥 Caso base de referencia: Clínica Salud Viva

Durante este taller, todos los equipos trabajarán en clase con un caso base común antes de aplicarlo a su cliente real.

## 🧠 Contexto

La Clínica Salud Viva es una institución médica de tamaño medio ubicada en una ciudad capital. Atiende pacientes tanto de manera presencial como virtual, y cuenta con una plataforma digital donde los usuarios pueden agendar citas médicas, recibir notificaciones y consultar su historial de atención. El proceso de agendamiento implica la selección de especialidad, disponibilidad del médico y confirmación vía correo electrónico o mensaje de texto. Este proceso es fundamental para garantizar una atención eficiente y organizada, especialmente en épocas de alta demanda como campañas de vacunación o jornadas preventivas.

**Descripción del caso:**
- La Clínica Salud Viva es una clínica mediana que ofrece atención médica presencial y virtual.
- Cuenta con un sistema de gestión de citas en línea, un ERP administrativo y alianzas con aseguradoras de salud.

**Proceso a modelar (en clase):**
> Agendamiento de Citas Médicas

- Actor: Paciente
- Flujo: Selección de especialidad → Médico → Fecha → Confirmación
- Interacciones: con sistema de citas, base de datos, notificación por correo/SMS

---

## 🧪 Parte 1: Trabajo en Clase

Durante la clase se espera que el equipo:

- Modele el proceso de agendamiento de citas de la Clínica Salud Viva utilizando BPMN.
- Identifique:
  - Evento de inicio y fin
  - Actividades principales
  - Decisiones (gateways)
  - Roles del proceso
- Use papel, pizarra o herramientas como draw.io o Camunda Modeler.
- Reciba retroalimentación del docente y registre avances.

---

## 🧠 Parte 2: Aplicación al Cliente Real

Después de la clase, el equipo debe:

- Seleccionar un proceso real del cliente asignado (puede ser análogo al caso de clase).
- Digitalizar el modelo BPMN específico del cliente.
- Redactar un informe explicando el proceso, diferencias con el caso base y justificaciones.
- Complementar con una investigación sobre buenas prácticas BPMN y ejemplos en la industria.

---

## 📁 Estructura esperada del repositorio

```
taller-01-bpmn/
├── README.md
├── clase/
│   ├── modelo.drawio              # Modelo BPMN del caso base (Clínica Salud Viva)
│   └── notas.md
├── entrega/
│   ├── modelo-final.drawio        # Modelo BPMN del proceso real del cliente
│   ├── informe.md
│   └── referencias.md
```

---

## 📊 Rúbrica de Evaluación

| Criterio                            | Excelente (5)                                                       | Aceptable (3) / Insuficiente (1–2)                     |
|-------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------|
| Claridad del diagrama BPMN          | Modelo limpio, con símbolos correctos y buena secuencia lógica       | Desordenado, símbolos incorrectos o secuencia confusa  |
| Representación del caso base        | Modelo representa adecuadamente el flujo propuesto (Clínica Salud Viva) | Modelo incompleto o incoherente con el caso de clase   |
| Aplicación al cliente real          | Se adapta adecuadamente el modelado al cliente con diferencias justificadas | No hay adaptación real o está desalineado              |
| Investigación complementaria        | Buenas prácticas BPMN aplicadas y bien citadas                       | Poco análisis o investigación desconectada              |

---

## ✅ Licencia

Este taller hace parte del curso de Arquitectura Empresarial - Universidad de La Sabana. Uso académico bajo licencia MIT.
