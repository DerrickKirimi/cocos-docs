# AllAuth

AllAuth provides authentication and authorization mechanisms for general purposes and for IoT. Some of the features we provide:

- User management with fine-grained access control
- Device management with fine-grained access control
- Messaging authentication and authorization using mProxy component

How it works:

Here is the architecture diagram:

![architecture](architecture.png)

There are two steps in developing the product:

1. Things and Users management
2. IoT/messaging auth component

## 1. Things and Users Management

Things and Users Clients services are used for user and things management. There is a simple UI that allows users to manage Users and Devices and groups - providing access control management. We also provide an SDK - which is really our gRPC client that can easily be generated from the Protobuf files we provide so anyone can easily integrate it with their software independently of technology stack they are using. This will result in User and device fleet management out of the box - which is something required by almost any project - so that the end-user can focus on developing the rest of their product. Ofc, the client can utilize only user management and access control in case their app is not focused on IoT and there are no devices in the context - just like, say, using KeyCloak or Auth0 or any other 3rd-party identity provider.

## 2. IoT/messaging auth component

This component provides messaging proxy between the message broker and the message sender. In context of IoT, it's usually the device, but it can really be anyThing (that is Things clients - clients can be an app or user or device). The best value we bring here is the we take care of authN/authZ in the least intrusive way possible. All the clients need to do is to configure devices to use mProxy - and we take care of everything else. :) Devices need to be configured anyways, so use of mProxy is transparent from the end-user perspective.
It's important to note that location of target server needs to be provided to mProxy.
