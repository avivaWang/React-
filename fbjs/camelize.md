# camelize

此文件用于将连字符的变量改写成驼峰式的变量

	　var _hyphenPattern = /-(.)/g;
	　
	　function camelize(string) {
	　	return string.replace(_hyphenPattern, function(_, character) {
	　		return character.toUpperCase();
	　	});
	　}
	　
## 知识点

1. 正则法则  **.**  是元字符  其含义用于查找单个字符，出了换行和行结束符
2. () 在正则表达式中可以被用作是一个记忆设备，在后面可以被利用。
3. replace方法 替换与正则表达式匹配的子串。	该方法接收两个参数，第一个参数是子字符串或要替换的模式的 RegExp 对象。 第二个参数是规定了替换文本或生成替换文本的函数。其中第二个参数为函数的情况下，函数的参数为：
	1. 第一个参数为每次匹配的全文本
	2. 中间参数为子表达式匹配字符串，个数不限 $1,$2,...$99
	3. 倒数第二个参数为匹配文本字符串的匹配下标位置
	4. 最后一个参数表示字符串本身
	
## 使用

camelize('background-color') // backgroundColor
	
	
	 	