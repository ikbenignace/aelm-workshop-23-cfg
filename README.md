# Introduction

Hi everybody and welcome to the ALM Workshop of 2023.

Goals:
* Learn new technologies
* Implement CI ALM concepts
* Securely manage secrets for your applications
* Automatically deploy new versions of your application

While it's easier to work with technologies that you use day-to-day, today I would like to try some technologies that you (probably) haven't really worked with yet:

* Golang
* DockerHub
* GitHub DevSpaces
* GitHub Actions
* RedHat OpenShift
    * You can also opt for running Kubernetes locally with **Kind** (Kubernetes in Docker) or **k3d** (k3s in docker)

# Workshop

The workshop will be divided in several tasks that each represent a checkpoint.
If one of the tasks is not working or you ran out of time you can always check-out the branch for that specific checkpoint and catch-up from there.

# Tasks

## Configuration repository
The configuration repository is called **aelm-workshop-23-cfg**. You've been provided with basic Kubernetes manifests to deploy on an Openshift cluster in the cloud. The industry standard way of doing this is by using Helm charts or Kustomize but these are a bit more complex so as such we're using the most basic setup.

## Task 1

:exclamation: **This task needs to be completed in the aelm-workshop-23 code repository**

## Task 2

:exclamation: **This task needs to be completed in the aelm-workshop-23 code repository**

## Task 3

* Login to RedHat Openshift Sandbox https://console.redhat.com/openshift/sandbox 
* Deploy your application from the Developer menu by selecting Add+ and from Container Image.
* Your application should now be available from a remote endpoint
    * This was a lot of manual effort, so we will automate this is the next task

## Task 4

1. Edit the Kubernetes openshift.yaml to use your Docker image
    * There's some other fields that you should also fill-in or check!
2. Provide the correct secrets to login to the Openshift cluster from your repository.
    * Should be the same as what you've did for code secrets
3. Your application should be publicly available after deploy, test it out.

## Task 5

:exclamation: **This task needs to be completed in the aelm-workshop-23 code repository**

## Task 6

* Create a new branch from dev called "tst"
* Update TST branch to give different names to the Deployment, Service and Route resource (prefix tst-)
    * Normally we would use "Namespaces" in Kubernetes to avoid this but OpenShift Sandbox does not support multiple namespaces for security reasons
* The TST branch should always deploy a released version, you can deploy version 1.0.0 first and then afterwards update to 1.1.0

## Finish?

**Congratulations, you've now got a functioning code pipeline!! You can update, release and expose you're application on demand now** :clap::muscle:
The next step is to now improve upon this, so that you as a developer can focus solely on producing the code. Choose some of the extra tasks to do, in both repositories are different tasks related to their type.

## Extra's
* Convert to Helm Chart instead of kubectl apply deploy method
    * Helm charts are the most popular way of managing Kubernetes resources, because you can use advanced templating features
    * As inspiration last years repository https://github.com/arnouthoebreckx/tafun-alm-workshop-cfg
* Add an extra environment / branch "tst". When you merge to the tst branch it should deploy a deployment + service + route for the TST environment
    * Easiest would be to have a new namespace as well but we're not allowed on Openshift Sandbox.
* Add a Horizontal Pod Autoscaler that based on amount of load (requests) to the service will automatically spin up extra pods
    * Simulate a load with Postman or just a bash while loop with curl.
* Add readinessProbes to your Deployment
    * They are used to check that the application is functionally ready to receive connections