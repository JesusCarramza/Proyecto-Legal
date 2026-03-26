# Diseño de Entradas y Salidas: Módulo de Autenticación y Acceso

Este documento detalla el flujo de datos para la interfaz de inicio de sesión y registro del Sistema de Justicia Soberana.

## 1. Entradas (Inputs)
| Campo / Elemento | Tipo de Dato | UI Component | Reglas de Validación y Lógica |
| :--- | :--- | :--- | :--- |
| **Correo Institucional** | `String` (Email) | `<input type="email">` | Obligatorio. Debe coincidir con formato email. Dominio sugerido: `@tribunal.gob` para funcionarios. |
| **Contraseña Segura** | `String` | `<input type="password">` | Obligatorio. Enmascarado en UI. Botón "visibility" alterna entre `text` y `password`. |
| **Botón de Acción UI** | `Booleano` | Tabs superiores | Alterna el estado de la vista entre "Iniciar Sesión" y "Registrarse". |

## 2. Salidas (Outputs)
| Elemento | Origen de Datos | UI Component | Descripción del Comportamiento |
| :--- | :--- | :--- | :--- |
| **Error de Credenciales** | Backend (Auth) | Banner rojo | Aparece si el login falla. Mensaje: "Credenciales inválidas. Por favor, verifique su ID..." |
| **Notificación de Registro** | Backend / Estado Local | Banner verde / azul | Se muestra al solicitar registro. Mensaje: "Su solicitud ha sido enviada. Un Secretario Principal verificará..." |
| **Redirección** | Router / Backend | Acción de Sistema | Si el login es exitoso, redirige al `index.html` (o router) que despacha al portal del rol correspondiente (Ciudadano, Admin, Juez). |