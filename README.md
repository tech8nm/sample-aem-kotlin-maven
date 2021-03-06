# Sample AEM project template

This is a sample project for integration kotlin in your maven based AEM project. **Tutorial can be found =>> [here](https://andreishilov.github.io/blog/aem-and-kotlin/) <== ** This project created with a standard maven AEM archetype.


## Modules

The main parts of the template are:

* core: Java bundle containing all core functionality like OSGi services, listeners or schedulers, as well as component-related Java code such as servlets or request filters.
* ui.apps: contains the /apps (and /etc) parts of the project, ie JS&CSS clientlibs, components, templates, runmode specific configs as well as Hobbes-tests
* ui.content: contains sample content using the components from the ui.apps
* ui.tests: Java bundle containing JUnit tests that are executed server-side. This bundle is not to be deployed onto production.
* ui.launcher: contains glue code that deploys the ui.tests bundle (and dependent bundles) to the server and triggers the remote JUnit execution

## How to build

To build all the modules run in the project root directory the following command with Maven 3:

    mvn clean install

If you have a running AEM instance you can build and package the whole project and deploy into AEM with  

    mvn clean install -PautoInstallPackage
    
Or to deploy it to a publish instance, run

    mvn clean install -PautoInstallPackagePublish
    
Or alternatively

    mvn clean install -PautoInstallPackage -Daem.port=4503

Or to deploy only the bundle to the author, run

    mvn clean install -PautoInstallBundle

## Testing

There are three levels of testing contained in the project:

* unit test in core: this show-cases classic unit testing of the code contained in the bundle. To test, execute:

    mvn clean test

* server-side integration tests: this allows to run unit-like tests in the AEM-environment, ie on the AEM server. To test, execute:

    mvn clean verify -PintegrationTests

* client-side Hobbes.js tests: JavaScript-based browser-side tests that verify browser-side behavior. To test:

    in the browser, open the page in 'Developer mode', open the left panel and switch to the 'Tests' tab and find the generated 'MyName Tests' and run them.


## Testing on AEM

After the applications is successfully build and deplyed to AEM, you can view the sample content and components that are built as part of this sample.

* Login to AEM, like http://localhost:4502
* Go to Navigation > Sites > aem-ktln (This is the sample content package. You can find the contents at 'sample-aem-kotlin-maven/ui.content/src/main/content/jcr_root/content/aem-ktln/en/' )
* Select English > Edit. As below:
![sample-aem-kotlin-content](https://user-images.githubusercontent.com/902972/38891467-10b3674a-424a-11e8-8b31-785ee5aef27f.png)

* Default components built along with this sample, visible in the left menu. As below:
![sample-aem-kotlin-components](https://user-images.githubusercontent.com/902972/38891466-107a3934-424a-11e8-9d50-e168b4dafbb9.png)


## Maven settings

The project comes with the auto-public repository configured. To setup the repository in your Maven settings, refer to:

    http://helpx.adobe.com/experience-manager/kb/SetUpTheAdobeMavenRepository.html




