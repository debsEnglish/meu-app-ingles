# ApexLex C1 — Pacote de Compilação Android (.APK)

Este pacote contém o projeto completo do **ApexLex C1** estruturado com **Capacitor** para gerar um arquivo instalável **`.apk`** para Android — tanto **sem instalar nada no computador (via GitHub Actions na nuvem)** quanto **localmente via Android Studio**.

---

## Opção 1: Gerar o `.apk` Gratuitamente na Nuvem (Sem Instalar Android Studio)

O pacote já inclui o arquivo `.github/workflows/build-apk.yml` pré-configurado para compilar o APK automaticamente nos servidores do GitHub:

1. Descompacte este arquivo `.zip` em uma pasta no seu computador.
2. Crie uma conta gratuita no **GitHub** (github.com) e crie um novo repositório (ex.: `apexlex-c1-app`).
3. Envie todos os arquivos descompactados para o repositório.
4. No GitHub, abra a aba **Actions** → selecione **"Build Android APK (ApexLex C1)"** → clique em **"Run workflow"**.
5. Aguarde ~3 minutos até o ícone ficar verde, clique na execução concluída e baixe o arquivo **`ApexLex-C1-Android-APK`** (que contém o `app-debug.apk` pronto para instalar no seu celular Android).

---

## Opção 2: Compilar Localmente no Seu Computador (Android Studio)

Pré-requisitos: **Node.js (v18+)** e **Android Studio** instalados.

1. Abra o terminal na pasta descompactada (`apexlex-android`) e execute:
   ```bash
   npm install
   npx cap add android
   npx cap sync android
   ```
2. Abra o arquivo `android/app/src/main/AndroidManifest.xml` e adicione a permissão de microfone (para a aba *Speaking*) logo acima da tag `<application>`:
   ```xml
   <uses-permission android:name="android.permission.RECORD_AUDIO" />
   <uses-permission android:name="android.permission.INTERNET" />
   ```
3. Abra o projeto no Android Studio ou compile direto pelo terminal:
   ```bash
   npx cap open android
   ```
   No menu superior do Android Studio, clique em **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
4. O arquivo final será salvo em:
   `android/app/build/outputs/apk/debug/app-debug.apk`

---

## Como Instalar o `.apk` no Celular Android
1. Transfira o arquivo `app-debug.apk` para o seu celular (via WhatsApp, Google Drive ou cabo USB).
2. Toque no arquivo `.apk` no celular e autorize **"Instalar apps desconhecidos"** quando solicitado pelo Android.
3. Ao abrir o **ApexLex C1** pela primeira vez e usar a etapa **Speaking**, permita o acesso ao microfone.
