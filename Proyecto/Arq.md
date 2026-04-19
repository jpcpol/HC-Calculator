# 🏗️ Proyecto: Arquitectura del Sistema Personal de Gestión de Insulina y Hidratos

---

## 1. 🎯 Objetivo de la Arquitectura

Diseñar una arquitectura **simple, escalable y mantenible** que permita:

* Calcular dosis de insulina de forma determinística
* Registrar datos históricos de comidas y glucemia
* Analizar patrones individuales
* Incorporar inteligencia artificial de forma controlada
* Facilitar despliegue y actualización continua

El enfoque principal es:

👉 **precisión + control + evolución progresiva**

---

## 2. 🧠 Principios de Diseño

### 🔹 Separación de responsabilidades

* Lógica médica → determinística (no IA)
* Análisis → capa inteligente (IA opcional)

### 🔹 Simplicidad inicial

* Evitar sobreingeniería (no GPU, no OpenCL)
* Priorizar CPU y servicios livianos

### 🔹 Evolución incremental

* Arquitectura preparada para crecer sin rehacer todo

### 🔹 Observabilidad

* Todo debe ser medible, trazable y auditable

---

## 3. 🏗️ Arquitectura General

---

[Usuario / Input]
        ↓
[Frontend (futuro) / API REST]
        ↓
[Backend - FastAPI]
        ↓
 ├── Motor determinístico (cálculo insulina)
 ├── Persistencia (Postgres)
 └── Motor de análisis
          ↓
      [Modelo local (Ollama)]
          ↓
   (fallback opcional API externa)

---

## 4. 🔧 Componentes del Sistema

### 4.1 Backend (Core del sistema)

* Tecnología: Python + FastAPI
* Responsabilidades:

  * Exponer API REST
  * Ejecutar cálculos
  * Orquestar componentes

---

### 4.2 Motor Determinístico

Responsable de:

* Cálculo de hidratos totales
* Aplicación de ratio (1:10)
* Aplicación de corrección (1 cada 50 >150)

🔴 **Regla crítica:**
No depende de IA bajo ninguna circunstancia

---

### 4.3 Base de Datos (Postgres)

Almacena:

* Alimentos
* Comidas
* Detalles de cada comida
* Glucemias pre y post
* Insulina aplicada

Objetivo:
👉 generar histórico confiable para análisis

---

### 4.4 Motor de Análisis

Funciones:

* Evaluar resultados postprandiales
* Detectar:

  * subestimación de HC
  * hiperglucemia tardía
  * patrones repetitivos

Inicialmente basado en reglas.

---

### 4.5 Capa de IA (modelo local)

Uso:

* Interpretación de patrones complejos
* Generación de insights
* Sugerencias no determinísticas

Implementación:

* Modelo local (Ollama) ejecutado en CPU

---

### 4.6 Modelo Local Phi-3 Mini 3.8B

Características:

* Liviano (cuantizado si es necesario)
* CPU-friendly
* Baja latencia

Uso limitado a:

* análisis textual
* clasificación de comportamiento

---

## 5. 🐳 Estrategia de Despliegue

### Infraestructura

* VPS estándar (sin GPU)
* Docker + Docker Compose

### Servicios

* API (FastAPI)
* Postgres
* Ollama

---

## 6. 🔄 Flujo de Actualización

### Método inicial

* Conexión por SSH
* Uso de Docker Compose

---

git pull
docker-compose pull
docker-compose up -d

---

### Evolución

* Integración con CI/CD (GitHub Actions)
* Deploy automatizado

---

## 7. 📊 Flujo de Datos

1. Usuario ingresa comida
2. API calcula:

   * HC totales
   * insulina sugerida
3. Se registra:

   * glucemia pre
   * insulina aplicada
4. Usuario registra valores post (2h / 4h)
5. Motor de análisis procesa resultados
6. IA (opcional) interpreta patrones

---

## 8. ⚠️ Decisiones Clave de Arquitectura

### 🔴 No usar GPU / OpenCL o mejor

**Motivo:**

* Baja necesidad computacional
* Reducción de complejidad
* Menor costo

---

### 🔴 IA como complemento, no como núcleo

**Motivo:**

* Evitar errores críticos
* Mantener control clínico
* Asegurar reproducibilidad

---

### 🔴 Uso de Docker

**Motivo:**

* Portabilidad
* Facilidad de despliegue
* Consistencia de entornos

---

### 🟡 Uso de modelo local en CPU

**Motivo:**

* Independencia de servicios externos
* Reducción de costos
* Mayor control de datos

---

## 9. 📈 Escalabilidad

### Horizontal

* Separar servicios (API, DB, IA)

### Vertical

* Aumentar recursos del VPS

### Evolución futura

* Integración con sensores
* Apps móviles
* Machine learning avanzado

---

## 10. 🔐 Seguridad

* Acceso por SSH con keys
* Protección de base de datos
* Backups periódicos
* Control de acceso a API

---

## 11. 🚀 Roadmap Técnico

### Fase 1

* Backend + DB + cálculo básico

### Fase 2

* Registro histórico + análisis simple

### Fase 3

* Integración modelo local

### Fase 4

* CI/CD + automatización

### Fase 5

* Visualización (dashboards)

---

## 12. 🧠 Objetivo de las Decisiones de Arquitectura

Cada decisión busca:

* Reducir complejidad innecesaria
* Maximizar control del sistema
* Permitir crecimiento sin rediseño
* Asegurar precisión en cálculos críticos
* Incorporar inteligencia de forma segura

---

## 13. 📌 Resultado Esperado

Un sistema:

* Confiable en cálculos
* Adaptado al comportamiento del usuario
* Evolutivo en inteligencia
* Eficiente en recursos
* Desplegable en infraestructura simple

---

**Estado:** Arquitectura validada para implementación
**Próximo paso:** Dockerización + despliegue en VPS
**Desarrollado por Juan Pablo Chancay Aural-Syncro** mail:juanpablo.chancay@aural-syncro.com.ar
