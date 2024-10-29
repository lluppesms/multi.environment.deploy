# Project Description

This is a demo project that uses multiple service connections to deploy items into multiple Azure environments.

Because of the way Azure Pipelines work, the variables that define the service connections need to be available at pipeline **compile time**. Therefore, they cannot be dynamically generated variables at runtime and must be hard-coded into the pipeline definition.

In this example, I have specified all of the service connection names that will be used in the [./.azdo/pipelines/vars/var-common.yml](/.azdo/pipelines/vars/var-common.yml) file.

The [main pipeline file](/.azdo/pipelines/multi-deploy-pipeline.yml) file calls the [bicep deploy template](/.azdo/pipelines/templates/deploy-bicep-template.yml) which then uses conditional steps to deploy the resources using a specific (pre-defined) service connection.

In addition, I've included some environment specific variable files such as [dev environment](/.azdo/pipelines/vars/var-dev.yml), which can be used to override the default values and make them unique to each environment.

The [main pipeline](/.azdo/pipelines/multi-deploy-pipeline.yml) gives the user to choose which environment they want to deploy to with a popup parameter at runtime.
