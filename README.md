# Consultorio Integral Equilibrio - Asistente IA para Gestión de Turnos
Sistema automatizado de gestión de turnos para psicología impulsado por Inteligencia Artificial, integrado mediante **n8n**, la **API de Telegram**, **OpenAI GPT-5 Mini** y **Notion** como base de datos centralizada y panel de métricas.
## 🚀 Arquitectura del Sistema
El flujo automatizado opera de la siguiente manera:
1. **Trigger**: El paciente envía un mensaje al bot de Telegram.
2. **Orquestador (n8n)**: Recibe el mensaje y lo procesa a través de un nodo de **AI Agent**.
3. **Modelo (OpenAI)**: Interpreta la intención del usuario y decide qué herramientas invocar.
4. **Herramientas (Notion MCP / Nodes)**: Consulta o escribe en las bases de datos correspondientes (Agenda, Psicólogos, FAQ, Pacientes).
5. **Human-in-the-Loop (HITL)**: El agente valida los datos de la reserva y solicita confirmación explícita al usuario antes de impactar en Notion.
6. **Respuesta**: El bot devuelve la contestación final al canal de Telegram.
## 🛠️ Stack Tecnológico
* **Orquestador de workflows**: n8n (Self-hosted / Cloud)
* **Canal de comunicación**: Telegram Bot API
* **Modelo de Lenguaje**: OpenAI GPT-5 Mini
* **Base de datos y Dashboard**: Notion (Bases de datos relacionales y vistas de KPIs)
## 📂 Estructura del Repositorio
* `/workflows`: Contiene el archivo JSON exportado del flujo principal de n8n.
* `/docs`: Capturas de pantalla de la arquitectura y del Dashboard de Notion.
## ⚙️ Guía de Configuración
1. Importar el archivo JSON del workflow en tu instancia de n8n.
2. Configurar las credenciales de la API de Telegram, la API Key de OpenAI y la integración con Notion.
3. Asegurar que las bases de datos en Notion tengan los permisos correspondientes otorgados a la integración.
4. Activar el workflow en n8n y comenzar a interactuar con el bot en Telegram.
