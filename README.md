# Afile_fast_build_GUI

该程序使用 aardio + WebView2 制作，用于批量管理 makefile 工程，以及实现一键编译等实用功能。

## 源码构建使用说明

### 向 aardio 基础库“process.popen”添加自定义方法 echo2

> 该方法由一位好心的群友【Runy】提供，我自己还没整明白这种写法，总之很感谢【Runy】能教我这个方法。
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

### aardio + WebView2 示例代码：

> 示例代码也是由【Runy】。
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

### Afile_fast_build_GUI 运行demo演示

![d7f9551639ed6253462eff74ce680b1b.gif](https://img.aarbbs.com:1024/images/2022/06/04/d7f9551639ed6253462eff74ce680b1b.gif)


## Afile_fast_build_GUI 使用说明

。。。待补充