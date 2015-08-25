# 介绍

7ghost是一款基于PHP的网站反向代理程序。能够快速高效的反向代理所指定的网站。

并拥有丰富的内容替换、请求头设置。让没有主机的朋友也可以反向代理和加速你的网站。

# 功能

* 指定网站完全代理
* 自定义页面代理
* 域名替换
* 内容替换
* 静态缓存
* cookies自定义
* 浏览器标识自定义
* referer自定义

# 说明

* 后台地址为：

        \_admin\

* 默认登录密码：123456

        可编辑:\_admin\data\config.php修改。

# 更新

* 1.2.4版本：
    1. 添加secache作为动态缓存储存模式
    2. 添加代理模式和api代理模式，防止单一ip被屏蔽
    3. 添加直接匹配和正则匹配模式
    4. 优化.htaccess处理静态缓存的方式，减少php调用
* 1.2.3版本：
    1. 添加伪原创功能
    2. 添加程序所在二级目录可设置，解决部分空间不能自动获取的问题
    3. 修正全文搜索的bug
* 1.2.2版本：
    1. 修正伪静态实现方式，对搜索引擎更加友好
    2. 修正自定义页面优先级别
    3. 添加自定义页面是否允许访问选项
* 1.2.1版本：
    1. 添加页面编码设置
    2. 修正自定义页面配置替换bug
    3. 动态缓存添加gzip支持
* 1.2版本：
    1. 增加IIS7支持
    2. 修改静态缓存模式，将静态文件集中保存
    3. 添加动态缓存
    4. 添加全站伪静态功能
    5. 添加内容替换DOM功能
    6. 添加清空静态、动态缓存功能
    7. 修正内容替换正则表达bug

# 修订

修订：oott123

修订说明：

其实我什么都没动这么说你信么XD

好吧，做了小幅改动的地方就是.htaccess文件了。

原来的.htaccess在我的空间工作不正常，于是呢就去修订了一下。

改良以后的htaccess应该是更加兼容了吧⋯⋯

还是把原来的.htaccess贴在这里吧，如果有的空间不行呢⋯⋯

源文件：

    ###7ghost原.htaccess
    RewriteEngine on
    RewriteCond %{SCRIPT_FILENAME} !-f
    RewriteCond %{SCRIPT_FILENAME} !-d
    RewriteRule ^(.*)$ index.php/$1
    ###end

改良后：

    ###33改良.htaccess
    RewriteEngine on
    RewriteBase /
    RewriteCond $1 ^(index\.php)?$ [OR]
    RewriteCond %{REQUEST_FILENAME} -f [OR]
    RewriteCond %{REQUEST_FILENAME} -d
    RewriteRule ^(.*)$ - [S=1]
    RewriteRule . /index.php [L]
    ###end
