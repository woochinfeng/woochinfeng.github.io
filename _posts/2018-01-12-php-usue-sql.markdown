---
layout: post
title: PHP常用函数
date: 2018-01-12 00:00:00 +0300
description: PHP # Add post description (optional)
img:  # Add image post (optional)
tags: [PHP, USUELLES, SQL] # add tag


---

- ```exit()``` 输出一条消息，并退出当前脚本（终止程序继续向下执行）；

- ```$_GET``` || ```$_POST``` 用来接收数据；它们都是一个数组 ```$_GET['key']```


- 在前端发送FORM表单数据时，一定要设置input的name属性,后端才可以正常接收


#### PHP ```echo``` 和 ```print()``` 、 ```print_r()``` 、 ```var_dump()``` 语句
- ```echo```      可以一次输出多个值，多个值之间用逗号分隔。echo是语言结构(language construct)，而并不是真正的函数，因此不能作为表达式的一部分使用。

- ```Print()```    函数print()打印一个值（它的参数），如果字符串成功显示则返回true，否则返回false。

- ```Print_r()```  可以把字符串和数字简单地打印出来，而数组则以括起来的键和值得列表形式显示，并以Array开头。但print_r()输出布尔值和NULL的结果没有意义，因为都是打印"\n"。因此用var_dump()函数更适合调试。

- ```Print()```只能打印出简单类型变量的值(如int,string)
print_r()可以打印出复杂类型变量的值(如数组,对象)

- ```var_dump()``` 判断一个变量的类型与长度,并输出变量的数值,如果变量有值输的是变量的值并回返数据类型。此函数显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构。

**提示**：```echo``` 输出的速度比 ```print()```/ ```print_r()```/ ```var_dump()```快， ```echo``` 没有返回值

```echo``` 是一个语言结构，使用的时候可以不用加括号，也可以加上括号： ```echo``` 或 ```echo()```


### 数学函数

- ```abs()``` 取绝对值

```php
echo abs(-1); // 1
```

- ```ceil()``` 向上取整

```php
echo ceil(1.01); // 2
```

- ```floor()``` 向下取整
```php
echo floor(1.01); // 1
```

- ```round()``` 四舍五入

```php
echo round(2.4449); // 2
```

- ```pow``` 返回x的n次方(接受负值与小数)

```php
echo pow(2,3); // (x,y) 8
```

- ```max``` 求最大值
```php
echo max(1,2,3,4,5,6); //6
```

- ```min``` 求最小值
```php
echo min(1,2,3,4,5,6); //1
```
- ```rand()``` 取随机数

```
echo rand(1,10);//(start,end)
echo mt_rand(1,10);//升级版，效率提高四倍，只支持新版php
```
- ```md5()``` md5加密

```php
echo md5(123) //32位md5码
```

- ```pi()``` 圆周率

```php
echo pi(3); //
```

### 字符串函数
- ```strlen()``` 返回字符串的长度

```php
$str = 'he llo';
echo strlen($str); //6 空格算一个字符
$str1 = '北京';
echo strlen($str1); //6 中文一个字代表三个长度
```

- ```mb_strlen()``` 返回字符串长度（中文支持）

```
$str1 = '北京';
echo strlen($str1); //2
```

- ```trim()``` 去除字符串两边的空格

 ```php
$str = '   hello   ';
echo trim($str) //'hello'
echo ltrim($str) //'hello  ' 加l代表left代表去除左边  
echo rtrim($str) //'   hello' 加r代表right代表去除左边
```

- ```substr()``` 返回字符串的一部分（中文）
    - 若出现乱码更改php.ini配置文件

```php
$str = 'hello 2018';
echo substr($str,6,2); //($str,start,length) 2018
//截取中文字符串
$str = '你好北京';
echo substr($str,2,4); //($str,start,length) 北京
```

- ```str_split``` 将字符串转换成索引数组

```php
$str = 'hello2018';
print_r (str_split($str,3)); //str_split($str,split_length)
/*Array
(
    [0] => hel
    [1] => lo2
    [2] => 018
    )
*/

```

```explode``` 通过指定的分隔符，把字符串拆成数组

```php
$str = 'hello,2018';
print_r (explode(',',3)); //hello2018
```

- ```str_replace()``` 替换字符串

    - 三个参数 1.要替换的内容 2.替换后的内容 3.要替换的字符串

- ```stroupper()``` 将字符串字母转换成大写

- ```strolower()``` 将字符串字母转换成小写

- ```strrpos()``` 获取一个字符串在另一个字符串最后一次出现的位置（大写敏感）

    - 获取文件后缀的方法
    ```
    substr($str,strrpos($str,'.')
    ```

- ```count ()``` 返回数组的长度

- ```in_array``` 判断一个值是否在数组中存在 (返回布尔值)     
    - (二维数组判断时不会转变数据类型)

- ```array_key_exists()``` 判断一个键名（key）是否在数组中存在

- ```array_keys()``` 返回数组中所有的键名(key)
    - 返回结果是一个索引数组
```php
$arr = [1,2,3,4,5];
var_dump(array_keys($arr,'1'));
```
- ```array_keys()```
    - 返回数组中所有的键名(key)
    返回结果是一个索引数组
    - 第二个参数是通过值(val)来获取对应的键名(key)
```php
$arr = [1,2,3,4,5];
var_dump(array_keys($arr,'1'));
/*
array(1) {
  [0] =>
  int(0)
}
*/
```

- ```array_values()``` 返回数组中所有的值(val),返回结果是一个**索引数组**

- ```array_pop($arr2)```  (改变数组) 删除数组最后一个元素 ,返回被删除元素的值(val)

```php
$arr = [1,2,3]
var_dump(array_pop($arr));
```

- ```array_push()``` (改变原数组) 向**末尾**添加数组
```php
array_push($arr,$res);
```

- ```array_shift()``` (改变原数组) 删除数组中第一个元素
,返回数组中第一个元素的值(val);

- ```array_unshift()``` (改变原数组) 向数组**首部**添加一个元素或多个元素，返回的是被添加的元素的值(val);

```php
array_unshift($arr,'1','2');
```
- ```array_unique()``` 对数组进行去重

```php
$arr = [1,2,3,2,1];
$a = array_unique($arr);
print_r($a);
/*
Array
(
    [0] => 1
    [1] => 2
    [2] => 3
)
*/
```

- ```array_search()``` 通过数组中的值(val)找到对应的键名(key),返回的是对应键名
```php
$arr = [1,2,3];
$a = array_search('2',$arr);
var_dump($a); //int(1)
```

- ```array_reverse``` 对数组进行反转，返回的是反转后的数组

```php
$arr = [1,2,3];
$a = array_reverse($arr);
var_dump($a);
/*
Array
(
    [0] => 3
    [1] => 2
    [2] => 1
)
*/
```

- ```sort()``` 升序排序（不改变下标）

```php
$arr = [1,2,3];
$a = sort($arr);
var_dump($arr);
/*
array(5) {
  [0] =>
  int(1)
  [1] =>
  int(2)
  [2] =>
  int(3)
  [3] =>
  int(5)
  [4] =>
  int(6)
}
*/
```

- ```asort()``` 对数组进行正向排序（保持原始对应关系）
- ```rsort()``` 对数组进行反向排序（保持原始对应关系）
- ```ksort()``` 对数组进行正向排序 （通过key）（不保持原始对应关系）
- ```krsort()``` 对数组进行反向排序 （通过key）（不保持原始对应关系）

#### 常用函数(验证码)
`implode` 将一维数组转换为字符串

`array_merge` 合并数组

`range` 取范围值的

`str_shuffle` 随机打乱字符串
