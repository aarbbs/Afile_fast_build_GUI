# Afile_fast_build_GUI

批量管理 makefile 和快速编译。

## 源码使用说明

注意：【Runy】大佬提供的回显方法，需要在 process.popen 中添加 each2 方法
```
	each2 = function(winform,callback,finish){ //在process.popen库里面添加这个each2方法
		var id = ..table.push(..varpool,callback);
		var finishid = ..table.push(..varpool,finish);
		var winform = ..win._form.getForm(winform.hwnd)
		winform.setTimeout(
    		function(){
        		for( all,out,err in this.each() ){
    				winform.webview.invoke("window.invoke",id,all,out,err)
				}
    			winform.webview.invoke("window.invoke",finishid)
    		}
    		,0
		)
	};
```

【Runy】大佬提供的aardio WebView2 示例代码：
```javascript
import process;
import process.popen;
import win.ui;
import web.view;
import console;

namespace process{
    ..process_ = self
}


var winform = win.form();

winform.show();

var webview = web.view(winform);
winform.webview = webview;

..varpool = table.array();

var aardio = {
	winform:winform,
	webview:webview,
	process:..process,
	process_:..process_,
	varpool:..varpool
};

webview.exportHostObject("aardio",aardio);

webview.html = `
<script>
    var aardio = window.chrome.webview.hostObjects.aardio;
	var aardios = window.chrome.webview.hostObjects.sync.aardio;
	window.invoke = (id,...data)=>{aardios.varpool[id - 1](...data)}

    var p = aardios.process_.popen("ping baidu.com")
    p.each2(aardios.winform,(a,o,e)=>{
        document.write(o + '</br>')
    },()=>{
    	document.write("运行结束")
    })
</script>
`

win.loopMessage();
```

## 运行demo演示

![d7f9551639ed6253462eff74ce680b1b.gif](https://img.aarbbs.com:1024/images/2022/06/04/d7f9551639ed6253462eff74ce680b1b.gif)


## 关于制作该程序时，遇到的问题和解决方案

![c19540abca1d993273d8aa3fc3ab0508.png](https://img.aarbbs.com:1024/images/2022/06/05/c19540abca1d993273d8aa3fc3ab0508.png)