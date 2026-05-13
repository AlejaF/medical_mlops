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
## Instrucciones

## Requisitos

-Docker Desktop instalado
-Docker funcionando correctamente

### Para verificar la instalación:
docker --version

## Construcción de la imagen Docker

### Descargar la carpeta predecir_estado

### Ubicarse en la carpeta del proyecto:
cd predecir_estado

### Construir la imagen:
```bash
docker build -t predecir_estado .
```

### Verificar imagen creada:
```bash
docker images
```

### Ejecutar el contenedor
```bash
docker run -p 5000:5000 predecir_estado
```

### Si la ejecución fue exitosa aparecerá:
```text
Running on http://127.0.0.1:5000
```

## Endpoint disponible
```text
POST http://localhost:5000/predecir
```

### Ejemplo de solicitud desde PowerShell
```powershell
Invoke-RestMethod `
-Uri "http://localhost:5000/predecir" `
-Method POST `
-ContentType "application/json" `
-Body '{"temperatura":39,"frecuencia_cardiaca":110,"nivel_dolor":8}'
```

### Respuesta esperada
```text
estado: ENFERMEDAD AGUDA
```
