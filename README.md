# Servicio Médico de Predicción Simulada con Docker

## Descripción

Este proyecto implementa una API REST usando Flask y Docker para simular un modelo de Machine Learning aplicado al área médica.

El sistema recibe parámetros clínicos básicos de un paciente (temperatura, frecuencia cardiaca y nivel de dolor) y retorna una clasificación simulada del estado de salud.

Estados posibles:

- NO ENFERMO
- ENFERMEDAD LEVE
- ENFERMEDAD AGUDA
- ENFERMEDAD CRÓNICA

---

## Estructura del proyecto
```text
predecir_estado/
│
├── app_flask.py
├── predictor.py
├── requirements.txt
├── Dockerfile
└── README.md
```
---

## Requisitos

- Docker Desktop instalado y funcionando correctamente

### Verificar la instalación:
docker --version

## Construcción y ejecución

### 1. Descargar o clonar el proyecto

```bash
git clone https://github.com/AlejaF/medical_mlops.git
```

o descargar la carpeta:

```text
predecir_estado
```

### 2. Entrar a la carpeta

```bash
cd predecir_estado
```

### 3. Construir imagen Docker

```bash
docker build -t predecir_estado .
```

Verificar imagen:

```bash
docker images
```

### 4. Ejecutar contenedor

```bash
docker run -p 5000:5000 predecir_estado
```

Si todo funciona correctamente:

```text
Running on http://127.0.0.1:5000
```

---

## Endpoint disponible

```text
POST http://localhost:5000/predecir
```

---

## Ejemplo de solicitud

```powershell
Invoke-RestMethod `
-Uri "http://localhost:5000/predecir" `
-Method POST `
-ContentType "application/json" `
-Body '{"temperatura":39,"frecuencia_cardiaca":110,"nivel_dolor":8}'
```

---

## Respuesta esperada

```text
estado
-------
ENFERMEDAD AGUDA
```

---

## Variables de entrada

| Variable | Tipo |
|-----------|------|
| temperatura | float |
| frecuencia_cardiaca | int |
| nivel_dolor | int |

---
