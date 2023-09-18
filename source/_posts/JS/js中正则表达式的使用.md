---
title: js中正则表达式的使用
date: 2020-12-14 11:10:10
tags:
  - JS
categories:
  - 前端三剑客
index_img: ../articleImages/6.jpg
banner_img: ../articleImages/6.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		
	</body>
</html>
<script type="text/javascript">
	/*
	正则表达式:按照指定的规则检测或者替换满足对应条件的字符串.通常多用于数据格式验证!
	
	1.如何创建正则表达式?
	new RegExp(参数1, 参数2);
	参数1:指定要匹配的规则,必须是字符串类型
	参数2:设置规则匹配的范围,可选值(可写可不写)
	范围写法:
	i  忽略大小写
	m  允许多行查找
	g  全局查找
	若没有指定参数2,默认查找到首次遇见满足规则的位置,就会停止查找! 如果设置g,则会一直查找到字符串末尾!!!
	*/
	
	//测试开始!!!!!!!!!!!!!!!!
	var str1 = "AbcBCadfg";
	//创建正则对象
	//检测是否包含 "ab"
	var reg = new RegExp("ab", "i");
	/*
	 正则对象的方法:
	 test() 检测指定字符串是否满足正则设置的规则,若满足就返回true; 若不满足则返回false;
	 */
	var isOK = reg.test(str1);
	console.log(isOK);
	
	//方式2---------------------简写形式 
	// 注意格式:   /参数1/参数2
	var reg1 = /ab/i;
	console.log("简写形式:" + reg1.test(str1));
	
	//--------------------------------------------
	/*
	 参数1的位置,专门设定了一些规则代称:
	 1.可以设置普通字符,例如"a"  "ab"  "12" "1a" "s" "中文"...等
	 2.元字符  (就是正则提供的一些字符代称)
	 \d    数字 等价于 [0123456789] 等价于 [0-9]
	 \D    非数字
	 \w    数字,字母,下划线
	 \W    非数字,字母,下划线
	 \s    空白(空格,换行,tab键)
	 \S    非空白
	 .     除\n之外的其他字符
	 \b    匹配单词的边界
	 
	 \n    换行
	 \t    tab键,制表键
	 \r    回车键
	 3.如果匹配转义字符,就例如想匹配  .  需要设置为  \. 才是匹配 .这个字符 
	 例如: 匹配邮箱  163\.com   这样.才是普通字符串.
	 
	 4. []用于匹配括号中出现的字符
	 5. 连字符  -  用于指定字符的范围 例如: 0-9
	 
	 6.量词 关键符号是{}
	 {m} 出现m次
	 {m, n} 最少出现m次, 最多出现n次
	 {m, } 最少出现m次
	 +   等价于{1, } 至少出现1次即可
	 ?   等价于{0, 1} 0到1次, 类似 有无
	 *   等价于{0,} 可以没有,也可以有无限个
	 
	  7.限定符
	  ^   必须以某某开头  例如: ^a 那就是必须以a开头
	  $   必须以某某结尾  例如: [(com)|(cn)]$  那就是必须是com或者cn结尾
	  |   或者
	  
	 */
	
	
	//测试--
	//1.是否包含数字
	var r1 = /\d/;
	console.log("是否包含数字", r1.test("1abcdefg"));
	var r2 = /\D/;
	console.log("是否包含非数字", r2.test("78*78979"));
	var r3 = /\w/;
	console.log("是否包含数字或字母或下划线", r3.test("   _&&**"));
	var r4 = /\W/;
	console.log("是否包含非数字字母下划线", r4.test("738jhj=+kj_3_"));
	var r5 = /\s/;
	console.log("是否包含空白", r5.test("666 "));
	var r6 = /\S/;
	console.log("是否包含非空白", r6.test("   j"));
	var r7 = /./;//  这个点 .不是匹配字符串 .
	console.log("是否包含非换行", r7.test("abc"));
	//怎么判断是否包含  .这个字符串呢
	var r8 = /\./;
	console.log("是否包含.这个字符串", r8.test("a.bc"));
	//匹配是否有字母d  不要怕:  \d才是数字   普通的写法 d就是字母d
	var r9 = /d/;
	console.log("是否包含字母d", r9.test("adbc"));
	//单词边界符
	var r10 = /ab\b/;
	console.log("单词边界是否是ab", r10.test("cb ccc"));
	console.log("单词边界是否是ab", r10.test("cb cab ggg"));
	console.log("单词边界是否是ab", r10.test("cb ccc abc"));
    // []范围
    var r11 = /[ab]/;
    console.log("是否包含a或者b", r11.test("sssagg"));
    console.log("是否包含a或者b", r11.test("bbbbc"));
    var r12 = /[a-zA-Z0-9_]/;
    console.log("是否包含数字大小写字母或者_", r12.test(" ..s..???+++"));
    //加上量词  {} 量词内不要加空格
    var r13 = /ab{2,8}/; //a一次 b至少2次   abb 
    console.log("是否包含a而且b至少2最多6次", r13.test("abbbbb hjk"));
    var r14 = /(ab){2,6}$/;
    console.log("是否包含ab,2-6次", r14.test("ababababababababababababab 必须连在一起至少两遍"));
	var r15 = /a{2,}/;
	console.log("是否包含a至少连续2次", r15.test("abaaaa"));
	var r16 = /^[a-z]{6}/;
	console.log("是否以小写字母开头", r16.test("asfsfds23zbsd"));
	var r17 = /(com)$|(cn)$/;
	console.log("是否以com或者cn为结尾", r17.test("abc345cn"));
	//练习:
	//手机号 11位
	var r18 = /^1[3-9]\d{9}$/;
	console.log("手机号", r18.test("132345678987"));
	//密码  6--16位  字母数字_组合,但是数字不能开头
	var r19 = /^[a-zA-Z]\w{5,15}$/;
	console.log("密码6-16位,数字不可开头", r19.test("abca_bn"));
	//判断正数  +量词 {1,}
//	/^\d+$/    /^\d{1,}$/
   var r20 = /^\d+$/;
   console.log("正数", r20.test("2a34"));
   
   //判断小数  正数负数都有小数   问号?是量词
// /^\-?\d+\.\d+$/    为甚 减号-需要转义?? 因为   -是连字符 例如a-z
  var r21 = /^\-?\d+\.\d+$/;
   console.log("是否是小数", r21.test("28.89"));
 //判断是否以 http:// 开头
// /^http:\/\/    注意  //是注释符号.需要通过  \/ 来转义!!
	var r22 = /^http:\/\//;
	console.log("是否以http://开头", r22.test("http:/www.baidu.com"));
	 
	//注意:量词加上定界符整体判断才更准确!以后有需要匹配的字符串规则,先百度!!
	//学习正则不要求每种规则都自己会写!!只要求能看懂,并且会用在代码中即可!
	//注意但凡是以上出现的元字符,连字符等特殊字符,要想当做普通字符串使用! 就一定要设置反斜杠\ 来转义!!
	//例如 .             \.  
	//例如/              \/ 
	//例如-连字符                  \-
	//例如?              \?
	
	
</script>
```
![](https://img-blog.csdnimg.cn/0d019c90fa124e199c52f4821d6dd241.png)

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
	
	/*
	 字符串中用于替换子串的函数,也可识别正则写法
	 replace(参数1, 参数2)
	 参数1如果是正则对象,那么就会将满足正则规则的子串都替换为参数2
	 参数2 就是新字符串
	*/
	
	var str1 = "abcdfgabdjfabdkfab";
	var r1 = /ab|f/g;
	var s1 = str1.replace(r1, "**");
	console.log(s1);
	
	//字符串中的match() 参数是字符串,则是查找是否含有指定的子字符串; 若参数是正则对象,则是查看满足指定规则的字符串并且以数组形式返回!!!
	//以str1为例子
	//参数为字符串  没有默认全局查找的功能
	var a = str1.match("ab");
	console.log(a);
	//参数是正则对象  更灵活更强大
	var a = str1.match(/ab|g|f/g);
	console.log(a);
	
	//字符串中的方法 search()  参数是字符串,则是查找对应字符串瘦子出现的位置下标;若没有找到,则返回-1; 若参数是正则对象,则是查找满足指定规则的子字符串首次出现的位置下标,若没有,则返回-1;但是正则写法更灵活 支持全局查找 支持多字符查找
	str1 = "你说什么狗子?你想吃骨头?不爱吃骨头的狗子不是好狗子!";
	//参数是字符串
	var a  = str1.search("狗子");
	console.log(a);
	//参数是正则对象   支持全局但是也只能查找到第一次出现的位置
	a = str1.search(/狗子|骨头/g);
	console.log(a);
	
	//字符串方法 split() 字符串  正则对象  最常用----重要!!!
	a = str1.split("狗子");
	console.log(a);
	a = str1.split(/狗子|骨头/);
	console.log(a);
	
</script>

```
![](https://img-blog.csdnimg.cn/5b421ce94e894f09be7f860164263d18.png)
