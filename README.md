## Uploader v2.0
uploader是一个可兼容pc端和移动端的上传插件，能满足各种项目的要求，可选择是否开启裁剪、使用base64上传/文件上传，依赖于webUploader和photoClip等多个插件，经过多个项目实践，兼容性良好，简单易用
## 开始使用
#### 加载插件

```
<script src="http://cdn.bootcss.com/jquery/2.2.1/jquery.min.js"></script>
<script src="js/webuploader.js"></script>
<script src="js/hammer.min.js"></script> //需要裁剪功能才引入
<script src="js/iscroll-zoom.js"></script> //需要裁剪功能才引入
<script src="js/lrz.all.bundle.js"></script> //需要裁剪功能才引入
<script src="js/photoClip.min.js"></script> //需要裁剪功能才引入
<script src="js/uploader.js"></script>
```
#### html内容
```
<div class="btn" id="filePicker">选择文件</div>
```
#### 初始化Uploader

```
<script type="text/javascript">
    window.onload = function(){
        myUploader = new uploader({
            submitBtn: '#submit',
            onFileQueued: function(src){
            	var dom  = '<li style="background-image:url('+src+')"></li>';
            	$('.upload-preview-wrapper').append(dom);
            }    			
        });
	};
</script>
```

## 配置选项

| Option | 类型 | 默认值 | 说明 |
| ------------- |:-------------:|:-------------:| :-------------|
inputFile | Selector | #filePicker | 指定选择文件的按钮容器 |
auto | Boolean | false | 是否开启自动上传 |
dnd | false/Selector | false | false时禁用拖拽上传，否则指定Drag And Drop拖拽的容器 |
uploadUrl | String | '' | 文件上传路径（必填） |
multiple | Boolean | false | 是否多张上传  false的情况下会自动将上一个队列文件删除） |
isCrop | Boolean | false | 是否剪裁 |
fileNumLimit | Number | 30 | 上传文件数量的最大限制 |
fileSizeLimit | Number | 7\*1024\*1024 | 上传文件的最大文件大小 |
cropW | Number | 200 | 剪裁框宽度 |
cropH | Number | 200 | 剪裁框高度 |
submitBtn | Selector | '' | 触发上传文件队列的按钮(禁用自动上传时生效) |
onclipFinish | Function | 参数：src—裁剪完成返回的base64 | 完成剪裁后执行函数
onFileQueued | Function | 参数:src—缩略图base64;file:对应的文件对象 |  文件加入队列后触发事件，可获得文件缩略图
onStartUpload | Function | 参数：无 | 文件开始上传触发事件
onUploadFinished | Function | 参数：无 | 文件上传完成触发事件
onUploadSuccess | Function | 参数：res—后台返回的数据 | 文件上传成功触发事件
onUploadError | Function | 参数：无 | 文件上传失败触发事件
## 规则介绍
-  程序会自动判断当前运行环境是pc还是mobile
-  mobile模式下，考虑到兼容各手机性能，若开启裁剪模式，自动上传将默认开启，由后台将上传的文件转成base64后返回再进行裁剪（本公司将返回的base64数据放在data中，若有需要此处可自行到源码修改）；不开启裁剪模式将在onFileQueued中返回缩略图的信息
-  pc模式下，若开启裁剪模式，将在添加文件后开始裁剪；不开启裁剪模式将在onFileQueued中返回缩略图的信息
-  如果是使用chrome的移动模拟，点击上传按钮可能需稍等片刻才会弹出文件框，但在手机上没问题

