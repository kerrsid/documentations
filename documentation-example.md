# Introduction

This is the back-end of an application for automating the flow of handling the orders, finishing the orders by sending emails with the attached invoice to the customer. The application has a database where we store all the license keys for using them based on the order information.

A boilerplate for the App
* For storing custom constant configurations within the `process.env` - [DotEnv](https://github.com/motdotla/dotenv) package is used.
* For Routing - Repo contains the use of [express-router](https://expressjs.com/en/guide/routing.html).
* For Route Auth Middleware - Api routes are configured with [CSRF Token](https://github.com/krakenjs/lusca) and [JSON Web Token](https://github.com/auth0/express-jwt)
* For Handling Errors - Repo contains more classes ie. `BaseError`, `AuthenticationError`, `BusinessError`, `DatabaseError`, `TamperError`, `UploadError` & `ValidationError`.
* For Logging - Repo contains the use of [Winston](https://github.com/winstonjs/winston).
* To Log - use `Logger.info("Your message!")`. Other options for logging are `Logger.error`, `Logger.warn`, `Logger.http` & `Logger.debug`.
* For data validator - Repo contains the use of [Joi](https://github.com/sideway/joi) for data validation.

# Contents
* [Global Requisites](#global-requisites)
* [App Structure](#app-structure)
* [Install, Configure & Run](#install-configure--run)
* [List of Routes](#list-of-routes)
* [cPanel](#cpanel)

# Global Requisites

* node (>= 14.17.0)
* tsc (>= ^4.4.3)
* typescript (>= 4.3.2)
* mysql (>= 5.7)

# App Structure

```bash
├── dist
├── sample
│   └── .env.domain
├── src
│   ├── api
│   │   ├── generate
│   │   │   ├── GenerateController.ts
│   │   │   ├── GenerateRepository.ts
│   │   │   └── GenerateService.ts
│   │   ├── login
│   │   │   ├── ILogin.ts
│   │   │   ├── LoginController.ts
│   │   │   ├── LoginRepository.ts
│   │   │   └── LoginService.ts
│   │   ├── logout
│   │   │   └── LogoutController.ts
│   │   ├── middleware
│   │   │   ├── auth.ts
│   │   │   ├── cookie.ts
│   │   │   ├── error.ts
│   │   │   └── morgan.ts
│   │   ├── routes
│   │   │   ├── check
│   │   │   │   └── index.ts
│   │   │   ├── generate
│   │   │   │   └── index.ts
│   │   │   ├── login
│   │   │   │   └── index.ts
│   │   │   ├── logout
│   │   │   │   └── index.ts
│   │   │   └── index.ts
│   │   ├── utils
│   │   │   ├── errors
│   │   │   │   ├── AuthenticationError.ts
│   │   │   │   ├── BaseError.ts
│   │   │   │   ├── BusinessError.ts
│   │   │   │   ├── DatabaseError.ts
│   │   │   │   ├── TamperError.ts
│   │   │   │   ├── UploadError.ts
│   │   │   │   └── ValidationError.ts
│   │   │   └── validation
│   │   │   │   ├── GeneratorValidation.ts
│   │   │   │   └── LoginValidation.ts
│   ├── infra
│   │   └── logging.ts
│   └── app.ts
├── .env
├── .eslintignore
├── .eslintrc.js
├── .gitignore
├── .htaccess
├── .npmrc
├── .sample.env
├── README.md
├── package-lock.json
├── package.json
├── server.ts
└── tsconfig.json
```

# Install, Configure & Run
 
Below mentioned are the steps to install, configure & run the application

```bash
# Clone the repo.
git clone https://github.com/username/repository-name.git

# Goto the cloned project folder.
cd repository-name

# Install NPM dependencies.
# Note: You can review the list of dependencies from the below link.
# https://github.com/username/repository-name/network/dependencies
npm install

# Edit your DotEnv file using any editor of your choice.
# Please Note: You should add all the configurations details
# or else default values will be used!
# Create a new file in the parent directory with name .env and copy the content from sample/.env.domain and complete the missing variables.

# Before starting the application you should have the database imported to the schema that you complete in the .env
# You can find an SQL export file in database/database.sql

# Run the app
npm start

# Prepare app for production
npm run tsc

# Run the app in production
npm run start:prod
```

# List of Routes

```sh
# API Routes:

+--------+-------------------------+
  Method │ URI
+--------+-------------------------+
  GET    │ /api/login
  POST   │ /api/login
  GET    │ /api/logout
  POST   │ /api/check
+--------+-------------------------+
```

# cPanel

* The application has a bug in production that stop the application (probably a memory leak). For fixing this bug and make the application run 24/7 we set up a cron job that is called every 5 mins that make a call to the API. Because the application is on a shared server we couldn't find another solution: cPanel -> Cron Jobs

```sh
curl -I https://api.domain.ro/api/login
```

* The production files can be found in: cPanel -> File Manager -> /home/name/folder-name && /home/name/folder-name
* You can find the web applications running into: cPanel -> Setup Node.js App -> api.domain.ro/api && api-staging.domain.ro/api
