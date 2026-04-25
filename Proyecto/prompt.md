# 🧠 Prompt del Proyecto

Diseñar y desarrollar un **Sistema Inteligente de Gestión de Insulina y Hidratos de Carbono** que combine precisión médica, análisis de datos y capacidad evolutiva, utilizando una arquitectura moderna, escalable y mantenible.

El sistema debe ser construido con estándares **Enterprise-grade**, asegurando:

- Alta confiabilidad en cálculos críticos
- Observabilidad completa (logs, métricas, trazabilidad)
- Seguridad de datos
- Escalabilidad horizontal y vertical
- Despliegue automatizable (CI/CD)
- Portabilidad mediante contenedores

A su vez, debe estar orientado a ser **accesible para cualquier persona**, lo que implica:

- Bajo costo de infraestructura
- Posibilidad de ejecución en hardware común (CPU, sin GPU)
- Facilidad de instalación (Docker, VPS estándar o incluso entornos locales)
- Interfaces simples e intuitivas (futuro frontend)
- Independencia de servicios pagos siempre que sea posible

Si el sistema requiere hardware adicional (sensores, dispositivos, etc.), se deberá:

👉 Priorizar siempre **tecnologías ampliamente disponibles, económicas y fáciles de conseguir**  
👉 Evitar soluciones propietarias o de alto costo  
👉 Favorecer estándares abiertos (ej: ONVIF, APIs públicas, dispositivos IoT comunes)

---

# 🎯 Objetivo del Proyecto

Desarrollar una solución integral que permita:

- Calcular dosis de insulina de forma **determinística y confiable**
- Registrar información histórica de:
  - comidas
  - hidratos de carbono
  - glucemia
  - insulina aplicada
- Detectar patrones individuales en el comportamiento glucémico
- Reducir errores en la estimación de hidratos y dosis
- Incorporar inteligencia artificial de forma **controlada y no crítica**

El sistema debe evolucionar progresivamente hacia un modelo **adaptativo**, manteniendo siempre:

👉 Control clínico  
👉 Reproducibilidad  
👉 Transparencia en decisiones  

---

# 🧩 Contexto del Sistema

El proyecto se basa en una arquitectura desacoplada con los siguientes principios:

## 🏗️ Arquitectura General

- Backend en **FastAPI (Python)**
- Base de datos relacional (**PostgreSQL/MySQL**)
- Motor determinístico para cálculos críticos
- Motor de análisis basado en reglas + IA opcional
- Integración con modelo local de lenguaje (ej: Ollama + modelos livianos)

## ⚙️ Características clave

### 🔴 Núcleo determinístico

- El cálculo de insulina:
  - NO depende de IA
  - Se basa en reglas médicas claras
  - Es totalmente auditable

### 🟡 Capa inteligente (IA)

- Uso exclusivo para:
  - análisis de patrones
  - sugerencias
  - interpretación de datos
- Implementación preferente:
  - modelos locales
  - ejecución en CPU
  - bajo consumo de recursos

### 🐳 Infraestructura

- Contenerización con Docker
- Orquestación con Docker Compose (inicial)
- Preparado para Kubernetes (futuro)
- Despliegue en:
  - VPS económicos
  - servidores on-premise
  - entornos híbridos

## 📊 Flujo del Sistema

1. Usuario registra comida y glucemia
2. Sistema calcula dosis sugerida
3. Se almacena la información
4. Se registran valores postprandiales
5. Motor de análisis detecta patrones
6. IA complementa con insights (opcional)

---

## 🌍 Enfoque de Accesibilidad

El sistema debe poder ser utilizado por:

- Usuarios individuales
- Profesionales de salud
- Entornos con recursos limitados

Por lo tanto:

- No requiere hardware especializado
- Puede ejecutarse en equipos domésticos o VPS básicos
- Minimiza dependencias externas
- Mantiene costos operativos bajos

---

## 🚀 Resultado Esperado

Una plataforma:

- **Confiable** en cálculos críticos
- **Escalable** como sistema Enterprise
- **Accesible** para cualquier usuario
- **Eficiente** en uso de recursos
- **Evolutiva** en inteligencia y capacidades
- **Segura y auditable**

---

## ⚠️ Consideración Final

Este sistema es una herramienta de soporte y debe diseñarse bajo el principio de:

👉 *"La automatización asiste, pero el control lo mantiene el usuario."*