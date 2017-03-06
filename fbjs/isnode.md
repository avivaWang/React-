# isNode

返回一个对象是否是DOM节点

	function isNode(object) {
		return !!(object
		&& (typeof Node === 'function' ? object instanceof Node : typeof object === 'object'
		&& typeof object.nodeType === 'number' && typeof object.nodeName === 'string'));
	}
	
	
## 知识点

1. typeofNode 在浏览器中运行返回值为function， 而在node环境中运行则返回undefined。
2. DOM节点的nodeType值是number类型的，1是Element 2 是Attr 3 Text 8 注释 10 documentType
3. DOM节点的nodeName属性是string类型的。“DIV”、“SPAN” 等等


# isTextNode

用来判断一个对象是否是文本节点

	function isTextNode(object) {
		return isNode(object) && object.nodeType == 3;
	}
	
文本节点的nodeType为3。


# containsNode

此函数用来判断一个node节点是否包含另一个node 节点， 接受两个参数：outerNode，innerNode。如果innerNode在outerNode的内部则返回true，否则返回false。

1. 如果outerNode或者innerNode不存在， 则直接返回false
2. 如果outerNode和innerNode完全相等， 则直接返回true
3. 如果outerNode是文本节点， 则返回false。因为文本节点内部不能包含其他的节点
4. 如果innerNode是文本节点，则获取innerNode的parentNode，然后继续调用此函数
5. 如果outerNode有contains方法，则直接返回outerNode.contains(innerNode)的结果，此方法为IE最先支持，后来大部分的浏览器也支持。
6. 最后调用w3c的标准方法compareDocumentPosition，该方法返回值可能为：
	* 0 元素一致  000000	
	* 1 节点在不同的文档 000001
	* 2 节点innerNode在outerNode之前 000010
	* 4 outerNode在innerNode之前 000100
	* 8 innerNode包含outerNode 001000
	* 16 outerNode包含innerNode 010000
	* 32 浏览器私有使用 100000
	
	
## 知识点

1. 了解contians 方法
2. 了解compareDocumentPosition方法及其返回值
3. 了解 & 运算 。& 是按位与运算。 在运算之前需要将数据转换成二进制进行运算。

	var a = 1, b = 16, c = 16;
	console.log(a && b) // true
	console.log(a & b) // 0 实际上就是 000001 & 010000 ＝ 000000
	console.log(b & c) // 16
	
