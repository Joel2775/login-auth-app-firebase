---
name: autenticacion-firebase
description: Implementa la verificación obligatoria de correo electrónico con Firebase Auth para un proyecto de Expo Router. Envía el correo de verificación con sendEmailVerification en el registro y bloquea el acceso a las rutas protegidas (pantalla de bienvenida) hasta que el correo esté verificado.
---

# Firebase Email Verification Handler

Esta skill instruye a la IA para agregar la Historia de Usuario (HU) de **Verificación de Correo Electrónico con Firebase Auth** dentro de la estructura existente de `src/`, modificando únicamente los archivos estrictamente necesarios.

## Regla Estricta de Modificación
- **Solo tocar los archivos necesarios**: Modificar únicamente los archivos vinculados a la lógica de autenticación y flujo de sesión (`src/context/sesion.tsx`, `src/app/_layout.tsx`, `src/app/login.tsx`, `src/app/registro.tsx` y `src/app/(app)/index.tsx`).
- **Respetar el resto del proyecto**: No modificar ningún otro componente, constantes, estilos ni configuraciones del proyecto.

---

## Requerimientos de la Historia de Usuario (HU)

1. **Envío de Correo**: Al registrar un nuevo usuario con `createUserWithEmailAndPassword`, se debe ejecutar inmediatamente `sendEmailVerification`.
2. **Restricción de Acceso**: La pantalla de bienvenida (`/` dentro del grupo `(app)`) **solo** debe ser accesible si `usuario.emailVerified === true`.
3. **Flujo Post-Registro**: Al completarse el registro, la app no debe dar acceso inmediato a la pantalla protegida; debe notificar al usuario que revise su bandeja de entrada.
4. **Pantalla / Estado de Verificación Pendiente**: Si un usuario con correo NO verificado intenta iniciar sesión, se debe bloquear el ingreso a la zona privada y permitirle reenviar el correo de verificación o recargar el estado para comprobar si ya lo verificó.

---

## Archivos a Modificar y Cambios Específicos

### 1. `src/context/sesion.tsx`
- Importar `sendEmailVerification` y `reload` desde `firebase/auth`.
- Agregar a `ValorSesion` la función `reenviarVerificacion: () => Promise<void>` y `recargarUsuario: () => Promise<void>`.
- En la función `registrarse`:
  - Tras llamar a `createUserWithEmailAndPassword`, ejecutar `sendEmailVerification(credencial.user)`.
- Implementar `recargarUsuario`:
  - Llama a `reload(auth.currentUser)` para actualizar el valor de `emailVerified` en tiempo real y refrescar el estado.

### 2. `src/app/_layout.tsx`
- En el guard de las rutas protegidas `Stack.Protected`, ajustar la condición para que solo dé acceso si el usuario existe **y** su correo está verificado:
  ```tsx
  const estaAutenticadoYVerificado = !!usuario && usuario.emailVerified;

  <Stack.Protected guard="{estaAutenticadoYVerificado}">
    <Stack.Screen name="(app)"/>
  </Stack.Protected>