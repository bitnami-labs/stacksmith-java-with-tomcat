# Java Tomcat Application with DB (MySQL): Customerapp

This is an example to show how to deploy an application using the `Java Tomcat application with DB (MySQL)` stack template in [Bitnami Stacksmith](stacksmith.bitnami.com).

## Package and deploy with Stacksmith

1. Go to [stacksmith.bitnami.com](https://stacksmith.bitnami.com)
2. Create a new application and select the _Java Tomcat application with DB (MySQL)_ stack template.
3. Select the targets you are interested on (AWS, Kubernetes,...)
4. Upload the [customerapp-1.0.0.war](../../releases/download/v1.0.0/customerapp-1.0.0.war) file (which can be found in [releases](../../releases) for the project.
5. Upload the [_boot.sh_](stacksmith/user-scripts/boot.sh) script from the [_stacksmith/user-scripts/_](stacksmith/user-scripts/) folder.
6. Click the <kbd>Create</kbd> button.
7. Launch it in [AWS](https://stacksmith.bitnami.com/support/quickstart-aws) or download the helm chart to run it in [Kubernetes](https://stacksmith.bitnami.com/support/quickstart-k8s)
8. Access your application: http://IP for AWS or http://IP:8080 for Kubernetes and Azure

## Scripts

There application requires a boot script that performs application specific initialization.

### boot.sh

This script takes care of initializing the database and configuring the application.

When the application is first run, it finds the folder where the application was deploed and then creates an `application.yml` file with database configuration settings.

## Packaging the application from source code

The _customerapp-1.0.0.war_ file can also be created by building the application in the [_app/_](app/) folder.

Simply run the following command in the [_app/_](app/) folder:

```
mvn package
```

The command sets up all required dependencies, builds and packages the application inside the `target` folder.

It can also be built using Docker by running:

```
$ ./build-with-docker.sh
```

This will pull an image of Maven and JDK 8 and perform build of the application.
