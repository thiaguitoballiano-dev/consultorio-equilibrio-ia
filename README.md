# 🧠 Consultorio Integral Equilibrio
### Ecosistema de Automatización IA Autónomo para Negocios

---

## 📌 Descripción

**Consultorio Integral Equilibrio** es un sistema de automatización basado en Inteligencia Artificial diseñado para gestionar de forma autónoma la atención inicial de pacientes de un consultorio psicológico.

El sistema utiliza un agente de IA capaz de comprender las consultas de los usuarios, buscar información en una base de datos estructurada, recomendar profesionales según las necesidades del paciente, consultar disponibilidad de turnos y gestionar reservas.

El objetivo es automatizar tareas administrativas y repetitivas sin perder el control humano en acciones críticas.

---

## 🎯 Objetivo del proyecto

El sistema busca automatizar el proceso de atención inicial de un paciente:

1. Recibir la consulta.
2. Comprender la intención del usuario.
3. Buscar información relevante.
4. Recomendar un psicólogo adecuado.
5. Consultar disponibilidad.
6. Proponer un turno.
7. Solicitar la validación correspondiente antes de realizar una acción crítica.
8. Actualizar la agenda.
9. Confirmar el resultado al paciente.
10. Registrar la información de la conversación y posibles errores.

De esta manera, el consultorio puede reducir tareas manuales y mejorar los tiempos de respuesta.

---

# 🏗️ Arquitectura del sistema

```text
                    ┌──────────────────┐
                    │     TELEGRAM     │
                    │  Mensaje paciente│
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │  TELEGRAM TRIGGER│
                    │     n8n          │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     AI AGENT     │
                    │ Equilibrio Bot   │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
              ▼              ▼              ▼
        ┌──────────┐   ┌──────────┐   ┌──────────┐
        │Psicólogos│   │  Agenda  │   │   FAQ    │
        │  Notion  │   │  Notion  │   │  Notion  │
        └──────────┘   └──────────┘   └──────────┘
              │              │              │
              └──────────────┼──────────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Redis Chat Memory│
                    └────────┬─────────┘
                             │
                             ▼
                  ¿Acción crítica?
                       /       \
                     NO         SÍ
                     │           │
                     │           ▼
                     │    ┌──────────────┐
                     │    │     HITL     │
                     │    │ Aprobación   │
                     │    │    humana    │
                     │    └──────┬───────┘
                     │           │
                     │           ▼
                     │    ┌──────────────┐
                     │    │ Update Agenda│
                     │    │    Notion    │
                     │    └──────┬───────┘
                     │           │
                     └───────────┤
                                 ▼
                       ┌─────────────────┐
                       │ Telegram Send   │
                       │     Message     │
                       └─────────────────┘
