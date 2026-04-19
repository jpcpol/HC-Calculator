# 📊 Sistema Personal de Gestión de Insulina y Hidratos

## 🧠 Descripción

Este proyecto es un sistema personal orientado a mejorar la precisión en el cálculo de dosis de insulina mediante:

* Conteo de hidratos de carbono
* Registro de glucemia
* Análisis de patrones individuales
* Uso opcional de modelos de lenguaje (LLM) para interpretación

El sistema combina **lógica determinística (reglas médicas)** con una **capa de análisis inteligente**.

---

## 🎯 Objetivos

* Calcular dosis de insulina de forma confiable
* Registrar historial de comidas y glucemia
* Detectar patrones personalizados
* Reducir errores en estimación de hidratos
* Evolucionar hacia un sistema adaptativo

---

## ⚙️ Arquitectura

```
[Input Usuario]
        ↓
[API - FastAPI]
        ↓
 ├── Motor determinístico
 ├── Base de datos (MySQL)
 └── Motor de análisis
          ↓
      [Ollama - modelo local]
```

---

## 🧮 Lógica de Cálculo

### Relación HC / Insulina

* 1 unidad cada 10 g de hidratos

### Corrección

* 1 unidad cada 50 mg/dl por encima de 150 mg/dl

### Fórmula

```python
insulina_hc = total_hc / 10
correccion = max(0, (glucemia - 150) / 50)
insulina_total = insulina_hc + correccion
```

---

## 🗄️ Modelo de Datos

### alimentos

* id
* nombre
* hc_por_porcion
* tipo_absorcion

### comidas

* id
* fecha
* glucemia_pre
* glucemia_post_2h
* glucemia_post_4h
* insulina_aplicada

### comida_detalle

* comida_id
* alimento_id
* cantidad

---

## 🤖 Uso de IA

La IA se utiliza exclusivamente para:

* Análisis de patrones
* Interpretación de resultados
* Sugerencias de ajuste

⚠️ **No se utiliza para calcular dosis de insulina**

---

## 🐳 Despliegue

### Requisitos

* VPS (2–4 vCPU, 4–8GB RAM)
* Docker
* Docker Compose

### Servicios

* API (FastAPI)
* postgres
* Ollama

---

## 🚀 Instalación

```bash
git clone <repo>
cd proyecto

docker-compose up -d
```

---

## 🔄 Actualizaciones

### Manual (SSH)

```bash
ssh user@server
git pull
docker-compose pull
docker-compose up -d
```

### Futuro

* CI/CD con GitHub Actions

---

## 📊 Flujo de Uso

1. Registrar comida
2. Ingresar glucemia pre
3. Obtener dosis sugerida
4. Aplicar insulina
5. Registrar glucemia post (2h / 4h)
6. Analizar resultados

---

## 📈 Roadmap

### Fase 1

* MVP funcional
* Cálculo básico

### Fase 2

* Registro histórico
* Análisis simple

### Fase 3

* Integración LLM local

### Fase 4

* CI/CD
* Dashboards

---

## 🔐 Seguridad

* Acceso por SSH con keys
* Protección de base de datos
* Backups periódicos

---

## ⚠️ Disclaimer

Este sistema es una herramienta de apoyo y **no reemplaza indicaciones médicas profesionales**.

---

## 🧠 Filosofía

* Simplicidad primero
* Control sobre automatización
* Datos reales > teoría
* Evolución continua

---

## 📌 Estado

🟢 En desarrollo – arquitectura definida, listo para implementación

**Desarrollado por Juan Pablo Chancay Aural-Syncro** mail:juanpablo.chancay@aural-syncro.com.ar
