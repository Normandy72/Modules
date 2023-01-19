# Modules in AngularJS
## Steps to create modules
#### Step 1: Declare / Create Module
```
angular.module('module1', []);
```
`.module` - declare module
`'module1'` - unique module name
`[]` - dependencies

##### Specify other modules as dependencies
```
// no dependencies
angular.module('module1', []);
angular.module('module2', []);

// dependent on module1 and module2
angular.module('module3', ['module1', 'module2']);
```
#### Step 2: Declare Module Artifacts
```
angular.module('module1')
.controller('MyController', MyController);
```
`('module1')` - second argument missing!
#### Step 3: ng-app='MainModule'
```
<!DOCTYPE html>
<html ng-app='module3'>
...
</html>
```
## Splitting Javascript into Several Files
```
<script src="src/mod1/module1.js"></script>
<script src="src/mod1/controller.js"></script>

<script src="src/mod2/module2.js"></script>
<script src="src/mod2/component.js"></script>
```
`<script src=".../module1.js"></script>` - declare / create 'module1'
`<script src=".../controller.js"></script>` - retrieve & use to declare Controller

##### Also correct variant
module2 before module1
```
<script src="src/mod2/module2.js"></script>
<script src="src/mod2/component.js"></script>

<script src="src/mod1/module1.js"></script>
<script src="src/mod1/controller.js"></script>
```
##### Incorrect variant
because component uses module2 (using module2 before it's created)
```
<script src="src/mod2/component.js"></script>
<script src="src/mod2/module2.js"></script>
```
## Configuration and Run Blocks
#### .config
```
angular.module('module1')
.config(function(){
    ...
});
```
`function()` - inject only Providers and Constants
#### .run
```
angular.module('module1')
.run(function(){
    ...
});
```
`function()` - inject only Instances (like Services) and Constants