# Lagom integration with IBM Message Hub and WebSphere Liberty

Lagom is a framework for developing reactive microservices in Java or Scala. Created by Lightbend, Lagom is built on the proven Akka toolkit and Play Framework, and provides a highly productive, guided path for creating responsive, resilient, elastic, message-driven applications.

[IBM Message Hub](https://www.ibm.com/software/products/en/ibm-message-hub) is a fully-managed Apache Kafka service running on the IBM Cloud PaaS. It exposes a native Kafka interface, so Lagom services can communicate with it using the standard Lagom Message Broker API.

This project demonstrates a simple service that integrates with the IBM Message Hub Kafka [Liberty sample application](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample). The source code demonstrates how to write a Lagom service that can both consume messages produced by the Liberty sample application, and produce messages that can be consumed by it. You can run the service in a local development environment, a local Kubernetes cluster created using IBM Cloud Private [ICP](https://www.ibm.com/cloud-computing/products/ibm-cloud-private/), or in the cloud using [IBM Cloud Container Service](https://www.ibm.com/cloud-computing/bluemix/containers).


## Flow
![architect](http://developer.ibm.com/code/wp-content/uploads/sites/118/2018/06/architecture-lagom.png)
1. User sets up message hub
2. User sets up Lagom service
3. User edit and build the sample app in local Liberty server
4. User deploys the app to IBM Cloud Container Service    
   OR User deploys the app to IBM Cloud Private

## Included components

[Lagom](https://www.lightbend.com/lagom-framework)   
[IBM Message Hub](https://www.ibm.com/software/products/en/ibm-message-hub)   
[IBM Cloud Private](https://www.ibm.com/cloud-computing/products/ibm-cloud-private/)   
[IBM Cloud Container Service](https://www.ibm.com/cloud-computing/bluemix/containers)   
[IBM Liberty](https://developer.ibm.com/wasdev/websphere-liberty/)   
[Apache Kafka](https://kafka.apache.org/)    

## Steps

1.  [Prerequisites](#prerequisites)   
2.  [Gather Message Hub credentials](#gather-message-hub-credentials)  
3.  [Download and set up the Lagom service](#download-and-set-up-the-lagom-service)   
4.  [Next steps](#next-steps)   

## Video on the pattern
  [![Video](https://img.youtube.com/vi/gBT9vRWAWD4/0.jpg)](https://youtu.be/gBT9vRWAWD4)
  
## Prerequisites

To build and run this example, you need:

- [git](https://git-scm.com/)
- [Java SE 8 JDK](http://www.oracle.com/technetwork/java/javase/overview/index.html)
- [Maven 3.2.1+](https://maven.apache.org/) to build and run the Lagom project (3.5.0 recommended)
- [Message Hub Service Instance](https://console.ng.bluemix.net/catalog/services/message-hub/) provisioned in [IBM Cloud](https://console.ng.bluemix.net/) — **Note:** the Liberty sample application requires the Message Hub Service Instance to have the name: "message-hub-service".
- [IBM Message Hub Kafka Liberty sample application](https://github.com/ibm-messaging/message-hub-samples/tree/master/kafka-java-liberty-sample) deployed to Cloud

## Gather Message Hub credentials

Follow these steps to get a copy of the Message Hub credentials that are needed for the Lagom service to authenticate with Message Hub.

1.  Log in to the [IBM Cloud console](https://console.ng.bluemix.net/).
2.  Navigate to the Message Hub service you have created.
3.  Navigate to "Service credentials".
4.  Create new credentials if needed (no special parameters are required).
5.  Click "View credentials".
6.  Copy the following credential values to use in the Lagom service:
    - `"kafka_brokers_sasl"` — **Note:** the Lagom service requires the list of brokers to be formatted as a single-line, comma-separated list of hostname:port pairs. For example: `"host1:port1,host2:port2"`.
    - `"user"`
    - `"password"`

## Download and set up the Lagom service

Follow these steps to get a local copy of this project and configure it with the Message Hub credentials you saved in the previous step.

1.  Open a command line shell and clone this repository:
    ```
    git clone https://github.com/lagom/ibm-integration-examples.git
    ```
2.  Change into the root directory for this example:
    ```
    cd ibm-integration-examples/lagom-message-hub-liberty-integration-example
    ```
3.  Open the `message-hub-liberty-integration-impl/src/main/resources/message-hub.conf` file in a text editor and fill in the empty values of the `brokers`, `user` and `password` properties from the credentials retrieved above.

    **Note:** Be sure not to commit this file with your credentials in it.

## Next steps

Now that the project has been downloaded and configured, you can proceed to running it in any of these three ways:

- [Run in development mode](docs/run-in-development-mode.md)
- [Deploy to IBM Cloud Private](docs/deploy-icp.md)
- [Deploy to IBM Cloud Container Service](docs/deploy-with-bluemix.md)

## Links
* [Lagom](https://www.lightbend.com/lagom-framework)     
* [IBM Cloud Private](https://www.ibm.com/cloud-computing/products/ibm-cloud-private/)   
* [IBM Cloud Container Service](https://www.ibm.com/cloud-computing/bluemix/containers)   
* [IBM Liberty](https://developer.ibm.com/wasdev/websphere-liberty/)   
* [Apache Kafka](https://kafka.apache.org/)    

## License
[Apache 2.0](LICENSE)
