Digitransit architecture is based on microservices architecture. Microservices are small, autonomous services that work together that allow us to build larger applications on top of APIs that the services provide.

![Architecture](images/architecture1.png)

Digitransit has three types of components:

1. UI
2. API Service components
3. Deployment

## UI

User interface is a responsive application built with React. Application connects to backend APIs.

## API Service components

Routing, Geocoding, Map tiles, and realtime data are provided through APIs. There are no dependencies between these logical entities. (e.g. Routing will not use geocoder, Map won't use routing). API service component consists of 1..n Docker containers.

## Deployment

Deployment project contains DevOps stuff that weaves components together and enables Ops to manage the service. 

