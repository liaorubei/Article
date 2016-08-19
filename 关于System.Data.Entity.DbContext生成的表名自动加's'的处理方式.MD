关于System.Data.Entity.DbContext生成的表名自动加's'的处理方式
今天在给一个DbContext添加字段时,添加了一个叫User的字段(表),但是运行的时候却跳了一个异常,
System.Data.SqlClient.SqlException:Invalid object name 'dbo.Users'
应该是说找不到数据库表Users了.EntityFrameWork在生成的Sql语句中'约定俗成'的给表名加上复数,如果想要解决这个异常,目前处理办法有3
1.把数据库在表改成Users,
2.在DbContext添加表(字段)的时候,给这个字段的类型加一个注解[Table("User")]
3.重写DbContext的OnModelCreating()方法,移除添加复数属性,(从DbContextBuilder里面找)