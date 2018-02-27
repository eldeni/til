```javascript
var lazyProperty = function(target, propertyName, callback){
    var result, done;
    Object.defineProperty(target, propertyName, {
        get: function(){ // Define the getter
            if(!done){
                // We cache the result and only compute once.
                done = true;
                result = callback.call(target);
            }
            return result;
        },
        // Keep it enumerable and configurable, certainly not necessary.
        enumerable: true,
        configurable: true
    });
}
```

### Reference
https://www.sitepen.com/blog/2012/10/19/lazy-property-access/