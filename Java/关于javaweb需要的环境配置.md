##### 关于javaweb需要的环境配置

***

对于大一的同学来说，刚进入校园，会接触到的C语言。首先我想要首先提及一下Java，Java是一种面向对象的语言，与C语言大同小异，唯一不同的是创建的函数（在java中叫对象）都在类中实现，就拿一个IT届最熟知的例子说明：

`public class test{`

`pulic static void main(String args[]){`

`System.out.println("Saluton mondo");`

`	}`

`}`

1.关于java的安装，首先要在[oracle](https://www.oracle.com/index.html)官网上下载[JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html)，之后如何配置JDK请参考[java环境变量设置怎么配置？jdk如何下载](https://www.zhihu.com/question/50428264/answer/120905041?utm_source=qq&utm_medium=social )(分享自知乎网)

2.关于java常用[IDE](https://baike.baidu.com/item/%E9%9B%86%E6%88%90%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83/298524?fr=aladdin&fromid=8232086&fromtitle=IDE)，首推使用[eclipse](https://www.eclipse.org/downloads/)，如果JDK配置没有问题，那eclipse设置好workspace之后就可以直接使用。

***

以上内容都配置好之后，想要创建一个dynamic web project（动态网页），我们还需要部署一个服务器才可以运行我们的项目，这里轻量级的应用服务器，首推[tomcat](http://tomcat.apache.org/)。为什么推荐tomcat？因为免费、实用。剩下还需要的一步是将我们的tomcat配置在eclipse上，具体请见[Eclipse和tomcat的配置-实用篇](https://zhuanlan.zhihu.com/p/25113582?utm_source=qq&utm_medium=social)（分享自知乎网）  



下面介绍正题，Javaweb工程的目录结构。

![javaweb工程目录结构图](http://upload-images.jianshu.io/upload_images/8499175-157d29ad91cd5bef.JPG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   

因为关于这篇文章很多内容都已经简化了，所以关于目录具体结构我也不详细赘述，重点说明一下我们经常会用到的。

| 目录                | 用途                                       |
| :---------------- | :--------------------------------------- |
| web app libraries | 一般是指向web工程的 WEB-INF/lib下的包               |
| src               | src文件夹里的java文件经过编译后，会把.class文件放在WEB-INF文件夹里的classes文件夹中 |
| WEB-INF           | 一些配置文件需要放到WEB-INF的classes文件夹下            |

那么到现在已经粗略的说完了javaweb环境配置以及介绍了目录结构，最后提及一下学习java要熟悉的框架SSH，这里也发现一个不错的内容[【如何在两到三个月之内熟悉 数据库，JavaWeb、框架，达到能写项目的水平？】David：… ](https://www.zhihu.com/question/41068277/answer/90573446?utm_source=qq&utm_medium=social)（分享自知乎网）  

文章尚有不成熟的地方还请指出。

