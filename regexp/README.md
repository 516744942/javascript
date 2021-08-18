### 正则表达式

<!--  -->
1. \d: 所有的数字
2. \D: 除了数字
3. \s: 空白 换行等
4. \S: 除了空白 换行等
5. \w 数字字母下划线
6. \W 除了数字字母下划线
7. \1 第一个括号的内容
<!--  -->
###
| 或者
{7,8} 7位或者8位
()   原子组 
(?:) 括号里面不记录不记录
(?=)断言 后面是谁的 但是后面不记录

[] [a-z]a到z  原子表 或的关系
[.+](.+) 点和加放入原子组内部 则表示点和加号
[^]
+ 一个或者多个
* 0个或者多个
. 除了换行符之外的任何字符
<!-- \ 转义 -->
\. 小数点
^ 开始
$ 结束 
?<con> 别名
### 方法

1. split  :  string.split("-") 字符串拆分为"-"     
2. search  :  string.search(regexp) 忽律g 第一个正则     
3. match  :  string.match(regexp) 返回一个数组   
4. matchAll  :  string.matchAll(regexp) 返回一个迭代对象 
5. test   :  reg.test(String)     返回一个Boolean
6. exec   :  reg.exec (String)     返回一个数组
7. replace : 字符串(string,替换字符)||(reg,(search)=>{})           返回一个字符串
replace $& 当前 $`左边 $'


### 面试对象 
 new RegExp('','g');//  第一个参数字符串, 第二个参数修正符
 ```
 g:全局  可以跳过
 y:连续的 从lastIndex开始及之后的字符串 
 i:大小写
 m:多行, 每一行单独处理
 s: 换行符当成空格 但是输出变成\n
 u:字符属性 
 ```