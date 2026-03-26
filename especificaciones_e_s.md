# 1. Mapa de Navegación de Interfaces (User Flows)
El acceso y la navegación dentro del Sistema de Justicia Soberana están estrictamente delimitados por el rol del usuario autenticado.

## Punto de Entrada Universal
- Inicio de Sesión: Todos los usuarios (Ciudadanos, Administradores y Jueces) ingresan al sistema a través del `1_modulo_autenticacion_acceso`.

- Decisión del Sistema: Tras validar las credenciales (Correo Institucional y Contraseña Segura), el backend determina el rol del usuario y lo redirige a su portal correspondiente.

## Flujo A: Usuario Ciudadano

1. Dashboard Principal: Redirección a `3_portal_ciudadano_dashboard_generador` tras autenticación exitosa.

2. Acciones Posibles:

    - Consultar actualizaciones en vivo y revisar el "Libro Mayor de Casos Activos".

    - Iniciar el "Generador de Demandas" asistido por IA.

    - Registrar "Información de la Contraparte" en los formularios correspondientes.

## Flujo B: Usuario Administrador (Funcionario Judicial)
1. Portal de Gestión: Redirección a `2_portal_administrador_gestion_asignacion`.

2. Acciones Posibles:

    - Gestionar el "Registro Ciudadano" (verificar usuarios, elevar a juez).

    - Revisar asignaciones pendientes y confirmar sugerencias de la IA.

    - Navegar hacia el `6_modulo_analitica_judicial` (mediante el menú de navegación) para ver métricas globales.

## Flujo C: Usuario Juez

1. Visor de Expedientes: Redirección a `4_portal_juez_visor_expediente_ia`.

2. Acciones Posibles:

    - Revisar la "Bandeja de Pendientes" y seleccionar un caso.

    - Consultar a la IA de Búsqueda Semántica dentro del expediente.

3. Transición a Resolución: Una vez analizado el caso, el flujo continúa hacia `5_portal_juez_emision_resolucion_cierre_inmutable`.

    - Punto de No Retorno: Al hacer clic en "Cerrar Caso y Publicar Sentencia", se activa el Protocolo de Inmutabilidad, cerrando el flujo de edición para ese caso específico.

4. Consulta Analítica: Al igual que el Administrador, el Juez puede navegar al `6_modulo_analitica_judicial` para revisar su propio desempeño o el volumen de procesamiento.