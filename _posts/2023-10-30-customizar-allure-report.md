---
title: Como Customizar un Reporte en ALLURE REPORT y Playwright 👽👽
tags: [Automation, QA, Tutoriales, Frontend, Playwright, Allure]
style: border
color: primary
description: Aca encontraras toda la informacion necesaria para customizar un reporte en Allure y aplicar los colores y el branding de tu empresa.
---

{% include elements/video.html id="o-Je28o4rl8" %}
-------------------------

# Personalización de Informes Allure en Windows con el Plugin Custom Logo

Los informes de Allure son una poderosa herramienta para visualizar y analizar los resultados de las pruebas en un formato atractivo y fácil de entender. Puedes llevar tus informes un paso más allá personalizándolos con tu propio logotipo utilizando el plugin `custom-logo-plugin`. En este artículo, te guiaré a través del proceso de personalización de informes Allure en un entorno Windows.

## Requisitos Previos

Antes de comenzar, asegúrate de tener instalado lo siguiente:

1. **Java Development Kit (JDK)**: Asegúrate de tener JDK instalado en tu sistema. Puedes descargarlo desde [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).

2. **Maven**: Si aún no lo tienes, puedes descargar y configurar Maven siguiendo la [documentación oficial](https://maven.apache.org/download.cgi).

3. **Allure CLI**: Instala la línea de comandos de Allure utilizando el siguiente comando:

   ```
   npm install -g allure-commandline
   ```

## Paso 1: Crear una Carpeta para el Logotipo

Crea una carpeta en tu proyecto que contenga tu logotipo personalizado. Asegúrate de que el logotipo tenga un nombre descriptivo, por ejemplo, `custom-logo.png`.

## Paso 2: Configurar el Plugin `custom-logo-plugin`

Para personalizar el informe Allure con tu logotipo, necesitas configurar el plugin `custom-logo-plugin`. Puedes hacerlo agregando una dependencia en tu archivo `pom.xml`:

```xml
<dependencies>
    <dependency>
        <groupId>ru.yandex.qatools.allure</groupId>
        <artifactId>allure-custom-logo-plugin</artifactId>
        <version>2.10</version>
    </dependency>
</dependencies>
```

Si estas en Playwright puedes editar el archivo allure.yml que se encuentra en "npm/node_modules/allure-commandline/dist/config/allure.yml"

```yml
plugins:
  - junit-xml-plugin
  - xunit-xml-plugin
  - trx-plugin
  - behaviors-plugin
  - packages-plugin
  - screen-diff-plugin
  - xctest-plugin
  - jira-plugin
  - xray-plugin
  - custom-logo-plugin
```

## Paso 3: Configurar la Ruta del Logotipo

A continuación, debes configurar la ubicación de tu logotipo en el archivo `allure.properties`. Si no tienes este archivo, créalo en la raíz de tu proyecto.

```properties
allure.custom-logo-plugin.logoPath = path/to/your/custom-logo.png
```

Reemplaza `path/to/your/custom-logo.png` con la ruta relativa a tu logotipo en el proyecto.

### Agregar Estilos y colores y tambien puedes modificar el logo en esta ruta

Puedo modificar el archivo "styles.css" ubicado dentro "allure-commandline/dist/plugins/custom-logo-plugin/static/styles.css"

Puedes copiar los estilos que te dejo como referencia:

```css

.side-nav__brand {
  background: url('custom-logo.svg') no-repeat left center !important;
  height: 100px;
  Background-size: contain !important;
  margin-left: 15px;
  width: 70%;
}

.side-nav__brand span {
  display: none
}

.link {
  color: #00beff;
  transition: color .15s ease-out;
  text-decoration: none;
}

.side-nav {
  background: #1b1f25;;
}

/* .side-nav__brand:after {
  content: "VMETRIX - AUTOMATION REPORT";
  width: fit-content;
  height: auto;
  margin: 0 auto;
  block-size: fit-content;
  font-size: 0.8vw;
  Margin-left: 3px;
} */

.app__content {
  position: relative;
  flex: 1;
  overflow: auto;
  background-color: #190d41;
  background: url('background.png') no-repeat left center !important;
  background-size: cover !important;
}

.island {
  background: #1b1f25;
  color: #fff;
  border: 1px solid #190d41;
  padding: 16px 16px 0;
  box-shadow: 0px 3px 12px -1px rgba(0, 0, 0, 0.26), 0px 2px 4px -1px rgba(0, 0, 0, 0.16);
  border-radius: 3px;
}

.table__row {
  border-bottom: 1px solid #fff;
  text-decoration: none;
  color: #fff;
}

.side-by-side {
  background-color: #fff;
}

.side-nav__link {
  white-space: nowrap;
}
.side-nav__collapse, .side-nav__link {
  color: #00beff;
}

.chart__caption {
  fill: white;
}

.chart__fill_status_passed {
  fill: #7dff00;
}

.chart__fill_status_failed {
  fill: #ff2500;
}

.bar__fill_status_failed {
  background: #ff2500;
}

.bar__fill_status_passed {
  background: #7dff00;
  color: #1b1f25;
}

.bar__fill_status_skipped {
  background: #aaa;
  color: #1b1f25;
}

.widget__subtitle {
  color: #00beff;
}
```

## Paso 4: Generar el Informe Allure

Ahora, puedes generar el informe Allure después de ejecutar tus pruebas. Utiliza el siguiente comando en la línea de comandos:

```bash
mvn clean test
allure serve
```

Esto generará un informe Allure y abrirá una ventana del navegador con tu logotipo personalizado en la parte superior de la página.

## Conclusión

Personalizar tus informes Allure con tu propio logotipo es una forma sencilla de hacer que tus informes sean más atractivos y representativos de tu marca. Siguiendo estos pasos en un entorno Windows y utilizando el plugin `custom-logo-plugin`, puedes lograr fácilmente este nivel de personalización.

¡Ahora tienes informes Allure personalizados que se destacan con tu propio logotipo en Windows!