>【强制】不允许任何魔法值(即未经定义的常量)直接出现在代码中。
 
反例:
```
String key = "Id#taobao_" + tradeId;  
cache.put(key, value);
```
>【强制】long 或者 Long 初始赋值时，使用大写的 L，不能是小写的 l，小写容易跟数字 1 混 淆，造成误解。

!> Long a = 2l; 写的是数字的 21，还是 Long 型的 2?  
 
>【推荐】不要使用一个常量类维护所有常量，按常量功能进行归类，分开维护。 

!> 大而全的常量类，非得使用查找功能才能定位到修改的常量，不利于理解和维护。

正例:

?> 缓存相关常量放在类 CacheConsts 下;系统配置相关常量放在类 ConfigConsts 下。

>【推荐】常量的复用层次有五层:跨应用共享常量、应用内共享常量、子工程内共享常量、包内共享常量、类内共享常量。  
 
- 跨应用共享常量:放置在二方库中，通常是client.jar中的constant目录下。  
- 应用内共享常量:放置在一方库中，通常是modules中的constant目录下。
    
反例:

?> 易懂变量也要统一定义成应用内共享常量，两位攻城师在两个类中分别定义了表示 “是”的变量:    
类 A 中:public static final String YES = "yes";  
类 B 中:public static final String YES = "y";  
A.YES.equals(B.YES);预期是true，但实际返回为false，导致线上问题。  


- 子工程内部共享常量:即在当前子工程的constant目录下。  
- 包内共享常量:即在当前包下单独的constant目录下。
- 类内共享常量:直接在类内部private static final定义。  

>【推荐】如果变量值仅在一个范围内变化，且带有名称之外的延伸属性，定义为枚举类。下面 正例中的数字就是延伸信息，表示星期几。

正例:
```   
public Enum { MONDAY(1), TUESDAY(2), WEDNESDAY(3), THURSDAY(4), FRIDAY(5), SATURDAY(6), SUNDAY(7);}
```
