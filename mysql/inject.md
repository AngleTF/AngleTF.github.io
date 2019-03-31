### 正常SQL查询
假设下图是一张简单用户信息表 , 用于用户的登录判断 , user 和 pwd 分别是用户的账号和密码
![](/assets/sql1.jpg)

我们正常登录的SQL语句如下
![](/assets/sql2.jpg)
我们可以看到用户输入正确的账号密码 , 成功取出了用户的数据

### 注入的SQL语句
![](/assets/sql3.jpg)
而这里用户输入的账号是 tao1';# 密码却是 **** 但是数据库还是把tao1用户的数据输出了, SQL注入的原理就是将MySQL特殊字符当做SQL语句执行 , 以上的这个例子当输入 ' 的时候就代表user的判断语句终结, 输入 ; 的时候表示后面的语句变成第二条SQL语句并且不会执行 , 当输入 # 的时候就表示#后的代码不起效

### 预防SQL注入
1. 将特殊字符转义后在进行数据库操作
2. 使用一些带占位符的封装类 例如 PHP的PDO预处理类
3. 使用框架 , 一般框架都会对SQL语句进行过滤