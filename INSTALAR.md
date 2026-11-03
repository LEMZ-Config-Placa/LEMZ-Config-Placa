# LEMZ Config Placa — como gerar e instalar o APK

App Android nativo (Kotlin + Jetpack Compose). Funciona 100% offline.
Nome: LEMZ Config Placa • Versão atual: 1.0.0 (versionCode 1) • Android 10 ou superior.

## Caminho A — Android Studio (grátis)
1. Instale o Android Studio (developer.android.com/studio).
2. File > Open > escolha a pasta LemzConfigPlaca. Aguarde o Gradle sincronizar (precisa de internet nessa etapa).
3. Menu Build > Build Bundle(s) / APK(s) > Build APK(s).
4. O arquivo fica em: app/build/outputs/apk/debug/app-debug.apk
   (para a versão release: Build > Generate Signed App Bundle / APK não é necessário; use no terminal `gradlew assembleRelease`
   ou o menu Build Variants > release. APK em app/build/outputs/apk/release/).

## Caminho B — Sem instalar nada no PC (GitHub Actions, grátis)
1. Crie uma conta gratuita no github.com e um repositório novo (pode ser privado).
2. Envie TODO o conteúdo da pasta LemzConfigPlaca (inclusive as pastas ocultas .github e keystore).
3. Aba Actions > "Build APK" > Run workflow. Em ~5 minutos aparece o artefato "LEMZ-Config-Placa-APK".
4. Baixe, descompacte o .zip e você terá o .apk.

## Instalar no Moto G45 5G
1. Envie o .apk para o celular (cabo USB, Google Drive, WhatsApp para você mesmo…).
2. Toque no arquivo. Se pedir, permita "Instalar apps desconhecidos" para o app que abriu o arquivo.
3. Instale e abra "LEMZ Config Placa" (ícone LEMZ na tela inicial).
4. Ligue o NFC: Configurações > Dispositivos conectados > Preferências de conexão > NFC.
5. Na gravação, encoste a plaquinha na parte de trás do celular (região da câmera) e mantenha parada.

## Atualizar sem perder dados
1. Em gradle.properties aumente APP_VERSION_CODE (ex.: 1 -> 2) e ajuste APP_VERSION_NAME (ex.: 1.1.0).
2. Gere o APK novamente e instale POR CIMA do app existente (não desinstale).
3. Estoque, clientes e histórico ficam no banco local e são preservados, desde que:
   - o arquivo keystore/lemz-release.jks seja o mesmo (FAÇA BACKUP DELE; sem ele, o Android recusa a atualização);
   - mudanças futuras no banco usem Migration do Room (nunca fallbackToDestructiveMigration).
4. Backup: aba Estoque > "Fazer backup" gera um arquivo .json (envie para o Drive/WhatsApp). "Restaurar backup" importa o arquivo e mescla com o estoque atual. Faça backup antes de trocar de celular ou desinstalar. "Exportar CSV" serve para planilha.

## Observação de segurança
A senha do keystore (lemz1234) está no build.gradle.kts para facilitar. É adequado para uso interno/pessoal;
não publique esse repositório como público se quiser manter a assinatura só sua.
