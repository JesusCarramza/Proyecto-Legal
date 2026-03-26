# Diseño de Entradas y Salidas: Portal Juez (Visor con IA)

Este documento detalla el flujo de análisis de expedientes asistido por inteligencia artificial.

## 1. Entradas (Inputs)
| Campo / Elemento | Tipo de Dato | UI Component | Reglas de Validación y Lógica |
| :--- | :--- | :--- | :--- |
| **Selección de Caso** | `ID de Caso` | Panel Lateral (Tarjetas)| Carga los datos completos del expediente en el panel principal. |
| **Prompt IA Semántica** | `String` | `<input type="text">` | Consulta en lenguaje natural a la IA (ej. "Identificar evidencia de aviso de terminación previo"). |
| **Botones de Resolución** | `Estado` (Enum) | Botones superiores | Cambia el estado procesal del caso: "Admitida", "Prevenida", "Desechada". |

## 2. Salidas (Outputs)
| Elemento | Origen de Datos | UI Component | Descripción del Comportamiento |
| :--- | :--- | :--- | :--- |
| **Bandeja de Pendientes** | Base de Datos | Panel Lateral | Lista de casos asignados con su estado y contador de documentos anexos. |
| **Resumen Legal IA** | Motor Semántico | Tarjeta de Resultados | Devuelve: 1) Hallazgo Clave (texto citado del documento), 2) % de Confianza, 3) Página donde se encontró. |
| **Compensación Demandada**| Base de Datos (Parseada) | Tarjeta Financiera | Muestra el monto total exigido y un desglose de los conceptos (ej. "Indemnización", "Daños Morales"). |
| **Documento Formal** | Base de Datos / Storage | Visor de Documento | Renderiza el texto del expediente. La IA **resalta dinámicamente** los párrafos relevantes basándose en la búsqueda semántica. |