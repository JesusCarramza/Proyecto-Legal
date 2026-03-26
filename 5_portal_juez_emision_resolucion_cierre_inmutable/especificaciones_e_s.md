# Diseño de Entradas y Salidas: Portal Juez (Emisión de Resolución)

Este documento detalla el proceso crítico de redacción de sentencias y el cierre criptográfico de expedientes.

## 1. Entradas (Inputs)
| Campo / Elemento | Tipo de Dato | UI Component | Reglas de Validación y Lógica |
| :--- | :--- | :--- | :--- |
| **Prompt Copiloto Judicial**| `String` | `<input type="text">` | Consulta a la IA para buscar precedentes (ej. "Pregunte por precedentes legales..."). |
| **Cuerpo de la Sentencia**| `Texto Enriquecido` | `<textarea>` / Editor WYSIWYG | Área de texto libre donde el juez redacta el fallo final. Soporta formato (negritas, cursivas, listas). |
| **Cerrar Caso y Publicar**| `Evento de Sistema` | Botón Crítico (Rojo) | Detona el "Protocolo de Inmutabilidad". Convierte la sentencia en un documento de solo lectura. |

## 2. Salidas (Outputs)
| Elemento | Origen de Datos | UI Component | Descripción del Comportamiento |
| :--- | :--- | :--- | :--- |
| **Inteligencia del Caso** | Base de Datos | Panel Lateral | Resumen del caso actual: Disputa Principal, Fecha, Valor, Documentos Clave. |
| **Copiloto Judicial** | Motor de IA Legal | Chat / Bloque de Texto | Sugerencia de la IA basada en precedentes legales (ej. citar jurisprudencia específica). |
| **Borrador de Sentencia** | Plantilla de Sistema | Editor de Texto | Carga un preámbulo inicial con los nombres de las partes generados automáticamente. |
| **Advertencia Inmutabilidad**| Regla de Negocio | Banner Rojo Alerta | Mensaje estático: Advierte al juez que se generará un hash criptográfico y no se permitirán más cambios. |