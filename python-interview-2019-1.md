## Python开发工程师笔试题

> 答题要求：将该项目从[地址1](https://github.com/jackfrued/python-interview-2019)或[地址2](https://gitee.com/jackfrued/python-interview-2019)fork到自己的[github]()或[gitee]()仓库并填写答案，完成之后将自己的仓库（public）地址发给面试官即可，答题时间120分钟。

1. 下面的Python代码会输出什么。

   ```Python
   print([(x, y) for x, y in zip('abcd', (1, 2, 3, 4, 5))])
   print({x: f'item{x ** 2}' for x in range(5) if x % 2})
   print(len({x for x in 'hello world' if x not in 'abcdefg'}))
   ```

   答案：

   ```
   KeyError
   {0: item{0}, 2: item{4}, 4: item{16}}
   9
   ```

2. 下面的Python代码会输出什么。

   ```Python
   from functools import reduce

   items = [11, 12, 13, 14] 
   print(reduce(int.__mul__, map(lambda x: x // 2, filter(lambda x: x ** 2 > 150, items))))
   ```

   答案：

   ```

   ```

3. 有一个通过网络获取数据的Python函数（可能会因为网络或其他原因出现异常），写一个装饰器让这个函数在出现异常时可以重新执行，但尝试重新执行的次数不得超过指定的最大次数。

   答案：

   ```Python
   def get_error(func):
       def try_again(*args, **kwargs):
           for i in range(n):
               try:
                   func()
                   break
               except:
                   continue
           return func
       return try_again
   ```

4. 下面的字典中保存了某些公司今日的股票代码及价格，用一句Python代码从中找出价格最高的股票对应的股票代码，用一句Python代码创建股票价格大于100的股票组成的新字典。

   > 说明：美股的股票代码是指英文字母代码，如：AAPL、GOOG。

   ```Python
   prices = {
       'AAPL': 191.88,
       'GOOG': 1186.96,
       'IBM': 149.24,
       'ORCL': 48.44,
       'ACN': 166.89,
       'FB': 208.09,
       'SYMC': 21.29
   }
   ```

   答案：

   ```Python
   (k for k, v in prices.items() if v == max(prices.values()))
   {k: v for k, v in prices.items() if v > 100}
   ```

5. 写一个函数，传入的参数是一个列表，如果列表中的三个元素`a`、`b`、`c`相加之和为`0`，就将这个三个元素组成一个三元组，最后该函数返回一个包含了所有这样的三元组的列表。例如：

   > 参数：`[-1, 0, 1, 2, -1, -4]`
   >
   > 返回：`[(-1, 0, 1), (-1, 2, -1)]`

   答案：

   ```Python
   def zero_tuple(list1):
       list2 = []
       for a in list1:
           for b in list1:
               for c in list1:
                   if a + b + c == 0:
                       if (a, b, c) not in list2:
                       	list2.append((a, b, c))
   	return list2                    
   ```

6. 写一个函数，传入的参数是一个列表（列表中的元素可能也是一个列表），返回该列表最大的嵌套深度，例如：

   > 参数：`[1, 2, 3]`
   >
   > 返回：`1`
   >
   > 参数：`[[1], [2, [3]]]`
   >
   > 返回：`3`

   答案：

   ```Python
   def get_list_deep(foo_list):
       deep = 1
       
   ```

7. 写一个函数，实现将输入的长链接转换成短链接，每个长链接对应的短链接必须是独一无二的且每个长链接只应该对应到一个短链接，假设短链接统一以`http://t.cn/`开头。例如：给定一个长链接：，会返回形如：的短链接。

   > 参数：`http://jackfrued.xyz/api/users/10001`
   >
   > 返回：`http://t.cn/E6MUth1`

   答案：

   ```Python

   ```

8. 用5个线程，将1~100的整数累加到一个初始值为0的变量上，每次累加时将线程ID和本次累加后的结果打印出来。

    答案：

    ```Python
    from threading import Thread
    	
    n = 0
    threads = [Thread() for i in range(5)]
    for thread in threads:
        thread.join()
        print(id(thread), thread.start(target=print(n+=1)))
    ```

9. 请阐述Python是如何进行内存管理的。

    答案：

    ```
    引用计数和垃圾回收机制
    ```

10. 在MySQL数据库中有名为`tb_result`的表如下所示，请写出能查询出如下所示结果的SQL。

   `tb_result`表：

   | rq         | shengfu |
   | ---------- | ------- |
   | 2017-04-09 | 胜       |
   | 2017-04-09 | 胜       |
   | 2017-04-09 | 负       |
   | 2017-04-09 | 负       |
   | 2017-04-10 | 胜       |
   | 2017-04-10 | 负       |
   | 2017-04-10 | 负       |

   查询结果：

   | rq         | 胜    | 负    |
   | ---------- | ---- | ---- |
   | 2017-04-09 | 2    | 2    |
   | 2017-04-10 | 1    | 2    |

   答案：

   ```SQL
   select rq, '胜', '负'
   from 
   (select rq, shengfu 
   from tb_result
   group by rq) 
   group by shengfu;
   ```

11. 列举出你知道的HTTP请求头选项并说明其作用。

     答案：

     ```
     Accept: 接收的请求类容的类型
     User-Agent: 用户代理
     Host: 主机
     Cookie: 缓存
     ```

12. 阐述Web应用中的Cookie和Session到底有什么区别和联系。

    答案：

    ```
    Cookie是浏览器缓存的数据,包括用户信息,网页信息等
    Session是浏览器与服务器建立的连接和会话, 没有session用户需要重新访问
    ```

13. 请阐述访问一个用Django或Flask开发的Web应用，从用户在浏览器中输入网址回车到浏览器收到Web页面的整个过程中，到底发生了哪些事情，越详细越好。

    答案：

    ```
    Django: 用户在浏览器中输入url, 浏览器向Web应用发起请求, Django通过urls.py里面的路由找到对应的视图函数view, 视图函数返回前端页面, 前端页面再通过url找到接口, 路由器urlpattern或者router找到接口异步请求数据库中的数据返回给前端页面, 前端页面渲染数据, 浏览器返回渲染后的页面给用户.

    Flask: 用户在浏览器中输入url, Flask通过蓝图blueprint找到对应的功能函数, 函数返回一个前端页面, 前端页面异步请求数据接口, 蓝图通过数据接口获取数据库的数据返回给前端页面渲染,浏览器将渲染好的页面返回给用户. 
    ```

14. 请阐述HTTPS的工作原理，并说明该协议与HTTP之间的区别。

    答案：

    ```
    浏览器向服务器发起https请求, 服务器验证证书,验证用户信息, 验证通过才返回请求的页面 
    ```

15. 简述你认为新浪微博是如何让订阅者在第一时间获得博主发布的消息。

    答案：

    ```

    ```

16. 简述如何检查数据库是不是系统的性能瓶颈以及你在工作中是如何优化数据库操作性能的。

    答案：

    ```
    数据库优化: 使用外键,索引,优化查询插入语句, 提高硬件性能.
    ```

17. 在Linux系统中，假设Nginx的访问日志位于`/var/log/nginx/access.log`，该文件的每一行代表一条访问记录，每一行都由若干列（以制表键分隔）构成，其中第1列记录了访问者的IP地址。请用一条命令找出最近的100000次访问中，访问频率最高的IP地址及访问次数。

    答案：

    ```Shell

    ```

18. 请阐述跨站脚本攻击（XSS）、跨站身份伪造（CSRF）和SQL注射攻击的原理及防范措施。

    答案：

    ```
    XSS: 用户访问浏览器的时候访问到错误的网址和伪装的前端页面。
    CSRF: 用户无意间下载了捆绑软件或者点击了流氓广告后, 木马在用户电脑后台运行, 用户访问浏览器后, 木马将用户的token等信息转发给攻击者, 攻击者利用用户的信息, 就实现了跨站身份伪造。
     	  用户使用公用电脑应重启且开启杀毒软件, 不要使用公用网络存钱,转账等。
    SQL: 攻击者利用程序拦截用户的请求并将有害的sql替换原来的sql以达到攻击的目的,比如:盗取数据, 恶意删除数据等。
    ```
