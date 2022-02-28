# Snapod Architecture
A Demonstration of Snapod's Architecture

> Feel free to file an issue if you encountered any problem during the use of Snapod, or if you have any suggestion for the product or our architecture.

<br/>


## Foreword
This project is used for describing the architecture and technologies behind Snapod. If you are looking for our development roadmap, we share that using Github Projects, check that out on our Github organization profile page.

> This project is work in progress

<br/>

## Front-end
Snapod App client is written in TypeScript using the Electron framework. Currently, it produces app packages for Windows and macOS. A Linux version can also be produced when needed.

+ App interface is developed using React.js;
+ CSS pre-processor is SASS/SCSS;
+ CSS framework is Tailwind CSS with JIT enabled;
+ Some of the UI components are from Headless UI;
+ Animation libraries used are Ant Motion and Framer Motion;
+ Data visualization library used is AntV;
+ Data fetching library used is SWR;

<br/>

## Back-end
### Snapod App API
Snapod App API is written in TypeScript using the Koa.js framework, deployed on Microsoft Azure App Engine, server location is Hong Kong.
+ REST API routes (requests to this endpoint are unauthenticated: login, signup etc.) utilize routing-controllers;
+ Implemented the dependency injection methodology using TypeDI;
+ GraphQL API endpoint (all requests are authenticated) utilizes TypeGraphQL and Apollo Client;
+ User identification method used is JWT;
+ Password encryption algorithm used is PBKDF2:
  - salt >= 8 bytes
  - iteration >= 400,000
  - digest: sha256
+ Database interaction ORM used is Prisma;
+ MySQL database is from Aliyun, server location is Hong Kong;
+ Static data storage service is provided by Qiniu, server location is mainland China;

<br/>

### Snapod Analytics
Snapod Analytics is written in TypeScript using the Express.js framework, deployed on AWS Elastic Beanstalk, server location is Hong Kong.
+ Database interaction ORM used is nohm;
+ Redis database is from Aliyun, server location is mainland China;

<br/>

### Snapod Sites
Snapod Sites is deployed as a serverless app on Netlify.
+ Custom domain is a feature of Netlify;
+ Custom domain creation is done through Netlify API;
