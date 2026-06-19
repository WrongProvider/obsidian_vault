# Setup — React Native no Linux (Ubuntu/Debian)

> Documentação baseada no setup real do projeto **Minuto Offline**

---

## Pré-requisitos

- Ubuntu / Debian (ou derivado)
- Node.js >= 18
- Conexão com internet

---

## 1. Instalar o JDK 17

React Native 0.73 requer **JDK 17**. A forma mais confiável no Linux é via SDKMAN:

```bash
# instala o SDKMAN
curl -s "https://get.sdkman.io" | bash
source ~/.sdkman/bin/sdkman-init.sh

# instala o JDK 17 Temurin
sdk install java 17.0.11-tem
sdk use java 17.0.11-tem

# confirma
java -version
# deve mostrar: openjdk version "17..."
```

Configura o JAVA_HOME:

```bash
echo 'export JAVA_HOME="$HOME/.sdkman/candidates/java/current"' >> ~/.bashrc
echo 'export PATH="$JAVA_HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

---

## 2. Instalar o Android SDK

### Opção A — Android Studio (recomendado para iniciantes)

Baixe e instale o Android Studio em https://developer.android.com/studio. Abra uma vez para ele baixar o SDK automaticamente em `~/Android/Sdk`.

### Opção B — Só as command-line tools (sem Android Studio)

```bash
cd ~/Android/Sdk
mkdir -p cmdline-tools
cd cmdline-tools

wget https://dl.google.com/android/repository/commandlinetools-linux-11076708_latest.zip
unzip commandlinetools-linux-11076708_latest.zip
mv cmdline-tools latest
```

---

## 3. Configurar variáveis de ambiente do Android

```bash
echo 'export ANDROID_HOME=$HOME/Android/Sdk' >> ~/.bashrc
echo 'export PATH=$PATH:$ANDROID_HOME/emulator' >> ~/.bashrc
echo 'export PATH=$PATH:$ANDROID_HOME/platform-tools' >> ~/.bashrc
echo 'export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin' >> ~/.bashrc
source ~/.bashrc

# confirma
echo $ANDROID_HOME
adb --version
sdkmanager --version
```

---

## 4. Instalar o CMake pelo SDK

> ⚠️ Não use o cmake instalado via pip (`~/.local/bin/cmake`). Use o do SDK.

```bash
# remove o cmake do Python se existir
pip uninstall cmake -y

# instala o cmake pelo SDK
sdkmanager "cmake;3.22.1"

# adiciona ao PATH
echo 'export PATH=$ANDROID_HOME/cmake/3.22.1/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# confirma
which cmake
# deve mostrar: ~/Android/Sdk/cmake/3.22.1/bin/cmake
```

---

## 5. Ativar aceleração de hardware (KVM)

Permite que o emulador use a CPU real em vez de emular:

```bash
sudo apt install qemu-kvm
sudo usermod -aG kvm $USER

# confirma (faça logout/login antes)
kvm-ok
# deve mostrar: KVM acceleration can be used
```

---

## 6. Criar o projeto React Native

```bash
npx react-native@0.73.4 init MinutoOffline --version 0.73.4
cd MinutoOffline
```

---

## 7. Corrigir o Gradle (versão compatível com RN 0.73)

```bash
nano android/gradle/wrapper/gradle-wrapper.properties
```

Altere a linha `distributionUrl` para:

```
distributionUrl=https\://services.gradle.org/distributions/gradle-8.3-bin.zip
```

---

## 8. Corrigir o build.gradle

```bash
cat > android/build.gradle << 'EOF'
buildscript {
    ext {
        buildToolsVersion = "35.0.0"
        minSdkVersion = 24
        compileSdkVersion = 35
        targetSdkVersion = 35
        ndkVersion = "27.1.12297006"
        kotlinVersion = "1.9.24"
    }
    repositories {
        google()
        mavenCentral()
    }
    dependencies {
        classpath("com.android.tools.build:gradle:8.3.2")
        classpath("com.facebook.react:react-native-gradle-plugin")
        classpath("org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.24")
    }
}

apply plugin: "com.facebook.react.rootproject"
EOF
```

---

## 9. Corrigir o settings.gradle

```bash
cat > android/settings.gradle << 'EOF'
pluginManagement { includeBuild("../node_modules/@react-native/gradle-plugin") }
plugins { id("com.facebook.react.settings") }
extensions.configure(com.facebook.react.ReactSettingsExtension){ ex -> ex.autolinkLibrariesFromCommand() }
rootProject.name = 'MinutoOffline'
include ':app'
includeBuild('../node_modules/@react-native/gradle-plugin')
EOF
```

---

## 10. Criar o local.properties

Aponta para onde o Android SDK está instalado:

```bash
echo "sdk.dir=$HOME/Android/Sdk" > android/local.properties
```

---

## 11. Instalar dependências do projeto

```bash
npm install
```

Se usar `react-native-safe-area-context`, use a versão compatível com RN 0.73:

```bash
npm install react-native-safe-area-context@4.8.2
```

---

## 12. Criar e iniciar o emulador Android

```bash
# baixa a imagem do Android
sdkmanager "system-images;android-36;google_apis;x86_64"

# aceita as licenças
sdkmanager --licenses

# lista os devices disponíveis
avdmanager list device | grep -i pixel

# cria o AVD (Pixel 7 recomendado)
avdmanager create avd -n MeuPixel \
  -k "system-images;android-36;google_apis;x86_64" \
  --device "pixel_7"

# confirma que foi criado
emulator -list-avds

# inicia o emulador com aceleração de GPU
emulator -avd MeuPixel \
  -gpu host \
  -accel on \
  -no-boot-anim \
  -no-snapshot &

# aguarda o Android carregar (~2 minutos) e confirma
adb devices
# deve mostrar: emulator-5554   device
```

---

## 13. Organizar a estrutura de pastas do projeto

```bash
mkdir -p src/screens src/components src/hooks

mv src/HomeScreen.tsx    src/screens/HomeScreen.tsx
mv src/MainButton.tsx    src/components/MainButton.tsx
mv src/TimerDisplay.tsx  src/components/TimerDisplay.tsx
mv src/StatsRow.tsx      src/components/StatsRow.tsx
mv src/SessionHistory.tsx src/components/SessionHistory.tsx
mv src/useOfflineTimer.ts src/hooks/useOfflineTimer.ts
```

Estrutura final:

```
MinutoOffline/
├── App.tsx
├── index.js
├── android/
├── ios/
├── src/
│   ├── screens/
│   │   └── HomeScreen.tsx
│   ├── components/
│   │   ├── MainButton.tsx
│   │   ├── TimerDisplay.tsx
│   │   ├── StatsRow.tsx
│   │   └── SessionHistory.tsx
│   └── hooks/
│       └── useOfflineTimer.ts
└── package.json
```

---

## 14. Rodar o projeto

Sempre abra **dois terminais**:

**Terminal 1 — Metro Bundler (servidor JS):**

```bash
npx react-native start
```

**Terminal 2 — Build e instalação:**

```bash
npm run android
```

> Após o primeiro build, mudanças em `.tsx/.ts` recarregam automaticamente. Só rode `npm run android` novamente se mudar arquivos nativos (`.java`, `.gradle`).

---

## Comandos úteis do dia a dia

```bash
# reinicia o Metro limpando o cache
npx react-native start --reset-cache

# recarrega o app no emulador
# pressione R, R no teclado com o emulador em foco

# ver logs em tempo real
adb logcat *:S ReactNative:V ReactNativeJS:V

# salvar logs em arquivo
adb logcat *:S ReactNative:V ReactNativeJS:V > log.txt

# limpa o build do Android
cd android && ./gradlew clean && cd ..

# lista emuladores disponíveis
emulator -list-avds

# inicia emulador
emulator -avd MeuPixel -gpu host -accel on -no-boot-anim &

# verifica dispositivos conectados
adb devices
```

---

## Erros comuns e soluções

|Erro|Causa|Solução|
|---|---|---|
|`IBM_SEMERU` / JDK incompatível|JDK errado|Instalar JDK 17 via SDKMAN|
|`SDK location not found`|ANDROID_HOME não configurado|Configurar `.bashrc` + `local.properties`|
|`No module named 'cmake'`|cmake do pip no PATH|`pip uninstall cmake` + instalar via `sdkmanager`|
|`No connected devices`|Emulador não iniciado|Iniciar com `emulator -avd MeuPixel &`|
|`Unable to load script`|Metro não está rodando|Rodar `npx react-native start`|
|`react_codegen_safeareacontext`|Versão incompatível|Usar `react-native-safe-area-context@4.8.2`|
|`Plugin not found`|`settings.gradle` incorreto|Corrigir conforme passo 9|