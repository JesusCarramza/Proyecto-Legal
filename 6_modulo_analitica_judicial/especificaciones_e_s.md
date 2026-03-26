# Diseño de Entradas y Salidas: Analítica Judicial

Este documento detalla el flujo de datos para la generación de reportes y métricas de desempeño del tribunal.

## 1. Entradas (Inputs)
| Campo / Elemento | Tipo de Dato | UI Component | Reglas de Validación y Lógica |
| :--- | :--- | :--- | :--- |
| **Filtro de Tiempo** | `Rango de Fechas` | Botones Superiores | Aplica filtros rápidos: "Últimos 30 Días", "Trimestral", "Anual". |
| **Especialidad del Juez** | `String` (Enum) | `<select>` | Filtra los datos por rama (Civil, Penal, Familia, etc.). |
| **Período Específico** | `Date` | `<input type="date">` | Permite buscar un día/mes específico. |
| **Sucursal del Distrito** | `String` (Enum) | `<select>` | Filtra por ubicación del tribunal. |

## 2. Salidas (Outputs)
| Elemento | Origen de Datos | UI Component | Descripción del Comportamiento |
| :--- | :--- | :--- | :--- |
| **Tarjetas KPI** | Motor Analítico | Tarjetas numéricas | Muestra métricas procesadas: Demandas Totales, Resolución Promedio, Tasa de Admisión, Revisión Pendiente (incluye comparativas ej. "+12% vs mes anterior"). |
| **Volumen de Casos** | Motor Analítico | Gráfico de Barras | Visualiza los casos procesados vs el objetivo por mes. |
| **Mezcla de Resultados** | Motor Analítico | Gráfico Circular (Donut) | Distribución de los resultados (Admitidos, Desechados, Apelados). |
| **Tabla de Rendimiento** | Base de Datos | `<table>` | Lista de jueces con sus Casos Activos, Casos Cerrados, Días Promedio y Estado de desempeño (Óptimo, Alerta). |
| **Perspectiva Soberana IA**| Motor de IA Analítica | Notificación Flotante | El sistema detecta anomalías en los datos y sugiere informes de forma proactiva (ej. "Los tiempos de resolución han aumentado un 15%"). |