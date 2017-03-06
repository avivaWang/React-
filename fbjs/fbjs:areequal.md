# fbjs/areEqual
此文件用来检测两个值是否相等，传入的值可以是基本数据类型、数组、对象。如果两个参数有相同的键名和键值完全相同，则返回true。

## 函数解读

### 第一步
	
	if (a === b) {
		return a !== 0 || 1 / a == 1 / b;
	}
	
这两句，首先判断a 和 b 两个参数的值是否完全相等， 如果完全相等， 则进一步判断 0 === -0 的这种情况。js中 0 === -0 返回true。但是实际上0 和 －0 有着不同的含义， 所以这里进一步判断：
	
	如果 a !== 0 则直接返回true 
	如果 a === 0,
	那么 1 ／ 0 等于Infinity 
	1 / -0 等于-Infinity 
	Infinity 与 －Infinity 不相等，通过这种方法就可以判断出 0 与 －0 不相等
	
### 第二步
如果不符合 a === b的这种情况，继续往下判断，判断a是null，b是undefined的这种情况。因为null == undefined是true, 但是null === undefined 是false，这里也是为了第三步判断两个对象完全相等做铺垫，把null和undefined这种情况先一步排除掉。
	
	if (a == null || b == null) {
		return false;
	}

### 第三步
继续判断类型，出了object类型，只要不通过第一步 **===**则返回false，也就是说基本类型的对比通过 === 就可以满足大多数情况。这里的意思是只要a和b中有一个是**基本类型** 不是**object类型**，如果没有通过前两步的判断， 那就返回false

	if (typeof a != 'object' || typeof b !== 'object') {
		return false;
	}
### 第四步
代码程序走到这里，基本上就剩下object类型的数据了。

	var objToStr = Object.prototype.toString;
	var className = objToStr.call(a);
	if (className != objToStr.call(b)) {
		return false;
	}

如果a和b的通过toString返回的数据不完全相等 则返回false


### 第五步
分别判断不同的情况

	switch(className) {
		case '[object String]':
			return a == String(b);
		case '[object, Number]':
			return isNaN(a) || isNaN(b) ? false : a == Number(b);
		case '[object Date]':
		case '[object Boolean]':
			return +a == +b;
		case '[object RegExp]':
			return a.source == b.source && a.global == b.global && a.multiline == b.multiline && a.ignoreCase == b.ignoreCase;
	}



