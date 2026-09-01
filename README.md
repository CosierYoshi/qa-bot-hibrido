#qa-bot-hibrido

####🤖 Chatbot híbrido para WhatsApp que combina flujos determinísticos e inteligencia artificial.

###📋 Descripción

qa-bot-hibrido es un proyecto de chatbot para WhatsApp basado en una arquitectura híbrida que combina dos mecanismos de procesamiento:

Motor determinístico: encargado de manejar flujos, reglas y procesos previamente definidos.
Motor AI: encargado de interpretar consultas en lenguaje natural y responder preguntas que no pueden ser resueltas mediante reglas tradicionales.

El objetivo es combinar la precisión y control de los flujos determinísticos con la flexibilidad de la inteligencia artificial.

###🎯 Objetivos
Automatizar la atención mediante WhatsApp.
Resolver consultas conocidas mediante flujos determinísticos.
Utilizar AI para consultas abiertas o ambiguas.
Mantener control sobre los procesos críticos.
Reducir la dependencia exclusiva de AI.
Permitir una experiencia conversacional más natural.
Facilitar la incorporación de nuevos flujos y funcionalidades.
###🏗️ Arquitectura
                         +----------------+
                         |    WhatsApp    |
                         +-------+--------+
                                 |
                                 v
                         +----------------+
                         |     Webhook    |
                         +-------+--------+
                                 |
                                 v
                         +----------------+
                         | Hybrid Router  |
                         +-------+--------+
                                 |
                   +-------------+-------------+
                   |                           |
                   v                           v
          +------------------+       +------------------+
          |  Deterministic   |       |       AI         |
          |     Engine       |       |     Engine       |
          +--------+---------+       +--------+---------+
                   |                           |
                   +-------------+-------------+
                                 |
                                 v
                         +----------------+
                         |    Response    |
                         |    Manager     |
                         +-------+--------+
                                 |
                                 v
                         +----------------+
                         |    WhatsApp    |
                         +----------------+

###🔀 Funcionamiento

El sistema recibe un mensaje desde WhatsApp y lo envía al Hybrid Router.

El router determina qué motor debe procesar la solicitud.

Mensaje
   |
   v
Hybrid Router
   |
   +----> ¿Existe un flujo conocido?
              |
              +---- SI ----> Motor Determinístico
              |                    |
              |                    v
              |              Respuesta controlada
              |
              +---- NO ----> Motor AI
                                   |
                                   v
                             Respuesta AI



Flujo determinístico

Se utiliza cuando el mensaje corresponde a una acción o proceso conocido.

Ejemplo:

Usuario:
"Quiero consultar mi solicitud"

        |
        v

Router

        |
        v

Flujo determinístico

        |
        v

Validación

        |
        v

Consulta al sistema

        |
        v

Respuesta

Flujo AI

Se utiliza cuando el usuario realiza una consulta que requiere interpretación del lenguaje natural.

Ejemplo:

Usuario:

"No sé qué hacer porque mi solicitud
todavía no aparece registrada"


El motor AI analiza la intención y genera una respuesta utilizando el contexto disponible.

###🤖 Motor determinístico

El motor determinístico está diseñado para procesos donde se necesita una respuesta controlada, predecible y reproducible.

Casos de uso
Menús.
Comandos.
Preguntas frecuentes.
Validaciones.
Flujos de negocio.
Consultas a sistemas internos.
Procesos transaccionales.
Escalamiento a un agente humano.
Ventajas
Característica	Resultado
Predictibilidad	Alta
Control	Alto
Testing	Fácil
Costo	Bajo
Reglas de negocio	Excelente
Procesos críticos	Excelente
###🧠 Motor AI

El motor AI permite procesar mensajes que no necesariamente coinciden con una regla o flujo previamente definido.

Casos de uso
Preguntas abiertas.
Lenguaje natural.
Clasificación de intención.
Interpretación de mensajes.
Consultas ambiguas.
Generación de respuestas.
Conversaciones contextuales.

Ejemplo:

Usuario:

"¿Me puedes explicar qué opciones tengo
para resolver mi problema?"


El motor AI puede interpretar la intención y generar una respuesta basada en el contexto disponible.

###🔄 Modelo híbrido

La principal característica de qa-bot-hibrido es que AI no necesariamente procesa todos los mensajes.

Los mensajes conocidos se procesan mediante reglas determinísticas y solamente aquellos que requieren mayor interpretación pasan al motor AI.

                    +-------------+
                    |   Mensaje   |
                    +------+------+
                           |
                           v
                  +------------------+
                  |  Hybrid Router   |
                  +--------+---------+
                           |
              +------------+------------+
              |                         |
              v                         v
       +-------------+           +-------------+
       | Deterministic|          |     AI      |
       |    Engine    |           |   Engine   |
       +------+------+           +------+------+
              |                         |
              +------------+------------+
                           |
                           v
                    +-------------+
                    |  Respuesta  |
                    +-------------+

###📊 Comparación
Característica	Determinístico	AI
Respuesta predecible	Sí	No siempre
Reglas de negocio	Excelente	Limitado
Validaciones	Excelente	Limitado
Preguntas abiertas	Limitado	Excelente
Lenguaje natural	Limitado	Excelente
Contexto	Limitado	Excelente
Control de respuesta	Alto	Medio
Flexibilidad	Media	Alta
Costo	Bajo	Variable
###📁 Estructura del proyecto
qa-bot-hibrido/
|
+-- app/
|   |
|   +-- deterministic/
|   |   |
|   |   +-- flows/
|   |   +-- rules/
|   |   +-- handlers/
|   |   +-- services/
|   |
|   +-- ai/
|   |   |
|   |   +-- prompts/
|   |   +-- handlers/
|   |   +-- services/
|   |   +-- providers/
|   |
|   +-- router/
|   |   |
|   |   +-- message_router.py
|   |   +-- intent_router.py
|   |
|   +-- whatsapp/
|   |   |
|   |   +-- webhook.py
|   |   +-- client.py
|   |
|   +-- config/
|   |   |
|   |   +-- settings.py
|   |
|   +-- main.py
|
+-- tests/
|   |
|   +-- deterministic/
|   +-- ai/
|   +-- router/
|   +-- whatsapp/
|
+-- .env.example
+-- .gitignore
+-- requirements.txt
+-- README.md

###🔐 Variables de entorno

Las credenciales y configuraciones sensibles deben mantenerse fuera del código fuente.

Ejemplo:

WHATSAPP_TOKEN=
WHATSAPP_PHONE_NUMBER_ID=
WHATSAPP_VERIFY_TOKEN=

AI_API_KEY=
AI_MODEL=


El archivo .env no debe incluirse en el repositorio.

###🧪 Testing

Las pruebas deben cubrir ambos motores y, especialmente, el comportamiento del router.

pytest

Casos principales
 Mensaje conocido.
 Comando.
 Menú.
 Flujo determinístico.
 Consulta AI.
 Clasificación de intención.
 Fallback.
 Error del motor AI.
 Error del servicio de WhatsApp.
 Escalamiento a agente humano.
###📈 Métricas

Para evaluar el comportamiento del bot se recomienda registrar:

Número total de conversaciones.
Número total de mensajes.
Mensajes procesados por el motor determinístico.
Mensajes procesados por AI.
Tasa de fallback.
Tiempo promedio de respuesta.
Errores.
Conversaciones escaladas a agentes humanos.

Ejemplo:

Mensajes procesados:       10,000

Determinísticos:            6,500
AI:                          3,000
Escalados:                    500

###🛡️ Seguridad

El sistema debe considerar:

Validación de entradas.
Protección de credenciales.
Manejo seguro de tokens.
Logs sin información sensible.
Control del contexto enviado al motor AI.
Manejo de errores.
Fallback ante fallos del servicio AI.
Control de respuestas generadas por AI.
###🚀 Roadmap
 Integración con WhatsApp.
 Implementar webhook.
 Implementar Hybrid Router.
 Implementar motor determinístico.
 Integrar motor AI.
 Implementar manejo de contexto.
 Implementar fallback.
 Implementar escalamiento a agente humano.
 Implementar logging.
 Implementar métricas.
 Agregar pruebas automatizadas.
 Preparar despliegue para producción.
###🧭 Principio de diseño

El proyecto sigue una regla sencilla:

Si podemos resolverlo de manera determinística, no necesitamos AI.

Esto permite utilizar AI donde realmente aporta valor, manteniendo los procesos críticos bajo reglas controladas.

                    ¿La solicitud es conocida?
                              |
                    +---------+---------+
                    |                   |
                   SI                  NO
                    |                   |
                    v                   v
             Determinístico            AI
                    |                   |
                    +---------+---------+
                              |
                              v
                         Respuesta

###📌 Resumen

qa-bot-hibrido busca combinar lo mejor de dos mundos:

Determinístico

Control + estabilidad + reglas de negocio

AI

Flexibilidad + lenguaje natural + contexto

El resultado es un chatbot de WhatsApp capaz de mantener control sobre los procesos importantes y, al mismo tiempo, ofrecer una experiencia conversacional más flexible.

###📄 Licencia

Definir la licencia correspondiente al proyecto.