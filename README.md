# The LinkWire Project

## Introduction

Linkwire is an open-source URL shortener and web traffic analysis platform. Our goal is to create a general purpose URL shortener that anyone can use, while also maintaining key features that empower cybersecurity researchers to identify threat actors.

DISCLAIMER: LinkWire's premium features are intended for educational/scambaiting purposes only.

## Project Structure

We currently maintain the code for LinkWire using a polyrepo approach. This allows us to open up certain parts of our codebase to broad collaboration, while limiting who updates more sensitive & decision driven code (such as our Terraform modules).

Our codebase consists of the following repos:
* [linkwire (You are here)](https://github.com/AjayBhatta16/linkwire) - The main repository for the LinkWire project, consisting of onboarding documentation and guidelines. Any issues with the LinkWire platform should be opened under this repository.
* [linkwire-architecture](https://github.com/AjayBhatta16/linkwire-architecture) - Files pertaining to LinkWire's system design schematics and cloud infrastructure. This includes, but is not limited to Terraform modules, database schemas, API Gateway configurations, and our architecture diagram. This repo is publicly available strictly for documentation purposes.
* [linkwire-ui-v2](https://github.com/AjayBhatta16/linkwire-ui-v2) - The Angular app that powers the LinkWire dashboard, which allows users to create and manage links.
* [linkwire-golang-shared](https://github.com/AjayBhatta16/linkwire-golang-shared) - Shared types and functions for our various Golang back-end components. When changes are pushed or merged into the main branch, a new package version will be created and become retrievable by running `go get https://github.com/AjayBhatta16/linkwire-golang-shared@latest`
* [linkwire-microservices](https://github.com/AjayBhatta16/linkwire-microservices) - The code for LinkWire's various microservices, which are currently written in Golang and Node.JS, and run on GCP Cloud Run functions. This repo also includes generator scripts, which can be used to quickly create a copy of our boiler plate code for a new microservice.
* [linkwire-redirect-server](https://github.com/AjayBhatta16/linkwire-redirect-server) - The code for LinkWire's redirect server, which is responsible for everything that happens when a LinkWire link is clicked.
* [linkwire-automation-tests](https://github.com/AjayBhatta16/linkwire-automation-tests) - The code for LinkWire's automation tests.

## Tech Stack & System Architecture

LinkWire currently uses the following tech stack:
* Front-End development: Angular, Bootstrap
* API development: Golang, Node.JS
* Database: Firestore
* Deployment: GCP Cloud Run, GCP App Engine, Firebase Hosting

In order to keep the app engine component isolated for processing click events, we use a microservice pattern for our other APIs. A new endpoint can be provisioned by opening an issue under the linkwire-architecture repo.

We leverage the Resend platform for all activities involving sending emails. This can be used by any back end component by submitting a SendEmail request to pub/sub.

## Environment Setup

### Angular App
Clone the UI repo listed above. Run npm install and npm start. The web app will be running on localhost:5000.

### Redirect Server
Clone the repo, run npm install and npm start. Database and Pub/Sub connections TBD, but feel free to bring your own :)

### Microservices
TBD
