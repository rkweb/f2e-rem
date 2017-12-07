# f2e-rem
rem布局
## 移动端头部 ##
    <meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0,  user-scalable=0;" name="viewport" />
## css缩放 ##
    @media screen and (max-height: 500px) {
	  .scale {
	    -webkit-transform: scale(0.9);
	    transform: scale(0.9);
	    -webkit-transform-origin: center center; 
	  } 
	}
	
	
	@media screen and (max-height: 450px) {
	  .scale {
	    -webkit-transform: scale(0.8);
	    transform: scale(0.8);
	    -webkit-transform-origin: center center; 
	  } 
	}
## js ##
    
	function rem(psd) {
		document.documentElement.style.fontSize = 100*document.documentElement.clientWidth / psd + 'px';
	}
	
	rem(640);//传psd宽度

## 注意 ##


1. 背景图要加`background-size:cover`属性
2. img要写width和height
3. 100px = 1rem 可以直接换算
4. js代码最好放在head里面


## demo ##
[点击查看](http://test.go.163.com/go/2017/1009/rem/)
