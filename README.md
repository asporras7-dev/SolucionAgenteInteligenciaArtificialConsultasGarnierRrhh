# Solución Agente de Inteligencia Artificial para Consultas RRHH Garnier

Este repositorio contiene el código fuente (Frontend y Backend) de un prototipo de una plataforma inteligente diseñada específicamente para el departamento de Recursos Humanos de la empresa Garnier y Garnier. El sistema emplea un **Agente de Inteligencia Artificial** con tecnología RAG (Retrieval-Augmented Generation) y el protocolo MCP (Model Context Protocol) para resolver consultas de los empleados respecto a las políticas y reglas de la empresa, y a los derechos, beneficios y seguros con los que cuentan dichos emplados de forma automatizada, contextual y segura.

## Stack Tecnológico

El proyecto está construido bajo una arquitectura cliente-servidor (Full-Stack), integrando motores de Inteligencia Artificial y procesamiento de lenguaje natural de última generación.

### Frontend (SPA)
- **Tecnologías Base**: 
  - **HTML5 & CSS3**: Estructuración semántica y accesibilidad.
  - **JavaScript (ES6+)**: Lógica asíncrona de alto rendimiento.
- **Framework & Build Tools**:
  - **React.js (v19)**: Construcción de interfaces de usuario interactivas basadas en Hooks.
  - **Vite**: Herramienta de construcción y empaquetado ultra rápida.
  - **React Router DOM v7**: Gestión de enrutamiento del lado del cliente.
- **Diseño, UX e Integraciones**:
  - **Tailwind CSS v4**: Framework de utilidades para un diseño moderno, responsivo y ágil.
  - **Lucide React**: Biblioteca de iconos consistentes y ligeros.

### Backend (API REST & AI)
- **Node.js & Express.js**: Creación de una API RESTful robusta y endpoints de comunicación.
- **Sequelize (ORM)**: Gestión de base de datos relacional orientada a objetos (MySQL) para el control de empleados, logs de analíticas, tickets de soporte y documentos RAG.
- **Protocolo MCP**: Integración con `@modelcontextprotocol/sdk` para estandarizar la comunicación y herramientas (Tools) del agente de IA.
- **Seguridad y Procesamiento**: 
  - *CORS & Multer*: Control de accesos cruzados y subida segura de archivos (límites de hasta 50MB para PDFs).
  - *Nodemailer*: Sistema de envío de correos electrónicos transaccionales para escalar tickets y alertas a agentes humanos.
- **Motor RAG (Retrieval-Augmented Generation)**:
  - Generación de *Embeddings* locales y cálculo de similitud del coseno (Cosine Similarity).
  - Extracción y fragmentación de texto desde PDFs (`pdf-parse`) para inyectar contexto corporativo a las respuestas del LLM.

---

## Funcionalidades Principales

El sistema moderniza la atención al empleado, combinando automatización con escalamiento inteligente:

### 1. Agente Inteligente RRHH (Chatbot AI)
- **Asistencia 24/7**: Chatbot conversacional integrado que responde consultas sobre políticas, vacaciones, beneficios y procesos internos basándose estrictamente en los documentos oficiales de la compañía.
- **Soporte Multilingüe**: Detección y traducción automática de consultas (Español/Inglés) permitiendo inclusión global sin barreras de idioma.

### 2. Motor de Búsqueda y Contexto (RAG)
- **Inyección de Documentos Corporativos**: Sistema que permite cargar PDFs de políticas, dividirlos en fragmentos estructurados (*chunks*) y vectorizarlos.
- **Respuestas Precisas**: Cuando el empleado pregunta, el agente realiza una búsqueda semántica en la base de datos de documentos, entregando respuestas con un alto índice de confianza y evitando alucinaciones (hallucinations).

### 3. Análisis de Intención y Escalamiento (Routing)
- **Clasificador de Contexto**: Cada consulta pasa por un motor de reglas y detección de intenciones que clasifica el mensaje como `STANDARD`, `ONBOARDING`, `SENSITIVE` o `URGENT`.
- **Redirección Automática**:
  - **Temas Sensibles/Urgentes**: Palabras clave como "acoso", "depresión" o "accidente" bloquean la IA generativa y abren un ticket de escalamiento inmediato al equipo humano (vía Email y Panel de Tickets).
  - **Onboarding**: Flujos conversacionales guiados para nuevos ingresos.

### 4. Panel de Administración (Gestión Operativa)
- **Seguridad y Control de Accesos**:
  - Sistema de Login seguro y gestión de perfiles de administradores RRHH.
- **Base de Conocimiento Dinámica**:
  - Panel para subir, activar y desactivar manuales y políticas de la empresa. Al subir un PDF, el sistema lo procesa y vectoriza automáticamente.
- **Soporte Técnico y Tickets**:
  - Recepción, seguimiento y resolución de tickets escalados por la IA.
  - Comunicación directa con los empleados mediante notificaciones para mantenerlos informados del estado de su consulta.
- **Métricas y Analíticas (Analytics)**:
  - Registro detallado de cada consulta (`AnalyticsLog`) para medir métricas como: nivel de confianza, consultas no resueltas y temáticas más preguntadas, permitiendo mejorar las políticas de la empresa.

---

## Valor de Negocio y Logros Técnicos (Highlights para Reclutadores)

Este proyecto fue concebido no solo como una solución de software, sino como un producto enfocado en resolver problemas reales en la gestión de capital humano (RRHH), demostrando capacidad para integrar arquitecturas complejas de Inteligencia Artificial de forma segura y ética:

- **Arquitectura Basada en Contexto (Model Context Protocol - MCP)**: Implementación de un servidor MCP nativo que estandariza herramientas (`Tools`), recursos (`Resources`) y plantillas (`Prompts`). Esto permite que el LLM actúe como un agente activo (ej: abriendo tickets o iniciando flujos de Onboarding), en lugar de ser un simple generador de texto.
- **RAG Local de Alta Precisión**: Se construyó un motor de Retrieval-Augmented Generation completo. Los PDFs de la empresa se procesan, fragmentan y vectorizan localmente calculando la similitud del coseno (Cosine Similarity). Esto garantiza privacidad corporativa y un estricto control sobre las "alucinaciones" del modelo.
- **Inteligencia Emocional y Escalamiento Seguro**: Algoritmos de enrutamiento que detectan intenciones sensibles (ej. crisis emocionales, acoso laboral o urgencias). Si se detectan, el flujo de IA generativa se bloquea para dar paso a plantillas de alta empatía y escalar un ticket crítico (vía Email a RRHH) automáticamente.
- **Data-Driven (Analíticas)**: Tracking de cada interacción en la plataforma, midiendo niveles de certeza (*confidence scores*), consultas no resueltas y vacíos de información. Esto entrega a la empresa *insights* directos sobre qué políticas deben actualizarse.

---

## Arquitectura Preparada para Producción (Production-Ready)

El proyecto aún no se encuentra desplegado en un servidor público, pero su arquitectura ha sido construida bajo estrictos estándares corporativos para facilitar un paso a producción (Go-Live) seguro y escalable:

- **Frontend (SPA)**: Listo para ser optimizado y transpilado a estáticos a través de Vite (`npm run build`). Los archivos resultantes están estructurados para un despliegue ágil en plataformas de *Edge Computing* y CDN globales (como **Vercel, Netlify o AWS S3 + CloudFront**), integrándose fácilmente en flujos de CI/CD para despliegues continuos.
- **Backend API & MCP**: El servidor de Node.js está diseñado bajo una arquitectura sin estado (*Stateless*), lo que permite que sea desplegado mediante múltiples opciones corporativas: gestores de procesos (**PM2**), orquestación de contenedores (**Docker / Kubernetes**), o plataformas PaaS (**AWS Elastic Beanstalk / Azure App Service**), garantizando escalabilidad horizontal y *Zero Downtime*.
- **Base de Datos Relacional**: La capa de datos gestionada por Sequelize facilita futuras migraciones a entornos Cloud (ej. AWS RDS), manteniendo intacta la estructura e integridad de la información de los empleados.
- **Enfoque en Seguridad**: Todo el flujo de datos ha sido diseñado anticipando el uso de proxies inversos y certificados SSL/TLS, lo que asegurará la confidencialidad absoluta de las consultas de Recursos Humanos una vez montado en un entorno real.

---

## Instalación y Ejecución Local (Guía Paso a Paso)

<details>
<summary><b>Haz clic aquí para ver la Guía de Instalación y Ejecución Local</b></summary>

### 1. Prerrequisitos
- [Node.js](https://nodejs.org/) (Versión 18+).
- [Git](https://git-scm.com/).
- **MySQL Server** corriendo localmente.

### 2. Clonar el Repositorio
```bash
git clone https://github.com/asporras7-dev/SolucionAgenteInteligenciaArtificialConsultasGarnierRrhh.git
cd SolucionAgenteInteligenciaArtificialConsultasGarnierRrhh
```

### 3. Configuración de la Base de Datos (MySQL)
1. Crea una base de datos vacía llamada `garnier_rrhh` en tu gestor (ej. phpMyAdmin o MySQL Workbench).
2. El ORM (Sequelize) se encargará de crear las tablas al iniciar si la sincronización está activa o mediante scripts de migración.

### 4. Configuración del Backend
1. Navega a la carpeta backend e instala dependencias:
   ```bash
   cd backend
   npm install
   ```
2. Crea el archivo `.env` en `backend/` con los parámetros correspondientes (BD, puerto, claves secretas y API Keys de IA si aplican).
3. Inicia el servidor de desarrollo:
   ```bash
   npm start
   ```
   *(El backend, incluyendo el servidor MCP, estará escuchando las peticiones locales).*

### 5. Configuración del Frontend
1. En otra terminal, navega a la carpeta frontend:
   ```bash
   cd frontend
   npm install
   ```
2. Configura tu entorno apuntando a la API local (`VITE_API_URL=http://localhost:3000/api`).
3. Inicia el entorno de desarrollo:
   ```bash
   npm run dev
   ```

El portal estará disponible en tu navegador en `http://localhost:5173` para interactuar con el Agente RRHH. ¡Listo para desarrollar!

</details>

---

## Estructura del Proyecto

<details>
<summary><b>Haz clic aquí para desplegar la Arquitectura de Carpetas</b></summary>

El proyecto mantiene una estricta separación entre el portal web y el servidor inteligente que orquesta la IA:

```text
GarnierRrhh/
├── backend/                 # Servidor de IA y API (Node.js)
│   ├── config/              # Configuraciones de BD
│   ├── mcp/                 # Definición del Model Context Protocol (mcpServer.js)
│   ├── migrations/          # Migraciones de base de datos
│   ├── models/              # Modelos relacionales de Sequelize
│   ├── scripts/             # Scripts de utilidad
│   ├── services/            # Servicios complejos (RAG, embeddings, notificaciones)
│   └── utils/               # Utilidades generales
├── frontend/                # Interfaz de usuario (React / Vite)
│   ├── public/              # Archivos públicos y assets (favicon, etc)
│   ├── src/                 
│   │   ├── assets/          # Recursos visuales compilables
│   │   └── components/      # Componentes de UI (Chat, Panel Admin)
```
</details>
