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
  "page_objects_path" : "./examples/pages",
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
Télécharger selenium-server-standalone-3.10.0.jar => selenium => server_path
Télécharger les drivers (./bin/geckodriver-0.23, ./bin/chromedriver-2.32) qui vont servir à piloter les différents navigateurs.

Possibilité de faire des screenshots en cas d'échec d'un test.

#### Pour lancer nightwatch: lancer l'éxecutable

```Javascript
/node_modules/.bin/nightwatch
```
