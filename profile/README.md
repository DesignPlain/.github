<h1 align="center">
DesignSphere
</h1>
<h4 align="center">
  - Design and deploy multi-cloud infrastructure. -
  <br>
</h4>
<br>

![DesignSphere_UI](https://github.com/DesignPlain/.github/assets/19748270/220741e9-2351-4684-a4f5-c916d95a7be0)

## DesignSphere aims to be:

-  A multi-cloud management and observability platform.
-  A simple and intuitive UI for architecting and deploying your software system of any scale.
-  A guided platform for learning new tools and technologies with related best practices.

## Build & Run

```
git clone https://github.com/DesignPlain/PlainServer.git

cd PlainServer

./docker_run.sh start
```

##### Application will be up at [`http://localhost:8080/app`](http://localhost:8080/app/)

## Components

Checkout the code in the following repos for more details  
| Component| Repository|
| :--------------- | :--------------- |
| Frontend UI | [DesignPlain/PlainDashboard](https://github.com/DesignPlain/PlainDashboard) |
| Backend Server | [DesignPlain/PlainServer](https://github.com/DesignPlain/PlainServer)|

## Features

- [x] Deploy GCP resources
- [x] Deploy AWS resources
- [ ] Deploy Azure resources
- [x] UI for configuring individual resources
- [x] UI to list deployed resources with related properties
- [x] UI for error messages and potential fixes
- [ ] Code snippet suggestions for communication between connected resources
- [ ] Supported all Pulumi resources
- [ ] UI suggestion for different resource best practices
- [ ] Plugin model to add other custom resources

## Design & Architecture

- DesignSphere UI is built on Angular and uses Angular drag-and-drop CDK for the drag functionality for the UI canvas.
- The Backend uses [Pulumi](https://www.pulumi.com) for deploying resources and is written in Golang. For data persistence, we use [Pebble](https://github.com/cockroachdb/pebble) KV database.
- Programmatic structures required for configuring and deploying the cloud resource are separately auto-generated from the Pulumi resource schemas
  - Example resource schema - [pulumi-aws resource schema](https://github.com/pulumi/pulumi-aws/blob/master/provider/cmd/pulumi-resource-aws/schema.json)
  - The code generator generates code for UI typescript and backend go constructs.
  - Generated code is used in rendering resource config properties in the UI and parsing the resource configs received at the backend APIs on config changes and deployment from the UI.
