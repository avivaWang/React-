# concatAllArray

此方法用于将多维数组合并为一个一维数组

	
## 知识点
	
	Array.prototype.push.apply([], [1,2,3]);
	
call和apply 都是为了改变某个函数运行时的 context 即上下文而存在的，换句话说，就是为了改变函数体内部 this 的指向。

call和apply不同的地方在于， call的参数需要一一指明，而apply则需要将所有的参数放入一个数组中。

举例子：
	
	var func1 = function(arg1, arg2) {
		// some code
	}
	
	// call
	func1.call(this, arg1, arg2);
	
	// apply
	
	func1.apply(this, [arg1, arg2]);
	

明白了call和apply的含义， 我们来看Array.prototype.push.apply([], [1,2,3]);这句话

实际上就是
	
	[].push(1, 2, 3);
	
	
有人会问 那我直接使用 [].push() 不就好了吗 为何要用apply呢？

‼️请注意传递参数的类型， push方法不接受数组作为参数。
	
	[].push([1,2,3]); // [[1, 2, 3]]
	
	
所以这里我们通过apply方法改写一下 就相当于

	[].push(1, 2, 3);