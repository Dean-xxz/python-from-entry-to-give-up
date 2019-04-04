# Python Checklist
******
## 一、排版
#### 1.overall-总则
  统一清晰的排版可以帮助代码阅读者迅速聚焦代码的关键逻辑，迅速定位区块的开始结束位置，大大提高代码阅读的效率。  
+ 排版风格在同一文件中，必须保持统一；
+ 尽量把关系密切的逻辑集中在一起，保证视线无需漂移即可浏览到整个逻辑单元；
+ 在尚未养成习惯之前，可采用flake8之类的工具软件格式化代码；
#### 2.indent-缩进
+ 缩进。4个空格的缩进（编辑器可以完成此功能），不使用Tap，更不能混合使用Tap和空格。
#### 3.comment-注释
+ 文件头部需注释说明该文件的用途和注意事项；
+ 函数头部必须注释说明该函数的功能，参数和返回值。并以测试案例运行结果形式注释函数用法。
#### 4.backspace-空格
+ 各种右括号前不要加空格。
+ 逗号、冒号、分号前不要加空格。
+ 函数的左括号前不要加空格。如Func(1)。
+ 序列的左括号前不要加空格。如list[2]。
+ 操作符左右各加一个空格，不要为了对齐增加空格。
+ 函数默认参数使用的赋值符左右省略空格。
+ 不要将多句语句写在同一行，尽管使用‘；’允许。
+ if/for/while语句中，即使执行语句只有一句，也必须另起一行。
+ 在 comprehension 中允许if for 在同一行, 比如[ x for x in foo if x > 0] 
+ 在模拟三元赋值是允许if else 同一行， 比如： x = v1 if y else v2
#### 5.column-代码行长度
+ 每行最大长度79，换行可以使用反斜杠，最好使用圆括号。换行点要在操作符的后边敲回车。
+ 允许字符串单独一行超过80列，少于120字符，在行最后需要空两个空格，用# noqa: E501表示忽略该行PEP8检查
+ 允许sf-apidesc的参数检查一行超过80列，少于120字符，在行最后需要空两个空格，用# noqa: E501表示忽略该行PEP8检查
#### 6.换行
+ 必须使用Unix格式的换行符，禁止使用DOS/Windows格式。原因：某些Python语法对换行数有要求，如装饰器需要隔两行，之前两种换行混用时遇到过问题
#### 7.隔行
+ 函数内逻辑无关的代码段之间空一行，同时加以功能注释说明。原因：提高可读性
***
## 二、注释
#### 1.overall-总则
注释的目的是提升代码可读性，帮助代码读者更快速的了解代码作者的实际意图。
+ 注释应重点阐述目的，而非过程；
+ 注释应重点阐述隐性知识，即代码无法直接反映的意图、原则，如扩展方法，锁策略，内存分配限制等等；
+ 注释应重点阐述模块/函数之间的关联知识，即对比分析多个函数才能得到的知识，比如参数及返回值的含义、约束，外部数据的含义、取值范围，函数/模块之间的协作关系,多个变量/函数之间的相互关系等等；
+ 注释应避免描述显而易见的知识，比如：“这是一个构造函数”，“定义一个整型变量”；
+ 注释内容需要和代码实际行为保持一致，不应涉及无关内容，如“今天天气很好”，“checklist规定这里要注释”；
+ 注释需要及时更新，反映代码当前的状态，否则反而误导代码读者；
#### 2.禁止行内注释
+ 禁止使用行内注释， 比如 foo（） # comment
#### 3.禁止用注释屏蔽无用代码
+ 禁止用注释注释掉代码，没用代码就删掉。原因：减少后人的维护量，如搜索时
#### 4.中文注释
+ 优先使用中文写注释，除非英级过专8
#### 5.PEP8注释
+ 禁止使用# flake8: noqa进行注释。原因：该注释是表示整个文件都不进行PEP8检查，而非单独一行。
+ 的确需要跳过PEP8检查时（如字符串超过79列），在该行最后使用# noqa: Exxx注释。其中Exxx表示规则号，如# noqa: E501表示该行不对超过列数进行检查。
***
## 三、命名
#### 1.overall-总则
+ 如果已有的库存在不同风格的，保持内部的一致性是首选的
#### 2.模块名
+ 使用小写和下划线， 禁止使用大写。
+ 禁止使用大写字母命名文件或文件夹
+ python模块名统一采用横杆做分隔，不要使用下划线。原因：与开源社区的命名方式保持一致
+ python模块PKG-INFO中的包名不需要python开头，RPM包必须是python开头。原因：pip是python的打包机制，再弄一个python就多余了，RPM包带python方便区分
#### 3.类名
+ 类名使用CapWords约定。内部使用的类外加一个前导下划线
#### 4.全局变量名
+ 使用全大写格式， 如果不想被别人import， 前面加下划线， 比如_XXXX.
#### 5.函数名
+ 函数名应该为小写，可用下划线风格单词以增加可读性.
+ 内部私有函数命名需使用一个下划线开头
+ 函数内部再定义函数（闭包），函数名需要使用一个下划线开头
+ 函数命名采用[模块+]动宾结构，动词在前，名词在后，某些情况再加副词修饰，如list_vm，edit_vm，而不为了整齐而用vm_list、vm_edit
#### 6.方法或实类变量名
+ 通常使用小写单词，必要时用下划线分隔增加可读性。仅为不打算作为类的公共界面的内部方法和实例使用一个前导下划线
+ 接受变量后如果不使用， 使用_unuse 变量。 比如： _unuse, result = foo()
#### 7.变量命名
+ 对于表示容量或时间的变量，推荐将单位写到命令结尾，方便阅读。如size_mb，size_gb，time_ms、time_second
+ 对于表示网络带宽或者流速的，不要用bps这种单位简写作为变量名，需要单位全拼，如byteps、bitps、in_bytes、in_bitps。原因：bit和byte无法从一个小b区分出来，如果用大B变量名又会变得不符合规范
#### 8.禁止关键字
+ 命名应该有上下文意义，不能以关键字命名，如list，type
#### 9.Shell命令行
+ 模块shell命令行子命令命名采用模块+动词（或动宾）结构命令，如apollo vm-create、apollo vm-edit-quota。原因：方便命名查找
***
## 四、REST API
#### 1.禁止下划线
+ url命名不允许有下划线（除非url中间的参数），和大写字母，如 /clusters/set_state，用短杠和全小写。原因：横杆是http协议允许的字符，下划线不是http标准
#### 2.Method
+ REST API需要区分POST和PUT操作，POST为创建资源，PUT为更新资源，删除资源使用DELETE
#### 3.CRUD之外的命名规范
+ REST API的CRUD无法表示的操作，采用在资源一级下动宾结构命名，如修改某个用户角色(ID 12345)：/xxxx/users/12345/edit-role
#### 4.参数类型及返回值定义
+ 参数需要进行参数检查和约束，参数类型要做到精确匹配，如可用整型表示，绝不声明字符串类型
+ 返回值需要进行返回值检查，定义需要做到精确匹配，如可用整型表示，绝不声明为字符串类型。原因：能自动生成的易读的API文档
+ 避免用空字符串表示没有数据。原因：如UUID类型的数据，使用空表示没有数据会导致无法使用UUID表示该类型，只能用String()，导致类型匹配不精确。可采用允许传None的方式支持两种场景。
+ 请求参数、json格式返回值的字段名称只允许下划线拼接，字母用小写，禁止非ascii字符
***
## 五、异常
#### 1.try作用域
+ 异常中try的代码尽可能少，尽量做到只捕获已知的异常异，不能整个函数盲目try ... except: 
#### 2.异常日志规范
+ 异常打印前需要把出现异常的条件和相关变量打印出来
+ 所有异常的地方都需要用LOG.exception打印堆栈，不能使用LOG.error（能确定异常抛出地方的除外，如一些约定好的异常类型）
+ LOG.exception只能用于发现异常处的except作用域内。原因：部分人误解这个是用于打堆栈
+ 异常不能用str(e)或者e.message获取异常信息，如有需要，可以用"%s" % e方式获取异常信息。原因：异常信息可能是中文字符，str()是处理ascii编码的，e.message可能是未格式化的字符串，每个异常实现不一样
#### 3.异常定义
+ 模块内的主动抛的异常，都必须继承统一的基类（模块定义的），原因：便于识别异常类型，或统一处理
#### 4.异常处理
+ except 的as命名统一用ex或xxx_ex，不要用单个字母e，如except Exception as ex。原因：提高代码可读性
+ except和finally子句中，必须保证不抛新的未知异常。except作用域中不能进行复杂的代码逻辑，只能调用LOG.exception打日志和异常类型转换，如果需要进行如资源回滚删除等操作，需要用try捕获异常，避免覆盖当前的异常。原因：except作用域中复杂的操作可能触发新的异常，覆盖之前抛出的异常
#### 5.NotImplemented和NotImplementedError区别
+ NotImplemented 是一个非异常对象，NotImplementedError 是一个异常对象。NotImplemented故名思议，就是“未实现”，一般是用在一些比较算法中的，如class的__eq__,__lt__等，注意NotImplemented并不是异常，所以不能使用raise，当没有实现时应该是return NotImplemented。
***
## 六、断言
#### 1.检查
+ 对于必须满足的条件， 尽量使用assert 进行检查。
***
## 七、import
#### 1.类库的导入顺序
+ 标准库
+ 开源的库
+ 我们的库
+ 每种类型（标准库、开源库、我们的库）之间用空行分隔，同类型内模块导入顺序要求按字母排序，不要求不同类型之间按字母排序。如：
        import abc  
        import six  
          
        from oslo_a import b  
        from oslo_b import a  
        from oslo_b import b  
        
        from my_project import a  
        from my_project.a import c  
        from my_project.b import b  
#### 2.全部导入
+ 业务代码内（基础库除外）禁止使用 import *导入所有模块
#### 3.不用不导入
+ 不要导入不使用的模块
#### 4.每行只允许import一个模块
+ 每个导入应该独占一行.禁止使用import os, sys;
#### 5.服务间禁止互相import
+ 服务不能依赖服务，容易出现配置冲突的问题
***
## 八、函数
#### 1.参数
+ 函数参数默认值禁止列表， 字典等可变变量。
+ 新添加的参数必须考虑向后兼容问题， 必须带有效默认值。
+ 不允许使用 foo(*args, **kwargs) 这样的写法。
+ 【推荐】函数参数顺序应当按重要性进行排序
+ 禁止使用locals()，globals()传递参数，这样会造成传参意图不清晰，代码难以维护，时不时来点意外惊喜
#### 2.命令行参数
+ 命令行参数的值不允许使用json格式。原因：对调用者不友好，示例也不好写，示例一旦写不好就会出现不知道怎么传参的问题
#### 3.默认值
+ 参数列表不能存在可变数据类型(dict,list,set)的默认值，如 def func(a=[])，原因：参数列表的默认数据在函数声明时就初始化，整个进程内都会生效
#### 4.装饰器
+ 实现装饰器时，返回的函数都得用six.wraps(func)装饰，func为被装饰函数
***
## 九、数据类型
#### 1.区分字典与json
+ Python里面的字典与JSON看起来很相近，但是我们将字典对象保存到文件或者数据库时，会发现保存的数据key和value前面都带了u前缀，导致C程序无法解析。这是因为我们直接将字典当成字符串处理时是调用了字典的__str()__函数，打印出来的是字段的内容而非JSON格式数据。正确的做法是用json.loads()、json.dumps()将字典转换为JSON字符串再写入
+ JSON数据存放MySQL，SQLAlchemy定义Column类型需采用JsonBlob类型。原因：该类型会自动调用json.dumps()函数解决1）的问题
#### 2.列表
+ 禁止在遍历列表过程中删除列表的元素。原因：原因是在删除list中的元素后，list的实际长度变小了，但是循环次数没有减少，依然按照原来list的长度进行遍历，所以会造成索引溢出，甚至抛异常IndexError: list index out of range。https://segmentfault.com/a/1190000007214571
***
## 十、性能
#### 1.获取GET请求参数
+ req.params不允许获取多次。原因：每次访问会构造一个MultiDict对象
#### 2.字符串拼接
+ 多于2个字符串的拼接，禁止使用“+”，而应该用join
#### 3.逻辑
+ 跟循环控制无关的逻辑应该放到循环外，以避免重复计算（示例见标注）
#### 4.字典更新
+ 单字段更新用索引赋值，如d['k']=v。多字段更新用update，如d.update(k=v)。原因：索引赋值比update性能要好
***
## 十一、风格
#### 1.特殊语法
+ 原类（metaclasses）， 如果替代方案， 禁止使用。
+ 简单的格式化字符串， 应使用"%s " % (xx) 方案， 避免使用str.format()
+ 导入黑客（import hacks）, 意思是必须import某个类， 后面代码才可以正常运行， 带代码看上去却用不到。
#### 2.null-空值判断
+ 不用使用==或者!=比较单件，比如None，使用is或者is not。
+ 不要使用==将一个布尔值与false比较，使用if not x:代替。当需要区分false和None时，使用if not x and x is not None语句判断。
+ 对于序列（字符串、列表、元组），空序列是false，尽量使用if not seq:或者if seq:，不要使用if len(seq):或者if not len(seq):。
+ 整形比较时，不要使用if x:或者if not x:，应该使用if x ==0代替，防止0与None值混淆。
+ 空的字典(dict)，列表(list)，元组(tuple)，集合(set)的判断用 if not seq，禁止if not len(seq)或者 if not seq.keys()等
#### 3.if判断
+ if的判断语句，不能超过一行，可通过声明变量或提取函数保存判断条件来解决，原因：超过一行可读性就会很差
+ [推荐]尽量使用内建的 all, any 处理2个以上的条件判断，如if any((x, y, z)) 要优于  if x or y or z原因：提高可读性，更pythonic
+ if和else代码块的行数不能超过10行，超过得拆成子函数调用。原因：提高代码可读性
+ 过长的if else语句，不能写成三目运算格式，需要使用传统if else多条语句格式，原因：可读性较差，不利于非python背景的人review和维护
#### 4.空行
+ [推荐]if,while,for等控制语句前面需要空一行。原因：提高可读性
#### 5.元祖
+ 元组(tuple)类型的数据，每个元素后必须加“,”，如 (1,)，(1,2,)。原因：只有一个元素时，“（）”的作用就不是表示元组
#### 6.字典
+ 在确定存在key的情况下，推荐使用dictB['keyA']而不使用dictB.get('keyA')。原因：dictB.get('keyA')在出BUG后还能继续往后执行，导致问题再后面才暴露，或者被隐藏了一直没发现，采用dictB['keyA']能尽早发现问题
+ 所有使用get的地方都需要显式声明默认值，如dictA.get('a', None)，禁止使用dictA.get('a')。原因：赋默认值写法能让编码者和阅读代码的人清楚你是有考虑获取不到数据的情况返回None
+ 字典使用if 'keyA' in dictA的写法判断是否存在key值，不使用dictA.has_key('keyA')的写法。原因：字典的has_key()是旧python版本的接口
+ 对字典赋默认值使用setdefault()函数，如dictA.setdefault('keyA', 'A')，不使用if判断然后再赋值。原因：不需要写两行，setdefault()会判断是否存在key，存在时不会对其赋值，不存在时采用默认值进行赋值
#### 7.返回值
+ 不建议采用Bool类型返回值判断函数执行成功，通过抛异常来表示是否执行结果，没抛异常表示执行正确
明确：is_xxx通过bool类型返回，check_xxx通过异常来表示结果。原因：代码可以减少判断逻辑，看起来更简洁
***
## 十二、日志
#### 1.日志等级
+ GET请求禁止使用LOG.info打日志，使用LOG.debug。原因：GET请求很频繁，每次都打日志会导致我们日志量很大，LOG.debug日志默认是屏蔽的，只有打开时才会记录，可通过killall -USR1 xxxx打开debug日志
+ Phoenix框架及Openstack框架的服务默认需要关闭debug日志。原因：Openstack框架每个请求到会产生两条日志，导致日志量非常庞大
#### 2.调试信息
+ 错误日志（含异常日志）需要带操作的资源的信息（ID等）。原因：出错后可以定位是对哪个资源的操作
#### 3.print日志
+ 后台服务不允许使用print打印调试信息
#### 4.敏感信息
+ 涉及客户数据的内容，只允许打debug日志，不能打info及以上。原因：默认debug不显示，不会造成客户数据泄露
+ 用户的明文密码不能直接打到日志中，包括后台日志。原因：避免泄露用户信息
#### 5.风格
+ 异常日志中，数字、英文两边需要各加一空格，如 "数量 %(num) 超过上限 %(max)！"，原因：不加空格显示很拥挤，提示信息在页面上不好看