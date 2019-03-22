# Install Angular 

## Install node js
```
  curl -sL https://rpm.nodesource.com/setup_9.x | sudo -E bash -
  
  yum remove -y nodejs npm
  
  mktemp 
  
  curl -sL -o '/tmp/tmp.e4rDEzz6jw' 'https://rpm.nodesource.com/pub_9.x/fc/25/x86_64/nodesource-release-fc25-1.noarch.rpm'
  
  rpm -i --nosignature --force '/tmp/tmp.e4rDEzz6jw'
  
  rm -f '/tmp/tmp.e4rDEzz6jw'
  
  rpm -qa 'node|npm' | grep -v nodesource
  
  sudo yum install -y nodejs
  
  curl -sL https://dl.yarnpkg.com/rpm/yarn.repo | sudo tee /etc/yum.repos.d/yarn.repo
  
  sudo yum install yarn
```

## Install CLI

```
  npm install -g @angular/cli
  
  npm i next@latest react@latest react-dom@latest
```

# AngularWebApp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 7.3.6. Commit your project to your github repo. If you are creating project with normal `ng new`, then you won't be able to commit same project to your own github repo easily. Please refer to StackOverflow page(https://stackoverflow.com/questions/45953905/add-angular-project-to-already-created-empty-repo) and add `--skip-git`

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

# Deploy to Openshift

Login to openshift using oc command and create new project first to have front-end angular separately in openshift. 
```
  oc new-project angular-examples
```

Checkout this code to your local folder or use your own code:
```
  git clone https://github.com/kodtodya/angular-on-openshift.git
```
Go inside your angular application directory and run below command:
```
  npx nodeshift --strictSSL=false --dockerImage=bucharestgold/centos7-s2i-web-app --imageTag=10.x --build.env OUTPUT_DIR=dist/angular-web-app --expose
```
Whoa..!!! Check your route using below command and invoke it using browser:

```
  oc get routes -o=custom-columns=HOST/PORT:.spec.host
```

Enjoy.!!! :)
