# f2e-rem
rem布局
## meta ##
    <meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0,  user-scalable=0" name="viewport"/>
## css ##
	.wrap{
		width: 6.4rem;
		height: 10.3rem;
		position: absolute;
		left: 50%;
		margin-left: -3.2rem;
		top: 50%;
		margin-top: -5.15rem;
		-webkit-transform-origin: center center; 
	}
    
	
## js ##
```javascript
//放在head里面
function rem(psd) {
	var wWidth = window.innerWidth;
	var fontSize = wWidth > 900 ? 100 : 100*wWidth / psd;
	document.documentElement.style.fontSize = fontSize + 'px';
}
rem(640);//传psd宽度


//放在所有wrap标签下面   给要缩放的wrap加上scale
function resizeRem() {
	if(initHeight*0.75 > $(window).height())return;
	var hh = 640 / $(window).width() * $(window).height();
    if(hh < 1000) {
    	 $('.scale').css({
	    	'-webkit-transform': 'scale(0.9)'
	    });
    }

     if(hh < 900) {
    	 $('.scale').css({
	    	'-webkit-transform': 'scale(0.8)'
	    });
    }
}
resizeRem();
$(window).on('resize', resizeRem);
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
[点击查看](http://test.go.163.com/go/2017/1009/rem/)
