# Snapod Architecture
A Demonstration of Snapod's Architecture

> Feel free to file an issue if you encountered any problem during the use of Snapod, or if you have any suggestion for the product or our architecture.

<br/>


## Foreword
This project is used for describing the architecture and technologies behind Snapod. If you are looking for our development roadmap, we share that using Github Projects, check that out on our Github organization profile page.

> This page is work in progress

<br/>

## Front-end
> Undergoing a major refactoring

Snapod App client is written in TypeScript using Electron framework. Currently, it produces app packages for Windows and macOS. A Linux version can also be produced when needed. During Beta phase, all packages are not signed.

+ App interface is developed using React.js;
+ CSS pre-processor is SASS/SCSS;
+ Atomic CSS framework is Tailwind CSS;
+ Some of the UI components are from Headless UI;
+ Animation libraries are Ant Motion and Framer Motion;
+ Data visualization libraries are AntV and `react-simple-map`;
+ Data fetching libraries:
  - SWR for REST API requests
  - Apollo Client for GraphQL requests

<br/>

## Back-end
### Snapod App API
Snapod App API is written in TypeScript using the Koa.js framework, deployed on (~~Microsoft Azure App Engine~~) Railway.app.
+ REST API routes (requests to this endpoint are unauthenticated: login, signup etc.) are powered by `routing-controllers`;
+ Implemented the dependency injection methodology using TypeDI;
+ GraphQL API endpoint (all requests are authenticated) utilizes TypeGraphQL and Apollo;
+ User identification method is JWT;
+ Password encryption algorithm used is PBKDF2:
  - salt >= 8 bytes
  - iteration >= 400,000
  - digest: sha256
+ Database interaction ORM is Prisma;
~~+ MySQL database is from Aliyun, server location is Hong Kong;~~
+ PostgreSQL database is from Supabase, server location is Frankfurt, Germany
+ Static data storage service is provided by Qiniu, server location is mainland China;

<br/>

### Snapod Analytics
Snapod Analytics is written in TypeScript using Express.js framework, deployed on (~~AWS Elastic Beanstalk, server location is Hong Kong~~) Railway.app.
+ Database interaction ORM is `nohm`;
~~+ Redis database is from Aliyun, server location is mainland China;~~
+ Redis database is deployed on ~~Fly.io, server location is Hong Kong, SAR~~ Railway

<br/>

### Snapod Release Server
Snapod Electron application release server is powered by [Nuts](https://github.com/GitbookIO/nuts) by Gitbook
+ Releases are published & distributed via Github

<br/>

### Snapod Sites
Snapod Sites is deployed as a serverless app on Netlify.
+ Custom domain is a feature provided by Netlify;
+ Custom domain creation is done through Netlify API;

<br/>

### Status Page
Snapod uses Better Uptime to monitor the health status of all cloud services, we share them through a status page.
+ Health check endpoints:
  - [https://api.snapodcast.com/v0/api/ping](https://api.snapodcast.com/v0/api/ping)
  - [https://analytics.snapodcast.com](https://analytics.snapodcast.com)
  - [https://rss.snapodcast.com](https://rss.snapodcast.com)
