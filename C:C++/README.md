
## 为什么要学习C语言？

为什么要学习、使用C语言？为什么要学习一个可能比自己都岁数大的编程语言？

选择一门编程语言，“为什么而学”这个目的是最重要的，目的不明确就没法学好。这也是为什么很多学生朋友在大学里必修C语言却觉得没学明白的原因。因为学习的目的不明确，学习当然也没有动力。还有一个原因是C语言是工程实践性很强的语言，它不是来自某个研究所某个大学学院，而是实实在在从项目需要中产生，伴随着Unix的兴起而流行，语义简明清晰，功能强大而不臃肿，简洁而又不过分简单，实在是居家旅行工作学习必备之良友。

C语言相比C++的优点之一就是最小惊讶原则，一是一二是二，不会在私底下产生一些莫名其妙的额外产物。用C++做个例子，比如这样一个函数原型void PassWithClassValue(COneClass clsParam1)，稍微了解C++的朋友都会知道，如果你没有实现COneClass的拷贝构造函数，编译器会好心的帮你实现一个，而且在调用这个函数PassWithClassValue的时候，偷偷地调用拷贝构造函数产生一个临时对象作为参数传递，对于某些情况，比如编写操作系统这类必须优化性能的情景下，这些自以为是的东西是非常邪恶的事情。

C语言本身只提供必要的语言特性，其它复杂一点功能如文件处理、数学计算等等都以库函数方式提供，甚至连malloc、free这种“必须有”的功能，也是以标准库函数的方式提供，而不是作为C语言核心出现。在伟大的著名的无所不包的《K&R》开头部分就提到了，for其实可以通过while来完成，只不过for可以写的更简洁，言外之意，对于C语言for其实不是必要的。跑题一点说，在其它程序语言中Lua可以说继承了C语言简洁的设计哲学，甚至连continue这种几乎必备的关键字都一直拒绝加入，在Lua的maillist以及wiki里都提到过continue这个问题，Lua语言维护者认为continue对于Lua而言不是必要的，也不考虑在后续版本中添加这个关键字。这种简洁哲学也让C语言的可移植性、便携性特别优秀，也使得很多嵌入式系统依然使用C语言作为主要编程工作语言。

Java语言有一个口号：“一次编写，处处运行”，就是跨平台这个噱头。实际上C语言从早期开始就几乎达到了“一次编写，处处编译”，在ANSI在1989年统一了C语言标准以后（称之为C89），只要特定平台上的编译器完整实现了C89标准，而且你的代码没有使用某些特殊的扩展（GCC以及微软都有自己的编译器特定扩展），那么代码一定可以编译通过，再实现一下操作系统相关的函数库，C语言的移植就是很简单的事情。可以用Lua作为例子，Lua本身是完全遵循C89标准，没有使用任何特定扩展，这也保证了有C语言编译器的平台，都可以编译使用Lua。可以编译运行C语言的硬件平台可以从A排到Z，真是非常有意思的事情。

C语言也是一个比较少见的应用领域极为广泛的语言。比如编写操作系统这种高难问题，只有C++、汇编语言可以做到。C语言可以编写服务器端软件如Apache、Nginx，或者编写GUI程序，如GTK。大多数程序语言的第一版是通过C语言实现，借助前面提到的“一次编写处处编译”，最大的保证了这些程序语言的可移植性。在Web开发领域，C语言的应用相对较少，这也是一种取舍的结果，Web开发需要使用PHP、Ruby、Python这样的动态语言，可以快速上线快速修改，可以最大程度满足用户时时变化的需求，这也是C语言的弱项。如果把程序语言的应用领域从硬件到管理软件、Web程序做一个很粗略从下到上的排列，C语言适合领域是比较底层靠近硬件的部分，而新兴语言比较偏重于高层管理或者Web开发这种相对贴近最终用户的领域。比较流行的混合开发模式是使用C语言编写底层高性能部分代码或后台服务器代码，而使用动态语言如Python做前端开发，充分发挥它们各自的优势力量。

提到C语言的缺点，常常是它缺少这种或者那种特性，比如有人建议加入GC，有人建议加入并行或者并发支持，有人提到没有一个比较完整的类似C++的异常策略。这些特性有的可以通过引入第三方库来实现，但C语言的设计哲学其实决定了它不会像C++那样“非常强大”。即使引入了某些人期望的特性，依然会是某些人喜欢某些人不喜欢的情形，现在的功能对于C语言应用领域来说已经够用，其它特性可以通过特定程序语言实现，并且通过C API与C语言编写的程序进行交互。任何一个工匠都不可能只使用一个工具完成他的工作，不同工具结合起来才能更快更好的完成任务。

提到C语言的API，也稍微介绍一下，我们知道windows操作系统的api也好，Linux的系统api也好，或者是想给Ruby、Python编写扩展模块，C语言形式的函数定义都是唯一的选择。C语言就好像是一个中间层或者是胶水，如果想把不同编程语言实现的功能模块混合使用，C语言是最佳的选择。

提了这么多关于C语言的好处，那么学习C语言是否适合就看你自己的判断了，例如要进行一个嵌入式项目，或者需要进行服务器端开发，或者写一个性能相关的组件等等，C语言都是比较好用的选择。另外也可以在C++的使用过程中有意的使用C语言的思考方式，汲取C语言简洁明快清晰地设计思路，对编程设计水平会有很大的提高。

## C语言学习方法

C语言学习可以按照下面参考的顺序：阅读参考书，阅读代码，编写调试实际程序，上网参与讨论，研究高级话题。

学习语言的开始一般是阅读参考书。我建议选择几本非常经典的好书，仔细完整反复阅读几遍，“书读百遍其义自现”。选择C语言学习的好处是，这几本书基本上完整涵盖了C语言编程领域的方方面面，不会像C++那样，即使读完一堆书还是有些糊涂，依然有这样那样难懂的陷阱。

#### 1. 参考书籍

在豆瓣上列了一个书单，大家可以直接参考http://book.douban.com/doulist/636329/ 。在下面简单点评一下，阅读顺序最好参照列出的顺序。

《The C Programming Language》http://book.douban.com/subject/1230004/ ：如果你只想买一本书学习C语言，只需要买这一本就够了。如果你经费足够，建议你多买几本，办公室、家里都放上一本，随手都可以翻翻。用三个词语来形容它就是：经典！经典！经典！这本薄薄的只有二百多页的小书涵盖了C语言的方方面面，前无古人而且后无来者，任何溢美之词都不足以形容它。

《The C Programming Language》（后面称为 K&R）里面包含了一个简单的语法解析器，包含了malloc如何实现，包含了一个完整的操作系统目录浏览程序，这些程序的实用性极高，可以这样说，如果学习任何一门语言能够自己独立动手实现以上的功能，基本上就可以算是入门了。K&R书里面每段都蕴含着非常值得探究的软件开发工程实践经验，如果没有一定的开发经验，其实是看不出来这些冰山下面的内容的，比如开头一章就提出用写完整代码这种方式来教学，而在书中那些C语言的陷阱或者可能出问题的地方，都有提到，但是由于篇幅所限，写的非常简约，很难让人一下就看懂。我正在完整的逐字逐句的阅读此书，希望能稍作注解，写几篇博客分享一下。

《C程序设计语言》http://book.douban.com/subject/1139336/ ：这是K&R的中文译本，可以先从中文译本看起，然后再读一遍英文原版，既可以学习英文，又可以体会原文那种简约优美的风格。

《C陷阱与缺陷》http://book.douban.com/subject/2778632/

《C专家编程》http://book.douban.com/subject/2377310/

这两本书也是学习及使用C语言的朋友必备的两本书，比如《C专家编程》，专门用两三个章节详细介绍C语言中数组与指针的不同之处，这两本书在某种程度上算是对K&R略过的地方做了详细补充，强烈推荐。

《C语言参考手册》http://book.douban.com/subject/2132084/：这是最后一本强烈推荐你最好买回家作为案头书必备的参考书。前面几本书或者稍显简略，或者专注某个特定专题，都不适合遇到问题时翻查。这本《C语言参考手册》可以看作是C语言编程的《新华字典》，全面而权威。里面还涵盖了C99的内容，紧跟时代潮流。

下面几本书都可以作为交叉参考，也都很有价值，也是建议大家都买下来，好书如朋友，日久弥新，像是我推荐的这几本书在douban或者amazon上评分都非常高，而且反复再版。

《C和指针》http://book.douban.com/subject/1229973/ ：指针的重要性如何，学过C语言（或者C++）的朋友都知道，这本书更是把指针拔高到了与C语言平起平坐的地位，其实也是从头开始介绍，作为教学参考书也是可以的。

《C标准库》http://book.douban.com/subject/3775842/ ：这本书是专门介绍C语言的标准库如何实现的，比如malloc算法，用标准的C语言该如何写？strlen这个函数应该如何实现？尽管书中不少代码与真实的C标准库相差很多（由于标准库需要考虑性能优化，很多函数有一些特定的trick），但是绝对值得参考。

《你必须知道的495个C语言问题》 http://book.douban.com/subject/3422332/ ：这本书其实就是C-FAQ的印刷版本，C-FAQ在各种编程语言的FAQ中可以称得上质量一流。如果你想应聘或者招聘C语言相关程序员，这本书一定要参考。

《Linux C编程一站式学习》http://book.douban.com/subject/4141733/ ：这本书是基于特定操作系统Linux来介绍C语言编程，可作为计算机相关专业的教科书或入门参考书，也是书单里面唯一一本国人原创的编程书籍，非常难得。书中几乎所有内容都在网上直接公开，针对读者的意见进行修改，这也是非常难得的一种开放态度。非常推荐大家买一本。

学习C语言，一定不能只读书，应该动手练习完成书里面的项目需求（比如编写一个目录浏览器）以及每章的练习题目。这就需要有可以实验的环境，下面针对不同操作系统简单做一下介绍。

#### 2. 动手实验环境搭建

也没有调查过，不知道现在学校里学习C语言是不是依然跟着谭浩强老师用TurboC2.0编程，如果还是这个组合的话，那就太差劲了，赶快抛开它们。

下面主要介绍不同操作系统平台下的集成编程环境，基于初学者以及我个人喜好，就不推荐大家命令行下用vim编程了，直接上IDE。

Windows系统下推荐大家使用Code::blocks这个软件。这个软件最大优点是自带了基于mingw的GCC以及GDB，只要下载70M左右软件包，就可以完整支持C++、C语言编程了。各种功能（比如调试功能）也很强大，版本更新也比较快。注意下载选择名字有mingw的文件，比如最新版本是codeblocks-10.05mingw-setup.exe（版本也许有所不同）。主页：http://www.codeblocks.org/

如果需要做Windows操作系统的开发，可以下载VS

因为Code::Blocks不包含Windows编程头文件（实际是因为没有Windows SDK），无法编写Windows操作系统相关的界面应用程序或者服务类程序。而VC++Express自带了这些头文件以及编程库，虽然功能稍微简陋，但对于练习使用基本够用。主页：http://www.microsoft.com/express/windows/

对于计算机专业的学生朋友，建议大家使用Linux操作系统，或者更详细一点是使用Xubuntu操作系统作为桌面，使用Netbeans和GCC这个组合（当然也可以选择Code::Blocks）。在Xubuntu下可以通过apt-get install build-essential这个命令安装gcc相关程序，已经可以在Terminal下编译C语言程序了，但为了使用方便，大家可以选择Netbeans的C++支持包，在Netbeans网站上就能下载。主页：http://netbeans.org/features/cpp/index.html

如果使用苹果Mac系统，毫无疑问XCode就是编程的绝佳选择，XCode可以在苹果开发者网站上免费下载，在IPhone SDK中也包含了XCode。主页：http://developer.apple.com/technologies/tools/xcode.html
或者Jetbrains 下的Clion

如果手头没有合适的编程环境，还需要实验一些简单的代码，可以用http://codepad.org/ 提供的服务，在线编写运行代码。

另外建议大家申请一个github.com的账号，在gist.github.com可以保存自己的练习代码，就不需要随身带着U盘了。

#### 3. 网络资源

如果想用十分钟时间了解一下C语言的来龙去脉、前世今生，维基百科这个页面http://en.wikipedia.org/wiki/C_%28programming_language%29 是最佳选择。

从维基百科可以看到，C语言1972年由Dennis Ritchie设计的命令式、结构化范式编程语言。类型为静态的弱类型，需要显式定义。最新国际标准为C99。设计上主要受到了B、ALGOL68、汇编语言、PL/I、FORTRAN的影响，C语言也影响了大量编程语言，如C++、Objective-C、C#、Java、Go、PHP、Python等等（个人觉得受C影响很大的是PHP，基本上有C编程基础的程序员，很容易就能上手PHP了，除了PHP的OO部分）。

在维基百科条目中有很大篇幅介绍了作者认为C语言缺失的特性，比如面向对象、多线程、GC、异常处理等等，当然这有些吹毛求疵，如果需要这些特性，完全可以用其它程序语言。另外一个介绍的重点是“未定义行为”，有些我们认为理所当然的结果，其实在C语言标准中并没有明确定义，假定这些行为应该如何，当程序使用另外的编译器或者不同版本编译器编译运行，都可能有bug产生。

接下来维基百科条目谈到了C语言的用处，必须承认尽管现在编程语言成百上千，能称之为“系统级”的少之又少，新兴语言中只有Go还能称得上。现在大规模软件项目中完全选用C语言可能性不大，但是核心部分完全可以用C搭建，相对C++开发工具的高昂价格，C语言相关的免费辅助开发软件非常丰富，比如splint，valgrind，不少核心库经过长期使用也都非常稳定。

由于C语言广泛支持各种平台以及编译器相对成熟可靠，不少编程语言选择C语言作为一个中间层，比如Glasgow Haskell编译器就是这样做的。

另一个可以找到大量C语言编程相关资料的地方是“美味书签”，通过搜索特定关键字 （C + programming）就可以找到很多值得挖掘的资源http://delicious.com/search?p=c+programming 。还可以参考dmoz.org的C语言分类http://www.dmoz.org/Computers/Programming/Languages/C/  相比美味书签时效性能差点，但是分类比较系统，查找也要容易一些。

程序员往往是懒惰的，“拿来主义”、“拷贝主义”很流行也很有效，当对某个函数或者关键字不是很理解的时候，看看别人是怎么使用的，会非常有启发性。这里介绍几个常用的代码搜索网站，最常用的是google的codesearch：http://codesearch.google.com ，可以通过不同条件及正则表达式搜索特定关键词。另外可以参考维基百科上一个“带有C语言示例的文章”分类，里面代码写的也很不错。还可以在github.com上搜索相关项目。在前面博客文章我还介绍了一个名为罗塞塔代码的网站http://rosettacode.org/ 这个网站上可以找到不同程序语言针对某个问题的解决方案，用于学习比较非常便利。

学习编程也需要大量阅读名家经典代码，与学中文英文需要大量阅读名著一个道理，C语言编程优质项目那是“彩旗飘舞，人山人海”，个人建议可以看看Lua、Sqlite、Nginx这些项目的代码，代码量不多，而且代码质量也都比较高。另外可以看看Linux内核代码，坊间有不少书籍可以帮助解读。关于如何很好的阅读代码，大家可以参考《Code Reading》这本书。

书看了几本，代码写了一些，也略微读了读其他人的代码，就应该用C语言来完成真实工作中碰到的问题，让C语言真正成为你的瑞士军刀。只有当你经常使用C语言来进行编程工作，经常思考如何通过C设计一个优雅高效的系统，才能更深刻的理解C语言设计哲学。

还可以到http://stackoverflow.com 参与回答问题，浏览其他人的问题解答来汲取知识，比如这篇http://stackoverflow.com/questions/2054939/char-is-signed-or-unsigned-by-default 就介绍了一个C语言关于char类型的小陷阱。

C语言学习当中，有一些难点需要多加注意，如pointer与array的不同之处，复杂类型定义如何解读，如何正确使用预处理preprocessor以及宏定义。其实这些内容在前面书籍都是反复提到，如果按部就班学习下来，应该不成问题。

当C语言学习的差不多时候，还可以学习一门动态语言，比如Lua或者Python，试着在实际工作项目中混合使用动态语言与C语言，一加一发挥出来的力量不仅仅是二，而是非常二（说笑一下，哈哈）。

#### 一些有用的C语言网络资源：

C语言标准化组织ISO JTC1/SC22/WG14的主页，在这里可以找到ISO C的文档：http://www.open-std.org/jtc1/sc22/wg14/

《The Development of the C Language》作者Dennis Ritchie，极为经典的论文。 http://cm.bell-labs.com/cm/cs/who/dmr/chist.html

“C语言全景”这个网站内容很全面：http://www.softpanorama.org/Lang/c.shtml

Dan Saks在embedded.com上的专栏Programming Pointer ，里面文章很有深度，值得一读。

http://www.lysator.liu.se/c/c-www.html 这也是一个C语言资源汇总页面。

http://www.ioccc.org/index.html 混乱C语言代码大赛，很著名。

http://en.wikipedia.org/wiki/Underhanded_C_Contest 另外一个C语言编程大赛，主要面向黑客。

comp.lang.c以及c.moderated这两个讨论组推荐订阅，相当于互联网最大的C相关编程问题论坛：

http://groups.google.com/group/comp.lang.c

http://groups.google.com/group/comp.lang.c.moderated

这里对C语言的各种bit操作做了收集整理，不少题目在面试时候经常出现。http://graphics.stanford.edu/~seander/bithacks.html

台湾的惯C达人Jserv博客，建议大家订阅：http://blog.linux.org.tw/~jserv/

一些值得关注及研究的C语言相关项目：

TinyCC，被很多项目用作动态编译C语言的编译器引擎：http://bellard.org/tcc/

GCC的标准库实现：http://en.wikipedia.org/wiki/GNU_C_Library

Glib是GTK的底层辅助编程库，与C标准库是不一样的，在C语言上实现了面向对象机制：http://en.wikipedia.org/wiki/GLib

dietlibc在前面博客文章介绍过，C标准库的另一种实现：http://www.fefe.de/dietlibc/

一些C语言编程时可以使用的工具软件，帮你提高代码质量：

http://www.splint.org/

http://valgrind.org/

http://www.dwheeler.com/flawfinder/

PMD可用于检测重复代码 http://pmd.sourceforge.net/cpd.html

llvm的静态分析项目 http://clang-analyzer.llvm.org/

C语言编程规范编程标准：

http://en.wikipedia.org/wiki/MISRA_C

http://www.eecs.harvard.edu/~ellard/CS50-96/programming-style.html

http://developers.sun.com/solaris/articles/secure.html

cert这个文档国内有中文翻译版本：https://www.securecoding.cert.org/confluence/display/seccode/CERT+C+Secure+Coding+Standard

http://www.cs.utah.edu/dept/old/texinfo/standards/standards_toc.html


## 附录

C语言编程电子书及教程：

http://publications.gbdirect.co.uk/c_book/ 这一本写的非常详细，你可以把它看成是类似谭浩强版的教科书。

http://www.knosof.co.uk/cbook/cbook.html 这一本云风曾经推荐过，相当深入的介绍了C99标准，深入细节时候需要读读。

http://www.duckware.com/bugfreec/index.html 这本书在网上流传一个中文版本，《编写优化、高效、无错地代码》，另外也有英文影印版《编程精粹》。

http://wangcong.org/blog/?page_id=196 作者王聪，也是相当hard geek，从两个样章看，包含了相当多的内容。

《C语言深度解剖》这本可以在百度文库或google搜到，可以读读，有些参考性。

《C标准和实现》作者姚新颜，他的《深度探索C、C++》算是当年比较有深度的书籍，可惜已经绝版了。这本书也可以在百度文库搜到。这本书也比较值得读。

良葛格C语言学习笔记 http://caterpillar.onlyfun.net/Gossip/CGossip/CGossip.html

C与C++的兼容性问题 http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B

另一个文档关于C与C++标准兼容性问题：http://david.tribble.com/text/cdiffs.htm

《C Elements of Style》http://www.oualline.com/books.free/style/index.html

《Linux安全编程》http://www.dwheeler.com/secure-programs/

《C Craft》电子版 http://crypto.stanford.edu/~blynn/c/

《The function pointer tutorials》函数指针教程。http://www.newty.de/fpt/index.html

C语言编程及Unix系统调用，想用C在Unix或者Linux编程的朋友可以参考。http://www.cs.cf.ac.uk/Dave/C/

优化C、C++代码 http://www.eventhelix.com/RealtimeMantra/Basics/OptimizingCAndCPPCode.htm

图文并茂介绍C语言的指针 http://boredzo.org/pointers/

另外一篇介绍C语言优化的文章 http://www.prism.uvsq.fr/~cedb/local_copies/lee.html

一个C语言教学ppt http://www.slideshare.net/petdance/just-enough-c-for-open-source-programmers

一些Unix下C语言编程相关的文章 http://users.actcom.co.il/~choo/lupg/tutorials/index.html

Unix下如何建立静态、动态C语言函数库 http://users.actcom.co.il/~choo/lupg/tutorials/libraries/unix-c-libraries.html

如何使用GDB http://users.actcom.co.il/~choo/lupg/tutorials/debugging/debugging-with-gdb.html

一些C语言编程技巧 http://users.bestweb.net/~ctips/

Advanced C programming，高级C语言编程，可以提高水平，非常有帮助 http://www.mpi-inf.mpg.de/departments/rg1/teaching/advancedc-ws08/literature.html

C语言问答，这些题目也可用于面试 http://www.gowrikumar.com/c/




原文：http://sunxiunan.com/archives/1661

