# snyk-demo

## NATAN comments:
* Project contains stand-alone Node/Express REST service(which can be tested through Postman (__localhost:3000__)) and
the [simplest] Vue client (__localhost:8080__), ,
so in order to work first run the __snyk-service__ (___npm run start___)
and then (___npm run serve___) __HERE(snyk-demo)__
* I'm not too familiar with Node.js(more of Java backend experience) - so the service is minimal
* Node service supports a GET request w PackageName & PackageVersion path params, and returns
a Cache of Packages - an index-by-name of Package objects (which hold version & 
dependencies data, but can hold Fixes etc.). 
* Caching is very simple - server-side, not-persisted between server runs, but could be 
loaded from some db, use 3rd party libs and/or have more sophisticated cache rules
* Versions of the packages(and semver arithmetics - ^~ etc) __were ignored__ - as i wasn't 
sure how it is handled in real life  
* Dependency TreeData from NPMJS.COM is loaded sync & depth-first -to increase the chances of 
caching basic packages, which probably have lots of dependants).
* ServerSide: I used both async/await and Promise style 
* ClientSide: I used axios 

## Tests
* i used Jest to write unit and functional(mock) tests - __for Node service only!!__. Obviously, there should be more
* for test i mocked the requests to NPMJS.com - read dummy JSON instead(with small timeout)




## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
