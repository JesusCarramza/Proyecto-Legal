# Especificación de Procesos Complejos (Core Logic)

Más allá de los formularios tradicionales, el Sistema de Justicia Soberana integra motores avanzados que procesan las entradas del usuario de forma no lineal. A continuación, se detalla el flujo de datos de estos sistemas centrales:

# 1. Motor de Inteligencia Artificial (NLP y Búsqueda Semántica)

El sistema utiliza IA en varios puntos del flujo (Generador de Demandas para ciudadanos, Copiloto Judicial y Búsqueda Semántica para jueces).

* **Input (Entrada):**
  * **Contexto Estático:** El ID del caso actual y todos los documentos asociados (PDFs, transcripciones, contratos).
  * **Consulta Dinámica:** Cadenas de texto en lenguaje natural ingresadas por el usuario (ej. *"Identificar evidencia de aviso de terminación previo"* o *"Dígame qué sucedió con el retraso logístico"*).
* **Procesamiento (El "Backend"):**
  * El texto se vectoriza y se compara contra la base de conocimiento legal (leyes, precedentes) y los documentos específicos del caso utilizando modelos de procesamiento de lenguaje natural (NLP).
* **Output (Salida):**
  * **En el Visor del Juez:** Devuelve un objeto JSON que contiene: un fragmento de texto exacto (cita), un índice de confianza (ej. `94%`), y la referencia de la página de origen. La interfaz resalta visualmente el párrafo en el documento principal.
  * **En el Portal Ciudadano:** Transforma la narrativa conversacional en un borrador de formato legal estructurado.

# 2. Protocolo de Inmutabilidad Criptográfica (Cierre de Casos)

Para garantizar la integridad y soberanía de las decisiones judiciales, el sistema bloquea cualquier alteración post-resolución.

* **Input (Acción Detonante):**
  * El Juez hace clic en el botón crítico "Cerrar Caso y Publicar Sentencia" en el Módulo 5.
  * *Payload de datos:* ID del Juez, Timestamp exacto, ID del Caso, y el string completo en formato texto enriquecido de la resolución final.
* **Procesamiento (El "Backend"):**
  * El sistema agrupa todos los documentos del caso, las pruebas, los registros de actividad y la sentencia final.
  * Se pasa este paquete por una función de hash criptográfico (ej. SHA-256) para generar una huella digital única del expediente en ese milisegundo exacto.
  * El estado del caso en la base de datos se actualiza de `En Revisión` a `Cerrado_Inmutable`.
* **Output (Salida y Efectos Secundarios):**
  * **Interfaz:** Los botones de guardado, edición de texto y carga de documentos se desactivan (disabled) para todos los roles.
  * **Registro:** Se emite un certificado visible que incluye el Hash de Identidad (ej. `0x882A...F3E2`) demostrando que el documento no ha sido alterado desde su firma.
