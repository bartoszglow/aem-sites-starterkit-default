# Default Sites Starter Kit

This is the Default Sites Starter Kit for rapid site development with AEM.

## Modules

The main parts of the project are:

* **site.content**: contains mutable content (not /apps) that is integral to the running of the site. This include template types, templates, policies and base-line organization page and asset structures.
* **site.theme**: contains front-end module which provides styling (CSS) and behavior (JS) for your AEM website.

## How to build

To build all the modules run in the project root directory the following command with Maven 3:

    mvn clean install

If you have a running AEM instance you can build and package the whole project using the `all` module with:

    mvn clean install -PautoInstallSinglePackage

Depending on your maven configuration, you may find it helpful to force the resolution of the Adobe public repo with

    mvn clean install -PautoInstallSinglePackage -Padobe-public

Or to deploy it to a publish instance, run

    mvn clean install -PautoInstallSinglePackagePublish

Or alternatively

    mvn clean install -PautoInstallSinglePackage -Daem.port=4503

Or to deploy only `ui.apps` to the author, run

    cd ui.apps
    mvn clean install-PautoInstallPackage

Or to deploy only the bundle to the author, run

    cd core
    mvn clean install -PautoInstallBundle

### Building for AEM 6.x.x

The project has been designed for **AEM as a Cloud Service**. The project is also backward compatible with AEM **6.4.8** and **6.5.5** by adding the `classic` profile when executing a build, i.e:

    mvn clean install -PautoInstallSinglePackage -Pclassic

### Building sample content

By default, sample content from `ui.content.sample` will be deployed and will overwrite (reset) any authored content during each build. If you wish to turn this behavior off, modify the [filter.xml](ui.content.sample/src/main/content/META-INF/vault/filter.xml) file and add the `mode=merge` attribute for the paths you don't want overwritten:

```diff
- <filter root="/content/wknd" />
+ <filter root="/content/wknd" mode="merge"/>
```

## Testing

There are three levels of testing contained in the project:

* unit test in core: this show-cases classic unit testing of the code contained in the bundle. To test, execute:

    ```
    mvn clean test
    ```

* server-side integration tests: this allows to run unit-like tests in the AEM-environment, ie on the AEM server. To test, execute:

    ```
    mvn clean verify -PintegrationTests
    ```

* client-side Hobbes.js tests: JavaScript-based browser-side tests that verify browser-side behavior. To test, go in the browser, open the page in 'Developer mode', open the left panel and switch to the 'Tests' tab and find the generated 'MyName Tests' and run them.


## Maven settings

The project comes with the auto-public repository configured. To setup the repository in your Maven settings, refer to:

    http://helpx.adobe.com/experience-manager/kb/SetUpTheAdobeMavenRepository.html