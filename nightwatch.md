## Nightwatch.js

### End-to-end testing

C'est un type de test fonctionnnel qui permet de contrôler le comportement général d'une application sur un support browser.
En complément des tests unitaires pour tester le code.

Nightwatch s'appuie sur l'outil selenium (écrit en java) qui sert à piloter les navigateurs.

Pré-requis : Java et JDK installé sur le système.

#### Installation:

```Javascript
npm i --save nightwatch
```

#### Configuration
Créer un fichier nightwatch.json à la racine du projet et copier la configuration fournit par la documentation de nightwatch.

```Javascript
{
  "src_folders" : ["./examples/tests", "./examples/mocha", "./examples/unittests"], // Dossier cible pour écrire les tests
  "custom_commands_path" : "./examples/custom-commands",
  "custom_assertions_path" : "./examples/custom-assertions",
  "page_objects_path" : "./examples/pages", // Dossier pages => fichiers descriptifs
  "globals_path" : "./examples/globalsModule.js",

  "webdriver" : {
    "start_process": true
  },

  "test_settings" : {
    "default" : {
      "webdriver": {
        "server_path": "./bin/geckodriver-0.23",
        "port": 4444,
        "cli_args": [
          "--log", "debug"
        ]
      },
      "filter": ["./examples/tests"],
      "desiredCapabilities" : {
        "browserName" : "firefox",
        "acceptInsecureCerts" : true
      }
    },

    "chrome" : {
      "webdriver": {
        "port": 9515,
        "server_path": "./bin/chromedriver-2.32",
        "cli_args": [
          "--verbose"
        ]
      },

      "desiredCapabilities" : {
        "browserName" : "chrome",
        "loggingPrefs": {"driver": "INFO", "server": "OFF", "browser": "INFO"}
      }
    },

    "selenium_server" : {
      "selenium" : {
        "start_process": true,
        "host": "localhost",
        "server_path": "./bin/selenium-server-standalone-3.10.0.jar",
        "cli_args": {
          "webdriver.gecko.driver": "./bin/geckodriver-0.23", // Firefox 
          "webdriver.chrome.driver": "./bin/chromedriver-2.32" // Chrome
        }
      },

      "desiredCapabilities" : {
        "browserName" : "firefox",
        "acceptSslCerts": true
      }
    }
  }
}
```
Les fichiers de test garde l'extension .js || faire une configuration spéciale pour gérer une autre extension.

- Télécharger selenium-server-standalone-3.10.0.jar => selenium => server_path
- Télécharger les drivers (./bin/geckodriver-0.23, ./bin/chromedriver-2.32) qui vont servir à piloter les différents navigateurs.

- Possibilité de faire des screenshots en cas d'échec d'un test.

#### Pour lancer nightwatch: lancer l'éxecutable

```Javascript
/node_modules/.bin/nightwatch
```

### Exemple de test d'un datepicker avec nightwatch

```Javascript
module.exports = {
    'Datepicker' : function (browser){
      browser
        .url('https://www.mydatepicker.com/index.html')
        .waitForElementVisible('body',1000)
        .click('.datepicker__container input:first-child')
        .waitForElement('.datepicker', 1000)
        .useXpath() // A partir de maintenant, tous les sélecteurs seront en Xpath
        .useCss() // Tous les sélecteurs sont de nouveau en css. PAR DEFAUT, ILS SONT EN CSS
        .useXpath()
        .click('//span[@class="datepicker__day__text" and text()="4"]'
        .pause(1000)
        .click('//button[text()="Ok"]')
        .waitForElementNotPresent('.datepicker', 1000)
        .end();
        
        browser.useCss().expect.element('.datepicker__container input:first-child').to.have.value('04/02/2016')
        browser.end()
    }
}
```
- La liste des assertions: https://nightwatchjs.org/api 

### Description de la page et de ses éléments (dossier cible décrit par page_objects_path)

```Javascript
module.exports = {
    url: 'https://www.mydatepicker.com/index.html',
    elements:{
      datepicker: '.datepicker',
      dateInput: '.datepicker__container input:first-child',
      okButton:{
        selector:'//button[text()="OK"]',
        locateStrategy: 'xpath'
      },
      dayButton: {
        selector: '//span[@class="datepicker__day__text" and text()="4"]',
        locateStrategy
      }
    }
}
```

### Simplifions notre premier test grâce à notre nouvelle page

```Javascript
module.exports = {
    'Datepicker' : function (browser){
      let page = browser.page.datepicker();
      page.navigate()
        .waitForElementVisible('body',1000)
        .click('@dateInput')
        .waitForElementVisible('@datepicker', 1000)
        .click('@dateButton')
        .click('@okButton')
        .waitForElementNotPresent('@datepicker', 1000)
        
        page.expect.element('@dateInput').to.have.value.that.equals('04/02/2016')
        browser.end()
    }
}
```

