# camelizeStyleName

此方法用于将连接符形式的css属性名字转化成驼峰式的变量

	// 参考camelize方法解读
	var camelize = require('./camelize');
	var msPattern = /^-ms-/;
	
	function  camelizeStyleName(string) {
		return camelize(string.replace(msPattern, 'ms-'));
	}
	
## 使用

camelizeStyleName('-ms-transtion') // msTranstion;