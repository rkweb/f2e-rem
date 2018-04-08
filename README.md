# f2e-rem
rem布局
## meta ##
    <meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0,  user-scalable=0" name="viewport"/>
    
	
## js ##
```
 // rem布局 放入head标签中
(function (psdWidth) {
    var psdWidth = psdWidth ? psdWidth : 640;
    var docEl = document.documentElement;
    var wHeight = window.innerHeight;
    var resizeEvent = 'orientationchange' in window ? 'orientationchange' : 'resize';
    var rem = function () {
	if (wHeight * 0.75 > window.innerHeight) {
	    return
	}; //屏蔽软键盘弹起时触发resize事件（只考虑竖屏）
	var wWidth = window.innerWidth;
	var fontSize = wWidth > 900 ? 100 : 100 * wWidth / psdWidth;
	docEl.style.fontSize = fontSize + 'px';
    }
    rem();
    $(window).on(resizeEvent, function () {
	clearTimeout(timer);
	var timer = setTimeout(rem, 300);
    });
})(640); //传入设计稿宽度




// 内容安全区域等比缩放 
(function (scaleHeight) {
    var wHeight = window.innerHeight;
    var scaleHeight = scaleHeight ? scaleHeight : 1030;
    var scale = function () {
	if (wHeight * 0.75 > window.innerHeight) {
	    return
	}; //屏蔽软键盘弹起时触发resize事件（只考虑竖屏）
	var wWidth = window.innerWidth;
	var wHeight = window.innerHeight;
	var h = 640 / wWidth * wHeight;
	if (wWidth > wHeight) { //横屏判断
	    h = 640 / wHeight * wWidth;
	}
	if (h <= scaleHeight) {
	    $('.scale').css({
		'-webkit-transform': 'scale(' + h / scaleHeight + ')'
	    });
	}
    }
    scale();
    $(window).on('orientationchange' in window ? 'orientationchange' : 'resize', scale);
})(1030) //传入内容安全区域高度（设计稿宽度换算成640）
</script>
```

## 注意 ##


1. 背景图要加`background-size:cover`属性
2. 雪碧图`background-size: 整个雪碧图的宽，整个雪碧图的高`，用`background-position`定位每个小图
3. img要写width和height
4. 100px = 1rem 可以直接换算
5. js代码最好放在head里面
6. chrome模拟手机时，用原始尺寸，不要用原来自己设置的尺寸
7. 当页面中有canvas时，canvas按照设计图尺寸写，最后把canvas整体缩一下
	
```javascript
//当canvas不是全屏
$('canvas').css({
	'width': $(window).width(), 
	'height': canva原始的高度*$(window).width()/640
})
//当canvas是全屏
$('canvas').css({
	'width': $(window).width(), 
	'height': $(window).height()
})
```


## demo ##
[点击查看](http://go.163.com/web/f2e_common/common/f2e-rem/)
