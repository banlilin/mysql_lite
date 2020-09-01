# 发起这个项目的初衷？

我觉得很多MySQL DBA的管理工作似乎有些俗套，不断的刷show processlist,show slave status,select user,host from mysql.user等等，背都能背出来的一些命令，我觉得反复敲一些相同的命令是很枯燥的，而且在很多维护管理中其实是有一种无力感，如果能够让命令很深刻，能够解读出很多的信息，我觉得我们的工作幸福度也会提高一些，所以我打算把一些常用的简单的命令能根据经验简化后固化下来。

# 为什么要做这个开源项目？

行业里有很多不错的管理工具了，比如pt工具，比如一些性能分析工具等，做这个工具的意义是什么？我觉得这个小工具的目标就是小巧，简单和实用，并不是要做多么宏大的目标去解决一揽子问题，是让基础的管理工作更轻松一些。

我可以说得更具体一些，比如我们要查看一张表的基本信息，但是我不知道在哪个数据库中，我们常规的思路如下：
- 1）通过information_schema.tables去定位表名
- 2）得到表名后实用show create table xxxx得到建表语句
- 3）实用desc得到表结构的基本信息

如果这个过程秒级就能够直达，就会让原本枯燥的过程变得“锋利”起来。


# 目前的思考和所得有哪些

目前这个初版的框架已经基本整理出来了，大体包括一些的一些内容。

![Alt text](https://github.com/jeanron100/mysql_lite/blob/master/mysql_lite.png)

我来简单解释一下，整个脚本内容可以按照find,show,check这三个基本维度展开， 
- find可以支持模糊匹配，精确查找，实现表，索引，字段层面的查找；
- show主要是对于一些对象和基本信息的展示，比如得到数据库的基本信息，得到binlog的基本信息，得到QPS等指标信息等；
- check是在这个基础上进一步完善的动作，我们可以实现一些快速检查工作，比如检查数据库中是否包含自增列溢出，检查用户权限，检查数据库中是否存在大量的短连接异常等，
- 此外补充了dump,internal,sql等几个模块，就是在这些基本管理之上进一步让工具更加丰富起来，支持一些更实用有效的功能。设计目标是小巧，简单和实用


# 有过哪些类似的经验

  之前开放了一部分脚本的项目dbm_lite,在Oracle数据库管理方向完全摆脱了界面管理，因为工作环境和网络限制等原因可以脚本化管理大量的线上环境，对于问题的快速定位是比较高效的，经历了大量的数据迁移的场景和问题排查。

