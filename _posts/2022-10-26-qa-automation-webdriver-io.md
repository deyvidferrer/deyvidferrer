---
title: Manual de Instalacion y uso de WebdriverIO 👽👽
tags: [Automation, QA, Tutoriales, Frontend]
style: border
color: primary
description: Aca encontraras toda la informacion necesaria para instalar webdriverIO y como entender la estructura del proyecto y como usarlo.
---

{% include elements/video.html id="eHIsHiaddwk" %}
-------------------------

# Herramienta de Automatización de Frontend tanto para dispositivos Mobiles como paginas Web, con soporte para interactuar con APIs.

Este Framework o marco de trabajo posee la integracion con Cucumber ( BDD, Gherkin )
es una herramienta basada en NodeJS y posee diferentes libreraias integradas y reporteadores  Allure Reports / JUnit Report. Posee soporte para su ejecución local o en entornos en la nube o servicios de device farming como BrowserStack or SauceLabs.

## Tabla de Contenido 

- [# Herramienta de Automatización de Frontend tanto para dispositivos Mobiles como paginas Web, con soporte para interactuar con APIs.](#mobile-and-web-test-automation-framework-with-support-to-interact-with-apis)
  - [Tabla de Contenido](#table-of-contents)
- [Guia de iniciacion](#getting-started)
    - [Pre-requisitos](#pre-requisites)
    - [Automatización Mobile](#mobile-exclusive)
      - [Instalación de Appium](#installing-appium-android-studio)
      - [Configuracion de variables de entorno](#configure-environment-variable)
      - [Creacion de nuevos dispositivos virtuales ( Emuladores ):](#creating-new-virtual-device)
- [Primera Ejecución](#first-time-run)
    - [Ejecutar test por etiquetas / tag @run](#run-tests-by-tag-run)
    - [Generar reportes de Allure luego de la ejecución](#generate-allure-reports-after-an-execution)
- [Estructura del Proyecto](#folders-structure)
  - [App](#app)
  - [Config](#config)
  - [features](#features)
  - [pages](#pages)
  - [stepDefinitions](#stepdefinitions)
  - [commons](#commons)
  - [pipelines](#pipelines)
- [package.json](#packagejson)
- [Page Object Generator (Outdated)](#page-object-generator-outdated)
  - [How to use](#how-to-use)
- [BrowserStack service configuration](#browserstack-service-configuration)
  - [Upload App](#upload-app)
- [SauceLabs service configuration](#saucelabs-service-configuration)
  - [Upload App](#upload-app-1)
  - [Mobile Capabilities for Android](#mobile-capabilities-for-android)
  - [Web Capabilities for **Windows**](#web-capabilities-for-windows)
  - [Web Capabilities for **MacOS**](#web-capabilities-for-macos)
- [Change log](#change-log)
- [Contributing](#contributing)
  - [Commits:](#commits)
- [Process](#process)

# Guia de Iniciacíon
### Pre-requisitos
### Lista de aplicaciones / Herramientas / Software que debe ser instalado
- Git
- Nodejs
- Npm
- Java SDK version 17 o superior
- Android Studio
- Xcode ( en caso de mac )
- Visual Estudio Code
- Plugins VS code
-- Eslint ( Linter )
-- Cucumber
- Appium Server GUI
- Appium Inspector
- Vizor - opcional ( para ver e interactuar con dispositivos locales )
- SCRCPY ( opcion libre para mac )

- Instalar un cliente git [Git Client](https://git-scm.com/downloads/guis) y clonar el proyecto base en mi github
- Instalar la version 14 de Node.js desde el sitio oficial [official website](https://nodejs.org/) o usando [nvm](https://github.com/creationix/nvm) (se recomienda el uso del manejador de versioens NVM).
	-  Si usted instala Node.js desde el sitio oficial asegurese de que el  'Tools for Native Modules' checkbox este habilitado durante la instalacion (No esta activado por default).
- Ir al [official website JDK 1.8 ](https://www.oracle.com/sa/java/technologies/javase/javase-jdk8-downloads.html), go to *Java SE Development Kit* descarga e instala la ultima version disponible.

### Automatización Mobile

#### Instalaccion de Appium

- Instalar android estudio desde la web oficial [official website](https://developer.android.com/studio).
- Versiones mas recientes desde la web oficial [official website](http://appium.io/).
- Las versiones mas recientes de appium estan divididas, es decir, una version para el servidor y otra version para el inspector.
  - [Appium-inspector](https://github.com/appium/appium-inspector/releases)
  - [Appium-server-GUI](https://github.com/appium/appium-desktop/releases)


#### Configuracion de variables de Entorno

##### Windows

1. Click derecho en el icono "Este equipo" ( My computer )
2. Seleccionar "Propiedades" desde el menu desplegable
3. Clickear la opcion de "Configuracion avanzada del sistema"
4. Click "Variables de Entorno"
5. En la seccion de variables de sistema, crea o modifica la variable **"ANDROID_HOME"** y establece la ruta de Android sdk. Por ejemplo:
```
Name  : ANDROID_HOME
Value : C:\Users\USERID\AppData\Local\Android\Sdk
```
6. En la seccion de variables de sistema, crea o modifica la variable **"JAVA_HOME"** y establece la ruta de Android sdk. Por ejemplo:
```
Name  : JAVA_HOME
Value : C:\Program Files\Java\jdk1.8.0_241
```

7. En la seccion de variables de sistema, crea o modifica la variable **"path"** y establece la ruta de Android sdk platform-tools. Por ejemplo:
```
Name  : path
Value : C:\Users\USERID\AppData\Local\Android\Sdk\platform-tools
```
8. En la seccion de variables de sistema, crea o modifica la variable **"path"** y establece la ruta de Android emulator. Por ejemplo:
```
Name  : path
Value : C:\Users\USERID\AppData\Local\Android\Sdk\emulator
```  
#### Creacion de nuevos dispositivos virtuales ( Emuladores ):

- Abrir **Android Studio** ir a: **Tools** -> **AVD Manager** -> **Create Virtual Device...**
- Seleccionar **Nexus 6** - > **Next** -> **API Level 10** -> **Next** -> Luego renombra el dispositivo como Nexus 6 -> **Finish**.

**Lista de dispositivos conectados o disponibles**

Con este comando podremos visualizar la lista de emuladores disponibles en nuestra maquina local.
```

	$ emulator -list-avds

```

**Abrir un emulador**

Podemos abrir un emulador con el comando **emulator** *@device_name* desde la lista de dispositivos disponibles en la maquina local.
Por ejemplo::

```

	$ emulator @Nexus_6

```


# Primera Ejecución

Como root o administrador
### Run tests by tag @run

para instalar las dependencias del proyecto
```console
$ npm install
```

para ejecutar las pruebas en chrome

```console
$ npm run start-web
```

Con un emulador abierto para ejecutar las pruebas mobile en la maquina local.

```console
$ npm run start-mobile
```

Exclusivo para integracion con **BrowserStack**: Con las llaves de usuario de tu cuenta de browserstak debes configurarlo en la ruta ubicada en: config\wdio.mobile.bs.conf.ts.

```console
$ npm run start-mobile-bs
```
Exclusivo para integracion con **SauceLabs**:Con las llaves de usuario de tu cuenta de Saucelab debes configurarlo en la ruta ubicada en: config\wdio.mobile.sl.conf.ts o config\wdio.chrome.sl.conf.ts.

Ejecución mobile en Android

```console
$ npm run start-mobile-sl
```
Web excecution

```console
$ npm run start-web-sl
```

### Como generar el reporte de la automatización en Allure-Report

```console
$ npm run clean-report
```

To Open an Allure Report

```console
$ npm run open-report
```
# Estructura del Proyecto

  

## App

En esta carpeta necesitamos tener el apk. o .ipa (para ios)


## Config


Tenemos los siguientes archivos:
- **wdio.chrome.conf.ts**:  with configurations to run tests on Chrome.
- **wdio.mobile.conf.ts**:  with configurations to run tests on a local mobile Android Device.
- **wdio.mobile.bs.conf.ts**: with configurations to run mobile tests on a BrowserStack mobile Android Device.
- **wdio.mobile.sl.conf.ts**: with configurations to run mobile tests on a SauceLabs mobile Android Device.
- **wdio.multi-browser.docker.conf.ts**: with configurations to run web tests on a Selenium Grid local docker image in Chrome, Firefox and MicrosoftEdge.

Configuration and parameters:
- **specs**: List of cucumber features to execute.
-  **reporters/reporter options:** Specifies the reporter to use, we use Allure Report.
-  **host/port/path:** Configuration of Appium server.
-  **maxInstances:** Maximus instances per execution, by default we must execute with 1 for mobile.
- **waitforTimeout/connectionRetryTimeout:** Parameters to set maximus time out.

-  **capabilities:** set of options related to device, platform, device name.
   - **browserName**: 'chrome' for web, empty for mobile.
   - **maxInstances**: To define the maximum amount to run parallel tests.
   - **platformName**: Android/iOS.
   - **app:** './app/**Android-NativeDemoApp-0.4.0.apk**'*.
   - **appPackage:**: Package name of the app.
     -  Field: **manifest.package** of AndroidManifest.xml file of apk.
   - **appActivity:**: Name of the first view or activity that open when we open our app.
     - Field: **manifest.activity** (**android:name**) of AndroidManifest.xml file of apk.
   - **platformVersion**: Associated to API version, Android version. **Por ejemplo:**: 10.
   - **deviceName:** Identifier of the device. **Por ejemplo:**: Nexus 6 of default value: emulator-5554.
   - **automationName:** We always use: **UiAutomator2** for Android.
-  **capabilities: (BrowserStack)** set of options related to device, platform, device name.
   - **appium:app**: **app_url** value that we get after uploading an app to BrowserStack, **Por ejemplo:**: *'bs://dbf4840f740e91f9d2e546479afd820ebc5a6e56'*.
   - **appium:deviceName**: Identifier of the device. **Por ejemplo:**: Google Pixel 3.
   - **appium:platformVersion**: Associated to API version, Android version. **Por ejemplo:**: 10.
   - **appium:automationName**: We always use: **UiAutomator2** for Android.
-  **capabilities: (SauceLabs)** set of options related to device, platform, device name.
   - **app**: **storage:filename=[APK_NAME]** name of apk, **Por ejemplo:**: *'storage:filename=Android-NativeDemoApp-0.4.0.apk'*.
   - **appium:deviceName**: Identifier of the device. **Por ejemplo:**: *'Samsung_Galaxy_S9_free'*.
   - **platformName**: Platform where the application will be tested. **Android** for android.
   - **appium:platformVersion**: Associated to API version, Android version. **Por ejemplo:**: *'10.0'* .
   - **appium:automationName**: We always use: **UiAutomator2** for Android.
- **services:**
  - For web we use **chromedriver**.
  - For mobile we use **appium** service.
  - To use **BrowserStack** service we use: **browserstack** and *browserstackLocal* property in true.
  - To use **SauceLab** service we use: **sauce**.

- **logLevel:** We can use debug to log all the actions on appium or silent mode only to log final results.
- **framework/cucumberOpts:** We use Cucumber framework to execute.
  - On **cucumberOpts.require** we specify the steps of .ts files to exectute of the folder **stepDefinitions**.

**List of hooks of Cucumber we use:**

**IMPORTANT:** All hooks must be implemented using async/await.

**Examples**:

```Typescript
    /**
     * Runs after a Cucumber step
     */
    afterStep: async function () {
        await browser.takeScreenshot();
    },
```

```Typescript
    /**
     * Runs after a Cucumber scenario
     */
    afterScenario: async function () {
        await browser.closeApp();
        await browser.reset();
    },
```

- **onPrepare:** Actions to to before de begin of the excecution.
- **afterCommand:** Actions to do after a command is executed, Por ejemplo: after a click we want to take a screenshot.
- **onComplete:** Actions to do after all test had been executed.
- **beforeScenario:** Actions to do before a scenario is executed. Por ejemplo:: we use **browser.reset();** to prepeare the initial conditions.
- **afterScenario:** Actions to do after a scenario was executed. Por ejemplo:: **browser.closeApp()**; to close a mobile app. **browser.reloadSession()**; to reload a web browser.

We can use differents hooks, please visit [WebDriver IO Hooks](https://webdriver.io/docs/options.html#hooks) for more details.

## features

On this folder we have the list of cucumber .feature files group by functionalities.

## pages

On this folder we have the definitions of each view of our application using  Page Object Model pattern to define using Typescript.

The basic structure of each POM must have:
Filename: **viewToModelPO.ts**

```Typescript
import Page from './page';

/**
 * sub page containing specific selectors and methods for a specific page
 */
class LoginPage extends Page {
    /**
     * define selectors using getter methods
     */
    get inputUsername() { return $('#username') }
    get inputPassword() { return $('#password') }
    get btnSubmit() { return $('button[type="submit"]') }

    /**
     * a method to encapsule automation code to interact with the page
     * e.g. to login using username and password
     */
    async login(username: string, password: string) {
        await (await this.inputUsername).setValue(username);
        await (await this.inputPassword).setValue(password);
        await (await this.btnSubmit).click();
    }

    /**
     * overwrite specifc options to adapt it to page object
     */
    open() {
        return super.open('login');
    }
}

export default new LoginPage();

```

## stepDefinitions

On this folder we have to create the steps per functionality out set of scenarios defined on our .feature files.

**Por ejemplo:**:
  We have an **login.feature** file with this definition to execute with a set of 2 groups of data:

```Gherkin
@run @web
Feature: The Internet Guinea Pig Website

  @login_web
  Scenario Outline: As a user <username>, I can log into the secure area

    Given I am on the login page
    When I login with <username> and <password>
    Then I should see a flash message saying <message>

    Examples:
      | username | password             | message                        |
      | tomsmith | SuperSecretPassword! | You logged into a secure area! |
      | foobar   | barfoo               | Your username is invalid!      |
```

For each **Given**, **When**, **Then** step we have to create a step to do the behavior that happen on the application.

**Por ejemplo::**
On our **loginSteps.ts** file, we will import our pages defined to create a test.

```Typescript
import { Given, Then, When } from '@cucumber/cucumber';
import LoginPage from '../../pages/web/login.page';
import Page from '../../pages/web/page';
import SecurePage from '../../pages/web/secure.page';


const pages: { [key: string]: Page } = { ["login"]: LoginPage };

Given(/^I am on the (\w+) page$/, async (page: string) => {
    await pages[page].open();
});

When(/^I login with (\w+) and (.+)$/, async (username: string, password: string) => {
    await LoginPage.login(username, password);
});

Then(/^I should see a flash message saying (.*)$/, async (message: string) => {
    await expect(SecurePage.flashAlert).toBeExisting();
    await expect(SecurePage.flashAlert).toHaveTextContaining(message);
});

```

## commons

On this folder we have a few utility classes Por ejemplo:: **constants.ts**, **utils.ts**.
  
## pipelines

We have some examples of pipelines for both local and cloud execution by using Browserstack integration:

- Azure
- GitHub

Recomendations: copy yml files to the root of project.

# package.json

Scripts desctiptions:


- `clean`: Delete all files generated on each execution like reports.
- `start-mobile`: with this script we only run the **scenarios** or **features** with **@run** tag. on every .feature file that we have on our **wdio ./config/wdio.mobile.config.ts** on field specs and have to be releated to the stepDefinition files on cucumberOpts.require from the same config file.
- `start-mobile-bs`: *exclusive to use **BrowserStack service***. With this script we only run the **scenarios** or **features** with **@run** tag. on every .feature file that we have on our **wdio ./config/wdio.mobile.bs.config.ts** on field specs and have to be releated to the stepDefinition files on cucumberOpts.require from the same config file.
- `start-mobile-sl`: *exclusive to use **SauceLab service***. With this script we only run the **scenarios** or **features** with **@run** tag. on every .feature file that we have on our **wdio ./config/wdio.mobile.bs.config.ts** on field specs and have to be releated to the stepDefinition files on cucumberOpts.require from the same config file.
- `start-web`: with this script we only run the **scenarios** or **features** with **@run** tag. on every .feature file that we have on our **wdio ./config/wdio.chrome.config.ts** on field specs and have to be releated to the stepDefinition files on cucumberOpts.require from the same config file.
- `start-web-docker`: with this script we run on Chrome, Firefox and MicrosoftEdge on a **Selenium Grid Docker image** all the **scenarios** and **features**. on every .feature file that we have on our **wdio ./config/wdio.multi-browser.docker.config.ts** on field specs and have to be releated to the stepDefinition files on cucumberOpts.require from the same config file.
- `clean-report`: We generate the allure reports after an excecution.
- `open-report`: We can open de allure reports.
- `version`: We can auto-generate release note of our changes.


# Page Object Generator (Outdated)

Generate *PO.ts files to have our Page Object Model class


## How to use

Open utils/generator/generator.ts file and set the list the elements that will be nessesary for our scripts.

Por ejemplo:: Header Page

```Typescript
import { Util } from './util';

/**
 * on fieldList we define the names of our UI Elements that we will model in our POM classes
 */
const fieldList: string[] = [
    'menu_side',
    'title_header',
    'logout_btn',
];

const util: Util = new Util();
util.generatePageObjectFile(fieldList);

```

Run generator

```
npm run generate-po
```

It will generate viewPO.ts file for page layer. We only need to change class name and fill the path to locale the elements.

Por ejemplo::

```
--------------------------------------------
poGenerated/viewPO.ts
--------------------------------------------
```

```Typescript
export class ViewPO {

    private menu_side: string;
    private title_header: string;
    private logout_btn: string;

    constructor() {
        this.menu_side = '#menu_side';
        this.title_header = '#title_header';
        this.logout_btn = '#logout_btn';
    }

    public validatePage(): void {
        browser.$(this.menu_side).waitForExist();
        browser.$(this.title_header).waitForExist();
        browser.$(this.logout_btn).waitForExist();
    }

    public menuSide(): WebdriverIO.Element {
        browser.$(this.menu_side).waitForExist();
        return browser.$(this.menu_side);
    }

    public titleHeader(): WebdriverIO.Element {
        browser.$(this.title_header).waitForExist();
        return browser.$(this.title_header);
    }

    public logoutBtn(): WebdriverIO.Element {
        browser.$(this.logout_btn).waitForExist();
        return browser.$(this.logout_btn);
    }

}

```

# BrowserStack service configuration

If you don't have an account but you want to try this service, firstly you need to create an **ACCESS_KEY**, that is **BROWSERSTACK_USERNAME** and **BROWSERSTACK_ACCESS_KEY**.

To create an account please go to [the official website](https://www.browserstack.com) to sign up.

When you are logged in, go to profile and click on *"Go to Dashboard"* to get username and access key.

This credentials have to be in config file, Por ejemplo: in: config\wdio.mobile.bs.conf.ts y fields: user and key entry respectively, we need to define the enviroment variables.

We need to create a local .env file with something like that:

BROWSERSTACK_USERNAME=OUR_BROWSERSTACK_USERNAME
BROWSERSTACK_ACCESS_KEY=OUR_BROWSERSTACK_ACCESS_KEY

## Upload App

An API to upload the App you want to test on the BrowserStack servers for interactive app testing. Use it to upload via CLI or automation scripts.

```console
curl -u "BROWSERSTACK_USERNAME:BROWSERSTACK_ACCESS_KEY" -X POST "https://api-cloud.browserstack.com/app-automate/upload" -F "file=@/path/to/app/file/Application-debug.apk"
```

Example:

**BROWSERSTACK_USERNAME**=sdetbaufest_zJFoTm
**BROWSERSTACK_ACCESS_KEY**=yMT1Mg8rXX3MnH1bvqFC

```console
curl -u "sdetbaufest_zJFoTm:yMT1Mg8rXX3MnH1bvqFC" -X POST "https://api-cloud.browserstack.com/app-automate/upload" -F "file=@C:/baf/app/Android-NativeDemoApp-0.4.0.apk"
```

**Note:**

```console

1. Supported file formats are .apk and .aab for Android apps and .ipa for iOS apps.
2. App upload will take few seconds to about a minute depending on the size of your app. Do not interrupt the curl command until you get the response back.
3. If you upload an iOS app, we will resign the app with our own provisioning profile to be able to install your app on our devices during test execution.
4. We will delete the uploaded app after 30 days from the date of upload.
5. Max file size supported is 1 GB.
```

After executing this command you will get the **app_url** value:

```json
{"app_url":"bs://f21b5b310fc6684c6f9dbd24d2549c7a586cde85"}
```

That **app_url** value is needed to add to capabilities in the config file to have a reference of our app to be automated.

```Typescript
    capabilities: [{
        "appium:app": 'bs://f21b5b310fc6684c6f9dbd24d2549c7a586cde85',
        "appium:deviceName": 'Google Pixel 3',
        "appium:platformVersion": '10.0',
        "appium:automationName": 'UiAutomator2',
        "platformName": "Android",
    }],
```

# SauceLabs service configuration

If you don't have an account but you want to try this service, firstly you need to create an **ACCESS_KEY**, that is **SAUCELAB_USER** and **SAUCELABS_KEY**.

To create an account please go to [the official website](https://saucelabs.com/) to sign up.

When you are logged in, go to "ACCOUNT" > "user settings". You can get USER NAME and ACCESS KEY.

This credentials have to be in config file, Por ejemplo: in: config\wdio.mobile.ls.conf.ts y fields: user and key entry respectively. 

## Upload App

An API to upload the App you want to test on the SauceLabs servers for interactive app testing. Use it to upload via CLI or automation scripts.

```console
$ curl -u $SAUCE_USERNAME:$SAUCE_ACCESS_KEY -X POST -H "Content-Type: application/octet-stream" \
"https://us-east-1.saucelabs.com/rest/v1/storage/$SAUCE_USERNAME/$APP_NAME?overwrite=true" --data-binary @path/to/your_file_name
```

Example:

**SAUCELAB_USER**=oauth-dotajoseqp92-c5c11
**SAUCELAB_KEY**=c3093141-e805-4e40-bcaa-638b490ae124

```console
$ curl -u oauth-dotajoseqp92-c5c11:c3093141-e805-4e40-bcaa-638b490ae124 -X POST -H "Content-Type: application/octet-stream" \
"https://us-east-1.saucelabs.com/rest/v1/storage/$SAUCE_USERNAME/$APP_NAME?overwrite=true" --data-binary @path/to/your_file_name

```

**Note:**

```console

1. Supported file formats are .apk and .aab for Android apps and .ipa for iOS apps.
2. App upload will take few seconds to about a minute depending on the size of your app. Do not interrupt the curl command until you get the response back.
3. If you upload an iOS app, we will resign the app with our own provisioning profile to be able to install your app on our devices during test execution.
4. We will delete the uploaded app after 60 days from the date of upload.
5. Max file size supported is 1 GB.
```

The **app** value is needed to add to capabilities in the config file to have a reference of our app to be automated, we can use the filename.


## Mobile Capabilities for Android

```Typescript
    capabilities: [{
        app: 'storage:filename=Android-NativeDemoApp-0.4.0.apk',
       deviceName: 'Samsung_Galaxy_S9_free', //  Real Device: 'Samsung_Galaxy_S9_free'
       platformVersion: '10.0',
       automationName: 'UiAutomator2',
       platformName: 'Android',
    }],
```
## Web Capabilities for **Windows**

```Typescript
    capabilities: [{
        browserName: 'chrome', // chrome, firefox, MicrosoftEdge, internet explorer
        platformName: 'Windows 10',
        browserVersion: 'latest',
    }],
```

## Web Capabilities for **MacOS**

```Typescript
    capabilities: [{
        browserName: 'safari',
        platformName: 'macOS 11.00',
        browserVersion: '14',
    }],
```

# Change log

Run "version" command to create the change log with details of changes that we made on each sprint.

```console
npm run version
```

This will create a HISTORY.md file.

# Contributing


## Commits:


For our commits message we use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification which provides an easy set of rules for creating an explicit commit history adding readable meaning to commit messages.

  
> See [Conventional Commits full specification](https://www.conventionalcommits.org/en/v1.0.0/#specification).

  

#  Process

1. Fork from `master`/`main` branch.

2. Create your branch with the reference of the associated ticket id of your project management tool like Jira, Azure DevOps  (`git checkout -b type/####-Description`)

3. Commit your changes (`git commit -am 'feat(feature):'`)

4. Push to the branch (`git push origin type/####-description`)

5. Create new Pull Request