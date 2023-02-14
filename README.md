# Guida da zero per programmare un gioco su PlayDate

## Indice
1. [Installazione dell'SDK](#install-SDK)
2. [Configurare il sistema](#conf-system)
3. [Configurazione di Visual Studio Code](#conf-VSC)
4. [Configurare il progetto (file di contorno)](#conf-file-secondary)
5. [Cartella '.vscode'](#conf-vscode-folder)
6. [Configurare il progetto (core)](#conf-file-primary)
7. [Buildare ed eseguire il gioco](#build-game)
8. [Debug](#debug)



### install-SDK
***
* Scaricare l'SDK playdate
* Installarlo magari cambiando il percorso che di default è nella cartella user
<br />(Il path è stato modificato perché ci sono stati problemi con i permessi)
* Mettere "C:\Program Files (x86)\PlaydateSDK"
* Se si è scelto di installare in una cartella diversa da quella dell'utente, abilitare i permessi di 'everyone' alla cartella 'PlaydateSDK

### conf-system
***
**Aggiungere il percorso dell'SDK alle variabili di ambiente**
* Propietà del sistema -> Avanzate -> Varaibili d'ambiente:
1. Variabili di sistema -> Doppio click su 'Path' -> In coda inserire 'C:\PERCORSO_SCELTO_SDK\PlaydateSDK\bin'
2. Variabili di sistema -> Nuova:
<br />- Nome variabile: PLAYDATE_SDK_PATH
<br />- Valore variabile: C:\PERCORSO_SCELTO_SDK\PlaydateSDK

### conf-VSC
***
* Installare le seguenti estensioni:
1. Lua: https://marketplace.visualstudio.com/items?itemName=sumneko.lua
2. Lua-plus: https://marketplace.visualstudio.com/items?itemName=jep-a.lua-plus

### conf-file-secondary
***
* Creazione cartella di configurazione '.vscode'
<br />(Inseriremo i file di configurazione per VSCode del progetto)
* Creazione cartella 'builds'
<br />(In questa carella verranno inseriti i progetti compilati (file da dare in pasto alla console)
* Creazione file '.gitignore' (se si usa GIT)
<br />Unica riga del file, (cartella da escludere): builds/*.pdx

### conf-vscode-folder
***
* Nella cartella '.vscode' creare il dile 'settings.json':
<br />{
<br /> "Lua.runtime.version": "Lua 5.4",
<br /> "Lua.diagnostics.disable": ["undefined-global", "lowercase-global"],
<br /> "Lua.diagnostics.globals": ["playdate", "import"],
<br /> "Lua.runtime.nonstandardSymbol": ["+=", "-=", "*=", "/="],
<br /> "Lua.workspace.library": ["$PLAYDATE_SDK_PATH/CoreLibs"],
<br /> "Lua.workspace.preloadFileSize": 1000,
<br /> "playdate.sdkPath": "$PLAYDATE_SDK_PATH/PlaydateSDK"
<br />}

### conf-file-primary
***
* Come da guida SDK conviene strutturare le cartelle in questo modo
<br /> [myProjectName]/
<br />  source/
<br />   main.lua
<br />   ...and other .lua files
<br />   images/
<br />    [myImageFile1].png
<br />    [myImageFile2].png
<br />    ...and so on
<br />   sounds/
<br />    [myAudioFile1].wav
<br />    [myAudioFile2].mp3
<br />    ...and other ADPCM- or MP3-formatted files
<br />  support/
<br />   Project files including Photoshop assets, project outlines, etc.
* In aggiunta alle cartelle predefinite, sullo stesso livello della carella 'source'
<br />Inseriremo i file/cartelle di controno specificati sopra
* All'interno della cartella 'source' è necessario creare un file di configurazione 'pdxinfo'
<br />    name=Your game's name
<br />    author=Your name
<br />    description=Description of your game
<br />    bundleID=com.yourname.yourgame
<br />    version=0.1
<br />    buildNumber=0001
<br />    imagePath=/images
<br />    launchSoundPath=/sounds

### build-game
***
* Buildare il gioco:
<br />Da terminale: 'pdc source builds\nome_build'
<br />Verrà creato un file all'interno della cartella builds, da dare in pasto al simulatore
* Avviare il simulatore: C:\PERCORSO_SCELTO_SDK\PlaydateSDK\bin\PlaydateSimulator.exe

### debug
***
Inserire info successivamente
