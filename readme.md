### Plantilla inicio rapaido
## Estructura del código 
    /features/pageobjects: Contiene un archivo .js para cada página del proyecto. En cada archivo, se encuentran las funciones / elementos que se utilizarán en la automatización.

    /features/steps-definitions: Contiene los steps de cada prueba que se ejecutará.

    /features: Contiene los archivos .features del proyecto, donde se describirán en lenguaje Gherkins las pruebas.

    /node_modules: Librerías necesarias para correr la automatización. Si no existe este folder correr "npm install" previo a la ejecución.

    /reports: se alojarán en formato .json los resultados de las pruebas.

    .env: Contiene las keys necesarias para la ejecución de la prueba.

    .gitignore: Archivos ignorados para los commits.

    database.csj: Permite la integración y ejecución de querys con una base de datos.

    package.json: Información del proyecto y librerías a utilizar.

    package-lock.json: Se autogenera al iniciar proyecto con npm install

    readme.md: Ayuda para configuración y ejecución de pruebas.

    qmetry-update.cjs: Contiene la lógica para actualizar los resultados de las pruebas y subirlas a QMetry. Posterior a la prueba ejecutar "node upload.js"

    wdio.conf.js: Configuración de WebDriverIo

**Clonar Proyecto**
1. Utilizar el comando "git clone <url>" para clonar el proyecto en local.
2. ejecutar "cd qa-sugus"

**Instalar Dependencias**
1. Una vez clonado el repositorio, instalar dependencias del proyecto ejecutando "npm install"

**Configurar variables de entorno**
1. Configurar las variables de entorno. Generar l archivo ".env" en el nivel raíz del directorio (a la misma altura que el wdio.conf.js)


    > #### QMETRY PARAMS ####
    > QA_QMETRY_APIKEY='apiKey. Reemplazar por el de QMETRY'
    > QA_QMETRY_URL='randstadqa.atlassian.net'
    > QA_QMETRY_IMPORT_URL='https://qtmcloud.qmetry.com/rest/api/automation/importresult'
    > QA_QMETRY_KEY_TESTRUN='QK-TR-35' 
    > QA_QMETRY_FOLDERID='788060'
    > ##### DB PARAMS #####
    > ##### Para windows no es necesario usar DB_USER y DB_PASSWORD. #####
    > DB_USER=""
    > DB_PASSWORD=""
    > DB_HOSTNAME="hostDB"
    > DB_NAME="nombreDB"
    > DB_MAX_RECORDS="10"
  
    

**Correr automatización**
1. Verificar conectividad a la VPN de Randstad
2. Ejecutar todas las pruebas
    > npm test
3. En caso de ejecutar una suite en particular, verificar el archivo wdio.conf.js la sección de Suites y corroborar aquella que necesites ejecutar. A continuación ejecutar "npm run wdio wdio.conf.js --suite nombre-de-la-suite"

    ***Nota:*** También puedes agregar "scripts" al package.json para facilitar la ejecución de comandos.

4. Generar reporte allure:
    > npm run allure-generate
5. Abrir reporte de allure:
    > npm run allure-open

**Actualización de resultado en QMETRY**
1. Una vez ejecutada la prueba automatizada, se puede actualizar la información en QMETRY ejecutando:
    > "npm run qmetry". 

    ***Es importante verificar el archivo .env que estén bien configuradas las siguientes entradas:***

    > QA_QMETRY_APIKEY='apiKey. Reemplazar por el de QMETRY'
    > QA_QMETRY_URL='randstadqa.atlassian.net'
    > QA_QMETRY_IMPORT_URL='https://qtmcloud.qmetry.com/rest/api/automation/importresult'
    > QA_QMETRY_KEY_TESTRUN='Pegar la key del Test Run'
    > QA_QMETRY_FOLDERID='pegar FolderID correspondiente al TestRun o Test Cycle'

**Iniciar proyecto**
>Comenzaremos la configuración de nuestro entorno de trabajo iniciando con el comando: 

npm init

El sistema nos irá solicitando que configuremos las propiedades de nuestro proyecto.Verificamos que el paso fue ejecutado correctamente comprobando que exista en la carpeta del proyecto un nuevo archivo llamado package.json
>Realizaremos la instalación de nuestro framework de automatización WebdriverIO, ejecutando el siguiente comando por consola:

npm install webdriverio --save

>Instalaremos el cliente de Web Driver ejecutando: 

npm install @wdio/cli --save

>Procedemos a instalar nuestra librería para Reporting en Allure:

npm install @wdio/allure-reporter --save && npm i allure-commandline

>Instalación de AutoCompletion para VSC (Visual Studio Code) que nos facilitará y servirá de ayuda a la hora de comenzar a desarrollar las automatizaciones. Para ello ejecutar:

 npm install @types/webdriverio --save-dev

>Modificaremos el package.json para que podamos correr nuestras pruebas con el comando: npm start. Para ello, es necesario abrir el package.json y modificar la sección de scripts:

		"scripts": {
"start": "npx wdio run ./wdio.conf.js"
}

>Comienzo de un nuevo proyecto. Ya dentro de VSC (Visual Studio Code) y posicionados en la carpeta de trabajo, ejecutaremos el comando de inició de proyecto con webdriverIO: 

npm init wdio

>Ahora ya podemos ejecutar el ejemplo de prueba automatizada que genero WebdriverIO, ejecutando :

npm run wdio

>
**GLOSARIO**
Appium
Appium es una herramienta open-source para la automatización de aplicaciones nativas e híbridas en las plataformas móviles iOS y Android
CMD
Terminal de Windows
GIT
Es un sistema maduro de control de versiones y revisiones de código abierto.
NPM
Las siglas npm vienen de Node Package Module. Es el sistema de gestión de paquetes por defecto para Node.js. Nos permite instalar y actualizar dependencias de nuestros proyectos que corren en Node.
NPX
Ejecutor de paquetes de Node. Al igual que el comando NPM nos permite ejecutar paquetes de node. Tiene cómo diferencia que no es necesario instalar la dependencia para ejecutarla con este comando.
Postman
Postman es una plataforma que permite y hace más sencilla la creación y el uso de APIs. Esta herramienta es muy útil para programar porque da la posibilidad hacer pruebas y comprobar el correcto funcionamiento de los proyectos
uiautomator2
Librería nativa de Android que nos permite ejecutar pruebas automatizadas para este sistema operativo.
VSC
Visual Studio Code
Visual Studio Code
Editor de texto. De los más utilizados para programación en distintos lenguajes.
Variable de Entorno
Una variable de entorno es una variable dinámica que puede afectar al comportamiento de los procesos en ejecución en un ordenador.
WebdriverIO
WebdriverIO es un marco de trabajo o framework “todo en uno” que nos permite ejecutar y automatizar pruebas de Aplicaciones móviles nativas, web o hibridas.
xcuitest
Ésta es una librería nativa compatible con Apple, que nos permite ejecutar nuestras pruebas automatizadas en aplicaciones para iOS.

**UTILES**
>Correr un solo feature:

npx wdio run ./wdio.conf.js --spec .\features\editarpais.feature

>Actualizar Chormedriver:

npm install chromedriver@latest --force

>Saltar un feature

@skip

>Clonar un repositorio:
en terminal
git clone y el codigo del repo
git clone https://github.com/********.git

>Actualizar dependencias
Para la actualización de dependencias utilizamos npm-check, una herramienta que podemos instalar ejecutando:
npm install -g npm-check
Para correr npm-check, el comando que utilizaremos es: npm-check -u
npm-check realizará un control de las dependencias del proyecto y nos retornará el listado de Patch update, minor version update or major version updates que tenemos disponibles

>BDD, Gherkins y Cucumber
npm install @wdio/cucumber-framework@8.24.0 --save    


>Github
git init

git add .

git commit -m "first commit"

git remote add origin https://github.com/NOMBRE_USUARIO/NOMBRE_PROYECTO.git

git push -u origin master
