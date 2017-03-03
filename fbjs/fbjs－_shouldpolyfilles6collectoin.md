# fbjs－_shouldPolyfillES6Collectoin

 此文件用来检测是否使用原生的es6集合方法,返回值为布尔类型，true：使用polyfill； false：使用es6的原生方法。
 
 
## 使用方法：
 
 	shouldPolyfillES6Collection（'Map'）
 
 主要的知识点如下：
 
  1. gobal 获取全局的是否支持某个方法
  	
  		global['Map'] 返回true 或者false
  		
  2. global.Symbol的值是否为函数，  只有global.Symbol为函数的情况下，才能执行迭代。
  
  
## 题外知识点
  
es6中的集合方法： Map， Set，WeakMap
 
####  Set

 有序列表集合，不会包含重复项.包含add(item), has(item), delete(item), clear()等方法，包含size属性.Set中NaN只能添加一次，Set中 0 －0 ＋0 可以同时存在。
 
#### Map

Map是es6中新增的有序键值对集合，键值对的 key 和 value 都可以是任何类型的元素。包含set(key, value), get(key), has(key), delete(key)等方法，包含size属性。 

⚠️注意：**Set和Map只能通过for...of 来遍历**

#### WeakMap
WeakMap也是键值对集合，只不过WeakMap的key只能是非空对象。WeakMap的最大好处是避免内存泄漏。WeakMap没有size属性，也不能被迭代。
 
 