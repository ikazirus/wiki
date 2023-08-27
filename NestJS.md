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

Add this lines in **main.ts**

```js
  const config = new DocumentBuilder().setTitle("Nest API").setDescription("Test API").setVersion("v1.0").build();
  const document = SwaggerModule.createDocument(app, config);
  SwaggerModule.setup('/', app, document);
```



## Database connectivity

CLI Migrations
```sh
npm i -g typeorm
npm install -g ts-node
```

To apply database migrations
```sh
npm run migration:generate -- UserMigration
```

You can also add yaml script.
```yaml
"scripts": {
    ...
    "typeorm": "node --require ts-node/register ./node_modules/typeorm/cli.js --config src/ormconfig.ts",
    "migration:generate": "npm run build && npm run typeorm migration:generate -- -n",
    "migration:run": "npm run build && npm run typeorm migration:run"   
}
```

### MySQL

Install
```sh
npm install --save @nestjs/typeorm typeorm sqlite3
```

Setup
```js
const config: MysqlConnectionOptions = {
    type: 'mysql',
    host: 'localhost',
    port: 3306,
    username: 'root',
    password: '',
    database: 'snet_nest',
    entities: ["dist/**/*.entity.js"],
    synchronize: false,
    migrations: [
        'dist/db/migrations/*.js'
    ],
    cli: {
        migrationsDir: 'src/db/migrations'
    }
}
export default config;
```

### SQLite
Install
```sh
npm install --save @nestjs/typeorm typeorm sqlite3
```

Setup
```js
const config: SqliteConnectionOptions = {
    type: 'sqlite',
    database: 'db',
    entities: ["dist/**/*.entity.js"],
    synchronize: true,
    migrations: [
        'dist/db/migrations/*.js'
    ],
    cli: {
        migrationsDir: 'src/db/migrations'
    }
}
export default config;
```


## Validations
Install
```sh
npm install class-validator class-transformer
```

Add this line in main.
```js
app.useGlobalPipes(new ValidationPipe());
```

### Auth

Authorization using Passport (OAUTH2)

```sh
npm i @nestjs/passport passport passport-oauth2
```
```sh
npm i -D @types/passport-oauth2
```
```sh
npm i @nestjs/jwt passport passport-jwt
```

### Install all libraries in one go.

With this it will install Swagger, TypeORM, JWT/Passport, Class validator/transformer

```
npm install --save @nestjs/swagger swagger-ui-express @nestjs/typeorm typeorm sqlite3 @nestjs/jwt passport passport-jwt @nestjs/passport  class-validator class-transformer 
npm install --save-dev @types/passport-jwt
```