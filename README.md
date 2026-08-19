# 🛠️ Servii AI - Copiloto Inteligente para Servicios del Hogar

**Proyecto: Segunda Pre-entrega - IA: Generación de Prompts**  
**Autor:** Mateo Bentos

---

## 1. Introducción
**Nombre del proyecto:** Servii AI

## 2. Presentación del problema a abordar
El problema central radica en la fricción, informalidad y pérdida de tiempo al contratar servicios de mantenimiento y reparaciones del hogar en Uruguay. Según datos del Instituto Nacional de Estadística (INE), la informalidad laboral en el sector de oficios alcanza un alarmante 43,1%. Los usuarios sin conocimientos técnicos suelen describir los problemas de forma vaga y confusa. Esto obliga a los profesionales (sanitarios, electricistas, albañiles, etc.) a realizar visitas presenciales "a ciegas" simplemente para diagnosticar, lo que genera pérdida de tiempo, costos operativos innecesarios y presupuestos altamente variables.

## 3. Desarrollo de la propuesta de solución
**Servii AI** es una plataforma que utiliza Inteligencia Artificial Generativa para actuar como un "Director Técnico Virtual". La IA toma la solicitud informal del usuario y la transforma en una **Ficha Técnica estructurada** en tiempo real mediante técnicas de **Fast Prompting**. 

Esta solución se vincula directamente al desarrollo de modelos de IA (LLMs) al utilizar el procesamiento de lenguaje natural para categorizar averías, inferir niveles de urgencia y listar los materiales necesarios. Esto estandariza el proceso, permitiendo al profesional cotizar a distancia de forma precisa y transparente.

## 4. Justificación de la viabilidad del proyecto
El proyecto es altamente viable tanto a nivel técnico como financiero:
*   **Viabilidad Técnica:** Fraccionar el problema (ejecutar un único prompt de diagnóstico directo y estructurado) mantiene la arquitectura simple y libre de alucinaciones.
*   **Viabilidad Financiera:** Utilizar modelos eficientes como **Gemini 1.5 Flash** junto con técnicas de *Fast Prompting* (restringiendo tokens de salida y evitando un chatbot conversacional) reduce drásticamente el costo computacional. Procesar una solicitud mediante la API cuesta fracciones de centavo de dólar, logrando que el modelo sea 100% rentable frente al valor de intermediar un servicio real.

## 5. Objetivos
*   **Objetivo General:** Desarrollar una Prueba de Concepto (POC) funcional utilizando Python que automatice el diagnóstico técnico de averías del hogar.
*   **Objetivos Específicos:**
    *   Reducir el tiempo de diagnóstico inicial utilizando IA.
    *   Estandarizar las solicitudes informales en un formato técnico estructurado (JSON) comprensible para los trabajadores.
    *   Optimizar el consumo de la API y los costos operativos utilizando un único *prompt* altamente restrictivo y limitando el tamaño máximo de la respuesta.

## 6. Metodología
El proyecto se lleva a cabo mediante un enfoque iterativo de pruebas (POC) desarrollado en una **Jupyter Notebook**. 
*   **Procedimiento:** Se implementó un *script* en Python que consume directamente la API REST de Google Gemini. Se dividió el código en funciones simples, implementando un simulador interactivo donde el usuario ingresa su problema. La IA inyecta este problema en el sistema y devuelve una Ficha Técnica en una sola consulta, maximizando la velocidad y rentabilidad del sistema. Adicionalmente, el código incluye una validación dinámica que detecta automáticamente qué versión del modelo Gemini está habilitada en la cuenta del usuario para evitar errores de conexión.

## 7. Herramientas y tecnologías
*   **Técnica principal:** **Fast Prompting (Zero-Shot con Output Estructurado).** 
    *   *Justificación:* En un entorno de producción, la velocidad y el costo son críticos. En lugar de darle contexto largo o múltiples ejemplos (Few-Shot), se utiliza un *System Prompt* directo, con restricciones severas ("Cero charla", "sin saludos") y un formato JSON estricto. Esto disminuye la latencia y reduce el uso de tokens, haciendo la app escalable.
*   **Tecnologías:** 
    *   Python y Jupyter Notebooks.
    *   API REST de Google Gemini (Modelo *gemini-1.5-flash* por su excelente relación velocidad/costo).
    *   Librerías `requests` y `json` para conexiones directas y parseo seguro de datos.

---

## 🚀 Cómo ejecutar la Prueba de Concepto (POC)
1. Abre el archivo `Servii_AI_POC.ipynb` en tu entorno preferido (Visual Studio Code, Jupyter o Google Colab).
2. Ejecuta la celda principal de código.
3. Ingresa tu API Key de Gemini cuando el sistema te lo solicite en la barra superior.
4. Interactúa con el simulador ingresando un problema doméstico real (ej. *"El calefón pierde agua por debajo y hace ruido a chispa"*).