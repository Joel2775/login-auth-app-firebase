---
name: estructura-proyecto
description: Genera y organiza únicamente la estructura del directorio src/ para un proyecto de React Native / Expo con Router (app/, components/, config/, constants/, context/, lib/), garantizando no modificar archivos o configuraciones fuera de src/.
---

# Expo Src Structure Generator

Esta skill instruye a la IA a generar, modificar y organizar archivos **únicamente dentro de la carpeta `src/`** de un proyecto React Native con Expo Router.

## Regla Estricta de Ámbito
- **Cero modificaciones fuera de `src/`**: Bajo ninguna circunstancia se deben modificar o crear archivos fuera de `src/` (tales como `package.json`, `app.json`, `tsconfig.json`, `babel.config.js`, `.env*`, etc.).
- Todo el código de rutas, componentes, estado global, estilos y configuración interna debe crearse estrictamente dentro de `src/`.

---

## Estructura Objetivo Exacta

```text
src/
├── app/
│   ├── (app)/
│   │   ├── _layout.tsx
│   │   ├── cambiar-clave.tsx
│   │   └── index.tsx
│   ├── _layout.tsx
│   ├── login.tsx
│   ├── recuperar.tsx
│   └── registro.tsx
├── components/
│   ├── aviso.tsx
│   ├── boton.tsx
│   ├── campo-texto.tsx
│   ├── curvas-de-nivel.tsx
│   └── pantalla-hoja.tsx
├── config/
│   └── firebase.ts
├── constants/
│   └── tema.ts
├── context/
│   └── sesion.tsx
└── lib/
    ├── errores-firebase.ts
    └── validaciones.ts