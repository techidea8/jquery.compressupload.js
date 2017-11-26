demo:
<!doctype html>
<html>
<head>
<title>www.imwinlion.com压缩上传解决方案</title>
<meta http-equiv="Content-Type" content="text/html;charset=UTF-8" />
<meta name="viewport" content="initial-scale=1.0, maximum-scale=1.0,user-scalable=no" />
<meta charset="utf-8" />
<meta name="renderer" content="webkit|ie-stand|ie-comp" />
<script src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="jquery.compressupload.js"></script>

</head>
<body>
<img src="" id="prev" style="height:120px;">
<input type="file" name="file" id="filedom" />
<input type="hidden" value="" id="fileurl" name="fileurl" />
</body>
</html>
<script>
function onpickup(e){
    console.log("onpickup",e)
    $("#prev").attr("src",e.target.result)
}
$(function(){
     
        $("#filedom").compressandupload({
            onpickup:onpickup,
            "maxWidth":200,
            maxHeight:200,
            quality:0.1,
            serveurl:"/attach/upload"
            }).then(
                function(result){
               console.log("result",result)
             })

    })
</script>

参数说明
/*
 * maxWidth:int,压缩后图片的最大宽度,默认400
 * maxHeight:int,压缩后图片的最大高度,默认400
 * quality:float,压缩图片质量,0-1之间小数,默认0.92
 * serveurl:string,后端处理上传的连接地址,
 * minSize:int,小于这个大小的文件都不压缩,
 * onpickup:function,当文件选中即进行的回调,我们一般使用 e.target.result 
 * 这是该文件的base64编码,
 * 类似于这样,data:image/png;base64,iVBORw0
 * 我们可以使用用来做预览,
 * postarg:{}//用户自定义的上传参数,如用户id等
 * base64key:string,后端接收base64文件编码参数的名字,默认为base64data
 * 
 * @result:该函数封装了jquery 的promis 对象,因此采用then的方式,无返回
 * 
 **/
