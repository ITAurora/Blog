---
title: js中数组Array的相关方法
date: 2020-11-27 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/5.jpg
banner_img: ../articleImages/5.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
	</body>
</html>
<script type="text/javascript">
	var a1 = [9, 78, 34,"哈哈", 298, "哈哈", 34];
	a1.pop();//删除末尾元素
	a1.push("在末尾新增");
	a1.shift();//删除第一个元素
	a1.unshift("在第一个位置新增元素");
	a1.splice(2,0, "哈哈", 90);
	console.log(a1);
	//新增
	//1.拼接
	var a2 = ["哈哈", "喜之螂", "娃娃鱼"];
	var newArray = a1.concat(a2);
	console.log(newArray);
	//2.查看元素在数组中的下标   如果元素不存在 则返回-1  因为下标从0开始不可能会有-1
	//indexOf() 查找元素第一次出现的下标  找到停止!!!
	var index = a2.indexOf("大鲨鱼"); //默认从下标0开始查找
	console.log(index);
	//以后再查找元素是否存在  就使用此方法!!!
	index = newArray.indexOf("哈哈", 5);//从下标5开始查找
	console.log(index);
	//lastIndexOf()  查找的是最后一次出现的下标!!
	index = newArray.lastIndexOf("哈哈");
	console.log(index);
	
	index = newArray.indexOf("哈哈");
	while(index != -1){
		console.log("-------------" + index);
		index = newArray.indexOf("哈哈", index+1);
		
	}
	//3.数组反转
//	newArray.reverse();
//	console.log(newArray);
	//4.数组转字符串
	var str = newArray.join();
	console.log(str);
	console.log(newArray.toString());
	
	//5.slice  从下标2开始截取  截止到下标6,但是不包含结束下标上的元素!!
	var arr = newArray.slice(2, 6);
	console.log(arr);
	
	//6.sort 排序 默认升序,并且不是按照大小是按照ASCII值!!!
	//并且是根据字符对应下标上的数值进行对比的
	var a1 = [12, 16, 111, 222, 234, 26, 21];
	a1.sort(function(obj1, obj2){
		//obj1就表示数组中0下标元素  那么obj2就表示下标1元素
		//注意!!此函数  只有在返回值 > 0 是正数!!!   才会内部交换元素值!!
		return obj1 - obj2;
	});
   console.log(a1);
   
    var a2 = ["abc", "abb", "bc","l", "f", "gg", "AC","ud", "m", "s"];
    for(var s in a2){
    	console.log(a2[s]);
    }
    console.log(a2.sort());
    console.log(a2.sort().reverse());
   //-------------------------------------------
     var stu1 = {
     	name:"Lily",
     	age:19
     };
      var stu2= {
     	name:"Aurora",
     	age:13
     };
      var stu3 = {
     	name:"Jack",
     	age:24
     };
      var stu4 = {
     	name:"Rose",
     	age:21
     };
     
     var a3 = [stu1, stu2, stu3, stu4];
     //注意  {}对象 一般不能直接排序  因为需要根据某个属性排序
     a3.sort(function(s1, s2){
     	return s1.age - s2.age;
     });
     console.log(a3);
   
   //9.for ...in遍历方式  对象级别的 
   //index的位置 就是接收一个一个的下标!!
   //a3 就是需要遍历的容器的位置!!
   for(var index in a3){
   	
   	 console.log(a3[index]);
   }
   
</script>
```
运行结果:
![](https://img-blog.csdnimg.cn/a79efd52e683406fba24d679997d768f.png)
