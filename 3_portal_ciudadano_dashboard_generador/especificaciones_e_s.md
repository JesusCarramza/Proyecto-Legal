# Diseño de Entradas y Salidas: Portal Ciudadano

Este documento detalla el flujo de datos para el tablero del ciudadano y la herramienta de generación de demandas.

## 1. Entradas (Inputs)
| Campo / Elemento | Tipo de Dato | UI Component | Reglas de Validación y Lógica |
| :--- | :--- | :--- | :--- |
| **Búsqueda** | `String` | `<input type="text">` | Búsqueda global de casos o identificaciones. |
| **Nombre Legal (Contraparte)**| `String` | `<input type="text">` | Obligatorio. Nombre de la persona o corporación demandada. |
| **Dirección (Contraparte)**| `String` | `<input type="text">` | Obligatorio. Domicilio legal para notificaciones. |
| **ID Entidad (Contraparte)**| `String` | `<input type="text">` | Opcional. Registro comercial. |
| **Chat de IA (Implícito)** | `String` | Interfaz de Chat | Input de texto natural del usuario detallando su problema (ej. "Perdieron la ventana de entrega..."). |

## 2. Salidas (Outputs)
| Elemento | Origen de Datos | UI Component | Descripción del Comportamiento |
| :--- | :--- | :--- | :--- |
| **Datos del Perfil** | Base de Datos | Tarjeta de Perfil | Muestra Nombre y el ID de Ciudadano Verificado (ej. `SVN-9921-X`). |
| **Actualizaciones en Vivo** | Sistema de Notificaciones| Lista | Feed de eventos (ej. "Audiencia Programada", "Firma Requerida") con marcas de tiempo. |
| **Libro Mayor de Casos** | Base de Datos | `<table>` | Tabla con casos activos: ID Digital, Título, Fecha y Estado (Abierto, En Revisión, Resolución Pendiente). |
| **Generador de Demandas** | Motor de NLP/IA | Chat Bubble | La IA procesa la historia del usuario y devuelve preguntas estructuradas o fragmentos de la demanda formateada. |