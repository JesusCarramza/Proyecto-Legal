# Estados Vacíos y Casos Extremos (Edge Cases & Empty States)

El diseño visual actual muestra el "camino feliz" (Happy Path) donde el sistema tiene datos y funciona perfectamente. Este documento especifica el comportamiento de las interfaces cuando no hay información disponible o cuando ocurren fallos técnicos.

## 1. Estados Vacíos (Empty States)

Situaciones donde las bases de datos o consultas no devuelven resultados. La interfaz no debe verse "rota", sino guiar al usuario.

* **Módulo 3 (Portal Ciudadano): Libro Mayor sin Casos**
  * *Condición:* El ciudadano recién registrado no tiene demandas activas.
  * *Comportamiento UI:* La tabla de "Libro Mayor de Casos Activos" se oculta. En su lugar, se muestra un contenedor `surface-container-lowest` con un ícono ilustrativo (ej. `folder_off`), un texto que diga "Aún no tiene casos registrados en el sistema", y un botón primario grande que diga "Iniciar Nuevo Trámite" que dirija al Generador de Demandas.
* **Módulo 6 (Analítica Judicial): Sin datos en el filtro**
  * *Condición:* El usuario selecciona un "Período de Reporte" o "Sucursal" donde no hubo actividad judicial.
  * *Comportamiento UI:* Las tarjetas de KPI numéricas muestran "0" o "--". El gráfico de "Volumen de Procesamiento" desaparece y se muestra el mensaje: "No hay suficientes datos procesados para el período o distrito seleccionado. Por favor, ajuste los filtros."

## 2. Casos Extremos y Manejo de Errores (Error Handling)

Situaciones donde ocurren interrupciones en el flujo lógico, problemas de red o fallos de los motores externos.

* **Módulo 1 (Autenticación): Bloqueo por fuerza bruta**
  * *Condición:* El usuario introduce credenciales inválidas más de 5 veces consecutivas.
  * *Comportamiento UI:* El input de contraseña se deshabilita (`disabled`). El banner de error cambia a estado rojo crítico (`error-container`) con el mensaje: "Por motivos de seguridad, su cuenta ha sido bloqueada temporalmente. Contacte a su administrador de distrito."
* **Módulo 4 (Visor de Expediente Juez): Fallo en la IA Semántica**
  * *Condición A (Sin coincidencias):* La consulta del juez (ej. "Identificar evidencia...") no encuentra base semántica en el texto.
    * *Comportamiento UI:* El asistente devuelve un mensaje neutral: *"La IA no encontró fragmentos con alta confianza (>85%) relacionados con su consulta en este expediente."*
  * *Condición B (Caída del servicio IA):* El servicio de NLP tarda más de 10 segundos en responder (Timeout).
    * *Comportamiento UI:* El botón de "Ejecutar" recupera su estado, la animación de carga se detiene y aparece un *toast notification*: *"Servicio de IA temporalmente no disponible. Intente la búsqueda estándar por palabras clave."*
* **Módulo 5 (Emisión de Resolución): Interrupción en Protocolo de Inmutabilidad**
  * *Condición:* El juez hace clic en "Cerrar Caso y Publicar Sentencia" pero hay una pérdida de conexión a internet antes de que el servidor confirme la generación del hash.
  * *Comportamiento UI:* El sistema previene el cierre. Muestra un overlay de bloqueo visual indicando *"Generando huella criptográfica..."* Si falla, revierte el estado, muestra un banner de alerta y asegura que el borrador de la sentencia siga guardado en el estado local (`localStorage`) para no perder la redacción del juez.
