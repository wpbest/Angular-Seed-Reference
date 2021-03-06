# Angular-Seed-Reference

Angular Seed Reference Application

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 8.2.0.

## Documentation

[Node.js](https://nodejs.org/en/docs/)

[Angular](https://angular.io/)

[AngularCLI](https://cli.angular.io/)

[RxJS](https://rxjs-dev.firebaseapp.com/)

[Firebase](https://firebase.google.com/docs/)

[Firebase CLI](https://firebase.google.com/docs/cli/)

[AnguarFire](https://github.com/angular/angularfire2)

[Firestore](https://github.com/angular/angularfire2/blob/master/docs/firestore/documents.md)

[Angular Universal](https://angular.io/guide/universal)

[Deploying your Universal application on Cloud Functions for Firebase](https://github.com/angular/angularfire2/blob/master/docs/universal/cloud-functions.md)

## Install the Angular CLI

```
npm install -g @angular/cli
```

# Install Firebase Tools

```
npm install -g firebase-tools  
```

## Generate Code scaffolding

### ng new command switches used

#### --style=[css | scss | less | sass | styl]

The style option specifies what CSS preprocessor is used in building the project. the options are: css, scss, less, sass, styl.

#### --routing

The routing option generates a file app-routing.module.ts file.

#### --skip-install

This skip-install option disables the npm install after code generation.

#### --skip-git

### Angular CLI Command

```
ng new angular-seed-reference --routing --style scss --skip-install --skip-git
```

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Polyfills Microsoft's Internet Explorer

Modify polyfills.ts to support Microsoft's Internet Explorer by uncommenting the lines:

```
/** IE10 and IE11 require the following for NgClass support on SVG elements */
import 'classlist.js';  // Run `npm install --save classlist.js`.

/** IE10 and IE11 requires the following to support `@angular/animation`. ALL Firefox browsers require the following to support `@angular/animation`. **/
import 'web-animations-js';  // Run `npm install --save web-animations-js`.
```

IE10 and IE11 requires the following for NgClass support on SVG elements

```
npm install --save classlist.js
```
Web Animations `@angular/platform-browser/animations`

```
npm install --save web-animations-js
```

Add a new tsconfig-es5.app.json file

```
{
 "extends": "./tsconfig.app.json",
 "compilerOptions": {
     "target": "es5" 
  }
}
```

Modify the angular.json file and add the es5 configuration

```
"build": {
  "builder": "@angular-devkit/build-angular:browser",
  "options": {
      ...
  },
  "configurations": {
    "production": {
        ...
    },
    "es5": {
      "tsConfig": "./tsconfig-es5.app.json"
    }
  }
},
"serve": {
  "builder": "@angular-devkit/build-angular:dev-server",
  "options": {
      ...
  },
  "configurations": {
    "production": {
     ...
    },
    "es5": {
      "browserTarget": "ie:build:es5"
    }
  }
},
```

Modify the project.json

```
    "start": "ng serve --configuration es5",
    "build": "ng build --configuration es5",
    "prod": "ng build --configuration es5 --prod",
```

Modify tsconfig.json to configure strict by adding "strict": true, to "compilerOptions":

```
    "strict": true,
```

Add Chrome debugging configuration

Create folder .vscode and add file launch.json

```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Launch Chrome against localhost:4200, with sourcemaps",
            "type": "chrome",
            "request": "launch",
            "url": "http://localhost:4200",
            "runtimeArgs": [
              "--new-window",
              "--incognito",
              "--remote-debugging-port=9222"
            ],
            "sourceMaps": true,
            "trace": "verbose",
            "webRoot": "${workspaceRoot}"
        },
        {
            "name": "Attach Chrome against, with sourcemaps",
            "type": "chrome",
            "request": "attach",
            "port": 9222,
            "sourceMaps": true,
            "trace": "verbose",
            "webRoot": "${workspaceRoot}"
        },
        {
            "name": "Launch Firefox against localhost:4200, with sourcemaps",
            "type": "firefox",
            "request": "launch",
            "reAttach": true,
            "url": "http://localhost:4200",
            "webRoot": "${workspaceFolder}"
          }
   
    ]
  }
```

### Add Firebase hosting

Add the needed packages

```
npm install --save firebase @angular/fire 
```

### Import the Angular Fire libraries

Modify app.module.ts to import the Firebase libraries. Add import for environment

```
import { AngularFireModule } from '@angular/fire';
import { AngularFirestoreModule } from '@angular/fire/firestore';
import { AngularFireStorageModule } from '@angular/fire/storage';
import { AngularFireAuthModule } from '@angular/fire/auth';
import { environment } from '../environments/environment';

@NgModule({
  imports: [
    ...
    AngularFireModule.initializeApp(environment.firebaseConfig), // initialize
    AngularFirestoreModule, // firestore
    AngularFireAuthModule, // auth
    AngularFireStorageModule // storage
  ],
  ...
})  
```

Modify environment.ts and environment.prod.ts and add the firebase credentials.

environment.ts:
```
export const environment = {
  production: false,
  firebaseConfig: {
    apiKey: 'AIzaSyDHKrTrrL2YBM3cBENLWQS1ZuHhPKoQbYM',
    authDomain: 'dev-angular-seed.firebaseapp.com',
    databaseURL: 'https://dev-angular-seed.firebaseio.com',
    projectId: 'dev-angular-seed',
    storageBucket: 'dev-angular-seed.appspot.com',
    messagingSenderId: '143058689931',
    appId: '1:143058689931:web:8cd65a018eb1e6fd'  
  }
};
```

environment.prod.ts

```
export const environment = {
  production: true,
  firebaseConfig: {
    apiKey: 'AIzaSyD_rYkOPa-m15OhNEA8trbkK-GAwRf-5eo',
    authDomain: 'prod-angular-seed.firebaseapp.com',
    databaseURL: 'https://prod-angular-seed.firebaseio.com',
    projectId: 'prod-angular-seed',
    storageBucket: 'prod-angular-seed.appspot.com',
    messagingSenderId: '638138759316',
    appId: '1:638138759316:web:533ec4fb4616f464'  
  }
};
```

## Add SEO (Search Engine optimization)

Create the file robots.txt to the src folder and create the text

```
User-agent: *
Allow: /
```

Create the file sitemap.xml to the src folder and create the text:

```
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
   <url>
      <loc>https://angularseed.org/</loc>
      <lastmod>2019-08-09</lastmod>
      <changefreq>always</changefreq>
      <priority>1.0</priority>
   </url>
</urlset>
```

Add the meta data in the ```<head>``` section in the index.html file in the src folder:

```
  <link rel="canonical" href="https://angularseed.org/" />
  <meta name="description" content="Angular seed. Essential components and best practices for building the perfect Angular application.">
```

Modify angular.json and add "src/robots.txt" and "src/sitemap.xml" in tha assets,

```
            "assets": [
              "src/favicon.ico",
              "src/assets",
              "src/robots.txt",
              "src/sitemap.xml
            ],
```

Add the meta data in the ```<head>``` section in the index.html file in the src folder:

## Separating Dev and Prod Environment on Firebase

Add an additional firebase project by using the firebase use --add. 

```
firebase use --add
? Which project do you want to add? prod-angular-seed
? What alias do you want to use for this project? (e.g. staging) prod
Created alias prod for prod-angular-seed.
```

To deploy a firebase project, there are two methods: Use with Deploy and Deploy with -P flag.

###  Use with Deploy

#### dev environment

```
firebase use default
firebase deploy
```

#### prod environment 

```
firebase use prod
firebase deploy
```

### Deploy with -P flag

#### dev environment

```
firebase deploy -P default
```

#### prod environment

```
firebase deploy -P prod
```

## Build and Deploy to the dev environment

```
npm run deploy:dev
```

## Build and Deploy to the prod environment

```
npm run deploy:prod
```

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
