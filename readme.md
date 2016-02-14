# LAB: Use AngularJS to create a simple Calculator in a CodePen

The purpose of this lab it to let the students get more practice with using an AngularJS controllers.
The controller provides data and methods for the view to display and interact with.

In addtion this lab uses the following built-in AngularJS directives:

* ng-app
* ng-controller
* ng-click

## Codepens

* [Starter](http://codepen.io/drmikeh/pen/raNMQv)

## Starter Code

### HTML

```html
<div ng-app="myApp" ng-controller="myController as ctrl">
  <h1>Simple Calculator with AngularJS</h1>
  <h3>Enter amount 1: <input type="number"
                             ng-model="ctrl.amount1"></h3>
  <h3>Enter amount 2: <input type="number"
                             ng-model="ctrl.amount2"></h3>
  <button ng-click="ctrl.add();">Add</button>
  <button ng-click="ctrl.sub();">Sub</button>
  <button ng-click="ctrl.clear();">Clear</button>
  <h3>The result is {{ ctrl.result | currency }}</h3>
</div>
```

#### Observations

* We bootstrap AngularJS via the `ng-app` directive.
* We use the "controller as" syntax to bind a controller object to the view.
* We bind the number input controls to the ctrl properites `ctrl.amount1` and `ctrl.amount2`
* We have 3 buttons with 3 `ng-click` handlers.
* We display the result as a data binding to the ctrl property `ctrl.result`.
* We use the built-in AngularJS `currency` filter to display the result.

### CSS

```css
body {
  padding: 20px 40px;
  font-family: "Verdana";
}

h1 {
  text-align: center;
}

button {
  font-size: 1.2em;
  color: blue;
  background: yellow;
}
```

#### Observations

* We have some simple CSS styling (not much to say here).

### JavaScript

```javascript
angular.module('myApp', []);

angular.module('myApp')
.controller('myController', function() {

  var vm = this;

  vm.clear = function() {
    vm.result = 0;
    vm.amount1 = 0;
    vm.amount2 = 0;
  }

  vm.clear();

  vm.add = function() {
    vm.result = vm.amount1 + vm.amount2;
  };
  vm.sub = function() {
    vm.result = vm.amount1 - vm.amount2;
  };
});
```

#### Observations

* We create an AngularJS _module_ called `myApp`.
* We create an AngularJS _controller_ that is connected to the `myApp` module.
* We have assigned the controller `this` object to the variable `vm` to make it easier to reference in nested functions.
* We have declared a few methods: `clear`, `add`, and `sub`.
* Each method makes references to the controller's properties: `result`, `amount1`, and `amount2`.

## For Student Practice

* Add some more methods and buttons for math operations such as `multiply` and `divide`.

## Bonus

* Try building other calculators, such as:
  - a salary calculator - enter the annual salary and calculate the monthly, weekly, and hourly rate.
  - a unit converter - enter a distance in feet and calculate the distance in meters.
  - a financial loan calculator - enter the amount of loan and the interest rate and number of payments and calculate the payment amount.
