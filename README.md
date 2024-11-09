# Automated Tests for TeamCity Server

### The framework includes scalable and reliable tests for a complex application.

## Best Practices 

The API part includes:
* Complete data generation by Model
* Easily scalable requests based on different types of APIs (CRUD, Search)
* Test parameterization by user sessions
* Automated test data preparation and cleanup

The UI part includes:
* Data setup reuse through API
* Use of Page Object and Page Element patterns
* Use of smart waits and environment assertions

The CI part includes:
* Full automation of environment setup via API
* Infrastructure setup in Docker (Selenoid)
* Raising a review app with changes, launching environment setup, and setting required parameters
* Calculation of API coverage using Swagger API Coverage
* Collection of metrics in reports and publishing of the Allure report with history on GitHub Pages
* Implementation of quality gates (for build verification, checkstyle, and unit tests).

## Local Run 

### Workflow Run
To run the workflow locally, use the command act - https://github.com/nektos/act.

### Test Run

To run the tests locally:
* Setup src/main/resources/config.properties:
```
host=<IP>:8111 # where <IP> is the result of the ipconfig getifaddr en0 command or similar 
superUserToken=<TOKEN> # where <TOKEN> is the super user authentication token of your TeamCity server
```

* Choose group and run:
```
./mvnw clean test -Dgroups=Regression
```

* Generate Allure Report:

```
./mvnw allure
```

The Allure report will be located at target/site/allure-maven-plugin/index.html.