# Evol
Find your love here, this is the beginning of best online date site/app

Tech stack: MEAN
MongoDB(Performance Not Only SQL), Express(Lightweighted), AngularJS, node.js



Use bootstrap for elegance

## AngularJS: 

(Data binding, front endMVC, both unit and end-to-end test easy)

it's a full-featured SPA framework, with MVC, Data Binding, routing, testing, templates, history

View- $scope-controller, scope is the glue,

Directives: 

Angular-only HTML attributes begins with : ng-app, ng-init, ng-repeat

filter is like function, lowercase, currency

module (model)

Controller for business logic, massage the data

Display using double braces{{}}

ng-model for two way data binding

ng-bind for one way data binding

dependency injection, angular.module(demoapp, [] #here is the DI), view route to different view, magic!



```html
<!DOCTYPE html>
<html>
<script src= "http://cdn.bootcss.com/angular.js/1.4.6/angular.min.js"></script>
<body ng-app="myApp" ng-controller="todoCtrl">

<h2>我的备忘录</h2>

<form ng-submit="todoAdd()">
    <input type="text" ng-model="todoInput" size="50" placeholder="新增">
    <input type="submit" value="新增">
</form>

<br>

<div ng-repeat="x in todoList">
    <input type="checkbox" ng-model="x.done"> <span ng-bind="x.todoText"></span>
</div>

<p><button ng-click="remove()">删除记录</button></p>

<script>
var app = angular.module('myApp', []); 
app.controller('todoCtrl', function($scope) {
    $scope.todoList = [{todoText:'Clean House', done:false}];

    $scope.todoAdd = function() {
        $scope.todoList.push({todoText:$scope.todoInput, done:false});
        $scope.todoInput = "";
    };

    $scope.remove = function() {
        var oldList = $scope.todoList;
        $scope.todoList = [];
        angular.forEach(oldList, function(x) {
            if (!x.done) $scope.todoList.push(x);
        });
    };
});
</script>

</body>
</html>
```

![âangular js moduleâçå¾çæç´¢ç»æ](https://aspblogs.blob.core.windows.net/media/dwahlin/Media/image_2D6D6780.png)

![âangular js moduleâçå¾çæç´¢ç»æ](https://aspblogs.blob.core.windows.net/media/dwahlin/Media/image_67C64CB0.png)

## MongoDB

Sharding
Using Map/Reduce
Map和Reduce。Map函数调用emit(key,value)遍历集合中所有的记录，将key与value传给Reduce函数进行处理。
Map函数和Reduce函数是使用Javascript编写的，并可以通过db.runCommand或mapreduce命令来执行MapReduce操作。

Collection-Table
document - row
field - column
有一些数据库名是保留的，可以直接访问这些有特殊作用的数据库。
admin： 从权限的角度来看，这是"root"数据库。要是将一个用户添加到这个数据库，这个用户自动继承所有数据库的权限。一些特定的服务器端命令也只能从这个数据库运行，比如列出所有的数据库或者关闭服务器。
local: 这个数据永远不会被复制，可以用来存储限于本地单台服务器的任意集合
config: 当Mongo用于分片设置时，config数据库在内部使用，用于保存分片的相关信息
MongoDB中聚合(aggregate)主要用于处理数据(诸如统计平均值,求和等)，并返回计算后的数据结果。有点类似sql语句中的 count(*)。
mongodump and mongorestore
mongostat

Deployment: Docker (Docker is not leveraged at this point, this will be used for minimizing deployment and configuration efforts), 



## TDD Testing:

Client/UI --- Selenium
Server --- Mocha

```javascript
var assert = require('assert');
describe('Array', function() {
  describe('#indexOf()', function() {
    it('should return -1 when the value is not present', function() {
      assert.equal([1,2,3].indexOf(4), -1);
    });
  });
});
```

Phase 1: Design note

Phase 2: Implement

Phase 3: Iteration and maintain

## ExpressJS

route

```javascript
app.get('/', function (req, res) {
  res.send('Hello World!');
});
```

