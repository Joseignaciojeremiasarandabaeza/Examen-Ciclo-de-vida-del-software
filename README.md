# TechMarket Orders: Operación Resiliencia
Examen Transversal - Ciclo de Vida del Software

Este repositorio contiene el desarrollo del Examen Transversal, planteado como un desafío de Ingeniería del Caos en un entorno productivo simulado. El objetivo principal es transformar un pipeline de CI/CD precario e inestable en una "Fortaleza Digital", migrando y robusteciendo el microservicio crítico TechMarket Orders dentro de un clúster de Amazon EKS.

El proyecto demuestra la integración avanzada de plantillas reutilizables, estrategias de despliegue de alta disponibilidad y mecanismos de remediación automática ante fallos inyectados en tiempo real.

 Objetivos del Proyecto

El flujo de trabajo se divide en tres pilares fundamentales de la metodología DevOps:
1. Estandarización y Migración a Amazon EKS

    CI/CD con GitHub Actions: Refactorización completa del pipeline básico a un flujo de trabajo moderno, modular y seguro.

    Plantillas Reutilizables: Implementación de workflows centralizados para las etapas de Build (construcción de imagen Docker y push a Amazon ECR) y Deploy (aplicación de manifiestos sobre el clúster EKS).

    Inyección Dinámica: Configuración de variables de entorno dinámicas según el entorno de despliegue.

2. Estrategia de Despliegue Avanzada

    Estrategia Implementada: [Blue-Green] (Nota: Selecciona la que hayas utilizado).

    Control de Tráfico: Manipulación avanzada de objetos de Kubernetes (Service / Ingress) para gestionar la transición del tráfico entre la versión estable y la nueva versión.

    Validación de Salud (Smoke Tests): Inclusión de una etapa crítica de verificación antes de conmutar el 100% del tráfico.

3. Ingeniería del Caos y Remediación Automática

    Rollback Automático: Configuración del pipeline para detectar métricas de fallo (ej. latencia alta o errores HTTP 500) durante la fase de validación.

    Auto-recuperación: Capacidad del sistema para revertir automáticamente los cambios en el clúster EKS a la última versión estable sin intervención humana, garantizando la resiliencia ante errores desconocidos en tiempo real.

 Arquitectura de la Solución

[Código Fuente] ──> [GitHub Actions] ──> [Amazon ECR]
                                                │
                                                ▼
[Remediación Automática] <── [Validación] <── [Amazon EKS]

techmarket-orders-fortress/
├── .github/
│   └── workflows/
│       └── main-pipeline.yml         <-- Pipeline Principal (Orquestador plano)
├── templates/                        <-- Las Plantillas Reutilizables de la EP1 (En la raíz)
│   ├── build-template.yml
│   └── deploy-template.yml
├── k8s/
│   ├── orders-blue.yaml
│   ├── orders-green.yaml
│   └── orders-service.yaml
└── README.md

 Demostración y Defensa

Este repositorio está estructurado para servir como el soporte visual y técnico único de la presentación final:

    Historial de Commits: Cada paso, decisión de arquitectura y configuración técnica se encuentra estrictamente documentado en el histórico de Git.

    Pipeline en Acción: Evidencia del funcionamiento de las automatizaciones solicitadas directamente desde la pestaña Actions.
