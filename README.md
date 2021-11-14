# Snapod Architecture
A Demonstration of Snapod's Architecture

> Feel free to file an issue if you encountered any problem during the use of Snapod, or if you have any suggestions for the product or our architecture.

<br/>


## Foreword
This project is used for describing the architecture and technologies behind Snapod. If you are looking for our development roadmap, we share that using Github Projects, check that out on our Github organization profile page.

> This project is work in progress

<br/>

## Front-end
Snapod App client is written in TypeScript using Electron framework. It's currently being packed to run on Windows and macOS. Linux version can also be produced when needed.

+ App interface is developed using React.js;
+ CSS pre-processor is SASS/SCSS;
+ CSS framework is TailwindCSS with JIT enabled;
+ Some of the UI components are from Headless UI;
+ Animation library is Ant Motion;
+ Data visualization library is AntV;
+ Data fetching library is SWR;

<br/>

## Back-end
### Snapod App API
Snapod App API is written in TypeScript using Koa.js framework, deployed on Microsoft Azure using App Engine, severs are in Hong Kong.
+ REST API routes (requests can be unauthenticated: login, signup etc.) utilize routing-controllers;
+ Implements the dependency injection methodology using TypeDI;
+ GraphQL API endpoint (all requests are authenticated) utilizes TypeGraphQL and Apollo Client;
+ User identification method is JWT;
+ Secret encryption algorithm is PBKDF2:
  - salt >= 8 bytes
  - iteration >= 400,000
  - digest: sha256
+ Database interaction ORM is Prisma;
+ MySQL database is from Aliyun, servers are in Hong Kong;
+ Static data storage service is provided by Qiniu, severs are in mainland China;

<br/>

### Snapod Analytics
Snapod Analytics is written in TypeScript using Express.js framework, deployed on AWS using ElasticBeanstalk, servers are in Hong Kong.
+ Database interaction ORM is nohm;
+ Redis database is from Aliyun, servers are in mainland China;

<br/>

### Snapod Sites
Snapod Sites is deployed as a serverless app on Netlify.
+ Custom domain is a feature of Netlify;
+ Custom domain creation is done through Netlify API;
