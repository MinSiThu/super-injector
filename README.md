# super-injector
 a dependency injection library 

## Sample Code
```javascript
// Simple Example
let SuperInjector = require("super-injector");
let superInjector = new SuperInjector();

superInjector.addDependency("User",class{
    constructor(name,age){
        this.name = name;
        this.age = age;
    }

    log(){
        console.log(`${this.name} is ${this.age} years old!`)
    }
})

class UserService{
    setUser(name,age){
        this.user = new this.injections.User(name,age);
    }

    render(){
        this.user.log();
    }
}

let injectedUserService = superInjector.inject(UserService,"User");
injectedUserService.setUser("The Creator of Super-Injector",19)
injectedUserService.render();

console.log(superInjector.dependencies())
```

### Removing Dependency
```javascript
superInjector.removeDependency("User");
```

## Middleware
```javascript
superInjector.applyMiddleware("User",function(){
    console.log("Before Injecting User");
})
```

## Error Event
```javascript
let superInjector = new SuperInjector();
superInjector.on("error",message=>{
    console.log(message);
})
superInjector.addDependency("User","User String can't be injected");
```