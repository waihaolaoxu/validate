# validate
jquery表单验证插件
# 内置验证方法
<ul>
	<li>required：必填</li>
	<li>email：邮箱</li>
	<li>phone：手机号</li>
	<li>number：数字</li>
	<li>url：url</li>
	<li>idcard：身份证号码（支持尾号为x字母）</li>
</ul>
# 可选参数
<ul>
	<li>error：function  错误信息（obj,err） 返回当前（jq对象，错误信息的key）</li>
	<li>validate：object  设置自定义验证规则</li>
	<li>messages：object  设置错误提示信息</li>
	<li>isone：Boolean  开启单条验证默认为false</li>
	<li>submitBtn：object  设置提交按钮提交状态</li>
	<li>ids：Array  设置指定表单元素提交</li>
</ul>
# 使用方法
html
<pre>
&lt;form action="" id="form"&gt;
	&lt;input type="text" validate="required|phone"&gt;
	&lt;input type="submit" value="提交"&gt;
&lt;/form&gt;
</pre>
基础用法
<pre>
$('#form').submit(function(){
		var b=$(this).validate();
		if(b){
			alert('验证通过')
		}
		return false
	})
})
</pre>
扩展用法
<pre>
$('#form').submit(function(){
		var b=$(this).validate({
			//自定义错误回调
			error:function(e,t){//接收两个参数 （当前对象，错误信息）
				$(e).addClass("error");
				alert(t);
			},
			//扩展验证方法
			validate:{
				remote:function(e){
					if(e.val()!=666){//自定义验证
						_error(e,'remote');
						return false	
					}
				}
			},
			messages:{ //扩展验证方法后必须的扩展当前方法的错误信息对象名称要保持一直
				remote:'必须输入666'
			},
			submitBtn:{//开启按钮提交状态
				flag:true,
			},
			isone:true //默认为批量验证，如想实现单条验证请设置isone：true
		});
		if(b){
			alert('验证通过')
		}
		return false
	})
})
</pre>
指定表单元素提交
<pre>
$('#form').submit(function(){
		var b=$(this).validate({
			ids:[$('#a'),$('#b')]
		});
		if(b){
			alert('验证通过')
		}
		return false
	})
})
</pre>


