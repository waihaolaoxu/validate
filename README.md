# validate
jquery表单验证插件
# 验证方法
<ul>
	<li>required：必填</li>
	<li>email：邮箱</li>
	<li>phone：手机号</li>
	<li>number：数字</li>
	<li>url：url</li>
	<li>idcard：身份证号码（支持尾号为x字母）</li>
</ul>
# 使用方法
<pre>
&lt;form action="" id="form"&gt;
	&lt;input type="text" validate="required|phone"&gt;
	&lt;input type="submit" value="提交"&gt;
&lt;/form&gt;
</pre>
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
