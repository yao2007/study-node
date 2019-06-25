# Array Map Set

### What is the diff by using Map and using array to implement map? <a id="https-blog-csdn-net-cathar-article-details-53363845"></a>

对象就可以实现Map的功能，为啥要有map？1.JavaScript的对象的键必须是字符串。2.是一组键值对的结构，具有极快的查找速度.



### **iterable类型遍历集合：Array、Map和Set都属于iterable类型**

for … of循环和for … in循环有何区别？前者只取集合本身元素，而不是属性，后者当我们给数组人为天添加属性后，就会方位所有的key，原数组则返回数组下标。

```text
var a = ['A', 'B', 'C'];
a.name = 'Hello';
for (var x in a) {
    alert(x); // '0', '1', '2', 'name'
}
/* for ... in循环将把name包括在内，但Array的length属性却不包括在内。for ... of循环则完全修复了这些问题，它只循环集合本身的元素：*/ 
var a = ['A', 'B', 'C'];
a.name = 'Hello';
for (var x of a) {
    alert(x); // 'A', 'B', 'C'
}
```

### Map and Set method

```text
<script type="text/javascript">
    // 初始化Map需要一个二维数组，或者直接初始化一个空Map
    var m1 = new Map([['a', 'a1'], ['b', 'b2'], ['c', 'c3']]);
    var m11 = new Map([['a', 'a1'], ['b', 'b2'], ['c', 'c3']]);
    var m2 = new Map();
	
    console.log(m1);			// 返回Map  {"a" => "a1", "b" => "b2", "c" => "c3"}
    console.log(typeof(m1));	// object, Map仍属于 object
    console.log(m1 == m11)		// flase  虽然两个Map里面的值一样，但是是属于不同的object

    // 1. size属性，返回 Map的元素数
    console.log(m1.size);		// 3

    // 2. keys()	获取Map的所有key
    console.log(m1.keys());		// 返回 MapIterator {"a", "b", "c"}

    // 3. values()	获取Map的所有value
    console.log(m1.values());	// 返回 MapIterator {"a1", "b2", "c3"}

    // 4. entries()	获取Map所有成员  
    console.log(m1.entries());	// 返回 MapIterator {"a" => "a1", "b" => "b2", "c" => "c3"}

    // 5. forEach()	循环操作映射元素
    m1.forEach(function(value, key, map) {
  	  // value:  key对应的值，  
	  // key: Map的key，(map参数已省略情况下，key可省略)
	  // map:  Map本身，(该参数是可省略参数)
	  console.log(value);			// key对应的值   a1  b2  c3
	  console.log(key);			// key 			a   b   c
	  console.log(map);			// Map本身      Map Map Map
    });

    // 6. set()		给Map添加数据，  返回添加后的Map
    console.log(m2.set('a', 1));	// 返回Map  {"a" => 1}
    console.log(m2.set('b', 2));	// {"a" => 1, "b" => 2}
    console.log(m2.set('a', 11));	// {"a" => 11, "b" => 2} 给已存在的键赋值会覆盖掉之前的值，  

    // 7. has()		检测是否存在某个key， 返回布尔值，有：true； 没有：false
    console.log(m2.has('a'));		// true
    console.log(m2.has('c'));		// false

    // 8. get()		获取某个key的值，返回key对应的值，没有则返回undefined	
    console.log(m2.get('a')); 		// 11
    console.log(m2.get('c'));		// undefined

    // 9. delete()	删除某个key及其对应的value，返回布尔值，成功：true； 失败：false
    console.log(m2.delete('b'));	// true
    console.log(m2.delete('d'));	// false
	
    console.log(m2.get('b'));		// undefined， 因为b已经删除

    // 10. clear()	清除所有的值，返回 undefined
    console.log(m1.clear());		// undefined
    console.log(m1);				// {} 
</script>
```

```text
<script type="text/javascript">
    // 初始化Map需要提供一个Array作为输入，或者直接创建一个空Set
    var s1 = new Set(['a', 'b', 'c']);
    var s11 = new Set(['a', 'b', 'c']);
    var s2 = new Set(['a', 'a', 'b', 'b', 'c', 'c']);
    var s3 = new Set();
	
    console.log(s1);				// 返回 Set(3) {"a", "b", "c"}
    console.log(s2);				// 返回 Set(3) {"a", "b", "c"}
    console.log(typeof(s1));		// object
    console.log(s1 == s11);		// false
    console.log(s1 == s2);		// false
	
    // 1. size属性  返回Set的元素数
    console.log(s1.size);			// 3
	
    // 2. keys() 获取Set的所有key	
    console.log(s1.keys());		// 返回 SetIterator {"a", "b", "c"}
	
    // 3. values()  获取Set的值，返回结果和 keys()一样
    console.log(s1.values());		// 返回 SetIterator {"a", "b", "c"}
	
    // 4. entries() 获取Set所有成员，返回同keys()
    console.log(s1.entries());	// 返回 SetIterator {"a", "b", "c"}
	
    // 5. forEach() 循环操作集合元素	
    s1.forEach(function(v, k, s){	// v、k是集合的键，s是集合本身
	  console.log(v);				//  a   b   c
	  console.log(k);				//  a   b   c
	  console.log(s);				// Set Set Set
    });
    // 6. add()   给集合添加数据	返回添加后的Set
    console.log(s3.add('aa'));		// Set(1) {"aa"}
    console.log(s3.add('bb'));		// Set(2) {"aa", "bb"}
    console.log(s3.add('aa'));		// Set(2) {"aa", "bb"}	添加重复的值，会被排重掉，
	
    // 7. has() 查询集合中是否包含某个元素  返回布尔值 有：true； 没有：false
    console.log(s3.has('aa'));		// true
    console.log(s3.has('ff'));		// false	

    // 8. delete() 删除集合中的某个元素  返回布尔值
    console.log(s3.delete('aa'));	// true
    console.log(s3.delete('ee'));	// false

    console.log(s3);				// Set(1) {"bb"}
	
    // 9. clear()  清除集合的所有值	返回undefined
    console.log(s1.clear());		// undefined
	
    console.log(s1);				// Set(0) {}
</script>
```



## 

### 

