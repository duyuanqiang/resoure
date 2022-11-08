**web安全**

xss(跨站脚本攻击)

原理就是恶意攻击者往web页面里面插入恶意执行的网页代码脚本,html,js之类的,当用户浏览该页时,嵌入其中脚本代码会被执行,从而达到盗取用户信息或者侵犯用户安全隐私的目的

例如通过解析url的参数,攻击者将恶意的js代码伪装成参数的形式,盗取信息

利用虚假输入表单骗取用户信息

窃取用户的cookie,在被害人不知情的情况下,帮助攻击这者发送恶意请求

显示伪造的文章和图片

不过浏览器内置了一些xss过滤器,可以防止大部分反射型xss攻击

非持久性sxx攻击特点

 即时性不经过服务器存储,直接通过http的get和post请求完成一次攻击,拿到用户隐私

攻击者需要诱骗点击,必须通过用户点击链接才能发起

反馈率低,较难发现和相应修复

盗取用户敏感保密信息

防范措施

web页面渲染内容和数据来自服务端

尽量不从url,document.referrer.document.forms等获取DOM API渲染

尽量不使用eval,new Function(),document.write(),等可执行字符串的方法

做不到以上几点,对设涉及dom渲染的方法传入的字符串做escape转义

持久型xss(存储型xss)

一般存在与From表单提交文章留言等,利用xss漏洞,将内容正常功能提交进数据库持久保存,当前端页面获得后端从数据库中读出的注入代码时,恰好将其渲染 \<script>alert(1)\</script>,在提交表单的地方完成注入

特点

持久性，植入在数据库中

盗取用户敏感信息

危害面广

解决办法

一 ：设置CSP，明确告诉浏览器那些外部资源可以加载和执行。

通过设置http header中 content-security-policy

设置meta 标签的方式

二：转义字符，对输入的引号和尖括号，斜杠进行转义 

str= strreplace(/&/g,'&amp')

**csrf**

(Cross Site Request Forgery) 跨站请求伪造

用户登录站点A,并记录本地cookie

在用户没有登出站点A的时候,访问恶意攻击者提供的引诱站点B

站点没有做csrf防御

如何防御

get请求不对数据进行修改

不让第三方网站访问cookie

阻止第三方网站请求接口

请求附带验证信息,比如验证码或者token

**点击劫持**

用户在登录A网站的系统后,被攻击者诱惑打开第三方网站,而第三方网站通过iframe引入了A网站的页面,实际上是点击了A网站的按钮

如何防御

设置http的响应头X-FRAME-OPTIONS防止iframe嵌套劫持

DENY,不允许通过iframe展示

SAMEORGIN 表示页面可以在相同域名下通过iframe展示

ALLOW-FROM表示页面可以在指定来源的iframe展示

**url跳转漏洞**

利用url跳转漏洞有道安全意识低的用户点击，导致用户信息泄露或者资金流失。伪造url，跳转到恶意网站

![1667926705731](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667926705731.png)

加入token验证

![1667926755871](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667926755871.png)

**SQL注入**

通过拼接SQL语句，修改攻击数据库

![1667926835366](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667926835366.png)

防御

限制web应用的数据库权限

后端检查输入的数据

对特殊字符转义

![1667926944637](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667926944637.png)

**os攻击**

类似SQL注入，只不过注入 命令针对os。

执行非法操作系统命令，攻击指定的web应用，一般攻击shell调用的地方。命令注入攻击可以向Shell发送命令，让Windows或Linux操作系统的命令行启动程序。也就是说，通过命令注入攻击可执行操作系统上安装着的各种程序。

防御

后端限制提交内容，进行正则替换

对传入参数转义

不要直接拼接命令语句。借助其他工具做拼接，转义。