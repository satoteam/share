#从MYSQL到hibernate的浅谈

在文章的开篇，我想简单的先介绍一下数据库，数据库有三大类数据结构模型，层次结构模型，网状结构模型，[关系结构模型](https://baike.baidu.com/item/%E5%85%B3%E7%B3%BB%E5%9E%8B%E6%95%B0%E6%8D%AE%E5%BA%93/8999831?fr=aladdin)，其中最常使用的就是关系结构型数据库。对于关系型数据库而言，我们可以看见最常用的就是Mysql、sqlserver和oracle，下面重点介绍mysql的连接以及使用方式。

##MYsql

数据库的语言分为三类，

1.数据操纵语言*DML*（Data Manipulation Language）

包括常用的select、insert、update、delete。（Select也可再分为一类，称为数据查询语言）

​	1.insert插入

```INSERT INTO tb_name(id,name,score)VALUES(NULL,'张三',140),(NULL,'张四',178),(NULL,'张五',134);```

​	2.update更新(修改)

`UPDATE tb_name SET score=189 WHERE id=2;`

​	3.delete删除

`DELETE FROM tb_name WHERE id=3;`

​	4.select查询

`select * from tb_name;`

2.数据定义语言DDL

数据定义语言DDL用来创建数据库中的各种对象-----表、视图、索引、同义词。（create）

3.数据控制语言DCL

数据控制语言DCL用来授予或回收访问数据库的某种特权，并控制
数据库操纵事务发生的时间及效果，对数据库实行监视等。

------

##[JDBC](http://www.baidu.com/link?url=j-nK5AaHr4FOJxLJl5LnpF5xhcmLbuB93GEcY1LRCs29XeIu9h9pn-DurPHKkf5-aFkjiXP31gtMY3lvkw_Lv_&wd=&eqid=e84b53fa00005df10000000359ef5e86)

为什么数据库之后介绍的是JDBC呢？因为数据库语言的所有操作是在数据库本身进行的，想要与别的语言相关，让其他语言（这里使用到的是java）操作数据库语言，就必须有一个对外的接口，这里JDBC就是java语言与数据库语言的一个接口，也是一个规范。

#####数据库驱动，connection

```
private static Connection getConn() {
    String driver = "com.mysql.jdbc.Driver";
    String url = "jdbc:mysql://localhost:3306/samp_db";
    String username = "root";
    String password = "";
    Connection conn = null;
    try {
        Class.forName(driver); //classLoader,加载对应驱动
        conn = (Connection) DriverManager.getConnection(url, username, password);
    } catch (ClassNotFoundException e) {
        e.printStackTrace();
    } catch (SQLException e) {
        e.printStackTrace();
    }
    return conn;
}
```

#####插入

    private static int insert(Student student) {
    Connection conn = getConn();
    int i = 0;
    String sql = "insert into students (Name,Sex,Age) values(?,?,?)";
    PreparedStatement pstmt;
    try {
        pstmt = (PreparedStatement) conn.prepareStatement(sql);
        pstmt.setString(1, student.getName());
        pstmt.setString(2, student.getSex());
        pstmt.setString(3, student.getAge());
        i = pstmt.executeUpdate();
        pstmt.close();
        conn.close();
    } catch (SQLException e) {
        e.printStackTrace();
    }
    return i;
    }
##### 更新（修改）

```
private static int update(Student student) {
    Connection conn = getConn();
    int i = 0;
    String sql = "update students set Age='" + student.getAge() + "' where Name='" + student.getName() + "'";
    PreparedStatement pstmt;
    try {
        pstmt = (PreparedStatement) conn.prepareStatement(sql);
        i = pstmt.executeUpdate();
        System.out.println("resutl: " + i);
        pstmt.close();
        conn.close();
    } catch (SQLException e) {
        e.printStackTrace();
    }
    return i;
}
```

##### 查询

```
private static Integer getAll() {
    Connection conn = getConn();
    String sql = "select * from students";
    PreparedStatement pstmt;
    try {
        pstmt = (PreparedStatement)conn.prepareStatement(sql);
        ResultSet rs = pstmt.executeQuery();
        int col = rs.getMetaData().getColumnCount();
        System.out.println("============================");
        while (rs.next()) {
            for (int i = 1; i <= col; i++) {
                System.out.print(rs.getString(i) + "\t");
                if ((i == 2) && (rs.getString(i).length() < 8)) {
                    System.out.print("\t");
                }
             }
            System.out.println("");
        }
            System.out.println("============================");
    } catch (SQLException e) {
        e.printStackTrace();
    }
    return null;
}
```

##### 删除

```
private static int delete(String name) {
    Connection conn = getConn();
    int i = 0;
    String sql = "delete from students where Name='" + name + "'";
    PreparedStatement pstmt;
    try {
        pstmt = (PreparedStatement) conn.prepareStatement(sql);
        i = pstmt.executeUpdate();
        System.out.println("resutl: " + i);
        pstmt.close();
        conn.close();
    } catch (SQLException e) {
        e.printStackTrace();
    }
    return i;
}
```

------

##[hibernate](https://baike.baidu.com/item/Hibernate/206989?fr=aladdin)

关于hibernate(ORM-对象关系映射框架)的介绍，其实hibernate这个框架在我眼里看来，就是一个打包好的JDBC，使用起来会比JDBC简单的多。我们可以在面向对象的思想下，使用java语言完成对数据库的操作，减少了使用关系型数据库SQL语言的操作。

hibernate框架介绍

![](http://upload-images.jianshu.io/upload_images/8499175-a1fb06cb8711146c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在做hibernate项目之前，首先需要我们导入hibernate的包跟JDBC的包，具体操作
右键项目名称-properties-Java build path-add external JARs，其余步骤：

1.写hibernate配置文件hibernate.cfg.xml

2.写好一个javabean，并生成其映射文件.hbm.xml。

3.将映射文件写入配置文件中。

4.写测试类。

​	关于测试类，我们重点需要写好：

​	配置信息：	`Configuration configuration = new Configuration().configure();`

​	sessionFactory：`SessionFactory sessionFactory = configuration.buildSessionFactory();`

​	session:		`Session session = sessionFactory.openSession();`

​	事务开启：	`session.beginTransaction();`

​	事务操作（包括增删改查）：

​	事务保存：	`session.save(user);`

​	事务提交：	`session.getTransaction().commit();`

​	关闭：		`session.close();`

 				`sessionFactory.close();`

关于hibernate的介绍也基本上说完了

[1Java新手如何学习Spring、Struts、Hibernate三大框架？](https://www.zhihu.com/question/21142149/answer/24120371?utm_source=qq&utm_medium=social )

