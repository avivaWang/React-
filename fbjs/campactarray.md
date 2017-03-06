# campactArray

此方法用于返回一个新数组，该新数据包含了原数组的所有元素 出了 undefined 和 null。

	function compactArray(array) {
		var result = [];
		for (var i = 0; i< array.length; i++) {
			var elem = array[i];
			if (elem != null) {
				result.push(elem);
			}
		}
		return result;
	}
	

目前该方法也可以通过Array.filter来实现

	var arr = [null, undefined, 1, 2, null, 3];
	var arr2 = arr.filter((item) => {
		return item != null;
	});
	
	console.log(arr2) // [1, 2, 3];