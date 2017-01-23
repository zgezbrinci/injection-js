# Dependency Injection

Fork of the Angular's dependency injection. This library can be used outside the framework.

# How to use?

## TypeScript

```ts
import 'reflect-metadata';
import { ReflectiveInjector, Injectable } from 'injection-js';

class Http {}

@Injectable()
class Service {
  constructor(private http: Http) {}
}

const injector = ReflectiveInjector.resolveAndCreate({
  Service,
  Http
});

injector.get(Service);
```

## ES5

```js
require('reflect-metadata');
var di = require('../dist');

var Http = di.Class({
  constructor: function () {}
});

var Service = di.Class({
  constructor: [Http, function (http) {
    this.http = http;
  }]
});

var injector = di.ReflectiveInjector.resolveAndCreate([Http, Service]);

console.log(injector.get(Service) instanceof Service);
```

For full documentation click [here](https://angular.io/docs/ts/latest/guide/dependency-injection.html).

# License

MIT

