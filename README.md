# JScollab 
1. Create promise polyfill
2. Bind polyfill without using call apply
3. What is scope its datatype (in depth)
4. Function hoisting (tricky)
5. this keyword
6. create object without using object (object datastructure without using objects and its methods)
7. create array without using array and implemet push, pop, length
8. create sets using objects and its methods
9. Make a react login component with two fields using hooks and submit data
10. Debounce throttle
11. Preflight request
12. Steps to solve CORS from FE
13. var input = {
  a: {
    d: {},
    b: {
      c: [],
    },
  },
  e: 'e',
  f: null,
  g: -2,
};
// expected output for above input, should be an array with all these keys in any order
var output = ['g', 'f', 'e', 'a.b.c', 'a.d'];

14. currying


# Bind function (without using call OR apply)
var myBind = function (context) {
    const toBeCalled = this;
    return function (){
        const args = Array.from(arguments);
        context['toBeCalled'] = toBeCalled;
        context.toBeCalled(...arguments);
    }
}

Function.prototype['myBind'] = myBind;

# Apply function

var myApply = function (context, args){
    context['c'] = this;
    context.c(...args); 
}

Function.prototype['myApply'] = myApply;

# Call function
var myCall = function () {
    const args = Array.from(arguments);
    const context = args[0];
    context['toBeCalled'] = this;
    context.toBeCalled(...args.slice(1));
}

Function.prototype['myCall'] = myCall;


# Preflight
A CORS preflight request is a CORS request that checks to see if the CORS protocol is understood and a server is aware using specific methods and headers. CORS relies on a mechanism by which browsers make a "preflight" request to the server hosting the cross-origin resource, in order to check that the server will permit the actual request. In that preflight, the browser sends headers that indicate the "HTTP method" and "headers" that will be used in the actual request.

- OPTIONS CALL request by browser
Access-Control-Request-Method: POST
Access-Control-Request-Headers: origin, x-requested-with

- Response by cross-origin server
Access-Control-Allow-Methods: POST, GET, OPTIONS, DELETE
Access-Control-Allow-Origin: https://foo.bar.org



# Bundling
The best way to introduce code-splitting into your app is through the dynamic import() syntax.

```
import("./math").then(math => {
  console.log(math.add(16, 26));
});
```
When Webpack comes across this syntax, it automatically starts code-splitting your app. 



# Forwarding Ref
Ref forwarding is a technique for automatically passing a ref through a component to one of its children. 
Ref forwarding is a feature that lets some components take a ref they receive, and pass it further down (in other words, “forward” it) to a child.

```
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="FancyButton">
    {props.children}
  </button>
));

// You can now get a ref directly to the DOM button:
const ref = React.createRef();
<FancyButton ref={ref}>Click me!</FancyButton>;
```


# Booleans, Null, and Undefined Are Ignored
false, null, undefined, and true are valid children. They simply don’t render. These JSX expressions will all render to the same thing:
 
