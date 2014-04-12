# onImagesLoad
---

图片加载状态检测

## 使用场景
页面上图片多，或者体积大时，由于天朝的网络必然无法秒加载，因此必定需要一定的`加载时间`，当我们需要给用户呈现一个loading过程时，请使用该模块。

需要注意的是，在上面的多图场景中，请使用延迟加载(`lazyload`)模式，所有图片给予一个小尺寸的占位(placeholder)图片，优先加载第一屏图片，其他屏的图片等`scroll`到相应区域(可以设置一定的offset距离提前200px加载)才加载。

> 可以配合`loading`UI模块(`未完成`)使用。

## 使用说明

```javascript
$('.imageSection img').onImagesLoad({
    each : function(selector){
        // 每个图片加载完成回调
    },
    all : function($selector){
        // 所有图片加载完成回调
    },
    callbackIfNoImagesExist: false // 没有图片时是否执行回调函数
});
```

## todo

+ 图片不存在时的处理
+ 增加事件机制


## 参考设计

+ http://www.cirkuit.net/projects/jquery/onImagesLoad/index.html
+ https://github.com/desandro/imagesloaded

