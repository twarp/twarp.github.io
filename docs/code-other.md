>【强制】在使用正则表达式时，利用好其预编译功能，可以有效加快正则匹配速度。

?> 不要在方法体内定义:Pattern pattern = Pattern.compile(规则);

>【强制】velocity 调用 POJO 类的属性时，建议直接使用属性名取值即可，模板引擎会自动按 规范调用 POJO 的 getXxx()，如果是 boolean 基本数据类型变量(boolean 命名不需要加 is 前缀)，会自动调用 isXxx()方法。

?> 注意如果是 Boolean 包装类对象，优先调用 getXxx()的方法。

>【强制】后台输送给页面的变量必须加$!{var}——中间的感叹号。 ?> 如果 var=null 或者不存在，那么${var}会直接显示在页面上。

---

>【强制】注意 Math.random() 这个方法返回是 double 类型，注意取值的范围 0≤x<1(能够 取到零值，注意除零异常)，如果想获取整数类型的随机数，不要将 x 放大 10 的若干倍然后 取整，直接使用 Random 对象的 nextInt 或者 nextLong 方法。

---

>【强制】获取当前毫秒数 System.currentTimeMillis(); 而不是 new Date().getTime(); ?> 如果想获取更加精确的纳秒级时间值，使用 System.nanoTime()的方式。在 JDK8 中， 针对统计时间等场景，推荐使用 Instant 类。

---

>【推荐】不要在视图模板中加入任何复杂的逻辑。

?> 根据 MVC 理论，视图的职责是展示，不要抢模型和控制器的活。

>【推荐】任何数据结构的构造或初始化，都应指定大小，避免数据结构无限增长吃光内存。

---

>【推荐】及时清理不再使用的代码段或配置信息。

?> 对于垃圾代码或过时配置，坚决清理干净，避免程序过度臃肿，代码冗余。 正例:对于暂时被注释掉，后续可能恢复使用的代码片断，在注释代码上方，统一规定使用三 个斜杠(///)来说明注释掉代码的理由。