# NestJS
This contains how to use NestJS Rest API with JWT and TypeORM.

### Introduction
Nest (NestJS) is a framework for building efficient, scalable Node.js server-side applications. It uses progressive JavaScript, is built with and fully supports TypeScript (yet still enables developers to code in pure JavaScript) and combines elements of OOP (Object Oriented Programming), FP (Functional Programming), and FRP (Functional Reactive Programming).

Under the hood, Nest makes use of robust HTTP Server frameworks like Express (the default) and optionally can be configured to use Fastify as well!

Nest provides a level of abstraction above these common Node.js frameworks (Express/Fastify), but also exposes their APIs directly to the developer. This gives developers the freedom to use the myriad of third-party modules which are available for the underlying platform.

[Official Documentation](https://docs.nestjs.com/)

### Installation

Install using Nest CLI

```sh
npm i -g @nestjs/cli
nest new project-name
```

Alternative way

```sh
git clone https://github.com/nestjs/typescript-starter.git project
cd project
npm install
npm run start
```

### Installation with Swagger Docs

## Basics


```sh
nest g module user
nest g controller user
nest g service user

nest g resource Tasks
```

### Swagger Docs
```sh
npm install --save @nestjs/swagger swagger-ui-express
```

Add this lines in main.ts

```js
  const config = new DocumentBuilder().setTitle("Nest API").setDescription("Test API").setVersion("v1.0").build();
  const document = SwaggerModule.createDocument(app, config);
  SwaggerModule.setup('/', app, document);
```