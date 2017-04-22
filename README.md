# myFocus
todoMVC自动获取焦点
JavaScript 引擎在执行 onkeypress 时，由于没有多线程的同步执行，不可能同时去处理刚创建元素的 focus 和 select 事件，由于这两个事件都不在队列中，在完成 onkeypress 后，JavaScript 引擎已经丢弃了这两个事件
解决办法：
```javascript
app.directive('setFocus', function () {
        return {
            link: function (scope, element, attr) {
                element.on('dblclick', function () {
                    console.log(111)
                    var that = this;
                    setTimeout(function(){
                        angular.element(that).parent().next().children()[0].focus();
                    },0);
                })
            }
        }
    });
```
