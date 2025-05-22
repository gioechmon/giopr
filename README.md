# PuntoNaranja App 👋

## Descripción del Proyecto

PuntoNaranja es una aplicación móvil desarrollada con [React Native](https://reactnative.dev/) y [Expo](https://expo.dev/) que ayuda a localizar y solicitar ayuda en puntos naranjas de seguridad. Utiliza [TypeScript](https://react.dev/learn/typescript) para un desarrollo robusto y seguro.

---

## Índice

- [Descripción del Proyecto](#descripción-del-proyecto)
- [Requisitos del Sistema](#requisitos-del-sistema)
- [Instalación y Configuración del Entorno](#instalación-y-configuración-del-entorno)
- [Configuración de Variables de Entorno](#configuración-de-variables-de-entorno)
- [Instalación de Dependencias](#instalación-de-dependencias)
- [Comandos Útiles](#comandos-útiles)
- [Uso](#uso)

---

## Requisitos del Sistema

- Sistema operativo Windows 8 o superior (64 bits, compatible con HAXM)
- Usuario local sin espacios en el nombre (ejemplo: `user`)
- PowerShell con Execution Policy en `unrestricted`
- Android Studio instalado

---

## Instalación y Configuración del Entorno

### 1. Configurar PowerShell

1. Abre PowerShell como administrador.
2. Verifica la política de ejecución:
   ```powershell
   Get-ExecutionPolicy
   ```
3. Si marca `Restricted`, cambia a `unrestricted`:
   ```powershell
   Set-ExecutionPolicy unrestricted
   ```
4. (Opcional) Agrega el perfil de Chocolatey:
   ```powershell
   notepad $profile
   ```
   Agrega lo siguiente y guarda:
   ```powershell
   # Chocolatey profile
   $ChocolateyProfile = "$env:ChocolateyInstall\helpers\chocolateyProfile.psm1"
   if (Test-Path($ChocolateyProfile)) {
     Import-Module "$ChocolateyProfile"
   }
   ```

### 2. Instalar Chocolatey

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
Verifica la instalación:
```powershell
choco -?
```

### 3. Instalar Node.js y JDK 17

```cmd
choco install -y nodejs-lts microsoft-openjdk17
```

### 4. Instalar Android Studio

1. Descarga desde [Android Studio](https://developer.android.com/studio)
2. Abre "SDK Manager" y en la pestaña **SDK Tools** selecciona:
   - Intel x86 Emulator Accelerator (HAXM installer)
   - Google Play services
   - Android SDK Command-line tools
   - Android SDK Platform-Tools
3. Si no aparece HAXM, agrega el sitio manualmente:
   - Nombre: Intel HAXM
   - URL: https://dl.google.com/android/repository/extras/intel/addon2-1.xml

### 5. Crear un Dispositivo Virtual

1. Abre "Virtual Device Manager" en Android Studio.
2. Crea un nuevo dispositivo con:
   - API: Api35 Vanillaicecream android15
   - Services: Google APIs o Google Play
   - System Image: Google APIs Intel x86 Atom System Image

---

## Configuración de Variables de Entorno

1. **ANDROID_HOME**
   - Nombre: `ANDROID_HOME`
   - Valor: Ruta a tu SDK, por ejemplo: `C:\Users\user\AppData\Local\Android\Sdk`
2. **platform-tools**
   - Agrega la ruta a platform-tools a tu variable de entorno `PATH`, por ejemplo: `C:\Users\user\AppData\Local\Android\Sdk\platform-tools`
3. Verifica en PowerShell:
   ```powershell
   Get-ChildItem -Path Env:\
   ```

---

## Instalación de Dependencias

1. Abre una terminal en la carpeta del proyecto.
2. Ejecuta:
   ```bash
   npm install
   ```

### Dependencias Esenciales

#### Expo

- `npm install expo-blur`
- `npm install expo-checkbox`
- `npx expo install expo-location`
- `npx expo install expo-notifications`
- `npx expo install expo-contacts`

#### React Native

- `npm install @react-navigation/drawer react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context react-native-vector-icons`
- `npm install @react-navigation/native`
- `npm install @react-navigation/stack`
- `npx expo install react-native-maps`
- `npx expo install @react-native-async-storage/async-storage`
- `npm install @react-native-community/netinfo`

#### Utilidades

- `npm install axios`
- `npm install dotenv`
- `npm install babel-plugin-module-resolver --save-dev`
- `npm install --save-dev eslint eslint-config-expo eslint-plugin-react eslint-plugin-react-hooks eslint-plugin-prettier prettier`
- `npm install @gorhom/bottom-sheet`

#### Notificaciones

- `npm install react-native-push-notification`
- `npm install @react-native-community/push-notification-ios`

---

## Comandos Útiles

- Iniciar el proyecto:
  ```bash
  npx expo start
  ```
- Ejecutar en Android:
  ```bash
  npm run android
  ```

---

## Uso

1. Asegúrate de tener un emulador Android corriendo o un dispositivo conectado.
2. En la terminal, ejecuta:
   ```bash
   npx expo start
   ```
3. Escanea el código QR con la app Expo Go o selecciona "Run on Android device/emulator" en la interfaz web de Expo.
4. Sigue las instrucciones en pantalla para registrarte y comenzar a usar la app.
