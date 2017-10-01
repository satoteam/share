# SATO TEAM 分享会

### 目录  
-  [通识教育](https://github.com/satoteam/share/tree/master/%E9%80%9A%E8%AF%86%E6%95%99%E8%82%B2)
-  [C:C++](https://github.com/satoteam/share/tree/master/C:C%2B%2B) 
-  [interview 笔试面试]()
-  [DataBase 数据库]()
-  [Java]()
-  [Python]()
-  [架构]()
-  [产品经理]()
-  [前端]()
-  [设计]()
-  [测试]()
-  [运维]()
-  [读书]()
-  [Other]()

请各位fork后能及时更新，一遍获得更新。

#添加项目A的远程仓库地址到upstream
git remote add upstream https://github.com/satoteam/share.git


#把项目A的更新来到本地的upstream里
git fetch upstream 

#切换到你自己想要merge的分支，这里我用举例：master
git checkout master

#merge项目A的更新到你的branch
git merge upstream/master