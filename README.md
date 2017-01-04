# Employee Pet Clinic

This application was generated using JHipster 3.12.2, you can find documentation and help at [https://jhipster.github.io/documentation-archive/v3.12.2](https://jhipster.github.io/documentation-archive/v3.12.2).

## Prerequisites

Before you can build and run this project, you must install and configure the following applications on your machine:

 * Install Java 8 from the [Oracle website](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
 * _(Optional)_ Install a Java build tool.
   * Whether you choose to use Maven or Gradle, you normally don’t have to install anything, as the project will automatically install the Maven Wrapper or the Gradle Wrapper for you.
   * If you don’t want to use those wrappers, go to the official [Maven](https://maven.apache.org/) website or [Gradle](https://gradle.org/) website to do your own installation.
 * Install [Git](git-scm.com). We recommend you also use a tool like [SourceTree](https://www.sourcetreeapp.com/) if you are starting with Git.
 * Install [Node.js](https://nodejs.org) from the Node.js website (prefer an LTS version). This will also install npm, which is the node package manager we are using in the next commands.
 * _(Recommended)_ Update npm: ```npm install -g npm```
 * Install Yeoman: ```npm install -g yo```
 * Install Bower: ```npm install -g bower```
 * Install Gulp: ```npm install -g gulp-cli``` (If you have previously installed a version of gulp globally, please run ```npm rm -g gulp``` to make sure your old version doesn’t collide with gulp-cli)
 * Install JHipster: ```npm install -g generator-jhipster```
 * _(Optional)_ Install Yarn: ```npm install -g yarn``` (So you can use the yarn flag ```yo jhipster --yarn```)

## Fast run

Run the following command in a terminal to run the application.

```
    ./mvnw    
```

Then navigate to [http://localhost:8080](http://localhost:8080) in your browser.

Congratulations! You’ve launched your application!

## Project profiles

The application comes with two profiles:

 * ```dev``` __for development:__ it focuses on ease of development and productivity.
 * ```prod``` __for production:__ it focuses on performance and scalability.

Those profiles come in two different configurations:

 * The Maven/Gradle profiles are used at build time. For example ```./mvnw -Pprod package``` or ```./gradlew bootRepackage -Pprod``` will package a production application.
 * The [Spring profiles](http://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-profiles.html) work at run time. Some Spring beans will behave differently, depending on the profile.
Spring profiles are set by Maven/Gradle, so we have a consistency between the two methods: you will have a prod profile on Maven/Gradle and Spring at the same time.

### Building for development. The ```dev``` profile

You can run the application in development directly using Maven or Gradle:

 * If you run the application with Maven, run ```./mvnw``` to use our Maven Wrapper, or ```mvn``` to use your own Maven installation. This will run our default Maven task, ```spring-boot:run```.
 * If you run the application with Gradle, run ```./gradlew``` to use our Gradle Wrapper, or ```gradle``` to use your own Gradle installation. This will run our default Gradle task, ```bootRun```.

Then navigate to [http://localhost:8080](http://localhost:8080) in your browser.

### Building for production. The ```prod``` profile

You can run the application in production directly using Maven or Gradle:

  * With Maven, run ```./mvnw -Pprod``` (or ```mvn -Pprod```). This will run our default Maven task, ```spring-boot:run```.
  * With Gradle, run ```./gradlew -Pprod``` (or ```gradle -Pprod```). This will run our default Gradle task, ```bootRun```.

If you want to package your application as an executable ```WAR``` file, you should provide Maven or Gradle with a profile. E.g.,:

  * With Maven, run ```./mvnw -Pprod package``` (or ```mvn -Pprod package```)
  * With Gradle, run ```./gradlew -Pprod bootRepackage``` (or ```gradle -Pprod bootRepackage```)

When you run your production application from a WAR file, the default is to use the same profile(s) as used during packaging. If you want to override this, you can explicitly provide an alternative in VM argument:

 * ```./java -jar [APLICATION_NAME]-[VERSION]-SNAPSHOT.war --spring.profiles.active=...```

Then navigate to [http://localhost:8080](http://localhost:8080) in your browser.

### Spring profiles switches

The application comes with three additional profiles used as switches:

 * ```swagger``` to enable swagger.
 * ```no-liquibase``` to disable liquibase.
 * ```shell``` to enable the [Spring Boot remote shell](http://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-remote-shell.html).

These can be used along with both the ```dev``` and ```prod``` profiles. Please note that by default, the ```swagger``` profile is disabled in ```prod``` and enabled in ```dev``` by setting the ```spring.profiles.include``` property in ```application.yml```.

```shell``` is only used at build time.

```swagger``` and ```no-liquibase``` are only used at runtime:

 * In your IDE, run your main application class with ```spring.profiles.active=dev,no-liquibase``` (please note you need to include the ```dev``` or ```prod``` profile explicitly)
 * With a packaged application: ```./java -jar jhipster-0.0.1-SNAPSHOT.war --spring.profiles.active=prod,no-liquibase```

With Maven, you can also use those profiles directly:

 * ```./mvnw -Pprod,swagger,no-liquibase```
 * ```./mvnw -Pdev,no-liquibase,shell```

With Gradle, you can also use those profiles directly:

 * ```./gradlew -Pprod -Pswagger -Pno-liquibase```
 * ```./gradlew -Pno-liquibase -Pshell```

## Testing the application

The application comes with an extensive set of tests:

 * Integration tests using the Spring Test Context Framework.
 * UI tests with [Karma.js](http://karma-runner.github.io/1.0/index.html).
 * Performance test with Gatling.
 * Behaviour-driven tests with Cucumber.
 * AngularJS integration tests with Protractor.

All those test are generated in the standard Maven ```src/test``` folder.

### Integration tests

Integration tests are done with the Spring Test Context framework, and are located in the src/test/java folder. JHipster will launch a specific Spring test context, which will be re-used along all tests, as:

 * Your Spring beans should be stateless and thread-safe, and thus can be re-used across your different tests suites.
 * Launching just one Spring context for all tests if a lot faster than launching a new Spring context for each test.

This Spring test context will use a specific test database to execute its tests:

 * If our case, we use an SQL database, the application will launch an in-memory H2 instance in order to use a temporary database for its integration tests. Liquibase will be run automatically, and will generate the database schema.

Those tests can be run directly in your IDE, by right-clicking on each test class, or by running ```./mvnw clean test``` (or ```./gradlew``` test if you run Gradle).

### UI tests

UI tests come in two flavors: unit tests with KarmaJS, and integration tests with Protractor. Only KarmaJS is provided by default, but if you want to have a good test coverage of your application, we recommend that you use both tools together.

#### KarmaJS

UI unit tests are written in Jasmine and run with Karma.js and PhantomJS, and are located in the ```src/test/javascript/spec``` folder.

Those tests will mock up the access to the application's REST endpoints, so you can test your UI layer without having to launch the Java back-end.

 + Those tests can be run using ```gulp test```.
 + To debug your JS tests, you will need to disable minification and Istanbul coverage on your Javascript files. To do so start Karma with the ```- - debug``` option, somethinglike this: ```./node_modules/karma/bin/karma start src/test/javascript/karma.conf.js --debug```, then navigate to [Karma debug page](http://localhost:9876/debug.html) and open your Javascript console.
 + __Tip:__ if you want to focus on a single test change the module description from ```describe('...', function() {``` to ```fdescribe('...', function() {``` and Jasmine will run this test only.

#### Protractor

UI Integration tests are done with [Protractor](http://www.protractortest.org/#/), and are located in the ```src/test/javascrtip/e2e``` folder.

Those tests will launch a Web browser and use the application like a real user would do, so you need to have a real application running, with its database set-up.

Those test can be run using ```gulp protractor``` or ```gulp itest```.

### Performance tests

Performance tests are done with [Gatling][] and written in Scala. They're located in `src/test/gatling` folder. They are generated for each entity, and allows to test each of them with a lot of concurrent user requests.

Gatling tests can be run with the following commands.

With Maven, you can also use those profiles directly:

 *  ```./mvnw gatling:execute```

With Gradle, you can also use those profiles directly:

 * ```./gradle gatlingRun -x cleanResources```

If you have several tests, the application will ask wich test should be run

## References

 * JHipster Homepage and latest documentation: https://jhipster.github.io
 * JHipster 3.12.2 archive: https://jhipster.github.io/documentation-archive/v3.12.2
 * Using JHipster in development: https://jhipster.github.io/documentation-archive/v3.12.2/development/
 * Using JHipster in production: https://jhipster.github.io/documentation-archive/v3.12.2/production/
 * Running tests page: https://jhipster.github.io/documentation-archive/v3.12.2/running-tests/
 * Setting up Continuous Integration: https://jhipster.github.io/documentation-archive/v3.12.2/setting-up-ci/
 * Gatling: http://gatling.io/
 * Node.js: https://nodejs.org/
 * Bower: http://bower.io/
 * Gulp: http://gulpjs.com/
 * BrowserSync: http://www.browsersync.io/
 * Karma: http://karma-runner.github.io/
 * Jasmine: http://jasmine.github.io/2.0/introduction.html
 * Protractor: https://angular.github.io/protractor/
