#移动开发接口及文档编写规范
>APP接口是移动设备和业务之间进行通信的途径。实质就是以特定的规则通过接口直接操作数据库的增删改查。

##接口编写原则
###实用性
编写接口API应遵从实用性原则。
1、**数据格式**：推荐使用JSON格式数据，因为JSON有较好的跨平台性，以及数据格式占用字节数较少，当然也可采用XML、TEXT作为程序开发辅助。
2、**接口执行效率（接口访问速度）**：APP有别于WEB服务，对服务器端要求是比较严格的，在移动端有限的带宽条件下，要求接口响应速度要快，所有在开发过程中尽量选择效率高的框架，PHP推荐使用YAF框架，.NET推荐使用Newtonsoft
3、**数据量**：按需分配，APP客户端需要什么数据就返回什么数据，过多的数据量影响处理速度，最重要的是影响传输效率和浪费用户流量。
4、**API缓存**：这点比较重要，不管是文件缓存还是memcache缓存。
###易用性
1、**接口、参数命名准确**：无论是接口还是参数，命名都应该有意义，让人一目了然。（接口推荐根据APP效果图栏目进行命名）
2、**一个页面尽可能就用一个接口**：现在很多的APP页面都有广告、焦点图、文章列表等，对于这些不同格式的数据，不可能都分配一个接口，这样加大了APP请求接口数，影响响应速度。建议服务器端尽可能处理好数据后通过一个接口返回给APP客户端。
3、**接口数据、状态**：接口必须提供明确的数据状态信息，不管是成功的，还是失败的，都必须返回给APP客户端。
4、**接口要有可扩展性**：方便后期功能性调整，接口应具备可扩展性。
###安全性
1、**接口安全**：目前一般都是在APP客户端和服务器通过约定的算法，对传递的参数值进行验证匹配。但是如果APP程序被反编译，这些约定的算法就会暴露，特别是在安卓APP中，有了算法，完全就可以通过验证模拟接口请求。
2、**加密规范**：在传递用户名密码时，应采用规范的加密算法如MD5、RSA、DES，进行数据通信请求。
3、**接口版本控制**：对于接口版本控制，需要应对不断的APP版本升级，新、旧接口的处理，因而需要关注接口版本控制。
##接口设计原则
1、**尽量减少参数传递**：在客户端发起HTTP请求接口操作时，应减少参数传递，如某些操作只需要ID不需要其他参数，这时候就应该只传递ID这个参数。
2、**尽量避免接口重复性**：在客户端APP调用接口时，尽量提高接口复用性，减少HTTP请求，提高程序稳定性。
3、**数据类型规范**：客户端APP调用接口时，应标注参数数据类型，以及是否可为空或者默认字段，如标注了Int型字段，就不能返回“null”的String类型字段，否则容易造成程序APP出现数据类型解析异常。
4、**设置调用html页面单独列表**：调用html页面应标明是否传递安全校验参数，建议表格中采用是或者否单独字段标识。
5、**编码规范**：整个API接口开发过程中，应标注接口编码方式，目前建议采用UTF-8编码，UTF-8通用性以及URL请求方面都较规范。
6、**请求方式**：编写API接口应该标注请求方式，请求方式一般有GET和POST方式
7、**GET和POST方式**：在数量较小情况下可以使用GET方式，但数据量超过1024字节就应该采用POST方式，避免出现请求失败或者请求异常的问题。
8、**返回接口调用状态**：所有API接口都应该统一标识调用的成功失败信息和规范错误编码信息，以及必要的提示字段信息。
9、**安全机制**：接口应规范验证签名机制，用户登录后统一调用KEY对接口安全验证。（关于KEY机制需由接口开发人员定义）
10、**参数说明**：应标注参数名称、是否必选、数据类型及范围、说明以及“否（必选）”传递默认的参数。

 
