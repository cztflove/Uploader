# Uploader
uploader是一个可兼容pc端和移动端的上传插件，能满足各种项目的要求，可选择是否开启裁剪、使用base64上传/文件上传，依赖于webUploader和photoClip等多个插件，简单易用

## 配置项
- inputFile: {Selector} [可选] [默认值：'#filePicker'] 指定选择文件的按钮容器
- use_base64: {Boolean} [可选] [默认值：true] 是否使用base64上传（注：开启裁剪的情况下必须使用base64）
- auto: {Boolean} [可选] [默认值：false] 是否开启自动上传
- dnd: {Selector} [可选] [默认值：false] 指定Drag And Drop拖拽的容器
- uploadUrl: {String} [可选] [默认值：''] 使用文件上传时上传的接口地址
- multiple: {Boolean} [可选] [默认值：false] 是否允许上传多张图片
- fileNumLimit: {Number} [可选] [默认值：30] 上传文件数量的最大限制
- fileSizeLimit:{Number} [可选] [默认值：7*1024*1024] 上传文件的最大文件大小
- isCrop: {Boolean} [可选] [默认值：false] 是否开启裁剪
- cropW: {Number} [可选] [默认值：200] 剪裁框宽度
- cropH: {Number} [可选] [默认值：200] 剪裁框高度度
- submitBtn: {Selector} [可选] [默认值：''] 触发上传文件队列的按钮
- onclipFinish: {Function} [可选] [参数—src：裁剪完成返回的base64] 完成剪裁后执行函数
	
- onFileQueued: {Function} [可选] [参数—src：缩略图base64;file:对应的文件对象] 文件加入队列后触发事件
- onStartUpload: {Function} [可选] [参数—无] 文件开始上传触发事件
- onUploadFinished: {Function} [可选] [参数—无] 文件上传完成触发事件
- onUploadSuccess: {Function} [可选] [参数—res:后台返回的数据] 文件上传成功触发事件
- onUploadError: {Function} [可选] [参数—无] 文件上传失败触发事件
> 注：onStartUpload、onUploadFinished、onUploadSuccess、onUploadError事件只有在使用文件队列上传的时候才会触发
