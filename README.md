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
				$(e).addClass("error").text(t);
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
			}
		});
		if(b){
			alert('验证通过')
		}
		return false
	})
})
</pre>

