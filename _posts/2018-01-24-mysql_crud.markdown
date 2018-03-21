---
layout: post
title: MySQL增删改查
date: 2018-01-24 00:00:00 +0300
description: MySQL # Add post description (optional)
img:  # Add image post (optional)
tags: [MySQL, DATA, PHP] # add tag

---




### MySQL操作命令大写
>区分变量和数据库语句,代码可读性

### INSERT（增）
```php
$sql = "INSERT INTO students (Name,Sex,Age) VALUES(?,?,?)";
```
### DELETE（删）
```
$sql = "DELETE FROM students WHERE Name='" + name + "'";
```

### UPDATE（改）
```php
$sql = "UPDATE students SET Age='" + student.getAge() + "' WHERE Name='" + student.getName() + "'";
```

### SELECT（查）
```
$sql = "SELECT * FROM students";
```

### 连接mysql
```php
$host = '127.0.0.1';
$user = 'root';
$password = '';
$database = 'user';//连接的库

$link = mysqli_connect($host,$user,$password,$database);//连接mysql数据库
```

### SQL查询命令
```php
if(!mysqli_connect_errno($link)) {
    echo 'successful!';
    //SQL查询命令
    $err = mysqli_query($link,$sql2);
    if ($err) {
        echo "插入数据成功";
    } else {
        echo "插入数据失败";
    }
} else {
    echo 'fail!' . mysqli_connect_error();
}
```

### 关闭数据库
```php
mysqli_close($link);
```
