---
name: animated-shake
description: Consulta la documentación de React Native Reanimated para implementar la animación de sacudida (Shake animation) en formularios cuando falla el inicio de sesión u ocurre un error de validación, modificando únicamente los archivos necesarios dentro de src/.
---

# Reanimated Shake On Error

Esta skill instruye a la IA a consultar la documentación de React Native Reanimated e implementar la animación de sacudida (shake) en caso de error de autenticación.

## Regla Estricta de Ámbito
- **Modificación Quirúrgica**: Modificar únicamente los componentes o pantallas afectados (`src/components/campo-texto.tsx`, `src/components/pantalla-hoja.tsx` o `src/app/login.tsx`).
- **Cero cambios innecesarios**: No alterar el resto de pantallas, archivos de configuración ni constantes fuera del flujo de animación de error.

---

## Requerimientos y Flujo de Implementación

1. **Consulta de Documentación Oficial**:
   - Referencia: [React Native Reanimated Docs](https://docs.swmansion.com/react-native-reanimated/)
   - Utilizar las APIs recomendadas de Reanimated (e.g. `useSharedValue`, `useAnimatedStyle`, `withSequence`, `withTiming`) para construir una secuencia suave de traslación horizontal ($X$).

2. **Lógica de la Animación (Shake)**:
   - Crear un valor animado con `useSharedValue(0)`.
   - Al detectarse un error en el login (por ejemplo, credencial inválida o validación fallida), disparar una secuencia con `withSequence` y `withTiming` desplazando el componente a la izquierda y derecha (e.g. `-10`, `10`, `-8`, `8`, `-4`, `4`, `0`).

3. **Integración en Componentes**:
   - Envolver el elemento contenedor (`CampoTexto` o la tarjeta de `PantallaHoja`) en un `Animated.View`.
   - Aplicar el estilo animado generado por `useAnimatedStyle`.
   - Exponer un trigger/prop de activación (o reaccionar ante el cambio de estado de `error` / `errorGeneral`).

---

## Modificaciones Específicas

### 1. Componentes de UI (`src/components/campo-texto.tsx` o `src/components/pantalla-hoja.tsx`)
- Importar `Animated`, `useSharedValue`, `useAnimatedStyle`, `withSequence`, `withTiming` desde `react-native-reanimated`.
- Añadir un `useEffect` o función disparadora que active la secuencia de sacudida cuando la propiedad de error cambie o se reciba la orden de animación.

### 2. Pantalla de Login (`src/app/login.tsx`)
- Al capturar un fallo en el bloque `catch` de `iniciarSesion`, gatillar la animación de sacudida en el formulario o campo correspondiente para dar un feedback visual inmediato al usuario.