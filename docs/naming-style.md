>【强制】代码中的命名均不能以`下划线或美元符号`开始，也不能以`下划线或美元符号`结束。  

反例:  
```
_name / __name / Object / name_ / name$ / Object$
```
>【强制】代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。  

正例:  
```
alibaba / taobao / youku / hangzhou 等国际通用的名称，可视同英文。
```
反例:
```
DaZhePromotion [打折] / getPingfenByName() [评分] / int 某变量 = 3
```
!> 正确的英文拼写和语法可以让阅读者易于理解，避免歧义。即使纯拼音命名方式 也要避免采用。

>【强制】类名使用 UpperCamelCase 风格，必须遵从驼峰形式，但以下情形例外:DO / BO / DTO / VO / AO

正例:
```
MarcoPolo / UserDO / XmlService / TcpUdpDeal / TaPromotion
``` 
反例: 
```
macroPolo / UserDo / XMLService / TCPUDPDeal / TAPromotion
``` 
>【强制】方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从 驼峰形式。

正例: 
```
localValue / getHttpMessage() / inputUserId
```
>【强制】常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。

正例:
```
MAX_STOCK_COUNT
```  
反例:
```
MAX_COUNT
```
>【强制】抽象类命名使用 Abstract 或 Base 开头;异常类命名使用 Exception 结尾;测试类 命名以它要测试的类的名称开始，以 Test 结尾。

---

>【强制】中括号是数组类型的一部分，数组定义如下:String[] args; 

反例:
```
使用String args[]的方式来定义。
```

>【强制】POJO 类中布尔类型的变量，都不要加 is，否则部分框架解析会引起序列化错误。

反例:
```
定义为基本数据类型Boolean isDeleted;的属性，它的方法也是isDeleted()，RPC框架在反向解析的时候，“以为”对应的属性名称是 deleted，导致属性获取不到，进而抛出异常。
```

>【强制】包名统一使用小写，点分隔符之间有且仅有一个自然语义的英语单词。包名统一使用 单数形式，但是类名如果有复数含义，类名可以使用复数形式。  

正例:
```
应用工具类包名为com.alibaba.open.util、类名为MessageUtils(此规则参考 spring 的框架结构)
```
>【强制】杜绝完全不规范的缩写，避免望文不知义。

反例:
```
AbstractClass“缩写”命名成 AbsClass;condition“缩写”命名成 condi，此类随 意缩写严重降低了代码的可阅读性。
```
>【推荐】为了达到代码自解释的目标，任何自定义编程元素在命名时，使用尽量完整的单词 组合来表达其意。

正例:
```
从远程仓库拉取代码的类命名为 PullCodeFromRemoteRepository。
```  
反例:
```
变量 int a; 的随意命名方式。
```
>【推荐】如果模块、接口、类、方法使用了设计模式，在命名时体现出具体模式。 说明:将设计模式体现在名字中，有利于阅读者快速理解架构设计理念。
 
正例:
```   
public class OrderFactory;  
public class LoginProxy;  
public class ResourceObserver;
```
>【推荐】接口类中的方法和属性不要加任何修饰符号(public 也不要加)，保持代码的简洁 性，并加上有效的 Javadoc 注释。尽量不要在接口里定义变量，如果一定要定义变量，肯定是 与接口方法相关，并且是整个应用的基础常量。

正例:
```   
接口方法签名:void f();  
接口基础常量表示:String COMPANY = "alibaba";
```  
反例:
```
接口方法定义:public abstract void f();
```
!> JDK8 中接口允许有默认实现，那么这个 default 方法，是对所有实现类都有价值的默 认实现。

**接口和实现类的命名有两套规则:**
> 1)【强制】对于 Service 和 DAO 类，基于 SOA 的理念，暴露出来的服务一定是接口，内部的实现类用 Impl 的后缀与接口区别。
    
正例:
```
CacheServiceImpl 实现 CacheService 接口。
```
> 2)【推荐】如果是形容能力的接口名称，取对应的形容词做接口名(通常是–able 的形式)。 

正例:
```
AbstractTranslator 实现 Translatable。
```
>【参考】枚举类名建议带上 Enum 后缀，枚举成员名称需要全大写，单词间用下划线隔开。

正例:
```
枚举名字为ProcessStatusEnum的成员名称:SUCCESS / UNKOWN_REASON。
```
!> 枚举其实就是特殊的常量类，且构造方法被默认强制是私有。 
 
>【参考】各层命名规约: 

``` 
A) Service/DAO层方法命名规约  
    1) 获取单个对象的方法用get做前缀。  
    2) 获取多个对象的方法用list做前缀。  
    3) 获取统计值的方法用count做前缀。  
    4) 插入的方法用save/insert做前缀。  
    5) 删除的方法用remove/delete做前缀。  
    6) 修改的方法用update做前缀。  
B) 领域模型命名规约
    1) 数据对象:xxxDO，xxx即为数据表名。
    2) 数据传输对象:xxxDTO，xxx为业务领域相关的名称。
    3) 展示对象:xxxVO，xxx一般为网页名称。
    4) POJO是DO/DTO/BO/VO的统称，禁止命名成xxxPOJO。
```