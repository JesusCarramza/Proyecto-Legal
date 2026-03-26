# Diseño de Entradas y Salidas: Portal Administrador

Este documento detalla el flujo de datos para la gestión de usuarios y asignación de casos del Funcionario Judicial/Administrador.

## 1. Entradas (Inputs)
| Campo / Elemento | Tipo de Dato | UI Component | Reglas de Validación y Lógica |
| :--- | :--- | :--- | :--- |
| **Búsqueda Ciudadano** | `String` | `<input type="text">` | Filtra la tabla "Registro Ciudadano" por nombre o Hash de Identidad. |
| **Elevar a Juez** | `ID de Usuario` | Botón `<button>` | Acción que envía una petición al backend para cambiar el rol del usuario (requiere confirmación). |
| **Asignación Manual** | `ID de Caso` | Botón `<button>` | Abre un modal o flujo secundario para elegir a un juez manualmente. |
| **Confirmar Asignación IA**| `ID Caso + ID Juez` | Botón primario | Aprueba la sugerencia del sistema de IA y mueve el caso a la bandeja del Juez. |

## 2. Salidas (Outputs)
| Elemento | Origen de Datos | UI Component | Descripción del Comportamiento |
| :--- | :--- | :--- | :--- |
| **Tabla de Ciudadanos** | Base de Datos | `<table>` | Muestra Nombre, Hash de Identidad (ej. `0x882A...F3E2`), Estado (Verificado/Esperando) y Última Actividad. |
| **Lista de Casos** | Base de Datos | Tarjetas | Muestra ID del caso, Título, Categoría y tiempo transcurrido (ej. "Presentado hace 4h"). |
| **Sugerencia de IA** | Motor de IA | Tarjeta destacada | Devuelve el Perfil del Juez recomendado, Porcentaje de coincidencia (Óptima), Carga de trabajo actual (ej. 65%) y Justificación de texto ("¿Por qué esta recomendación?"). |
| **Gráfica de Eficiencia** | Motor de Analítica | Gráfico de barras | Representación visual del volumen; incluye un output de texto procesado: "tiempo de respuesta promedio: 1.4 horas". |