# Contexto Completo del Proyecto CV-CREATOR-APP


================================================
📄 ARCHIVO: .env.example
================================================

EXPO_PUBLIC_FIREBASE_API_KEY=tu-api-key
EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN=tu-proyecto.firebaseapp.com
EXPO_PUBLIC_FIREBASE_PROJECT_ID=tu-proyecto
EXPO_PUBLIC_FIREBASE_STORAGE_BUCKET=tu-proyecto.firebasestorage.app
EXPO_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=000000000000
EXPO_PUBLIC_FIREBASE_APP_ID=1:000000000000:web:0000000000000000000000


================================================
📄 ARCHIVO: .env.local
================================================

EXPO_PUBLIC_FIREBASE_API_KEY=AIzaSyDhM9SrjwczGd44eiYf7bqfd-TPWWTDPTQ
EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN=esfot-login-f1a1b.firebaseapp.com
EXPO_PUBLIC_FIREBASE_PROJECT_ID=esfot-login-f1a1b
EXPO_PUBLIC_FIREBASE_STORAGE_BUCKET=esfot-login-f1a1b.firebasestorage.app
EXPO_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=617768948745
EXPO_PUBLIC_FIREBASE_APP_ID=1:617768948745:web:2e6ebda2f005661ab554d8


================================================
📄 ARCHIVO: .github\skills\estructura-proyecto\SKILL.md
================================================

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

================================================
📄 ARCHIVO: .gitignore
================================================

# Learn more https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files

# dependencies
node_modules/

# Expo
.expo/
dist/
web-build/
expo-env.d.ts

# Native
.kotlin/
*.orig.*
*.jks
*.p8
*.p12
*.key
*.mobileprovision

# Metro
.metro-health-check*

# debug
npm-debug.*
yarn-debug.*
yarn-error.*

# macOS
.DS_Store
*.pem

# local env files
.env*.local

# typescript
*.tsbuildinfo

example

# generated native folders
/ios
/android


================================================
📄 ARCHIVO: AGENTS.md
================================================

This is an Expo/React Native mobile application. Prioritize mobile-first patterns, performance, and cross-platform compatibility.

## Expo has changed — do not trust your training data

Expo ships breaking changes every SDK release. APIs you remember are likely renamed, moved, or removed. Before writing any code that touches an Expo, EAS, or React Native API:

1. Read the major version of the `expo` package in `package.json`.
2. Fetch the matching versioned docs: `https://docs.expo.dev/versions/v<major>.0.0/`
3. For anything else, fetch https://docs.expo.dev/llms.txt — an index of all Expo docs with corrections to common LLM misconceptions. Follow its links to the specific page you need; never answer from memory.

## Commands

Use `bunx` instead of `npx` if the project uses bun (`bun.lock` present).

```bash
npx expo install <package>  # ALWAYS use instead of npm/yarn/pnpm/bun add — resolves SDK-compatible versions
npx expo start              # start the dev server
npx expo lint               # lint
npx tsc --noEmit            # typecheck
npx expo-doctor             # diagnose dependency and config issues
npx expo install --fix      # fix incompatible package versions
```

Run lint and typecheck before declaring any task done.

## Navigation & Routing

- Use **Expo Router** for all navigation. Routes live in `src/app/` — every file there is a screen, `_layout.tsx` files define navigators. Keep non-route code (components, hooks, utils) outside `src/app/`.
- Import `Link`, `router`, and `useLocalSearchParams` from `expo-router`.
- Docs: https://docs.expo.dev/router/introduction.md

## Building with EAS

Use EAS to build, sign, and submit the app in the cloud (`eas build`, `eas submit`) and to ship over-the-air updates (`eas update`) — no local Xcode or Android Studio required. Run EAS CLI as `bunx eas-cli <command>` in Bun projects, or `npx eas-cli@latest <command>` otherwise; substitute that for bare `eas` in docs examples.
Docs: https://docs.expo.dev/eas/index.md

## Rules

- If `ios/` and `android/` directories do not exist, they are generated (Continuous Native Generation). Never create or edit them by hand — configure native behavior in `app.json` and config plugins.
- Expo Go only includes its bundled native modules. After adding a library with native code, the app needs a development build: `npx expo run:ios|android` locally, or `eas build --profile development`.
- Prefer recommended Expo modules over third-party libraries, and check your available skills before adding dependencies. Docs: https://docs.expo.dev/versions/latest/index.md


================================================
📄 ARCHIVO: app.json
================================================

{
  "expo": {
    "name": "Login_Firebase",
    "slug": "Login_Firebase",
    "version": "1.0.0",
    "orientation": "portrait",
    "icon": "./assets/images/icon.png",
    "scheme": "loginfirebase",
    "userInterfaceStyle": "automatic",
    "ios": {
      "icon": "./assets/expo.icon"
    },
    "android": {
      "adaptiveIcon": {
        "backgroundColor": "#E6F4FE",
        "foregroundImage": "./assets/images/android-icon-foreground.png",
        "backgroundImage": "./assets/images/android-icon-background.png",
        "monochromeImage": "./assets/images/android-icon-monochrome.png"
      },
      "predictiveBackGestureEnabled": false
    },
    "web": {
      "output": "static",
      "favicon": "./assets/images/favicon.png"
    },
    "plugins": [
      "expo-router",
      [
        "expo-splash-screen",
        {
          "backgroundColor": "#208AEF",
          "image": "./assets/images/splash-icon.png",
          "imageWidth": 76
        }
      ]
    ],
    "experiments": {
      "typedRoutes": true,
      "reactCompiler": true
    }
  }
}


================================================
📄 ARCHIVO: example\scripts\reset-project.js
================================================

#!/usr/bin/env node

/**
 * This script is used to reset the project to a blank state.
 * It deletes or moves the /src and /scripts directories to /example based on user input and creates a new /src/app directory with an index.tsx and _layout.tsx file.
 * You can remove the `reset-project` script from package.json and safely delete this file after running it.
 */

const fs = require("fs");
const path = require("path");
const readline = require("readline");

const root = process.cwd();
const oldDirs = ["src", "scripts"];
const exampleDir = "example";
const newAppDir = "src/app";
const exampleDirPath = path.join(root, exampleDir);

const indexContent = `import { Text, View, StyleSheet } from "react-native";

export default function Index() {
  return (
    <View style={styles.container}>
      <Text>Edit src/app/index.tsx to edit this screen.</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: "center",
    justifyContent: "center",
  },
});
`;

const layoutContent = `import { Stack } from "expo-router";

export default function RootLayout() {
  return <Stack />;
}
`;

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

const moveDirectories = async (userInput) => {
  try {
    if (userInput === "y") {
      // Create the app-example directory
      await fs.promises.mkdir(exampleDirPath, { recursive: true });
      console.log(`📁 /${exampleDir} directory created.`);
    }

    // Move old directories to new app-example directory or delete them
    for (const dir of oldDirs) {
      const oldDirPath = path.join(root, dir);
      if (fs.existsSync(oldDirPath)) {
        if (userInput === "y") {
          const newDirPath = path.join(root, exampleDir, dir);
          await fs.promises.rename(oldDirPath, newDirPath);
          console.log(`➡️ /${dir} moved to /${exampleDir}/${dir}.`);
        } else {
          await fs.promises.rm(oldDirPath, { recursive: true, force: true });
          console.log(`❌ /${dir} deleted.`);
        }
      } else {
        console.log(`➡️ /${dir} does not exist, skipping.`);
      }
    }

    // Create new /src/app directory
    const newAppDirPath = path.join(root, newAppDir);
    await fs.promises.mkdir(newAppDirPath, { recursive: true });
    console.log("\n📁 New /src/app directory created.");

    // Create index.tsx
    const indexPath = path.join(newAppDirPath, "index.tsx");
    await fs.promises.writeFile(indexPath, indexContent);
    console.log("📄 src/app/index.tsx created.");

    // Create _layout.tsx
    const layoutPath = path.join(newAppDirPath, "_layout.tsx");
    await fs.promises.writeFile(layoutPath, layoutContent);
    console.log("📄 src/app/_layout.tsx created.");

    console.log("\n✅ Project reset complete. Next steps:");
    console.log(
      `1. Run \`npx expo start\` to start a development server.\n2. Edit src/app/index.tsx to edit the main screen.\n3. Put all your application code in /src, only screens and layout files should be in /src/app.${
        userInput === "y"
          ? `\n4. Delete the /${exampleDir} directory when you're done referencing it.`
          : ""
      }`
    );
  } catch (error) {
    console.error(`❌ Error during script execution: ${error.message}`);
  }
};

rl.question(
  "Do you want to move existing files to /example instead of deleting them? (Y/n): ",
  (answer) => {
    const userInput = answer.trim().toLowerCase() || "y";
    if (userInput === "y" || userInput === "n") {
      moveDirectories(userInput).finally(() => rl.close());
    } else {
      console.log("❌ Invalid input. Please enter 'Y' or 'N'.");
      rl.close();
    }
  }
);


================================================
📄 ARCHIVO: example\src\app\explore.tsx
================================================

import { Image } from 'expo-image';
import { SymbolView } from 'expo-symbols';
import { Platform, Pressable, ScrollView, StyleSheet } from 'react-native';
import { useSafeAreaInsets } from 'react-native-safe-area-context';

import { ExternalLink } from '@/components/external-link';
import { ThemedText } from '@/components/themed-text';
import { ThemedView } from '@/components/themed-view';
import { Collapsible } from '@/components/ui/collapsible';
import { WebBadge } from '@/components/web-badge';
import { BottomTabInset, MaxContentWidth, Spacing } from '@/constants/theme';
import { useTheme } from '@/hooks/use-theme';

export default function TabTwoScreen() {
  const safeAreaInsets = useSafeAreaInsets();
  const insets = {
    ...safeAreaInsets,
    bottom: safeAreaInsets.bottom + BottomTabInset + Spacing.three,
  };
  const theme = useTheme();

  const contentPlatformStyle = Platform.select({
    android: {
      paddingTop: insets.top,
      paddingLeft: insets.left,
      paddingRight: insets.right,
      paddingBottom: insets.bottom,
    },
    web: {
      paddingTop: Spacing.six,
      paddingBottom: Spacing.four,
    },
  });

  return (
    <ScrollView
      style={[styles.scrollView, { backgroundColor: theme.background }]}
      contentInset={insets}
      contentContainerStyle={[styles.contentContainer, contentPlatformStyle]}>
      <ThemedView style={styles.container}>
        <ThemedView style={styles.titleContainer}>
          <ThemedText type="subtitle">Explore</ThemedText>
          <ThemedText style={styles.centerText} themeColor="textSecondary">
            This starter app includes example{'\n'}code to help you get started.
          </ThemedText>

          <ExternalLink href="https://docs.expo.dev" asChild>
            <Pressable style={({ pressed }) => pressed && styles.pressed}>
              <ThemedView type="backgroundElement" style={styles.linkButton}>
                <ThemedText type="link">Expo documentation</ThemedText>
                <SymbolView
                  tintColor={theme.text}
                  name={{ ios: 'arrow.up.right.square', android: 'link', web: 'link' }}
                  size={12}
                />
              </ThemedView>
            </Pressable>
          </ExternalLink>
        </ThemedView>

        <ThemedView style={styles.sectionsWrapper}>
          <Collapsible title="File-based routing">
            <ThemedText type="small">
              This app has two screens: <ThemedText type="code">src/app/index.tsx</ThemedText> and{' '}
              <ThemedText type="code">src/app/explore.tsx</ThemedText>
            </ThemedText>
            <ThemedText type="small">
              The layout file in <ThemedText type="code">src/app/_layout.tsx</ThemedText> sets up
              the tab navigator.
            </ThemedText>
            <ExternalLink href="https://docs.expo.dev/router/introduction">
              <ThemedText type="linkPrimary">Learn more</ThemedText>
            </ExternalLink>
          </Collapsible>

          <Collapsible title="Android, iOS, and web support">
            <ThemedView type="backgroundElement" style={styles.collapsibleContent}>
              <ThemedText type="small">
                You can open this project on Android, iOS, and the web. To open the web version,
                press <ThemedText type="smallBold">w</ThemedText> in the terminal running this
                project.
              </ThemedText>
              <Image
                source={require('@/assets/images/tutorial-web.png')}
                style={styles.imageTutorial}
              />
            </ThemedView>
          </Collapsible>

          <Collapsible title="Images">
            <ThemedText type="small">
              For static images, you can use the <ThemedText type="code">@2x</ThemedText> and{' '}
              <ThemedText type="code">@3x</ThemedText> suffixes to provide files for different
              screen densities.
            </ThemedText>
            <Image source={require('@/assets/images/react-logo.png')} style={styles.imageReact} />
            <ExternalLink href="https://reactnative.dev/docs/images">
              <ThemedText type="linkPrimary">Learn more</ThemedText>
            </ExternalLink>
          </Collapsible>

          <Collapsible title="Light and dark mode components">
            <ThemedText type="small">
              This template has light and dark mode support. The{' '}
              <ThemedText type="code">useColorScheme()</ThemedText> hook lets you inspect what the
              user&apos;s current color scheme is, and so you can adjust UI colors accordingly.
            </ThemedText>
            <ExternalLink href="https://docs.expo.dev/develop/user-interface/color-themes/">
              <ThemedText type="linkPrimary">Learn more</ThemedText>
            </ExternalLink>
          </Collapsible>

          <Collapsible title="Animations">
            <ThemedText type="small">
              This template includes an example of an animated component. The{' '}
              <ThemedText type="code">src/components/ui/collapsible.tsx</ThemedText> component uses
              the powerful <ThemedText type="code">react-native-reanimated</ThemedText> library to
              animate opening this hint.
            </ThemedText>
          </Collapsible>
        </ThemedView>
        {Platform.OS === 'web' && <WebBadge />}
      </ThemedView>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  scrollView: {
    flex: 1,
  },
  contentContainer: {
    flexDirection: 'row',
    justifyContent: 'center',
  },
  container: {
    maxWidth: MaxContentWidth,
    flexGrow: 1,
  },
  titleContainer: {
    gap: Spacing.three,
    alignItems: 'center',
    paddingHorizontal: Spacing.four,
    paddingVertical: Spacing.six,
  },
  centerText: {
    textAlign: 'center',
  },
  pressed: {
    opacity: 0.7,
  },
  linkButton: {
    flexDirection: 'row',
    paddingHorizontal: Spacing.four,
    paddingVertical: Spacing.two,
    borderRadius: Spacing.five,
    justifyContent: 'center',
    gap: Spacing.one,
    alignItems: 'center',
  },
  sectionsWrapper: {
    gap: Spacing.five,
    paddingHorizontal: Spacing.four,
    paddingTop: Spacing.three,
  },
  collapsibleContent: {
    alignItems: 'center',
  },
  imageTutorial: {
    width: '100%',
    aspectRatio: 296 / 171,
    borderRadius: Spacing.three,
    marginTop: Spacing.two,
  },
  imageReact: {
    width: 100,
    height: 100,
    alignSelf: 'center',
  },
});


================================================
📄 ARCHIVO: example\src\app\index.tsx
================================================

import * as Device from 'expo-device';
import { Platform, StyleSheet } from 'react-native';
import { SafeAreaView } from 'react-native-safe-area-context';

import { AnimatedIcon } from '@/components/animated-icon';
import { HintRow } from '@/components/hint-row';
import { ThemedText } from '@/components/themed-text';
import { ThemedView } from '@/components/themed-view';
import { WebBadge } from '@/components/web-badge';
import { BottomTabInset, MaxContentWidth, Spacing } from '@/constants/theme';

function getDevMenuHint() {
  if (Platform.OS === 'web') {
    return <ThemedText type="small">use browser devtools</ThemedText>;
  }
  if (Device.isDevice) {
    return (
      <ThemedText type="small">
        shake device or press <ThemedText type="code">m</ThemedText> in terminal
      </ThemedText>
    );
  }
  const shortcut = Platform.OS === 'android' ? 'cmd+m (or ctrl+m)' : 'cmd+d';
  return (
    <ThemedText type="small">
      press <ThemedText type="code">{shortcut}</ThemedText>
    </ThemedText>
  );
}

export default function HomeScreen() {
  return (
    <ThemedView style={styles.container}>
      <SafeAreaView style={styles.safeArea}>
        <ThemedView style={styles.heroSection}>
          <AnimatedIcon />
          <ThemedText type="title" style={styles.title}>
            Welcome to&nbsp;Expo
          </ThemedText>
        </ThemedView>

        <ThemedText type="code" style={styles.code}>
          get started
        </ThemedText>

        <ThemedView type="backgroundElement" style={styles.stepContainer}>
          <HintRow
            title="Try editing"
            hint={<ThemedText type="code">src/app/index.tsx</ThemedText>}
          />
          <HintRow title="Dev tools" hint={getDevMenuHint()} />
          <HintRow
            title="Fresh start"
            hint={<ThemedText type="code">npm run reset-project</ThemedText>}
          />
        </ThemedView>

        {Platform.OS === 'web' && <WebBadge />}
      </SafeAreaView>
    </ThemedView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    flexDirection: 'row',
  },
  safeArea: {
    flex: 1,
    paddingHorizontal: Spacing.four,
    alignItems: 'center',
    gap: Spacing.three,
    paddingBottom: BottomTabInset + Spacing.three,
    maxWidth: MaxContentWidth,
  },
  heroSection: {
    alignItems: 'center',
    justifyContent: 'center',
    flex: 1,
    paddingHorizontal: Spacing.four,
    gap: Spacing.four,
  },
  title: {
    textAlign: 'center',
  },
  code: {
    textTransform: 'uppercase',
  },
  stepContainer: {
    gap: Spacing.three,
    alignSelf: 'stretch',
    paddingHorizontal: Spacing.three,
    paddingVertical: Spacing.four,
    borderRadius: Spacing.four,
  },
});


================================================
📄 ARCHIVO: example\src\app\_layout.tsx
================================================

import { DarkTheme, DefaultTheme, ThemeProvider } from 'expo-router';
import * as SplashScreen from 'expo-splash-screen';
import { useColorScheme } from 'react-native';

import { AnimatedSplashOverlay } from '@/components/animated-icon';
import AppTabs from '@/components/app-tabs';

SplashScreen.preventAutoHideAsync();

export default function TabLayout() {
  const colorScheme = useColorScheme();
  return (
    <ThemeProvider value={colorScheme === 'dark' ? DarkTheme : DefaultTheme}>
      <AnimatedSplashOverlay />
      <AppTabs />
    </ThemeProvider>
  );
}


================================================
📄 ARCHIVO: example\src\components\animated-icon.tsx
================================================

import { Image } from 'expo-image';
import * as SplashScreen from 'expo-splash-screen';
import { useState } from 'react';
import { Dimensions, StyleSheet, View } from 'react-native';
import Animated, { Easing, Keyframe } from 'react-native-reanimated';
import { scheduleOnRN } from 'react-native-worklets';

const INITIAL_SCALE_FACTOR = Dimensions.get('screen').height / 90;
const DURATION = 600;

export function AnimatedSplashOverlay() {
  const [animate, setAnimate] = useState(false);
  const [visible, setVisible] = useState(true);

  if (!visible) return null;

  const splashKeyframe = new Keyframe({
    0: {
      transform: [{ scale: 1 }],
      opacity: 1,
    },
    20: {
      opacity: 1,
    },
    70: {
      opacity: 0,
      easing: Easing.elastic(0.7),
    },
    100: {
      opacity: 0,
      transform: [{ scale: 1 }],
      easing: Easing.elastic(0.7),
    },
  });

  const image = <Image style={styles.image} source={require('@/assets/images/expo-logo.png')} />;

  return animate ? (
    <Animated.View
      entering={splashKeyframe.duration(DURATION).withCallback((finished) => {
        'worklet';
        if (finished) {
          scheduleOnRN(setVisible, false);
        }
      })}
      style={styles.splashOverlay}>
      {image}
    </Animated.View>
  ) : (
    <View
      onLayout={() => {
        SplashScreen.hideAsync().finally(() => {
          setAnimate(true);
        });
      }}
      style={styles.splashOverlay}>
      {image}
    </View>
  );
}

const keyframe = new Keyframe({
  0: {
    transform: [{ scale: INITIAL_SCALE_FACTOR }],
  },
  100: {
    transform: [{ scale: 1 }],
    easing: Easing.elastic(0.7),
  },
});

const logoKeyframe = new Keyframe({
  0: {
    transform: [{ scale: 1.3 }],
    opacity: 0,
  },
  40: {
    transform: [{ scale: 1.3 }],
    opacity: 0,
    easing: Easing.elastic(0.7),
  },
  100: {
    opacity: 1,
    transform: [{ scale: 1 }],
    easing: Easing.elastic(0.7),
  },
});

const glowKeyframe = new Keyframe({
  0: {
    transform: [{ rotateZ: '0deg' }],
  },
  100: {
    transform: [{ rotateZ: '7200deg' }],
  },
});

export function AnimatedIcon() {
  return (
    <View style={styles.iconContainer}>
      <Animated.View entering={glowKeyframe.duration(60 * 1000 * 4)} style={styles.glow}>
        <Image style={styles.glow} source={require('@/assets/images/logo-glow.png')} />
      </Animated.View>

      <Animated.View entering={keyframe.duration(DURATION)} style={styles.background} />
      <Animated.View style={styles.imageContainer} entering={logoKeyframe.duration(DURATION)}>
        <Image style={styles.image} source={require('@/assets/images/expo-logo.png')} />
      </Animated.View>
    </View>
  );
}

const styles = StyleSheet.create({
  imageContainer: {
    justifyContent: 'center',
    alignItems: 'center',
  },
  glow: {
    width: 201,
    height: 201,
    position: 'absolute',
  },
  iconContainer: {
    justifyContent: 'center',
    alignItems: 'center',
    width: 128,
    height: 128,
    zIndex: 100,
  },
  image: {
    width: 76,
    height: 71,
  },
  background: {
    borderRadius: 40,
    experimental_backgroundImage: `linear-gradient(180deg, #3C9FFE, #0274DF)`,
    width: 128,
    height: 128,
    position: 'absolute',
  },
  splashOverlay: {
    ...StyleSheet.absoluteFill,
    backgroundColor: '#208AEF',
    alignItems: 'center',
    justifyContent: 'center',
    zIndex: 1000,
  },
});


================================================
📄 ARCHIVO: example\src\components\animated-icon.web.tsx
================================================

import { Image } from 'expo-image';
import { StyleSheet, View } from 'react-native';
import Animated, { Keyframe, Easing } from 'react-native-reanimated';

import classes from './animated-icon.module.css';
const DURATION = 300;

export function AnimatedSplashOverlay() {
  return null;
}

const keyframe = new Keyframe({
  0: {
    transform: [{ scale: 0 }],
  },
  60: {
    transform: [{ scale: 1.2 }],
    easing: Easing.elastic(1.2),
  },
  100: {
    transform: [{ scale: 1 }],
    easing: Easing.elastic(1.2),
  },
});

const logoKeyframe = new Keyframe({
  0: {
    opacity: 0,
  },
  60: {
    transform: [{ scale: 1.2 }],
    opacity: 0,
    easing: Easing.elastic(1.2),
  },
  100: {
    transform: [{ scale: 1 }],
    opacity: 1,
    easing: Easing.elastic(1.2),
  },
});

const glowKeyframe = new Keyframe({
  0: {
    transform: [{ rotateZ: '-180deg' }, { scale: 0.8 }],
    opacity: 0,
  },
  [DURATION / 1000]: {
    transform: [{ rotateZ: '0deg' }, { scale: 1 }],
    opacity: 1,
    easing: Easing.elastic(0.7),
  },
  100: {
    transform: [{ rotateZ: '7200deg' }],
  },
});

export function AnimatedIcon() {
  return (
    <View style={styles.iconContainer}>
      <Animated.View entering={glowKeyframe.duration(60 * 1000 * 4)} style={styles.glow}>
        <Image style={styles.glow} source={require('@/assets/images/logo-glow.png')} />
      </Animated.View>

      <Animated.View style={styles.background} entering={keyframe.duration(DURATION)}>
        <div className={classes.expoLogoBackground} />
      </Animated.View>

      <Animated.View style={styles.imageContainer} entering={logoKeyframe.duration(DURATION)}>
        <Image style={styles.image} source={require('@/assets/images/expo-logo.png')} />
      </Animated.View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    alignItems: 'center',
    width: '100%',
    zIndex: 1000,
    position: 'absolute',
    top: 128 / 2 + 138,
  },
  imageContainer: {
    justifyContent: 'center',
    alignItems: 'center',
  },
  glow: {
    width: 201,
    height: 201,
    position: 'absolute',
  },
  iconContainer: {
    justifyContent: 'center',
    alignItems: 'center',
    width: 128,
    height: 128,
  },
  image: {
    position: 'absolute',
    width: 76,
    height: 71,
  },
  background: {
    width: 128,
    height: 128,
    position: 'absolute',
  },
});


================================================
📄 ARCHIVO: example\src\components\app-tabs.tsx
================================================

import { NativeTabs } from 'expo-router/unstable-native-tabs';
import { useColorScheme } from 'react-native';

import { Colors } from '@/constants/theme';

export default function AppTabs() {
  const scheme = useColorScheme();
  const colors = Colors[scheme === 'unspecified' ? 'light' : scheme];

  return (
    <NativeTabs
      backgroundColor={colors.background}
      indicatorColor={colors.backgroundElement}
      labelStyle={{ selected: { color: colors.text } }}>
      <NativeTabs.Trigger name="index">
        <NativeTabs.Trigger.Label>Home</NativeTabs.Trigger.Label>
        <NativeTabs.Trigger.Icon
          src={require('@/assets/images/tabIcons/home.png')}
          renderingMode="template"
        />
      </NativeTabs.Trigger>

      <NativeTabs.Trigger name="explore">
        <NativeTabs.Trigger.Label>Explore</NativeTabs.Trigger.Label>
        <NativeTabs.Trigger.Icon
          src={require('@/assets/images/tabIcons/explore.png')}
          renderingMode="template"
        />
      </NativeTabs.Trigger>
    </NativeTabs>
  );
}


================================================
📄 ARCHIVO: example\src\components\app-tabs.web.tsx
================================================

import {
  Tabs,
  TabList,
  TabTrigger,
  TabSlot,
  TabTriggerSlotProps,
  TabListProps,
} from 'expo-router/ui';
import { SymbolView } from 'expo-symbols';
import { Pressable, useColorScheme, View, StyleSheet } from 'react-native';

import { ExternalLink } from './external-link';
import { ThemedText } from './themed-text';
import { ThemedView } from './themed-view';

import { Colors, MaxContentWidth, Spacing } from '@/constants/theme';

export default function AppTabs() {
  return (
    <Tabs>
      <TabSlot style={{ height: '100%' }} />
      <TabList asChild>
        <CustomTabList>
          <TabTrigger name="home" href="/" asChild>
            <TabButton>Home</TabButton>
          </TabTrigger>
          <TabTrigger name="explore" href="/explore" asChild>
            <TabButton>Explore</TabButton>
          </TabTrigger>
        </CustomTabList>
      </TabList>
    </Tabs>
  );
}

export function TabButton({ children, isFocused, ...props }: TabTriggerSlotProps) {
  return (
    <Pressable {...props} style={({ pressed }) => pressed && styles.pressed}>
      <ThemedView
        type={isFocused ? 'backgroundSelected' : 'backgroundElement'}
        style={styles.tabButtonView}>
        <ThemedText type="small" themeColor={isFocused ? 'text' : 'textSecondary'}>
          {children}
        </ThemedText>
      </ThemedView>
    </Pressable>
  );
}

export function CustomTabList(props: TabListProps) {
  const scheme = useColorScheme();
  const colors = Colors[scheme === 'unspecified' ? 'light' : scheme];

  return (
    <View {...props} style={styles.tabListContainer}>
      <ThemedView type="backgroundElement" style={styles.innerContainer}>
        <ThemedText type="smallBold" style={styles.brandText}>
          Expo Starter
        </ThemedText>

        {props.children}

        <ExternalLink href="https://docs.expo.dev" asChild>
          <Pressable style={styles.externalPressable}>
            <ThemedText type="link">Docs</ThemedText>
            <SymbolView
              tintColor={colors.text}
              name={{ ios: 'arrow.up.right.square', web: 'link' }}
              size={12}
            />
          </Pressable>
        </ExternalLink>
      </ThemedView>
    </View>
  );
}

const styles = StyleSheet.create({
  tabListContainer: {
    position: 'absolute',
    width: '100%',
    padding: Spacing.three,
    justifyContent: 'center',
    alignItems: 'center',
    flexDirection: 'row',
  },
  innerContainer: {
    paddingVertical: Spacing.two,
    paddingHorizontal: Spacing.five,
    borderRadius: Spacing.five,
    flexDirection: 'row',
    alignItems: 'center',
    flexGrow: 1,
    gap: Spacing.two,
    maxWidth: MaxContentWidth,
  },
  brandText: {
    marginRight: 'auto',
  },
  pressed: {
    opacity: 0.7,
  },
  tabButtonView: {
    paddingVertical: Spacing.one,
    paddingHorizontal: Spacing.three,
    borderRadius: Spacing.three,
  },
  externalPressable: {
    flexDirection: 'row',
    justifyContent: 'center',
    alignItems: 'center',
    gap: Spacing.one,
    marginLeft: Spacing.three,
  },
});


================================================
📄 ARCHIVO: example\src\components\external-link.tsx
================================================

import { Href, Link } from 'expo-router';
import { openBrowserAsync, WebBrowserPresentationStyle } from 'expo-web-browser';
import { type ComponentProps } from 'react';

type Props = Omit<ComponentProps<typeof Link>, 'href'> & { href: Href & string };

export function ExternalLink({ href, ...rest }: Props) {
  return (
    <Link
      target="_blank"
      {...rest}
      href={href}
      onPress={async (event) => {
        if (process.env.EXPO_OS !== 'web') {
          // Prevent the default behavior of linking to the default browser on native.
          event.preventDefault();
          // Open the link in an in-app browser.
          await openBrowserAsync(href, {
            presentationStyle: WebBrowserPresentationStyle.AUTOMATIC,
          });
        }
      }}
    />
  );
}


================================================
📄 ARCHIVO: example\src\components\hint-row.tsx
================================================

import type { ReactNode } from 'react';
import { View, StyleSheet } from 'react-native';

import { ThemedText } from './themed-text';
import { ThemedView } from './themed-view';

import { Spacing } from '@/constants/theme';

type HintRowProps = {
  title?: string;
  hint?: ReactNode;
};

export function HintRow({ title = 'Try editing', hint = 'app/index.tsx' }: HintRowProps) {
  return (
    <View style={styles.stepRow}>
      <ThemedText type="small">{title}</ThemedText>
      <ThemedView type="backgroundSelected" style={styles.codeSnippet}>
        <ThemedText themeColor="textSecondary">{hint}</ThemedText>
      </ThemedView>
    </View>
  );
}

const styles = StyleSheet.create({
  stepRow: {
    flexDirection: 'row',
    justifyContent: 'space-between',
  },
  codeSnippet: {
    borderRadius: Spacing.two,
    paddingVertical: Spacing.half,
    paddingHorizontal: Spacing.two,
  },
});


================================================
📄 ARCHIVO: example\src\components\themed-text.tsx
================================================

import { Platform, StyleSheet, Text, type TextProps } from 'react-native';

import { Fonts, ThemeColor } from '@/constants/theme';
import { useTheme } from '@/hooks/use-theme';

export type ThemedTextProps = TextProps & {
  type?: 'default' | 'title' | 'small' | 'smallBold' | 'subtitle' | 'link' | 'linkPrimary' | 'code';
  themeColor?: ThemeColor;
};

export function ThemedText({ style, type = 'default', themeColor, ...rest }: ThemedTextProps) {
  const theme = useTheme();

  return (
    <Text
      style={[
        { color: theme[themeColor ?? 'text'] },
        type === 'default' && styles.default,
        type === 'title' && styles.title,
        type === 'small' && styles.small,
        type === 'smallBold' && styles.smallBold,
        type === 'subtitle' && styles.subtitle,
        type === 'link' && styles.link,
        type === 'linkPrimary' && styles.linkPrimary,
        type === 'code' && styles.code,
        style,
      ]}
      {...rest}
    />
  );
}

const styles = StyleSheet.create({
  small: {
    fontSize: 14,
    lineHeight: 20,
    fontWeight: 500,
  },
  smallBold: {
    fontSize: 14,
    lineHeight: 20,
    fontWeight: 700,
  },
  default: {
    fontSize: 16,
    lineHeight: 24,
    fontWeight: 500,
  },
  title: {
    fontSize: 48,
    fontWeight: 600,
    lineHeight: 52,
  },
  subtitle: {
    fontSize: 32,
    lineHeight: 44,
    fontWeight: 600,
  },
  link: {
    lineHeight: 30,
    fontSize: 14,
  },
  linkPrimary: {
    lineHeight: 30,
    fontSize: 14,
    color: '#3c87f7',
  },
  code: {
    fontFamily: Fonts.mono,
    fontWeight: Platform.select({ android: 700 }) ?? 500,
    fontSize: 12,
  },
});


================================================
📄 ARCHIVO: example\src\components\themed-view.tsx
================================================

import { View, type ViewProps } from 'react-native';

import { ThemeColor } from '@/constants/theme';
import { useTheme } from '@/hooks/use-theme';

export type ThemedViewProps = ViewProps & {
  lightColor?: string;
  darkColor?: string;
  type?: ThemeColor;
};

export function ThemedView({ style, lightColor, darkColor, type, ...otherProps }: ThemedViewProps) {
  const theme = useTheme();

  return <View style={[{ backgroundColor: theme[type ?? 'background'] }, style]} {...otherProps} />;
}


================================================
📄 ARCHIVO: example\src\components\ui\collapsible.tsx
================================================

import { SymbolView } from 'expo-symbols';
import { PropsWithChildren, useState } from 'react';
import { Pressable, StyleSheet } from 'react-native';
import Animated, { FadeIn } from 'react-native-reanimated';

import { ThemedText } from '@/components/themed-text';
import { ThemedView } from '@/components/themed-view';
import { Spacing } from '@/constants/theme';
import { useTheme } from '@/hooks/use-theme';

export function Collapsible({ children, title }: PropsWithChildren & { title: string }) {
  const [isOpen, setIsOpen] = useState(false);
  const theme = useTheme();

  return (
    <ThemedView>
      <Pressable
        style={({ pressed }) => [styles.heading, pressed && styles.pressedHeading]}
        onPress={() => setIsOpen((value) => !value)}>
        <ThemedView type="backgroundElement" style={styles.button}>
          <SymbolView
            name={{ ios: 'chevron.right', android: 'chevron_right', web: 'chevron_right' }}
            size={14}
            weight="bold"
            tintColor={theme.text}
            style={{ transform: [{ rotate: isOpen ? '-90deg' : '90deg' }] }}
          />
        </ThemedView>

        <ThemedText type="small">{title}</ThemedText>
      </Pressable>
      {isOpen && (
        <Animated.View entering={FadeIn.duration(200)}>
          <ThemedView type="backgroundElement" style={styles.content}>
            {children}
          </ThemedView>
        </Animated.View>
      )}
    </ThemedView>
  );
}

const styles = StyleSheet.create({
  heading: {
    flexDirection: 'row',
    alignItems: 'center',
    gap: Spacing.two,
  },
  pressedHeading: {
    opacity: 0.7,
  },
  button: {
    width: Spacing.four,
    height: Spacing.four,
    borderRadius: 12,
    justifyContent: 'center',
    alignItems: 'center',
  },
  content: {
    marginTop: Spacing.three,
    borderRadius: Spacing.three,
    marginLeft: Spacing.four,
    padding: Spacing.four,
  },
});


================================================
📄 ARCHIVO: example\src\components\web-badge.tsx
================================================

import { version } from 'expo/package.json';
import { Image } from 'expo-image';
import { useColorScheme, StyleSheet } from 'react-native';

import { ThemedText } from './themed-text';
import { ThemedView } from './themed-view';

import { Spacing } from '@/constants/theme';

export function WebBadge() {
  const scheme = useColorScheme();

  return (
    <ThemedView style={styles.container}>
      <ThemedText type="code" themeColor="textSecondary" style={styles.versionText}>
        v{version}
      </ThemedText>
      <Image
        source={
          scheme === 'dark'
            ? require('@/assets/images/expo-badge-white.png')
            : require('@/assets/images/expo-badge.png')
        }
        style={styles.badgeImage}
      />
    </ThemedView>
  );
}

const styles = StyleSheet.create({
  container: {
    padding: Spacing.five,
    alignItems: 'center',
    gap: Spacing.two,
  },
  versionText: {
    textAlign: 'center',
  },
  badgeImage: {
    width: 123,
    aspectRatio: 123 / 24,
  },
});


================================================
📄 ARCHIVO: example\src\constants\theme.ts
================================================

/**
 * Below are the colors that are used in the app. The colors are defined in the light and dark mode.
 * There are many other ways to style your app. For example, [Nativewind](https://www.nativewind.dev/), [Tamagui](https://tamagui.dev/), [unistyles](https://reactnativeunistyles.vercel.app), etc.
 */

import '@/global.css';

import { Platform } from 'react-native';

export const Colors = {
  light: {
    text: '#000000',
    background: '#ffffff',
    backgroundElement: '#F0F0F3',
    backgroundSelected: '#E0E1E6',
    textSecondary: '#60646C',
  },
  dark: {
    text: '#ffffff',
    background: '#000000',
    backgroundElement: '#212225',
    backgroundSelected: '#2E3135',
    textSecondary: '#B0B4BA',
  },
} as const;

export type ThemeColor = keyof typeof Colors.light & keyof typeof Colors.dark;

export const Fonts = Platform.select({
  ios: {
    /** iOS `UIFontDescriptorSystemDesignDefault` */
    sans: 'system-ui',
    /** iOS `UIFontDescriptorSystemDesignSerif` */
    serif: 'ui-serif',
    /** iOS `UIFontDescriptorSystemDesignRounded` */
    rounded: 'ui-rounded',
    /** iOS `UIFontDescriptorSystemDesignMonospaced` */
    mono: 'ui-monospace',
  },
  default: {
    sans: 'normal',
    serif: 'serif',
    rounded: 'normal',
    mono: 'monospace',
  },
  web: {
    sans: 'var(--font-display)',
    serif: 'var(--font-serif)',
    rounded: 'var(--font-rounded)',
    mono: 'var(--font-mono)',
  },
});

export const Spacing = {
  half: 2,
  one: 4,
  two: 8,
  three: 16,
  four: 24,
  five: 32,
  six: 64,
} as const;

export const BottomTabInset = Platform.select({ ios: 50, android: 80 }) ?? 0;
export const MaxContentWidth = 800;


================================================
📄 ARCHIVO: example\src\hooks\use-color-scheme.ts
================================================

export { useColorScheme } from 'react-native';


================================================
📄 ARCHIVO: example\src\hooks\use-color-scheme.web.ts
================================================

import { useEffect, useState } from 'react';
import { useColorScheme as useRNColorScheme } from 'react-native';

/**
 * To support static rendering, this value needs to be re-calculated on the client side for web
 */
export function useColorScheme() {
  const [hasHydrated, setHasHydrated] = useState(false);

  useEffect(() => {
    setHasHydrated(true);
  }, []);

  const colorScheme = useRNColorScheme();

  if (hasHydrated) {
    return colorScheme;
  }

  return 'light';
}


================================================
📄 ARCHIVO: example\src\hooks\use-theme.ts
================================================

/**
 * Learn more about light and dark modes:
 * https://docs.expo.dev/guides/color-schemes/
 */

import { Colors } from '@/constants/theme';
import { useColorScheme } from '@/hooks/use-color-scheme';

export function useTheme() {
  const scheme = useColorScheme();
  const theme = scheme === 'unspecified' ? 'light' : scheme;

  return Colors[theme];
}


================================================
📄 ARCHIVO: expo-env.d.ts
================================================

/// <reference types="expo/types" />

// NOTE: This file should not be edited and should be in your git ignore

================================================
📄 ARCHIVO: package.json
================================================

{
  "name": "login_firebase",
  "main": "expo-router/entry",
  "version": "1.0.0",
  "dependencies": {
    "@expo-google-fonts/big-shoulders": "^0.4.1",
    "@expo-google-fonts/space-grotesk": "^0.4.1",
    "@expo/ui": "~57.0.26",
    "@react-native-async-storage/async-storage": "2.2.0",
    "expo": "~57.0.31",
    "expo-constants": "~57.0.22",
    "expo-device": "~57.0.2",
    "expo-font": "~57.0.4",
    "expo-glass-effect": "~57.0.4",
    "expo-image": "~57.0.5",
    "expo-linking": "~57.0.13",
    "expo-router": "~57.0.29",
    "expo-splash-screen": "~57.0.10",
    "expo-status-bar": "~57.0.1",
    "expo-symbols": "~57.0.3",
    "expo-system-ui": "~57.0.4",
    "expo-web-browser": "~57.0.3",
    "firebase": "^13.1.0",
    "react": "19.2.3",
    "react-dom": "19.2.3",
    "react-native": "0.86.3",
    "react-native-gesture-handler": "~2.32.0",
    "react-native-reanimated": "4.5.1",
    "react-native-safe-area-context": "~5.7.0",
    "react-native-screens": "~4.26.0",
    "react-native-svg": "15.15.4",
    "react-native-web": "~0.21.0",
    "react-native-worklets": "0.10.1"
  },
  "devDependencies": {
    "@types/react": "~19.2.2",
    "typescript": "~6.0.3"
  },
  "scripts": {
    "start": "expo start",
    "reset-project": "node ./scripts/reset-project.js",
    "android": "expo start --android",
    "ios": "expo start --ios",
    "web": "expo start --web",
    "lint": "expo lint"
  },
  "private": true
}


================================================
📄 ARCHIVO: README.md
================================================

# Welcome to your Expo app 👋

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

## Get started

1. Install dependencies

   ```bash
   npm install
   ```

2. Start the app

   ```bash
   npx expo start
   ```

In the output, you'll find options to open the app in a

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go), a limited sandbox for trying out app development with Expo

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

## Get a fresh project

When you're ready, run:

```bash
npm run reset-project
```

This command will move the starter code to the **app-example** directory and create a blank **app** directory where you can start developing.

### Other setup steps

- To set up ESLint for linting, run `npx expo lint`, or follow our guide on ["Using ESLint and Prettier"](https://docs.expo.dev/guides/using-eslint/)
- If you'd like to set up unit testing, follow our guide on ["Unit Testing with Jest"](https://docs.expo.dev/develop/unit-testing/)
- Learn more about the TypeScript setup in this template in our guide on ["Using TypeScript"](https://docs.expo.dev/guides/typescript/)

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.


================================================
📄 ARCHIVO: src\app\(app)\cambiar-clave.tsx
================================================

/**
 * Cambiar contraseña (solo con sesión iniciada).
 *
 * Pedimos la contraseña actual por dos razones:
 *   1. Firebase exige un inicio de sesión reciente para cambiar la clave
 *      (si no, lanza auth/requires-recent-login). Con la clave actual
 *      reautenticamos al usuario en el momento.
 *   2. Si alguien toma un teléfono desbloqueado, no puede cambiar la clave
 *      sin conocer la actual.
 */
import { router } from 'expo-router';
import { useState } from 'react';
 
import { Aviso } from '@/components/aviso';
import { Boton } from '@/components/boton';
import { CampoTexto } from '@/components/campo-texto';
import { PantallaHoja } from '@/components/pantalla-hoja';
import { useSesion } from '@/context/sesion';
import { mensajeDeError } from '@/lib/errores-firebase';
import { LONGITUD_MINIMA_CLAVE, validarClave, validarConfirmacion } from '@/lib/validaciones';
 
type Errores = Partial<Record<'actual' | 'nueva' | 'confirmacion', string | null>>;
 
export default function PantallaCambiarClave() {
  const { cambiarClave } = useSesion();
 
  const [actual, setActual] = useState('');
  const [nueva, setNueva] = useState('');
  const [confirmacion, setConfirmacion] = useState('');
  const [errores, setErrores] = useState<Errores>({});
  const [errorGeneral, setErrorGeneral] = useState<string | null>(null);
  const [listo, setListo] = useState(false);
  const [enviando, setEnviando] = useState(false);
 
  async function manejarCambio() {
    const nuevosErrores: Errores = {
      actual: actual ? null : 'Escribe tu contraseña actual.',
      nueva:
        validarClave(nueva) ??
        (nueva === actual ? 'La nueva contraseña debe ser distinta de la actual.' : null),
      confirmacion: validarConfirmacion(nueva, confirmacion),
    };
    setErrores(nuevosErrores);
    setErrorGeneral(null);
    if (Object.values(nuevosErrores).some(Boolean)) return;
 
    setEnviando(true);
    try {
      await cambiarClave(actual, nueva);
      setListo(true);
      // Limpiamos los campos: no conviene dejar contraseñas en memoria visible.
      setActual('');
      setNueva('');
      setConfirmacion('');
    } catch (error) {
      setErrorGeneral(
        // En esta pantalla, "credencial inválida" significa clave actual incorrecta.
        mensajeDeError(error, {
          'auth/invalid-credential': 'La contraseña actual no es correcta.',
          'auth/wrong-password': 'La contraseña actual no es correcta.',
        }),
      );
    } finally {
      setEnviando(false);
    }
  }
 
  return (
    <PantallaHoja
      conVolver
      titulo={'Cambia tu\ncontraseña'}
      bajada={`Confirma la actual y elige una nueva de al menos ${LONGITUD_MINIMA_CLAVE} caracteres.`}>
      {listo ? (
        <Aviso
          tipo="exito"
          mensaje="Contraseña actualizada. La próxima vez que inicies sesión usa la nueva."
        />
      ) : null}
      {errorGeneral ? <Aviso tipo="error" mensaje={errorGeneral} /> : null}
 
      <CampoTexto
        etiqueta="Contraseña actual"
        value={actual}
        onChangeText={setActual}
        error={errores.actual}
        esClave
        textContentType="password"
        autoComplete="current-password"
      />
      <CampoTexto
        etiqueta="Contraseña nueva"
        value={nueva}
        onChangeText={setNueva}
        error={errores.nueva}
        esClave
        textContentType="newPassword"
        autoComplete="new-password"
      />
      <CampoTexto
        etiqueta="Repite la contraseña nueva"
        value={confirmacion}
        onChangeText={setConfirmacion}
        error={errores.confirmacion}
        esClave
        textContentType="newPassword"
        autoComplete="new-password"
        onSubmitEditing={manejarCambio}
      />
 
      {listo ? (
        <Boton texto="Volver a la bienvenida" onPress={() => router.back()} />
      ) : (
        <Boton texto="Guardar contraseña" onPress={manejarCambio} cargando={enviando} />
      )}
    </PantallaHoja>
  );
}


================================================
📄 ARCHIVO: src\app\(app)\index.tsx
================================================

/**
 * Pantalla de bienvenida (solo con sesión iniciada).
 */
import { router } from 'expo-router';
import { useState } from 'react';
import { StyleSheet, Text, View } from 'react-native';
import Animated, { FadeInDown } from 'react-native-reanimated';
 
import { Boton } from '@/components/boton';
import { PantallaHoja } from '@/components/pantalla-hoja';
import { colores, espacio, fuentes, radio } from '@/constants/tema';
import { useSesion } from '@/context/sesion';
 
/** Convierte la fecha que entrega Firebase (texto) a "27 de octubre de 2026". */
function formatearFecha(fecha?: string): string {
  if (!fecha) return 'Sin registro';
  return new Date(fecha).toLocaleDateString('es-EC', {
    day: 'numeric',
    month: 'long',
    year: 'numeric',
  });
}
 
export default function PantallaBienvenida() {
  const { usuario, nombre: nombrePerfil, cerrarSesion } = useSesion();
  const [saliendo, setSaliendo] = useState(false);
 
  // Gracias a Stack.Protected esta pantalla nunca se muestra sin usuario,
  // pero TypeScript no lo sabe; por eso el operador ?.
  // Para el saludo basta el primer nombre; la ficha muestra el nombre completo.
  const nombre =
    nombrePerfil?.split(' ')[0] || usuario?.email?.split('@')[0] || 'estudiante';
 
  async function manejarSalida() {
    setSaliendo(true);
    await cerrarSesion();
    // No navegamos: al quedar usuario = null, Stack.Protected lleva al login.
  }
 
  return (
    <PantallaHoja
      titulo={'Bienvenido\na la APP,\nestudiante\nde la ESFOT'}
      extraEncabezado={
        // La única animación de la app: confirma que el ingreso funcionó.
        // Reanimated respeta la opción "reducir movimiento" del sistema.
        <Animated.Text entering={FadeInDown.duration(1000).delay(150)} style={styles.saludo}>
          Hola, {nombre}.
        </Animated.Text>
      }>
      {/* Ficha con los datos de la cuenta que guarda Firebase. */}
      <View style={styles.ficha}>
        <Fila etiqueta="Nombre" valor={nombrePerfil || 'Sin nombre'} />
        <Fila etiqueta="Correo" valor={usuario?.email ?? ''} />
        <Fila etiqueta="Cuenta creada" valor={formatearFecha(usuario?.metadata.creationTime)} />
        <Fila
          etiqueta="Último ingreso"
          valor={formatearFecha(usuario?.metadata.lastSignInTime)}
          ultima
        />
      </View>
 
      <Boton texto="Cambiar contraseña" onPress={() => router.push('/cambiar-clave')} />
      <Boton variante="secundario" texto="Cerrar sesión" onPress={manejarSalida} cargando={saliendo} />
    </PantallaHoja>
  );
}
 
/** Una fila etiqueta-valor de la ficha. Componente local: solo se usa aquí. */
function Fila({ etiqueta, valor, ultima = false }: { etiqueta: string; valor: string; ultima?: boolean }) {
  return (
    <View style={[styles.fila, !ultima && styles.filaSeparada]}>
      <Text style={styles.filaEtiqueta}>{etiqueta}</Text>
      <Text style={styles.filaValor} numberOfLines={1} ellipsizeMode="middle">
        {valor}
      </Text>
    </View>
  );
}
 
const styles = StyleSheet.create({
  saludo: {
    color: colores.senal,
    fontFamily: fuentes.textoMedio,
    fontSize: 18,
    marginTop: espacio.m,
  },
  ficha: {
    backgroundColor: colores.hoja,
    borderRadius: radio.control + 4,
    paddingHorizontal: espacio.m,
    borderWidth: 1,
    borderColor: colores.borde,
  },
  fila: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    gap: espacio.m,
    paddingVertical: espacio.m - 2,
  },
  filaSeparada: {
    borderBottomWidth: StyleSheet.hairlineWidth,
    borderBottomColor: colores.borde,
  },
  filaEtiqueta: {
    color: colores.lapiz,
    fontFamily: fuentes.texto,
    fontSize: 14,
  },
  filaValor: {
    flexShrink: 1,
    color: colores.grafito,
    fontFamily: fuentes.textoMedio,
    fontSize: 15,
    textAlign: 'right',
  },
});


================================================
📄 ARCHIVO: src\app\(app)\_layout.tsx
================================================


import { Stack } from "expo-router";
import { colores } from "@/constants/tema";

export default function LayoutApp() {
    return (
        <Stack
            screenOptions={{
                headerShown: false,
                contentStyle: {backgroundColor: colores.tinta}
            }}
        />
    );
}

================================================
📄 ARCHIVO: src\app\login.tsx
================================================

/**
 * Pantalla de inicio de sesión.
 */
import { router } from 'expo-router';
import { useState } from 'react';
import { StyleSheet, Text, View } from 'react-native';
 
import { Aviso } from '@/components/aviso';
import { Boton } from '@/components/boton';
import { CampoTexto } from '@/components/campo-texto';
import { PantallaHoja } from '@/components/pantalla-hoja';
import { colores, espacio, fuentes } from '@/constants/tema';
import { useSesion } from '@/context/sesion';
import { mensajeDeError } from '@/lib/errores-firebase';
import { validarCorreo } from '@/lib/validaciones';
 
export default function PantallaLogin() {
  const { iniciarSesion } = useSesion();
 
  // Estado del formulario: un useState por campo es lo más claro para empezar.
  const [correo, setCorreo] = useState('');
  const [clave, setClave] = useState('');
  const [errores, setErrores] = useState<{ correo?: string | null; clave?: string | null }>({});
  const [errorGeneral, setErrorGeneral] = useState<string | null>(null);
  const [enviando, setEnviando] = useState(false);
 
  async function manejarIngreso() {
    // 1. Validamos en el teléfono antes de llamar a Firebase.
    const nuevosErrores = {
      correo: validarCorreo(correo),
      clave: clave ? null : 'Escribe tu contraseña.',
    };
    setErrores(nuevosErrores);
    setErrorGeneral(null);
    if (nuevosErrores.correo || nuevosErrores.clave) return;
 
    // 2. Llamamos a Firebase. Si funciona, el layout raíz cambia de pantalla solo.
    setEnviando(true);
    try {
      await iniciarSesion(correo, clave);
    } catch (error) {
      setErrorGeneral(mensajeDeError(error));
      // finally no sirve aquí para todo: si el ingreso funciona, esta pantalla
      // se desmonta y no debemos actualizar su estado.
      setEnviando(false);
    }
  }
 
  return (
    <PantallaHoja
      antetitulo="ESFOT, Escuela Politécnica Nacional"
      titulo={'Inicia\nsesión'}
      bajada="Ingresa con el correo y la contraseña de tu cuenta.">
      {errorGeneral ? <Aviso tipo="error" mensaje={errorGeneral} /> : null}
 
      <CampoTexto
        etiqueta="Correo"
        placeholder="nombre.apellido@epn.edu.ec"
        value={correo}
        onChangeText={setCorreo}
        error={errores.correo}
        keyboardType="email-address"
        textContentType="emailAddress" // permite autocompletar en iOS
        autoComplete="email" // y en Android
        returnKeyType="next"
      />
 
      <CampoTexto
        etiqueta="Contraseña"
        value={clave}
        onChangeText={setClave}
        error={errores.clave}
        esClave
        textContentType="password"
        autoComplete="current-password"
        returnKeyType="go"
        onSubmitEditing={manejarIngreso} // "Enter" en el teclado también envía
      />
 
      <View style={styles.olvido}>
        <Boton
          variante="enlace"
          texto="¿Olvidaste tu contraseña?"
          // Pasamos el correo escrito para no obligar a escribirlo otra vez.
          onPress={() => router.push({ pathname: '/recuperar', params: { correo } })}
        />
      </View>
 
      <Boton texto="Iniciar sesión" onPress={manejarIngreso} cargando={enviando} />
 
      <View style={styles.pie}>
        <Text style={styles.pieTexto}>¿Aún no tienes cuenta?</Text>
        <Boton variante="enlace" texto="Crea una" onPress={() => router.push('/registro')} />
      </View>
    </PantallaHoja>
  );
}
 
const styles = StyleSheet.create({
  olvido: {
    alignItems: 'flex-end',
  },
  pie: {
    flexDirection: 'row',
    justifyContent: 'center',
    alignItems: 'center',
    gap: espacio.s - 2,
    marginTop: espacio.m,
  },
  pieTexto: {
    color: colores.lapiz,
    fontFamily: fuentes.texto,
    fontSize: 15,
  },
});


================================================
📄 ARCHIVO: src\app\recuperar.tsx
================================================

/**
 * Recuperar contraseña.
 *
 * Flujo completo:
 *   1. El estudiante escribe su correo y toca "Enviar enlace".
 *   2. Firebase envía un correo (plantilla editable en la consola:
 *      Authentication > Templates > Password reset).
 *   3. El enlace abre una página de Firebase donde se escribe la contraseña nueva.
 *   4. El estudiante vuelve a la app e inicia sesión con esa contraseña.
 */
import { router, useLocalSearchParams } from 'expo-router';
import { useState } from 'react';
 
import { Aviso } from '@/components/aviso';
import { Boton } from '@/components/boton';
import { CampoTexto } from '@/components/campo-texto';
import { PantallaHoja } from '@/components/pantalla-hoja';
import { useSesion } from '@/context/sesion';
import { mensajeDeError } from '@/lib/errores-firebase';
import { validarCorreo } from '@/lib/validaciones';
 
export default function PantallaRecuperar() {
  const { enviarCorreoRecuperacion } = useSesion();
  // Recibimos el correo que el usuario ya había escrito en el login (si lo hizo).
  const params = useLocalSearchParams<{ correo?: string }>();
 
  const [correo, setCorreo] = useState(params.correo ?? '');
  const [errorCampo, setErrorCampo] = useState<string | null>(null);
  const [errorGeneral, setErrorGeneral] = useState<string | null>(null);
  const [enviado, setEnviado] = useState(false);
  const [enviando, setEnviando] = useState(false);
 
  async function manejarEnvio() {
    const error = validarCorreo(correo);
    setErrorCampo(error);
    setErrorGeneral(null);
    if (error) return;
 
    setEnviando(true);
    try {
      await enviarCorreoRecuperacion(correo);
      setEnviado(true);
    } catch (e) {
      setErrorGeneral(mensajeDeError(e));
    } finally {
      // Aquí sí usamos finally: la pantalla sigue montada en ambos casos.
      setEnviando(false);
    }
  }
 
  return (
    <PantallaHoja
      conVolver
      titulo={'Recupera\ntu acceso'}
      bajada="Te enviaremos un enlace para que crees una contraseña nueva.">
      {/*
        Mensaje neutro a propósito: no confirmamos si el correo existe.
        Decir "ese correo no está registrado" permitiría a un atacante
        averiguar qué correos tienen cuenta (enumeración de usuarios).
      */}
      {enviado ? (
        <Aviso
          tipo="exito"
          mensaje={`Si ${correo.trim()} tiene una cuenta, en unos minutos recibirás el enlace. Revisa también la carpeta de spam.`}
        />
      ) : null}
      {errorGeneral ? <Aviso tipo="error" mensaje={errorGeneral} /> : null}
 
      <CampoTexto
        etiqueta="Correo de tu cuenta"
        placeholder="nombre.apellido@epn.edu.ec"
        value={correo}
        onChangeText={(texto) => {
          setCorreo(texto);
          setEnviado(false); // si cambia el correo, el aviso anterior ya no aplica
        }}
        error={errorCampo}
        keyboardType="email-address"
        textContentType="emailAddress"
        autoComplete="email"
        onSubmitEditing={manejarEnvio}
      />
 
      {enviado ? (
        <>
          <Boton texto="Volver a iniciar sesión" onPress={() => router.back()} />
          <Boton variante="secundario" texto="Enviar otra vez" onPress={manejarEnvio} cargando={enviando} />
        </>
      ) : (
        <Boton texto="Enviar enlace" onPress={manejarEnvio} cargando={enviando} />
      )}
    </PantallaHoja>
  );
}


================================================
📄 ARCHIVO: src\app\registro.tsx
================================================

/**
 * Pantalla de registro de una cuenta nueva.
 *
 * Ojo: este registro es abierto. Cualquier persona con un correo puede crear
 * una cuenta. El texto "estudiante de la ESFOT" de la bienvenida no verifica
 * nada; para restringir de verdad habría que crear las cuentas desde la consola
 * o validar el dominio en el servidor.
 */
import { router } from 'expo-router';
import { useState } from 'react';
import { StyleSheet, Text, View } from 'react-native';
 
import { Aviso } from '@/components/aviso';
import { Boton } from '@/components/boton';
import { CampoTexto } from '@/components/campo-texto';
import { PantallaHoja } from '@/components/pantalla-hoja';
import { colores, espacio, fuentes } from '@/constants/tema';
import { useSesion } from '@/context/sesion';
import { mensajeDeError } from '@/lib/errores-firebase';
import {
  LONGITUD_MINIMA_CLAVE,
  validarClave,
  validarConfirmacion,
  validarCorreo,
  validarNombre,
} from '@/lib/validaciones';
 
type Errores = Partial<Record<'nombre' | 'correo' | 'clave' | 'confirmacion', string | null>>;
 
export default function PantallaRegistro() {
  const { registrarse } = useSesion();
 
  const [nombre, setNombre] = useState('');
  const [correo, setCorreo] = useState('');
  const [clave, setClave] = useState('');
  const [confirmacion, setConfirmacion] = useState('');
  const [errores, setErrores] = useState<Errores>({});
  const [errorGeneral, setErrorGeneral] = useState<string | null>(null);
  const [enviando, setEnviando] = useState(false);
 
  async function manejarRegistro() {
    const nuevosErrores: Errores = {
      nombre: validarNombre(nombre),
      correo: validarCorreo(correo),
      clave: validarClave(clave),
      confirmacion: validarConfirmacion(clave, confirmacion),
    };
    setErrores(nuevosErrores);
    setErrorGeneral(null);
    // Object.values + some: ¿hay al menos un error?
    if (Object.values(nuevosErrores).some(Boolean)) return;
 
    setEnviando(true);
    try {
      await registrarse(nombre, correo, clave);
      // Al crear la cuenta Firebase inicia sesión y el layout muestra la bienvenida.
    } catch (error) {
      setErrorGeneral(mensajeDeError(error));
      setEnviando(false);
    }
  }
 
  return (
    <PantallaHoja
      conVolver
      titulo={'Crea tu\ncuenta'}
      bajada="Con esta cuenta entrarás a la app desde cualquier teléfono.">
      {errorGeneral ? <Aviso tipo="error" mensaje={errorGeneral} /> : null}
 
      <CampoTexto
        etiqueta="Nombre"
        placeholder="Como quieres que te saludemos"
        value={nombre}
        onChangeText={setNombre}
        error={errores.nombre}
        autoCapitalize="words"
        textContentType="name"
        autoComplete="name"
      />
      <CampoTexto
        etiqueta="Correo"
        placeholder="nombre.apellido@epn.edu.ec"
        value={correo}
        onChangeText={setCorreo}
        error={errores.correo}
        keyboardType="email-address"
        textContentType="emailAddress"
        autoComplete="email"
      />
      <CampoTexto
        etiqueta="Contraseña"
        placeholder={`Mínimo ${LONGITUD_MINIMA_CLAVE} caracteres`}
        value={clave}
        onChangeText={setClave}
        error={errores.clave}
        esClave
        // "newPassword" hace que iOS sugiera una contraseña segura.
        textContentType="newPassword"
        autoComplete="new-password"
      />
      <CampoTexto
        etiqueta="Repite la contraseña"
        value={confirmacion}
        onChangeText={setConfirmacion}
        error={errores.confirmacion}
        esClave
        textContentType="newPassword"
        autoComplete="new-password"
        onSubmitEditing={manejarRegistro}
      />
 
      <Boton texto="Crear cuenta" onPress={manejarRegistro} cargando={enviando} />
 
      <View style={styles.pie}>
        <Text style={styles.pieTexto}>¿Ya tienes cuenta?</Text>
        <Boton variante="enlace" texto="Inicia sesión" onPress={() => router.back()} />
      </View>
    </PantallaHoja>
  );
}
 
const styles = StyleSheet.create({
  pie: {
    flexDirection: 'row',
    justifyContent: 'center',
    alignItems: 'center',
    gap: espacio.s - 2,
    marginTop: espacio.m,
  },
  pieTexto: {
    color: colores.lapiz,
    fontFamily: fuentes.texto,
    fontSize: 15,
  },
});


================================================
📄 ARCHIVO: src\app\_layout.tsx
================================================

/**
 * Layout raíz: es lo primero que se ejecuta al abrir la app.
 *
 * Responsabilidades:
 *   1. Cargar las fuentes.
 *   2. Envolver la app en el ProveedorSesion (para que todas las pantallas
 *      conozcan al usuario).
 *   3. Decidir qué pantallas existen según haya o no sesión (Stack.Protected).
 *   4. Mantener visible la pantalla de carga (splash) hasta tener todo listo.
 */
import { BigShoulders_800ExtraBold } from '@expo-google-fonts/big-shoulders';
import {
  SpaceGrotesk_400Regular,
  SpaceGrotesk_500Medium,
  SpaceGrotesk_700Bold,
  useFonts,
} from '@expo-google-fonts/space-grotesk';
import { Stack } from 'expo-router';
import * as SplashScreen from 'expo-splash-screen';
import { useEffect } from 'react';
 
import { colores } from '@/constants/tema';
import { ProveedorSesion, useSesion } from '@/context/sesion';
 
// Se ejecuta al importar el módulo: evita que el splash se oculte solo.
SplashScreen.preventAutoHideAsync();
 
export default function LayoutRaiz() {
  // useFonts de cualquier paquete @expo-google-fonts sirve para cargar fuentes
  // de distintas familias a la vez.
  const [fuentesListas] = useFonts({
    BigShoulders_800ExtraBold,
    SpaceGrotesk_400Regular,
    SpaceGrotesk_500Medium,
    SpaceGrotesk_700Bold,
  });
 
  return (
    <ProveedorSesion>
      <Navegacion fuentesListas={fuentesListas} />
    </ProveedorSesion>
  );
}
 
/**
 * Está separado de LayoutRaiz porque useSesion solo funciona DENTRO del
 * ProveedorSesion, y LayoutRaiz es justamente quien lo crea.
 */
function Navegacion({ fuentesListas }: { fuentesListas: boolean }) {
  const { usuario, cargando } = useSesion();
  const listo = fuentesListas && !cargando;
 
  useEffect(() => {
    // Cuando hay fuentes y Firebase ya respondió, quitamos el splash.
    if (listo) SplashScreen.hideAsync();
  }, [listo]);
 
  // Mientras tanto no dibujamos nada: el splash sigue cubriendo la pantalla.
  if (!listo) return null;
 
  return (
    <Stack
      screenOptions={{
        headerShown: false, // cada pantalla dibuja su propio encabezado
        contentStyle: { backgroundColor: colores.tinta },
        animation: 'slide_from_right',
      }}>
      {/*
        Stack.Protected: si `guard` es false, esas rutas "no existen".
        Si alguien está en una ruta que deja de existir (por ejemplo, cierra
        sesión estando en la bienvenida), Expo Router lo lleva a la primera
        ruta disponible. Así no hace falta escribir redirecciones a mano.
      */}
      <Stack.Protected guard={!!usuario}>
        <Stack.Screen name="(app)" />
      </Stack.Protected>
 
      <Stack.Protected guard={!usuario}>
        <Stack.Screen name="login" />
        <Stack.Screen name="registro" />
        <Stack.Screen name="recuperar" />
      </Stack.Protected>
    </Stack>
  );
}


================================================
📄 ARCHIVO: src\components\aviso.tsx
================================================

/**
 * Mensaje de resultado (error o éxito) que aparece sobre el formulario.
 * La barra lateral de color permite distinguir el tipo sin leer el texto.
 */
import { StyleSheet, Text, View } from 'react-native';
 
import { colores, espacio, fuentes } from '@/constants/tema';
 
type Props = {
  tipo: 'error' | 'exito';
  mensaje: string;
};
 
export function Aviso({ tipo, mensaje }: Props) {
  const esError = tipo === 'error';
  return (
    <View
      // "alert" hace que el lector de pantalla anuncie el mensaje de inmediato.
      accessibilityRole="alert"
      style={[
        styles.caja,
        {
          backgroundColor: esError ? colores.errorFondo : colores.exitoFondo,
          borderLeftColor: esError ? colores.error : colores.exito,
        },
      ]}>
      <Text style={[styles.texto, { color: esError ? colores.error : colores.exito }]}>
        {mensaje}
      </Text>
    </View>
  );
}
 
const styles = StyleSheet.create({
  caja: {
    borderLeftWidth: 4,
    borderRadius: 8,
    paddingVertical: espacio.m - 4,
    paddingHorizontal: espacio.m,
  },
  texto: {
    fontFamily: fuentes.textoMedio,
    fontSize: 14,
    lineHeight: 20,
  },
});


================================================
📄 ARCHIVO: src\components\boton.tsx
================================================

/**
 * Botón con tres variantes:
 *  - primario:   amarillo de seguridad. Una sola vez por pantalla.
 *  - secundario: contorno azul, para acciones alternativas.
 *  - enlace:     solo texto, para navegar ("¿Olvidaste tu contraseña?").
 *
 * El primario tiene una "base" oscura debajo y al presionarlo baja 4 px,
 * como una tecla física. La respuesta visual confirma que el toque se registró.
 */
import { ActivityIndicator, Pressable, StyleSheet, Text, View } from 'react-native';
 
import { colores, espacio, fuentes, radio } from '@/constants/tema';
 
type Props = {
  texto: string;
  onPress: () => void;
  variante?: 'primario' | 'secundario' | 'enlace';
  /** Muestra un indicador y bloquea el botón mientras se espera a Firebase. */
  cargando?: boolean;
  deshabilitado?: boolean;
};
 
const PROFUNDIDAD = 4;
 
export function Boton({
  texto,
  onPress,
  variante = 'primario',
  cargando = false,
  deshabilitado = false,
}: Props) {
  const inactivo = cargando || deshabilitado;
 
  if (variante === 'enlace') {
    return (
      <Pressable onPress={onPress} disabled={inactivo} hitSlop={8} accessibilityRole="link">
        {({ pressed }) => (
          <Text style={[styles.enlace, pressed && { opacity: 0.55 }]}>{texto}</Text>
        )}
      </Pressable>
    );
  }
 
  const esPrimario = variante === 'primario';
 
  return (
    <Pressable
      onPress={onPress}
      disabled={inactivo}
      accessibilityRole="button"
      accessibilityState={{ disabled: inactivo, busy: cargando }}
      style={styles.envoltura}>
      {({ pressed }) => (
        <>
          {/* Base que da la sensación de relieve (solo en el primario). */}
          {esPrimario && <View style={styles.base} />}
          <View
            style={[
              styles.cara,
              esPrimario ? styles.caraPrimaria : styles.caraSecundaria,
              // Al presionar, la cara baja hasta tocar la base.
              esPrimario && { transform: [{ translateY: pressed ? PROFUNDIDAD : 0 }] },
              !esPrimario && pressed && { backgroundColor: colores.tinta + '12' },
              inactivo && { opacity: 0.7 },
            ]}>
            {cargando ? (
              <ActivityIndicator color={esPrimario ? colores.tintaProfunda : colores.tinta} />
            ) : (
              <Text style={[styles.texto, !esPrimario && { color: colores.tinta }]}>{texto}</Text>
            )}
          </View>
        </>
      )}
    </Pressable>
  );
}
 
const styles = StyleSheet.create({
  envoltura: {
    marginTop: espacio.s,
    paddingBottom: PROFUNDIDAD,
  },
  base: {
    position: 'absolute',
    left: 0,
    right: 0,
    top: PROFUNDIDAD,
    bottom: 0,
    borderRadius: radio.control,
    backgroundColor: colores.tintaProfunda,
  },
  cara: {
    minHeight: 56,
    borderRadius: radio.control,
    alignItems: 'center',
    justifyContent: 'center',
    paddingHorizontal: espacio.l,
  },
  caraPrimaria: {
    backgroundColor: colores.senal,
  },
  caraSecundaria: {
    borderWidth: 1.5,
    borderColor: colores.tinta,
    backgroundColor: 'transparent',
  },
  texto: {
    color: colores.tintaProfunda,
    fontFamily: fuentes.textoFuerte,
    fontSize: 16,
  },
  enlace: {
    color: colores.tinta,
    fontFamily: fuentes.textoFuerte,
    fontSize: 15,
    textDecorationLine: 'underline',
    textDecorationColor: colores.senal,
  },
});


================================================
📄 ARCHIVO: src\components\campo-texto.tsx
================================================

/**
 * Campo de texto con etiqueta, estado de foco, mensaje de error y,
 * si es una contraseña, el botón para mostrarla u ocultarla.
 */
import { useState } from 'react';
import { Pressable, StyleSheet, Text, TextInput, View, type TextInputProps } from 'react-native';
 
import { colores, espacio, fuentes, radio } from '@/constants/tema';
 
type Props = TextInputProps & {
  etiqueta: string;
  error?: string | null;
  /** Si es true, el texto se oculta y aparece el botón Mostrar/Ocultar. */
  esClave?: boolean;
};
 
export function CampoTexto({ etiqueta, error, esClave = false, style, ...props }: Props) {
  const [enfocado, setEnfocado] = useState(false);
  const [claveVisible, setClaveVisible] = useState(false);
 
  // El color del borde comunica el estado: error > foco > reposo.
  const colorBorde = error ? colores.error : enfocado ? colores.tinta : colores.borde;
 
  return (
    <View style={styles.contenedor}>
      <Text style={styles.etiqueta}>{etiqueta}</Text>
 
      <View style={[styles.caja, { borderColor: colorBorde }, enfocado && styles.cajaEnfocada]}>
        <TextInput
          {...props}
          style={[styles.entrada, style]}
          placeholderTextColor={colores.lapiz + '99'}
          secureTextEntry={esClave && !claveVisible}
          // Nunca autocorregir ni poner mayúscula inicial en correos y claves.
          autoCapitalize={props.autoCapitalize ?? 'none'}
          autoCorrect={false}
          accessibilityLabel={etiqueta}
          onFocus={(e) => {
            setEnfocado(true);
            props.onFocus?.(e);
          }}
          onBlur={(e) => {
            setEnfocado(false);
            props.onBlur?.(e);
          }}
        />
        {esClave && (
          <Pressable
            onPress={() => setClaveVisible((v) => !v)}
            hitSlop={8}
            accessibilityRole="button"
            accessibilityLabel={claveVisible ? 'Ocultar contraseña' : 'Mostrar contraseña'}>
            <Text style={styles.alternar}>{claveVisible ? 'Ocultar' : 'Mostrar'}</Text>
          </Pressable>
        )}
      </View>
 
      {/* accessibilityLiveRegion hace que Android lea el error en voz alta al aparecer. */}
      {error ? (
        <Text style={styles.error} accessibilityLiveRegion="polite">
          {error}
        </Text>
      ) : null}
    </View>
  );
}
 
const styles = StyleSheet.create({
  contenedor: {
    gap: espacio.s - 2,
  },
  etiqueta: {
    color: colores.grafito,
    fontFamily: fuentes.textoMedio,
    fontSize: 14,
  },
  caja: {
    flexDirection: 'row',
    alignItems: 'center',
    backgroundColor: colores.hoja,
    borderWidth: 1.5,
    borderRadius: radio.control,
    paddingHorizontal: espacio.m,
    minHeight: 54,
  },
  cajaEnfocada: {
    // Al enfocar, una línea amarilla abajo refuerza dónde está el cursor.
    borderBottomColor: colores.senal,
    borderBottomWidth: 3,
  },
  entrada: {
    flex: 1,
    color: colores.grafito,
    fontFamily: fuentes.texto,
    fontSize: 16,
    paddingVertical: espacio.m - 2,
  },
  alternar: {
    color: colores.tinta,
    fontFamily: fuentes.textoFuerte,
    fontSize: 14,
    paddingLeft: espacio.s,
  },
  error: {
    color: colores.error,
    fontFamily: fuentes.textoMedio,
    fontSize: 13,
  },
});


================================================
📄 ARCHIVO: src\components\curvas-de-nivel.tsx
================================================

/**
 * Fondo de curvas de nivel (como un plano topográfico del Pichincha).
 *
 * No es una imagen: las curvas se calculan con matemáticas y se dibujan con
 * react-native-svg. Así pesan casi nada y se ven nítidas en cualquier pantalla.
 *
 * Cómo se construye cada curva:
 *   1. Se toman 64 ángulos alrededor de una "cumbre" (el centro).
 *   2. Para cada ángulo se calcula un radio que ondula con senos: así la
 *      curva no es un círculo perfecto sino un contorno irregular de montaña.
 *   3. Los puntos se unen con curvas Bézier suaves (técnica Catmull-Rom).
 *   4. Se repite con radios cada vez más grandes: cada anillo es una "cota".
 */
import { useMemo } from 'react';
import { StyleSheet } from 'react-native';
import Svg, { Circle, Path } from 'react-native-svg';
 
import { colores } from '@/constants/tema';
 
// Tamaño del "lienzo" interno. El SVG se escala al tamaño real del contenedor.
const ANCHO = 400;
const ALTO = 560;
 
type Punto = { x: number; y: number };
 
/** Convierte una lista cerrada de puntos en un trazo SVG suave. */
function trazoSuave(puntos: Punto[]): string {
  const n = puntos.length;
  let d = `M ${puntos[0].x.toFixed(1)} ${puntos[0].y.toFixed(1)}`;
  for (let i = 0; i < n; i++) {
    // Para cada tramo usamos el punto anterior y el siguiente como guía.
    const p0 = puntos[(i - 1 + n) % n];
    const p1 = puntos[i];
    const p2 = puntos[(i + 1) % n];
    const p3 = puntos[(i + 2) % n];
    const c1 = { x: p1.x + (p2.x - p0.x) / 6, y: p1.y + (p2.y - p0.y) / 6 };
    const c2 = { x: p2.x - (p3.x - p1.x) / 6, y: p2.y - (p3.y - p1.y) / 6 };
    d += ` C ${c1.x.toFixed(1)} ${c1.y.toFixed(1)}, ${c2.x.toFixed(1)} ${c2.y.toFixed(1)}, ${p2.x.toFixed(1)} ${p2.y.toFixed(1)}`;
  }
  return `${d} Z`;
}
 
/** Genera los anillos alrededor de una cumbre ubicada en (cx, cy). */
function generarCurvas(cx: number, cy: number, anillos: number): string[] {
  const curvas: string[] = [];
  for (let k = 1; k <= anillos; k++) {
    const radioBase = 14 + k * 21;
    const puntos: Punto[] = [];
    for (let i = 0; i < 64; i++) {
      const angulo = (i / 64) * Math.PI * 2;
      // La ondulación crece con el anillo: las cotas bajas son más irregulares.
      const ondulacion =
        Math.sin(angulo * 3 + k * 0.55) * (4 + k * 1.6) +
        Math.sin(angulo * 5 - k * 0.8) * (2 + k * 0.7) +
        Math.cos(angulo * 2 + k * 0.3) * k * 1.3;
      const r = radioBase + ondulacion;
      // Estiramos en X para que la montaña sea alargada, como una cordillera.
      puntos.push({ x: cx + Math.cos(angulo) * r * 1.35, y: cy + Math.sin(angulo) * r });
    }
    curvas.push(trazoSuave(puntos));
  }
  return curvas;
}
 
export function CurvasDeNivel() {
  // useMemo: los trazos se calculan una sola vez y no en cada render.
  const curvas = useMemo(() => generarCurvas(300, 70, 20), []);
  const cumbre = { x: 300, y: 70 };
 
  return (
    <Svg
      style={StyleSheet.absoluteFill}
      viewBox={`0 0 ${ANCHO} ${ALTO}`}
      // "slice" recorta como object-fit: cover, sin deformar las curvas.
      // "YMin" ancla arriba: la cumbre queda siempre a la vista.
      preserveAspectRatio="xMidYMin slice"
      pointerEvents="none">
      {curvas.map((d, i) => (
        <Path
          key={i}
          d={d}
          fill="none"
          stroke={colores.curva}
          // Cada quinta curva es una "curva maestra", más gruesa, como en los mapas reales.
          strokeWidth={i % 5 === 4 ? 1.8 : 0.9}
        />
      ))}
      {/* Punto de cota en la cumbre: el único detalle amarillo del encabezado. */}
      <Circle cx={cumbre.x} cy={cumbre.y} r={3.5} fill={colores.senal} />
      <Circle cx={cumbre.x} cy={cumbre.y} r={9} fill="none" stroke={colores.senal} strokeWidth={1} />
    </Svg>
  );
}


================================================
📄 ARCHIVO: src\components\pantalla-hoja.tsx
================================================

/**
 * Plantilla común de todas las pantallas:
 *
 * Centralizar esto en un componente hace que cada pantalla solo se ocupe
 * de su lógica y no repita el manejo del teclado ni de las zonas seguras.
 */
import { router } from 'expo-router';
import { StatusBar } from 'expo-status-bar';
import type { ReactNode } from 'react';
import {
  KeyboardAvoidingView,
  Pressable,
  ScrollView,
  StyleSheet,
  Text,
  View,
} from 'react-native';
import { useSafeAreaInsets } from 'react-native-safe-area-context';
import Svg, { Path } from 'react-native-svg';
 
import { CurvasDeNivel } from '@/components/curvas-de-nivel';
import { colores, espacio, fuentes, radio } from '@/constants/tema';
 
type Props = {
  /** Línea pequeña sobre el título (por ejemplo, el nombre de la escuela). */
  antetitulo?: string;
  titulo: string;
  bajada?: string;
  /** Muestra el botón "Volver" en el encabezado. */
  conVolver?: boolean;
  /** Contenido extra dentro del encabezado, debajo del título. */
  extraEncabezado?: ReactNode;
  children: ReactNode;
};
 
export function PantallaHoja({
  antetitulo,
  titulo,
  bajada,
  conVolver = false,
  extraEncabezado,
  children,
}: Props) {
  // insets = espacio ocupado por la muesca (notch) y la barra de gestos.
  const insets = useSafeAreaInsets();
 
  return (
    // El teclado tapa los campos; KeyboardAvoidingView empuja el contenido.
    // También se necesita en Android: con edge-to-edge (siempre activo en SDK
    // recientes) el sistema ya no redimensiona la ventana al abrir el teclado.
    <KeyboardAvoidingView style={styles.raiz} behavior="padding">
      {/* Íconos de la barra de estado en blanco, porque el fondo es oscuro. */}
      <StatusBar style="light" />
      <ScrollView
        contentContainerStyle={styles.scroll}
        // "handled": un toque en un botón funciona aunque el teclado esté abierto.
        keyboardShouldPersistTaps="handled"
        bounces={false}>
        <View style={[styles.encabezado, { paddingTop: insets.top + espacio.m }]}>
          <CurvasDeNivel />
 
          {conVolver && (
            <Pressable
              onPress={() => router.back()}
              accessibilityRole="button"
              accessibilityLabel="Volver"
              hitSlop={12}
              style={({ pressed }) => [
                styles.volver,
                { top: insets.top + espacio.s },
                pressed && { opacity: 0.6 },
              ]}>
              <Svg width={18} height={18} viewBox="0 0 24 24">
                <Path
                  d="M15 5 L8 12 L15 19"
                  stroke={colores.papel}
                  strokeWidth={2.4}
                  fill="none"
                  strokeLinecap="round"
                  strokeLinejoin="round"
                />
              </Svg>
              <Text style={styles.volverTexto}>Volver</Text>
            </Pressable>
          )}
 
          <View style={styles.bloqueTitulo}>
            {antetitulo ? <Text style={styles.antetitulo}>{antetitulo}</Text> : null}
            {/* accessibilityRole="header" ayuda a los lectores de pantalla. */}
            <Text style={styles.titulo} accessibilityRole="header">
              {titulo}
            </Text>
            {bajada ? <Text style={styles.bajada}>{bajada}</Text> : null}
            {extraEncabezado}
          </View>
        </View>
 
        <View style={[styles.hoja, { paddingBottom: insets.bottom + espacio.xl }]}>
          {children}
        </View>
      </ScrollView>
    </KeyboardAvoidingView>
  );
}
 
const styles = StyleSheet.create({
  raiz: {
    flex: 1,
    backgroundColor: colores.tinta,
  },
  scroll: {
    // flexGrow permite que la hoja ocupe todo el alto aunque haya poco contenido.
    flexGrow: 1,
  },
  encabezado: {
    backgroundColor: colores.tinta,
    paddingHorizontal: espacio.l,
    // El espacio extra abajo queda oculto bajo la hoja (que sube con margen negativo).
    paddingBottom: espacio.xxl + radio.hoja,
    overflow: 'hidden',
    minHeight: 280,
    justifyContent: 'flex-end',
  },
  volver: {
    position: 'absolute',
    left: espacio.m,
    flexDirection: 'row',
    alignItems: 'center',
    gap: 2,
    paddingVertical: espacio.s,
    paddingHorizontal: espacio.s,
    // top se calcula en el render con insets.top (depende del teléfono).
  },
  volverTexto: {
    color: colores.papel,
    fontFamily: fuentes.textoMedio,
    fontSize: 15,
  },
  bloqueTitulo: {
    marginTop: espacio.xxl + espacio.l,
    maxWidth: 520,
  },
  antetitulo: {
    color: colores.senal,
    fontFamily: fuentes.textoMedio,
    fontSize: 14,
    letterSpacing: 0.2,
    marginBottom: espacio.s,
  },
  titulo: {
    color: colores.papel,
    fontFamily: fuentes.titular,
    fontSize: 58,
    lineHeight: 56,
    letterSpacing: -0.5,
  },
  bajada: {
    color: colores.papel,
    opacity: 0.78,
    fontFamily: fuentes.texto,
    fontSize: 16,
    lineHeight: 23,
    marginTop: espacio.m,
    maxWidth: 340,
  },
  hoja: {
    flex: 1,
    backgroundColor: colores.papel,
    borderTopLeftRadius: radio.hoja,
    borderTopRightRadius: radio.hoja,
    // La hoja "sube" sobre el encabezado para que parezca apoyada encima.
    marginTop: -radio.hoja,
    paddingHorizontal: espacio.l,
    paddingTop: espacio.xl,
    gap: espacio.m,
  },
});


================================================
📄 ARCHIVO: src\config\firebase.ts
================================================


import AsyncStorage from '@react-native-async-storage/async-storage'
import { getApp, getApps, initializeApp } from 'firebase/app'
import { getAuth, getReactNativePersistence, initializeAuth, type Auth } from 'firebase/auth'

const firebaseConfig = {
    apiKey: process.env.EXPO_PUBLIC_FIREBASE_API_KEY,
    authDomain: process.env.EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN,
    projectId: process.env.EXPO_PUBLIC_FIREBASE_PROJECT_ID,
    storageBucket: process.env.EXPO_PUBLIC_FIREBASE_STORAGE_BUCKET,
    messagingSenderId: process.env.EXPO_PUBLIC_FIREBASE_MESSAGING_SENDER_ID,
    appId: process.env.EXPO_PUBLIC_FIREBASE_APP_ID,
};

const app = getApps().length ? getApp() : initializeApp(firebaseConfig);

function crearAuth(): Auth {
    try {

        return initializeAuth(app, {
            persistence: getReactNativePersistence(AsyncStorage),
        })

    } catch {
        return getAuth(app);
    }
}

export const auth = crearAuth();

================================================
📄 ARCHIVO: src\constants\tema.ts
================================================

export {};export const colores = {
  tinta: '#14213D', // azul politécnico: fondo del encabezado
  tintaProfunda: '#0C1529', // sombra del encabezado y texto sobre amarillo
  curva: '#2C3D68', // curvas de nivel dibujadas sobre la tinta
  papel: '#EEF1F5', // fondo de la hoja (gris frío, no crema)
  hoja: '#FFFFFF', // superficie de los campos y tarjetas
  senal: '#F5B700', // amarillo de seguridad: botón principal
  grafito: '#1F232B', // texto principal sobre la hoja
  lapiz: '#5A6274', // texto secundario y etiquetas
  borde: '#CBD2DD', // bordes de campos en reposo
  error: '#B3361F',
  errorFondo: '#FBE9E5',
  exito: '#22704F',
  exitoFondo: '#E3F3EA',
} as const;


export const fuentes = {
  titular: 'BigShoulders_800ExtraBold',
  texto: 'SpaceGrotesk_400Regular',
  textoMedio: 'SpaceGrotesk_500Medium',
  textoFuerte: 'SpaceGrotesk_700Bold',
} as const;
 
/** Escala de espacios basada en múltiplos de 4 px. */
export const espacio = {
  xs: 4,
  s: 8,
  m: 16,
  l: 24,
  xl: 32,
  xxl: 48,
} as const;
 
/** Radios: la hoja es más redondeada que los controles para marcar jerarquía. */
export const radio = {
  control: 12,
  hoja: 28,
} as const;


================================================
📄 ARCHIVO: src\context\sesion.tsx
================================================

/**
 * Contexto de sesión: el único lugar de la app que habla con Firebase Auth.
 *
 * Las pantallas no importan Firebase directamente; llaman a las funciones de
 * este contexto (iniciarSesion, registrarse, etc.). Así, si mañana se cambia
 * Firebase por otro proveedor, solo se reescribe este archivo.
 */
import {
  createUserWithEmailAndPassword,
  EmailAuthProvider,
  onAuthStateChanged,
  reauthenticateWithCredential,
  sendPasswordResetEmail,
  signInWithEmailAndPassword,
  signOut,
  updatePassword,
  updateProfile,
  type User,
} from 'firebase/auth';
import { createContext, use, useEffect, useState, type ReactNode } from 'react';
 
import { auth } from '@/config/firebase';
 
type ValorSesion = {
  /** Usuario conectado, o null si nadie ha iniciado sesión. */
  usuario: User | null;
  /** Nombre del perfil (displayName), siempre actualizado tras el registro. */
  nombre: string | null;
  /** true mientras Firebase revisa si hay una sesión guardada. */
  cargando: boolean;
  iniciarSesion: (correo: string, clave: string) => Promise<void>;
  registrarse: (nombre: string, correo: string, clave: string) => Promise<void>;
  enviarCorreoRecuperacion: (correo: string) => Promise<void>;
  cambiarClave: (claveActual: string, claveNueva: string) => Promise<void>;
  cerrarSesion: () => Promise<void>;
};
 
const ContextoSesion = createContext<ValorSesion | null>(null);
 
/** Hook para leer la sesión desde cualquier pantalla. */
export function useSesion(): ValorSesion {
  // `use` es la forma moderna (React 19) de leer un contexto.
  const valor = use(ContextoSesion);
  if (!valor) {
    throw new Error('useSesion debe usarse dentro de <ProveedorSesion>.');
  }
  return valor;
}
 
export function ProveedorSesion({ children }: { children: ReactNode }) {
  const [usuario, setUsuario] = useState<User | null>(null);
  const [cargando, setCargando] = useState(true);
  // Nombre del perfil guardado aparte: updateProfile modifica el mismo objeto
  // `user` sin cambiar su referencia, así que React no detectaría el cambio
  // si las pantallas leyeran usuario.displayName directamente.
  const [nombre, setNombre] = useState<string | null>(null);

  useEffect(() => {
    // onAuthStateChanged se dispara al arrancar (con la sesión guardada o null)
    // y cada vez que alguien inicia o cierra sesión. Es la fuente de verdad:
    // la navegación (Stack.Protected en _layout.tsx) depende de este estado.
    const cancelarSuscripcion = onAuthStateChanged(auth, (usuarioFirebase) => {
      setUsuario(usuarioFirebase);
      setNombre(usuarioFirebase?.displayName ?? null);
      setCargando(false);
    });
    // Al desmontar el proveedor dejamos de escuchar para no fugar memoria.
    return cancelarSuscripcion;
  }, []);
 
  async function iniciarSesion(correo: string, clave: string) {
    await signInWithEmailAndPassword(auth, correo.trim(), clave);
    // No navegamos aquí: onAuthStateChanged actualiza `usuario` y el
    // Stack.Protected muestra automáticamente la pantalla de bienvenida.
  }
 
  async function registrarse(nombreCompleto: string, correo: string, clave: string) {
    // Crear la cuenta también inicia la sesión.
    const credencial = await createUserWithEmailAndPassword(auth, correo.trim(), clave);
    // Guardamos el nombre en el perfil de Firebase (campo displayName).
    const nombreLimpio = nombreCompleto.trim();
    await updateProfile(credencial.user, { displayName: nombreLimpio });
    // La bienvenida ya se mostró (onAuthStateChanged corre al crear la cuenta,
    // antes de updateProfile), así que actualizamos el nombre en el estado.
    setNombre(nombreLimpio);
  }
 
  async function enviarCorreoRecuperacion(correo: string) {
    // Firebase envía un correo con un enlace a su página de restablecimiento.
    // Si el correo no existe, por la protección de enumeración NO lanza error:
    // por eso la pantalla muestra un mensaje neutro.
    await sendPasswordResetEmail(auth, correo.trim());
  }
 
  async function cambiarClave(claveActual: string, claveNueva: string) {
    const actual = auth.currentUser;
    if (!actual?.email) throw new Error('No hay una sesión activa.');
 
    // updatePassword es una operación sensible: Firebase la rechaza con
    // "auth/requires-recent-login" si la sesión no es reciente. Por eso
    // primero confirmamos la identidad con la contraseña actual.
    const credencial = EmailAuthProvider.credential(actual.email, claveActual);
    await reauthenticateWithCredential(actual, credencial);
    await updatePassword(actual, claveNueva);
  }
 
  async function cerrarSesion() {
    await signOut(auth);
  }
 
  return (
    <ContextoSesion
      value={{
        usuario,
        nombre,
        cargando,
        iniciarSesion,
        registrarse,
        enviarCorreoRecuperacion,
        cambiarClave,
        cerrarSesion,
      }}>
      {children}
    </ContextoSesion>
  );
}


================================================
📄 ARCHIVO: src\lib\errores-firebase.ts
================================================

/**
 * Traduce los códigos de error de Firebase Auth a mensajes claros en español.
 *
 * Firebase devuelve errores como "auth/invalid-credential". Mostrar eso al
 * usuario no sirve: el mensaje debe decir que paso y cómo corregirlo.
 */
import { FirebaseError } from 'firebase/app';
 
const mensajes: Record<string, string> = {
  // Desde 2023 los proyectos nuevos tienen activada la "protección contra la
  // enumeración de correos": Firebase ya no distingue entre "el correo no
  // existe" y "la contraseña es incorrecta". Ambos llegan como invalid-credential.
  'auth/invalid-credential': 'El correo o la contraseña no coinciden. Revisa los datos e inténtalo de nuevo.',
  'auth/wrong-password': 'El correo o la contraseña no coinciden. Revisa los datos e inténtalo de nuevo.',
  'auth/user-not-found': 'El correo o la contraseña no coinciden. Revisa los datos e inténtalo de nuevo.',
  'auth/invalid-email': 'El correo no tiene un formato válido. Ejemplo: nombre.apellido@epn.edu.ec',
  'auth/missing-email': 'Escribe tu correo para continuar.',
  'auth/missing-password': 'Escribe tu contraseña para continuar.',
  'auth/email-already-in-use': 'Ya existe una cuenta con ese correo. Inicia sesión o recupera tu contraseña.',
  'auth/weak-password': 'La contraseña es muy débil. Usa al menos 8 caracteres.',
  'auth/password-does-not-meet-requirements':
    'La contraseña no cumple la política del proyecto. Combina mayúsculas, minúsculas y números.',
  'auth/too-many-requests': 'Hubo demasiados intentos seguidos. Espera unos minutos y vuelve a intentarlo.',
  'auth/network-request-failed': 'No hay conexión con Firebase. Revisa tu internet e inténtalo otra vez.',
  'auth/requires-recent-login': 'Por seguridad, cierra sesión, vuelve a ingresar y repite el cambio.',
  'auth/user-disabled': 'Esta cuenta fue deshabilitada. Comunícate con el administrador.',
  // Este suele aparecer en clase: falta habilitar el proveedor en la consola.
  'auth/operation-not-allowed':
    'El acceso con correo y contraseña no está habilitado en la consola de Firebase.',
  'auth/invalid-api-key': 'La configuración de Firebase no es válida. Revisa el archivo .env.local.',
};
 
/**
 * @param error  Lo que llegó al bloque catch.
 * @param reemplazos  Mensajes propios de una pantalla para ciertos códigos.
 *   Ejemplo: al cambiar la contraseña, invalid-credential significa
 *   "la contraseña actual no es correcta", no "el correo no coincide".
 */
export function mensajeDeError(error: unknown, reemplazos: Record<string, string> = {}): string {
  if (error instanceof FirebaseError) {
    if (reemplazos[error.code]) return reemplazos[error.code];
    if (mensajes[error.code]) return mensajes[error.code];
    // La API key mal copiada produce un código largo que empieza así.
    if (error.code.startsWith('auth/api-key-not-valid')) return mensajes['auth/invalid-api-key'];
    // Para errores no previstos mostramos el código: ayuda a depurar en el taller.
    return `No se pudo completar la operación (${error.code}).`;
  }
  return 'Ocurrió un error inesperado. Inténtalo de nuevo.';
}


================================================
📄 ARCHIVO: src\lib\validaciones.ts
================================================

/**
 * Validaciones del lado del cliente.
 * Sirven para dar respuesta inmediata sin gastar una petición a Firebase.
 * No reemplazan la validación del servidor: Firebase vuelve a validar todo.
 * Cada función devuelve un mensaje de error o null si el valor es válido.
 */
 
// Patrón simple: algo@algo.dominio. La validación estricta la hace Firebase.
const PATRON_CORREO = /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/;
 
/** Firebase exige 6 caracteres como mínimo; en el taller pedimos 8. */
export const LONGITUD_MINIMA_CLAVE = 8;
 
export function validarCorreo(correo: string): string | null {
  if (!correo.trim()) return 'Escribe tu correo.';
  if (!PATRON_CORREO.test(correo.trim())) return 'Revisa el formato del correo.';
  return null;
}
 
export function validarClave(clave: string): string | null {
  if (!clave) return 'Escribe una contraseña.';
  if (clave.length < LONGITUD_MINIMA_CLAVE) {
    return `Usa al menos ${LONGITUD_MINIMA_CLAVE} caracteres.`;
  }
  return null;
}
 
export function validarConfirmacion(clave: string, confirmacion: string): string | null {
  if (!confirmacion) return 'Repite la contraseña.';
  if (clave !== confirmacion) return 'Las contraseñas no coinciden.';
  return null;
}
 
export function validarNombre(nombre: string): string | null {
  if (nombre.trim().length < 3) return 'Escribe tu nombre (mínimo 3 letras).';
  return null;
}


================================================
📄 ARCHIVO: tsconfig.json
================================================

{
  "extends": "expo/tsconfig.base",
  "compilerOptions": {
    "strict": true,
    "paths": {
      "@/*": [
        "./src/*"
      ],
      "@/assets/*": [
        "./assets/*"
      ],
      "@firebase/auth": [
        "./node_modules/@firebase/auth/dist/index.rn.d.ts"
      ]
    }
  },
  "include": [
    "**/*.ts",
    "**/*.tsx",
    ".expo/types/**/*.ts",
    "expo-env.d.ts"
  ]
}
