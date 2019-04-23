# 编程
## 命名规约
1. 【强制】 代码中的命名均不能以下划线或美元符号开始，也不能以下划线或美元符号结束。
反例：``_role/ __ role / $ role / role _ / role $ / role __``
2. 【强制】 代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。
说明： 正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式也要避免采用。
正例： ``alibaba / taobao / youku / hangzhou`` 等国际通用的名称，可视同英文
反例：``
ChuangJianJueSe[创建角色] / getJueSe() [查看角色详情] ``
3. 【强制】类名使用 UpperCamelCase 风格，但以下情形例外： DTO等。
正例：``BasePoJo / RoleDTO /XmlService / ModuleService``
反例：``basePolo / RoleDto / XMLService / moduleService``
4. 【强制】方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式。
正例：``updateRole() / queryUtil / parentCode /userOrgIdsList``
5. 【 强制】常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。
正例： ``DRIVER_CLASS_NAME``
反例：`` CLASS_NAME``
6. 【强制】抽象类命名使用 Abstract开头； 异常类命名使用 Exception 结尾； 测试类
命名以它要测试的类的名称开始，以 Test 结尾。
正例：``BusinessException/ SystemConfigurationServiceTest``
7. 【强制】类型与中括号紧挨相连来表示数组。
正例： 定义字符型数组 ``String[] idArr;``
反例： ``String idArr []``
8. 【强制】POJO 类中布尔类型的变量，都不要加 is 前缀，否则部分框架解析会引起序列化错误。
反例： 定义为基本数据类型`` Boolean isDeleted`` 的属性，它的方法也是`` isDeleted()``， RPC
框架在反向解析的时候， “误以为” 对应的属性名称是 ``deleted``，导致属性获取不到，进而抛
出异常。
9. 【强制】包名统一使用小写，点分隔符之间有且仅有一个自然语义的英语单词。包名统一使用单数形式，但是类名如果有复数含义，类名可以使用复数形式。
正例： 应用工具类包名为`` com.system.util``、类名为 ``TextUtils``（ 此规则参考`` spring``
的框架结构）
10. 【强制】杜绝完全不规范的缩写， 避免望文不知义。
反例： ``ConfigurationRest ``“缩写” 命名成`` ConRest``； ``assignee`` “ 缩写” 命名成 ``assi``，此类随意缩写严重降低了代码的可阅读性。
11. 【推荐】为了达到代码自解释的目标，任何自定义编程元素在命名时，使用尽量完整的单词组合来表达其意。
反例： 变量`` int c``的随意命名方式。
12. 【推荐】如果模块、 接口、类、方法使用了设计模式，在命名时需体现出具体模式。
说明： 将设计模式体现在名字中，有利于阅读者快速理解架构设计理念。
正例：`` public class ResourceObserver;``
13. 【推荐】接口类中的方法和属性不要加任何修饰符号（ public 也不要加） ，保持代码的简洁性，并加上有效的 Javadoc 注释。尽量不要在接口里定义变量，如果一定要定义变量，肯定是与接口方法相关，并且是整个应用的基础常量。
正例： 接口方法签名 
```java
List<BreadcrumbDTO> getBreadcrumb(Integer moduleId) throws BusinessException;
```
接口基础常量 
```java
String COMPANY = "logic";
```
反例： 接口方法定义 
```java
public ArrayList getAutoNumbers(String entityName) throws BusinessException;
```
说明： JDK8 中接口允许有默认实现，那么这个 default 方法，是对所有实现类都有价值的默认实现。
14. 接口和实现类的命名：
1）【强制】对于Persistence，mybatis配置文件xml以Mapper结尾， Java接口也以Mapper结尾。
正例：``AutoNumberReadMapper.xml，AutoNumberReadMapper.java``
2） 【强制】对于 Service，基于 SOA 的理念，暴露出来的服务一定是接口，内部的实现类用 Impl 的后缀与接口区别。
正例：``AddressServiceImpl implements IAddressService``
3）【强制】对于WS，类名以Rest结尾
正例：``EmailRest``
15. 【参考】枚举类名建议带上 Enum 后缀，枚举成员名称需要全大写，单词间用下划线隔开。
说明： 枚举其实就是特殊的类， 域成员均为常量， 且构造方法被默认强制是私有。
正例： 枚举名字为 ``SysConfigEnum``的成员名称：`` SUCCESS / FILE_LOCAT_PATH``。
16. 【参考】各层命名规约：
A）Persistence层方法命名规约
1） 获取单个对象的方法用 select做前缀。``selectTimeZone``
2） 获取多个对象的方法用 select做前缀，复数形式结尾如： ``selectCorporateUsers``
3） 分页获取多个对象的方法用query做前缀。``queryInformation(QueryUtil queryUtil)``
4） 获取统计值的方法用 count 做前缀。
5） 插入的方法用insertSelective。
7） 删除的方法用 deleteByPrimaryKey。
9） 修改的方法用 updateByPrimaryKeySelective。
B) Service 层方法命名规约
1） 获取单个对象的方法用 get 做前缀。``getPageInformation``
2） 获取多个对象的方法用 list 做前缀，复数形式结尾如： ``listModules``
3） 分页获取多个对象的方法用query做前缀。``queryInformation(QueryUtil queryUtil)``
4） 获取统计值的方法用 count 做前缀。
5） 插入的方法用insert 做前缀。
6）插入多个对象的方法用batchInsert做前缀。
7） 删除的方法用 delete 做前缀。
8）删除多个对象的方法用batchDelete做前缀
9） 修改的方法用 update 做前缀。
10）修改多个对象的方法用batchUpdate做前缀
C)WS 层方法命名规约
参考Service层
## 常量定义
1. 【强制】不允许任何魔法值（ 即未经预先定义的常量） 直接出现在代码中。
反例：``breadcrumbDTO.setLabel("Home");``
2. 【强制】 在 long 或者 Long 赋值时， 数值后使用大写的 L，不能是小写的 l，小写容易跟数字1 混淆，造成误解。
说明： Long a = 2l; 写的是数字的 21，还是 Long 型的 2?
3. 【推荐】不要使用一个常量类维护所有常量， 要按常量功能进行归类，分开维护。
说明： 大而全的常量类， 杂乱无章， 使用查找功能才能定位到修改的常量，不利于理解和维护。
正例： 邮件类型相关常量放在在类 MailTypeEnum下； 表单类型相关常量放在类 FormTypeEnum下。
4. 【推荐】 如果变量值仅在一个固定范围内变化用 enum 类型来定义。
说明： 如果存在名称之外的延伸属性应使用 enum 类型，下面正例中的数字就是延伸信息，表示角色级别中的第几个级别。
正例：
```java
public enum RoleLevelEnum{
CORPORATE_ADMIN(2),CORPORATE_USER(3)
    private Integer roleLevel;
    public Integer getRoleLevel() {
        return roleLevel;
    }
    RoleLevelEnum(Integer roleLevel) {
        this.roleLevel = roleLevel;
}
}
```
## 代码格式
1. 【强制】大括号的使用约定。如果是大括号内为空，则简洁地写成{}即可，不需要换行； 如果
是非空代码块则：
1） 左大括号前不换行。
2） 左大括号后换行。
3） 右大括号前换行。
4） 右大括号后还有 else 等代码则不换行； 表示终止的右大括号后必须换行。
2. 【强制】左小括号和字符之间不出现空格； 同样，右小括号和字符之间也不出现空格；而左大括号前需要空格。详见第 5 条下方正例提示。
反例：`` if (空格 a == b 空格)``
3. 【强制】 ``if/for/while/switch/do`` 等保留字与括号之间都必须加空格。
4. 【强制】任何二目、 三目运算符的左右两边都需要加一个空格。
说明： 运算符包括赋值运算符=、逻辑运算符&&、加减乘除符号等。
5. 【强制】 采用 4 个空格缩进，禁止使用 tab 字符。
说明： 如果使用 tab 缩进，必须设置 1 个 tab 为 4 个空格。 IDEA 设置 tab 为 4 个空格时，请勿勾选`` Use tab character``；而在 eclipse 中，Text Editors必须勾选`` insert spaces for tabs``。
正例： （ 涉及 1-5 点）
```java
public static void main(String[] args) {
// 缩进 4 个空格
String say = "hello";
// 运算符的左右必须有一个空格
int flag = 0;
// 关键词 if 与括号之间必须有一个空格，括号内的 f 与左括号， 0 与右括号不需要空格
if (flag == 0) {
System.out.println(say);
}
// 左大括号前加空格且不换行；左大括号后换行
if (flag == 1) {
System.out.println("world");
// 右大括号前换行，右大括号后有 else，不用换行
} else {
System.out.println("ok");
// 在右大括号后直接结束，则必须换行
}
}
```
6. 【强制】注释的双斜线与注释内容之间有且仅有一个空格。
正例：
// 这是示例注释，请注意在双斜线之后有一个空格
``String ygb = new String();``
7. 【强制】单行字符数限制不超过 120 个，超出需要换行，换行时遵循如下原则：
1） 第二行相对第一行缩进 4 个空格，从第三行开始，不再继续缩进，参考示例。
2） 运算符与下文一起换行。
3） 方法调用的点符号与下文一起换行。
4） 方法调用中的多个参数需要换行时， 在逗号后进行。
5） 在括号前不要换行，见反例。
正例：
```java
StringBuffer sb = new StringBuffer();
// 超过 120 个字符的情况下，换行缩进 4 个空格， 点号和方法名称一起换行
sb.append("zi").append("xin")...
.append("huang")...
.append("huang")...
.append("huang");
```
反例：
```java
StringBuffer sb = new StringBuffer();
// 超过 120 个字符的情况下，不要在括号前换行
sb.append("zi").append("xin")...append
("huang");
// 参数很多的方法调用可能超过 120 个字符， 不要在逗号前换行
method(args1, args2, args3, ...
, argsX);
```
8. 【强制】方法参数在定义和传入时，多个参数逗号后边必须加空格。
正例： 下例中实参的 args1， 后边必须要有一个空格。
```java
method(args1, args2, args3);
```
9. 【强制】 IDE Workspace中的`` Text file encoding`` 设置为 UTF-8; IDE 中的``New text file line delimiter``使用 Unix 格式，不要使用 Windows 格式。
10. 【推荐】单个方法的总行数不超过 80 行。
说明： 包括方法签名、结束右大括号、方法内代码、注释、空行、回车及任何不可见字符的总
行数不超过 80 行。
正例： 代码逻辑分清红花和绿叶， 个性和共性，绿叶逻辑单独出来成为额外方法，使主干代码
更加清晰； 共性逻辑抽取成为共性方法，便于复用和维护。
11. 【推荐】没有必要增加若干空格来使某一行的字符与上一行对应位置的字符对齐。
正例：
```java
int one = 1;
long two = 2L;
float three = 3F;
StringBuffer sb = new StringBuffer();
```
说明： 增加 sb 这个变量，如果需要对齐，则给 a、 b、 c 都要增加几个空格，在变量比较多的情况下，是非常累赘的事情。
12. 【推荐】 不同逻辑、不同语义、不同业务的代码之间插入一个空行分隔开来以提升可读性。
说明： 任何情形， 没有必要插入多个空行进行隔开。
## OOP 规约
1. 【强制】避免通过一个类的对象引用访问此类的静态变量或静态方法，无谓增加编译器解析成本，直接用类名来访问即可。
2. 【强制】所有的覆写方法，必须加@Override 注解。
说明： getObject()与 get0bject()的问题。一个是字母的 O，一个是数字的 0，加@Override
可以准确判断是否覆盖成功。另外，如果在抽象类中对方法签名进行修改，其实现类会马上编译报错。
3. 【强制】相同参数类型，相同业务含义，才可以使用 Java 的可变参数，避免使用 Object。
说明： 可变参数必须放置在参数列表的最后。 （尽量不用可变参数编程）
正例：``public List<User> listUsers(String type, Long... ids) {...}``
4. 【强制】外部正在调用或者二方库依赖的接口，不允许修改方法签名，避免对接口调用方产生影响。接口过时必须加@Deprecated 注解，并清晰地说明采用的新接口或者新服务是什么。
5. 【强制】不能使用过时的类或方法。
说明： java.net.URLDecoder 中的方法 decode(String encodeStr) 这个方法已经过时，应
该使用双参数 decode(String source, String encode)。接口提供方既然明确是过时接口，
那么有义务同时提供新的接口； 作为调用方来说，有义务去考证过时方法的新实现是什么。
6. 【强制】 Object 的 equals 方法容易抛空指针异常，应使用常量或确定有值的对象来调用equals。
正例： 
```java
"test".equals(object);
```
反例： 
```java
object.equals("test");
```
说明： 推荐使用``java.util.Objects#equals``（ JDK7 引入的工具类）
7. 【强制】所有的相同类型的包装类对象之间值的比较，全部使用 equals 方法比较。
说明： 对于``Integer var = ?`` 在-128 至 127 范围内的赋值， Integer 对象是在
``IntegerCache.cache`` 产生，会复用已有对象，这个区间内的 Integer 值可以直接使用==进行
判断，但是这个区间之外的所有数据，都会在堆上产生，并不会复用已有对象，这是一个大坑，推荐使用 equals 方法进行判断。
8. 关于基本数据类型与包装数据类型的使用标准如下：
1） 【强制】 所有的 POJO 类属性必须使用包装数据类型。
2） 【强制】 RPC 方法的返回值和参数必须使用包装数据类型。
3） 【 推荐】 所有的局部变量使用基本数据类型。
说明： POJO 类属性没有初值是提醒使用者在需要使用时，必须自己显式地进行赋值，任何
NPE 问题，或者入库检查，都由使用者来保证。
正例： 数据库的查询结果可能是 null，因为自动拆箱，用基本数据类型接收有 NPE 风险。
反例： 比如显示成交总额涨跌情况，即正负 x%， x 为基本数据类型，调用的 RPC 服务，调用不成功时，返回的是默认值，页面显示为 0%，这是不合理的，应该显示成中划线。所以包装数据类型的 null 值，能够表示额外的信息，如：远程调用失败，异常退出。
9. 【强制】定义 DO/DTO/VO 等 POJO 类时，不要设定任何属性默认值。
反例： POJO 类的 gmtCreate 默认值为 new Date()， 但是这个属性在数据提取时并没有置入具体值，在更新其它字段时又附带更新了此字段，导致创建时间被修改成当前时间。
10. 【强制】序列化类新增属性时，请不要修改 ``serialVersionUID ``字段，避免反序列失败； 如果完全不兼容升级，避免反序列化混乱，那么请修改 ``serialVersionUID ``值。
说明： 注意 ``serialVersionUID`` 不一致会抛出序列化运行时异常。
11. 【强制】构造方法里面禁止加入任何业务逻辑，如果有初始化逻辑，请放在 init 方法中。
12. 【强制】 POJO 类必须写 toString 方法。使用 IDE 中的工具：`` source> generate toString``
时，如果继承了另一个 POJO 类，注意在前面加一下 ``super.toString``。
说明： 在方法执行抛出异常时，可以直接调用 POJO 的 ``toString()``方法打印其属性值，便于排查问题。
13. 【强制】禁止在 POJO 类中，同时存在对应属性 xxx 的`` isXxx()``和 ``getXxx()``方法。
说明： 框架在调用属性 xxx 的提取方法时，并不能确定哪个方法一定是被优先调用到。
14. 【推荐】使用索引访问用 String 的 split 方法得到的数组时，需做最后一个分隔符后有无内容的检查，否则会有抛`` IndexOutOfBoundsException`` 的风险。
说明：
```java
String str = "a,b,c,,";
String[] ary = str.split(",");
// 预期大于 3，结果是 3
System.out.println(ary.length);
```
15. 【推荐】当一个类有多个构造方法，或者多个同名方法，这些方法应该按顺序放置在一起，便于阅读，此条规则优先于第 16 条规则。
16. 【推荐】 类内方法定义的顺序依次是：公有方法或保护方法 > 私有方法 > getter/setter
方法。
说明： 公有方法是类的调用者和维护者最关心的方法，首屏展示最好； 保护方法虽然只是子类关心，也可能是“模板设计模式”下的核心方法； 而私有方法外部一般不需要特别关心，是一个黑盒实现； 因为承载的信息价值较低，所有 Service 和 DAO 的`` getter/setter ``方法放在类体最后。
17. 【推荐】 setter 方法中，参数名称与类成员变量名称一致， this.成员名 = 参数名。在
``getter/setter ``方法中， 不要增加业务逻辑，增加排查问题的难度。
反例：
```java
public Integer getData() {
if (condition) {
return this.data + 100;
} else {
return this.data - 100;
}
}
```
18. 【推荐】循环体内，字符串的连接方式，使用 StringBuilder 的 append 方法进行扩展。
说明： 下例中， 反编译出的字节码文件显示每次循环都会 new 出一个 StringBuilder 对象，
然后进行 append 操作，最后通过 toString 方法返回 String 对象，造成内存资源浪费。
反例：
```java
String str = "start";
for (int i = 0; i < 100; i++) {
str = str + "hello";
}
```
19. 【推荐】 final 可以声明类、成员变量、方法、以及本地变量，下列情况使用 final 关键字：
1） 不允许被继承的类，如： String 类。
2） 不允许修改引用的域对象。
3） 不允许被重写的方法，如： POJO 类的 setter 方法。
4） 不允许运行过程中重新赋值的局部变量。
5） 避免上下文重复使用一个变量，使用 final 描述可以强制重新定义一个变量，方便更好
地进行重构。
20. 【推荐】慎用 Object 的 clone 方法来拷贝对象。
说明： 对象的 clone 方法默认是浅拷贝，若想实现深拷贝需要重写 clone 方法实现域对象的深度遍历式拷贝。深拷贝可参考``org.apache.commons.beanutils.BeanUtilsBean``
21. 【推荐】类成员与方法访问控制从严：
1） 如果不允许外部直接通过 new 来创建对象，那么构造方法必须是 private。
2） 工具类不允许有 public 或 default 构造方法。
3） 类非 static 成员变量并且与子类共享，必须是 protected。
4） 类非 static 成员变量并且仅在本类使用，必须是 private。
5） 类 static 成员变量如果仅在本类使用，必须是 private。
6） 若是 static 成员变量， 考虑是否为 final。
7） 类成员方法只供类内部调用，必须是 private。
8） 类成员方法只对继承类公开，那么限制为 protected。
说明： 任何类、方法、参数、变量，严控访问范围。过于宽泛的访问范围，不利于模块解耦。
思考：如果是一个 private 的方法，想删除就删除，可是一个 public 的 service 成员方法或
成员变量，删除一下，不得手心冒点汗吗？变量像自己的小孩，尽量在自己的视线内，变量作用域太大， 无限制的到处跑，那么你会担心的。
## 集合处理
1. 【强制】 关于 hashCode 和 equals 的处理，遵循如下规则：
1） 只要重写 equals，就必须重写 hashCode。
2） 因为 Set 存储的是不重复的对象，依据 hashCode 和 equals 进行判断，所以 Set 存储的对象必须重写这两个方法。
3） 如果自定义对象作为 Map 的键，那么必须重写 hashCode 和 equals。
说明： String 重写了 hashCode 和 equals 方法，所以我们可以非常愉快地使用 String 对象作为 key 来使用。
2. 【强制】 ArrayList的subList结果不可强转成ArrayList，否则会抛出 ClassCastException
异常， 即 ``java.util.RandomAccessSubList cannot be cast to java.util.ArrayList。``
说明： subList 返回的是 ArrayList 的内部类 SubList，并不是 ArrayList 而是 ArrayList
的一个视图，对于 SubList 子列表的所有操作最终会反映到原列表上。
3. 【强制】在 subList 场景中， 高度注意对原集合元素的增加或删除， 均会导致子列表的遍历、增加、删除产生 ConcurrentModificationException 异常。
4. 【强制】使用集合转数组的方法，必须使用集合的`` toArray(T[] array)``，传入的是类型完全
一样的数组，大小就是 list.size()。
说明： 使用 toArray 带参方法，入参分配的数组空间不够大时， toArray 方法内部将重新分配内存空间，并返回新数组地址； 如果数组元素个数大于实际所需，下标为``[ list.size() ]``
的数组元素将被置为 null，其它数组元素保持原值，因此最好将方法入参数组大小定义与集
合元素个数一致。
正例：
```java
List<String> list = new ArrayList<String>(2);
list.add("guan");
list.add("bao");
String[] array = new String[list.size()];
array = list.toArray(array);
```
反例： 直接使用 toArray 无参方法存在问题，此方法返回值只能是 Object[]类，若强转其它类型数组将出现 ClassCastException 错误。
5. 【强制】使用工具类 Arrays.asList()把数组转换成集合时，不能使用其修改集合相关的方
法，它的 add/remove/clear 方法会抛出 UnsupportedOperationException 异常。
说明： asList 的返回对象是一个 Arrays 内部类，并没有实现集合的修改方法。``Arrays.asList``
体现的是适配器模式，只是转换接口，后台的数据仍是数组。
```java
String[] str = new String[] { "you", "wu" };
List list = Arrays.asList(str);
```
第一种情况：`` list.add("yangguanbao")``; 运行时异常。
第二种情况：`` str[0] = "gujin"``; 那么 list.get(0)也会随之修改。
6. 【强制】泛型通配符``<? extends T>``来接收返回的数据，此写法的泛型集合不能使用 add 方
法， 而``<? super T>``不能使用 get 方法，作为接口调用赋值时易出错。
说明： 扩展说一下 ``PECS(Producer Extends Consumer Super)``原则： 第一、 频繁往外读取内容的，适合用``<? extends T>``。 第二、 经常往里插入的，适合用``<? super T>``。
7. 【强制】不要在 foreach 循环里进行元素的 remove/add 操作。 remove 元素请使用 Iterator方式，如果并发操作，需要对 Iterator 对象加锁。
正例：
```java
List<String> list = new ArrayList<>();
list.add("1");
list.add("2");
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
String item = iterator.next();
if (删除元素的条件) {
iterator.remove();
}
}
```
反例：
```java
for (String item : list) {
if ("1".equals(item)) {
list.remove(item);
}
}
```
说明： 以上代码的执行结果肯定会出乎大家的意料，那么试一下把“1”换成“2”，会是同样的
结果吗？
8. 【强制】 在 JDK7 版本及以上， Comparator 实现类要满足如下三个条件，不然 ``Arrays.sort，Collections.sort ``会报 IllegalArgumentException 异常。
说明： 三个条件如下
1） x， y 的比较结果和 y， x 的比较结果相反。
2） ``x>y， y>z``， 则 ``x>z``。
3）`` x=y``， 则 x， z 比较结果和 y， z 比较结果相同。
反例： 下例中没有处理相等的情况，实际使用中可能会出现异常：
```java
new Comparator<Student>() {
@Override
public int compare(Student o1, Student o2) {
return o1.getId() > o2.getId() ? 1 : -1;
}
};
```
9. 【推荐】 集合泛型定义时， 在 JDK7 及以上，使用 diamond 语法或全省略。
说明： 菱形泛型，即 diamond， 直接使用<>来指代前边已经指定的类型。
正例：
```java
// <> diamond 方式
HashMap<String, String> userCache = new HashMap<>(16);
// 全省略方式
ArrayList<User> users = new ArrayList(10);
```
10. 【推荐】集合初始化时， 指定集合初始值大小。
说明： HashMap 使用 ``HashMap(int initialCapacity)`` 初始化。
正例：``initialCapacity = (需要存储的元素个数 / 负载因子) + 1``。注意负载因子 （ 即 loader
factor） 默认为 0.75， 如果暂时无法确定初始值大小，请设置为 16（即默认值） 。
反例： HashMap 需要放置 1024 个元素， 由于没有设置容量初始大小，随着元素不断增加，容
量 7 次被迫扩大， resize 需要重建 hash 表，严重影响性能。
11. 【推荐】使用 entrySet 遍历 Map 类集合 KV，而不是 keySet 方式进行遍历。
说明： keySet 其实是遍历了 2 次，一次是转为 Iterator 对象，另一次是从 hashMap 中取出
key 所对应的 value。而 entrySet 只是遍历了一次就把 key 和 value 都放到了 entry 中，效
率更高。如果是 JDK8，使用`` Map.foreach ``方法。
正例： values()返回的是 V 值集合，是一个 list 集合对象； keySet()返回的是 K 值集合，是
一个 Set 集合对象； entrySet()返回的是 K-V 值组合集合。
12. 【推荐】高度注意 Map 类集合 K/V 能不能存储 null 值的情况，如下表格：
集合类 Key Value Super 说明
Hashtable 不允许为 null 不允许为 null Dictionary 线程安全
ConcurrentHashMap 不允许为 null 不允许为 null AbstractMap 锁分段技术（ JDK8:CAS）
TreeMap 不允许为 null 允许为 null AbstractMap 线程不安全
HashMap 允许为 null 允许为 null AbstractMap 线程不安全
反例： 由于 HashMap 的干扰，很多人认为 ConcurrentHashMap 是可以置入 null 值，而事实上，存储 null 值时会抛出 NPE 异常。
13. 【参考】合理利用好集合的有序性(sort)和稳定性(order)，避免集合的无序性(unsort)和
不稳定性(unorder)带来的负面影响。
说明： 有序性是指遍历的结果是按某种比较规则依次排列的。 稳定性指集合每次遍历的元素次
序是一定的。 如： ArrayList 是 order/unsort； HashMap 是 unorder/unsort； TreeSet 是
order/sort。
14. 【参考】利用 Set 元素唯一的特性，可以快速对一个集合进行去重操作，避免使用 List 的contains 方法进行遍历、对比、 去重操作。
## 控制语句
1. 【强制】在一个 switch 块内，每个 case 要么通过 break/return 等来终止，要么注释说明程序将继续执行到哪一个 case 为止； 在一个 switch 块内，都必须包含一个 default 语句并且放在最后，即使空代码。
2. 【强制】在`` if/else/for/while/do ``语句中必须使用大括号。 即使只有一行代码，避免采用
单行的编码方式：
```java
if (condition) statements;
```
4. 【推荐】 表达异常的分支时， 少用 ``if-else ``方式， 这种方式可以改写成：
```java
if (condition) {
...
return obj;
}
```
// 接着写 else 的业务逻辑代码;
说明： 如果非得使用`` if()...else if()...else...``方式表达逻辑，【强制】 避免后续代码维
护困难， 请勿超过 3 层。
正例： 超过 3 层的 if-else 的逻辑判断代码可以使用卫语句、策略模式、状态模式等来实现，其中卫语句示例如下：
```java
public void today() {
if (isBusy()) {
System.out.println(“change time.”);
return;
}
if (isFree()) {
System.out.println(“go to travel.”);
return;
}
System.out.println(“stay at home to learn Alibaba Java Coding Guidelines.”);
return;
}
```
5. 【推荐】除常用方法（如 ``getXxx/isXxx``）等外，不要在条件判断中执行其它复杂的语句，将复杂逻辑判断的结果赋值给一个有意义的布尔变量名，以提高可读性。
说明： 很多 if 语句内的逻辑相当复杂，阅读者需要分析条件表达式的最终结果，才能明确什么
样的条件执行什么样的语句，那么，如果阅读者分析逻辑表达式错误呢？
```java
//正例：
// 伪代码如下
final boolean existed = (file.open(fileName, "w") != null) && (...) || (...);
if (existed) {
...
}
//反例：
if ((file.open(fileName, "w") != null) && (...) || (...)) {
...
}
```
6. 【推荐】循环体中的语句要考量性能，以下操作尽量移至循环体外处理，如定义对象、变量、获取数据库连接，进行不必要的 try-catch 操作（ 这个 try-catch 是否可以移至循环体外） 。
7. 【推荐】避免采用取反逻辑运算符。
说明： 取反逻辑不利于快速理解，并且取反逻辑写法必然存在对应的正向逻辑写法。
正例： 使用 ``if (x < 628) ``来表达`` x 小于 628``。
反例： 使用 ``if (!(x >= 628))`` 来表达 ``x 小于 628``。
8. 【推荐】接口入参保护，这种场景常见的是用作批量操作的接口。
9. 【参考】 下列情形，需要进行参数校验：
1） 调用频次低的方法。
2） 执行时间开销很大的方法。 此情形中， 参数校验时间几乎可以忽略不计，但如果因为参数错误导致中间执行回退，或者错误，那得不偿失。
3） 需要极高稳定性和可用性的方法。
4） 对外提供的开放接口，不管是 RPC/API/HTTP 接口。
5） 敏感权限入口。
10. 【参考】 下列情形， 不需要进行参数校验：
1） 极有可能被循环调用的方法。但在方法说明里必须注明外部参数检查要求。
2） 底层调用频度比较高的方法。毕竟是像纯净水过滤的最后一道，参数错误不太可能到底
层才会暴露问题。一般 DAO 层与 Service 层都在同一个应用中，部署在同一台服务器中，所以 DAO 的参数校验，可以省略。
3） 被声明成 private 只会被自己代码所调用的方法，如果能够确定调用方法的代码传入参
数已经做过检查或者肯定不会有问题，此时可以不校验参数。
## 注释规约
1. 【强制】类、类属性、类方法的注释必须使用 Javadoc 规范，使用``/**``内容``*/``格式，不得使用``// xxx`` 方式。
说明： 在 IDE 编辑窗口中， Javadoc 方式会提示相关注释，生成 Javadoc 可以正确输出相应注释； 在 IDE 中，工程调用方法时，不进入方法即可悬浮提示方法、参数、返回值的意义，提高阅读效率。
2. 【强制】所有的抽象方法（ 包括接口中的方法） 必须要用 Javadoc 注释、除了返回值、参数、异常说明外，还必须指出该方法做什么事情，实现什么功能。
说明： 对子类的实现要求，或者调用注意事项，请一并说明。
3. 【强制】所有的类都必须添加创建者和创建日期。
4. 【强制】方法内部单行注释，在被注释语句上方另起一行，使用//注释。方法内部多行注释
使用/* */注释，注意与代码对齐。
5. 【强制】所有的枚举类型字段必须要有注释，说明每个数据项的用途。
6. 【推荐】与其“半吊子”英文来注释，不如用中文注释把问题说清楚。专有名词与关键字保持英文原文即可。
反例： “TCP 连接超时”解释成“传输控制协议连接超时”，理解反而费脑筋。
7. 【推荐】代码修改的同时，注释也要进行相应的修改，尤其是参数、返回值、异常、核心逻辑等的修改。
说明： 代码与注释更新不同步，就像路网与导航软件更新不同步一样，如果导航软件严重滞后，就失去了导航的意义。
8. 【参考】 谨慎注释掉代码。 在上方详细说明，而不是简单地注释掉。 如果无用，则删除。
说明： 代码被注释掉有两种可能性： 1） 后续会恢复此段代码逻辑。 2） 永久不用。前者如果没有备注信息，难以知晓注释动机。后者建议直接删掉（ 代码仓库保存了历史代码） 。
9. 【参考】对于注释的要求：第一、能够准确反应设计思想和代码逻辑； 第二、能够描述业务含
义，使别的程序员能够迅速了解到代码背后的信息。完全没有注释的大段代码对于阅读者形同天书，注释是给自己看的，即使隔很长时间，也能清晰理解当时的思路； 注释也是给继任者看的，使其能够快速接替自己的工作。
10. 【参考】好的命名、代码结构是自解释的，注释力求精简准确、表达到位。避免出现注释的一个极端：过多过滥的注释，代码的逻辑一旦修改，修改注释是相当大的负担。
反例：`` put elephant into fridge / put(elephant, fridge)``;
方法名 put，加上两个有意义的变量名 elephant 和 fridge，已经说明了这是在干什么，语
义清晰的代码不需要额外的注释。
11. 【参考】特殊注释标记，请注明标记人与标记时间。注意及时处理这些标记，通过标记扫描，经常清理此类标记。线上故障有时候就是来源于这些标记处的代码。
1） 待办事宜（ TODO） :（标记人，标记时间， [预计处理时间]）
表示需要实现，但目前还未实现的功能。这实际上是一个 Javadoc 的标签，目前的 Javadoc
还没有实现，但已经被广泛使用。只能应用于类，接口和方法（ 因为它是一个 Javadoc 标签） 。
2） 错误，不能工作（ FIXME） :（ 标记人，标记时间， [预计处理时间]）
在注释中用 FIXME 标记某代码是错误的，而且不能工作，需要及时纠正的情况。
## 其它
1. 【强制】在使用正则表达式时，利用好其预编译功能，可以有效加快正则匹配速度。
说明： 不要在方法体内定义：`` Pattern pattern = Pattern.compile(“规则”)``;
2. 【强制】 velocity 调用 POJO 类的属性时，建议直接使用属性名取值即可，模板引擎会自动按规范调用 POJO 的 ``getXxx()``，如果是 boolean 基本数据类型变量（ boolean 命名不需要加 is前缀） ，会自动调用`` isXxx()``方法。
说明： 注意如果是 Boolean 包装类对象，优先调用 getXxx()的方法。
3. 【强制】后台输送给页面的变量必须加$!{var}——中间的感叹号。
说明： 如果 var 等于 null 或者不存在，那么${var}会直接显示在页面上。
4. 【强制】注意 Math.random() 这个方法返回是 double 类型，注意取值的范围 ``0≤x<1``（ 能够取到零值，注意除零异常） ，如果想获取整数类型的随机数，不要将 x 放大 10 的若干倍然后取整，直接使用 Random 对象的 nextInt 或者 nextLong 方法。
5. 【强制】获取当前毫秒数 ``System.currentTimeMillis()``; 而不是 ``new Date().getTime()``;
说明： 如果想获取更加精确的纳秒级时间值， 使用`` System.nanoTime()``的方式。在 JDK8 中，
针对统计时间等场景，推荐使用 Instant 类。
6. 【推荐】 不要在视图模板中加入任何复杂的逻辑。
说明： 根据 MVC 理论，视图的职责是展示，不要抢模型和控制器的活。
7. 【推荐】 任何数据结构的构造或初始化，都应指定大小，避免数据结构无限增长吃光内存。
8. 【推荐】 及时清理不再使用的代码段或配置信息。
说明： 对于垃圾代码或过时配置，坚决清理干净，避免程序过度臃肿，代码冗余。
正例： 对于暂时被注释掉，后续可能恢复使用的代码片断，在注释代码上方，统一规定使用三个斜杠(///)来说明注释掉代码的理由。
# 异常日志
## 异常处理
1. 【强制】 Java 类库中定义的可以通过预检查方式规避的 RuntimeException 异常不应该通过catch 的方式来处理，比如： NullPointerException， IndexOutOfBoundsException 等等。
说明： 无法通过预检查的异常除外，比如，在解析字符串形式的数字时，不得不通过 catch
NumberFormatException 来实现。
正例： ``if (obj != null) {...}``
反例：`` try { obj.method(); } catch (NullPointerException e) {…}``
2. 【强制】异常不要用来做流程控制，条件控制。
说明： 异常设计的初衷是解决程序运行中的各种意外情况，且异常的处理效率比条件判断方式要低很多。
3. 【强制】 catch 时请分清稳定代码和非稳定代码，稳定代码指的是无论如何不会出错的代码。
对于非稳定代码的 catch 尽可能进行区分异常类型，再做对应的异常处理。
说明： 对大段代码进行 try-catch，使程序无法根据不同的异常做出正确的应激反应，也不利于定位问题，这是一种不负责任的表现。
正例： 用户注册的场景中，如果用户输入非法字符， 或用户名称已存在， 或用户输入密码过于简单，在程序上作出分门别类的判断，并提示给用户。
4. 【强制】捕获异常是为了处理它，不要捕获了却什么都不处理而抛弃之，如果不想处理它，请将该异常抛给它的调用者。最外层的业务使用者，必须处理异常，将其转化为用户可以理解的内容。
5. 【强制】有 try 块放到了事务代码中， catch 异常后，如果需要回滚事务，一定要注意手动回滚事务。
6. 【强制】 finally 块必须对资源对象、流对象进行关闭，有异常也要做 try-catch。
说明： 如果 JDK7 及以上，可以使用 try-with-resources 方式。
7. 【强制】不要在 finally 块中使用 return。
说明： finally 块中的 return 返回后方法结束执行，不会再执行 try 块中的 return 语句。
8. 【强制】捕获异常与抛异常，必须是完全匹配，或者捕获异常是抛异常的父类。
说明： 如果预期对方抛的是绣球，实际接到的是铅球，就会产生意外情况。
9. 【推荐】方法的返回值可以为 null，不强制返回空集合，或者空对象等，必须添加注释充分说明什么情况下会返回 null 值。
说明： 本手册明确防止 NPE 是调用者的责任。即使被调用方法返回空集合或者空对象，对调用者来说，也并非高枕无忧，必须考虑到远程调用失败、 序列化失败、 运行时异常等场景返回null 的情况。
10. 【推荐】防止 NPE，是程序员的基本修养，注意 NPE 产生的场景：
1）返回类型为基本数据类型， return 包装数据类型的对象时，自动拆箱有可能产生 NPE。
反例： public int f() { return Integer 对象}， 如果为 null，自动解箱抛 NPE。
2） 数据库的查询结果可能为 null。
3） 集合里的元素即使 isNotEmpty，取出的数据元素也可能为 null。
4） 远程调用返回对象时，一律要求进行空指针判断，防止 NPE。
5） 对于 Session 中获取的数据，建议 NPE 检查，避免空指针。
6） 级联调用 obj.getA().getB().getC()； 一连串调用，易产生 NPE。
正例： 使用 JDK8 的 Optional 类来防止 NPE 问题。
11. 【推荐】定义时区分 unchecked / checked 异常，避免直接抛出 new RuntimeException()，
更不允许抛出 Exception 或者 Throwable，应使用有业务含义的自定义异常。推荐业界已定义过的自定义异常，如： DAOException / ServiceException 等。
12. 【 参考】 对于公司外的 http/api 开放接口必须使用“错误码”； 而应用内部推荐异常抛出；跨应用间 RPC 调用优先考虑使用 Result 方式，封装 isSuccess()方法、 “错误码”、 “错误简短信息”。
说明： 关于 RPC 方法返回方式使用 Result 方式的理由：
1） 使用抛异常返回方式，调用方如果没有捕获到就会产生运行时错误。
2） 如果不加栈信息，只是 new 自定义异常，加入自己的理解的 error message，对于调用
端解决问题的帮助不会太多。如果加了栈信息，在频繁调用出错的情况下，数据序列化和传输的性能损耗也是问题。
13. 【参考】避免出现重复的代码（ Don’t Repeat Yourself） ，即 DRY 原则。
说明： 随意复制和粘贴代码，必然会导致代码的重复，在以后需要修改时，需要修改所有的副本，容易遗漏。必要时抽取共性方法，或者抽象公共类，甚至是组件化。
正例： 一个类中有多个 public 方法，都需要进行数行相同的参数校验操作，这个时候请抽取：
private boolean checkParam(DTO dto) {...}
## 日志规约
1. 【强制】应用中不可直接使用日志系统（ Log4j、 Logback） 中的 API，而应依赖使用日志框架SLF4J 中的 API，使用门面模式的日志框架，有利于维护和各个类的日志处理方式统一。
```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
private static final Logger logger = LoggerFactory.getLogger(MailServiceImpBySpringMail.class);
```
2. 【强制】日志文件至少保存 15 天，因为有些异常具备以“周”为频次发生的特点。
3. 【强制】应用中的扩展日志（ 如打点、临时监控、访问日志等） 命名方式：
appName_logType_logName.log。
logType:日志类型， 如 stats/monitor/access 等； logName:日志描述。这种命名的好处：
通过文件名就可知道日志文件属于什么应用，什么类型，什么目的，也有利于归类查找。
正例： mppserver 应用中单独监控时区转换异常，如：``mppserver_monitor_timeZoneConvert.log``
说明： 推荐对日志进行分类， 如将错误日志和业务日志分开存放，便于开发人员查看，也便于通过日志对系统进行及时监控。
4. 【强制】对 trace/debug/info 级别的日志输出，必须使用条件输出形式或者使用占位符的方式。
说明： ``logger.debug("Processing trade with id: " + id + " and symbol: " + symbol);``
如果日志级别是 warn，上述日志不会打印，但是会执行字符串拼接操作，如果 symbol 是对象，会执行 toString()方法，浪费了系统资源，执行了上述操作，最终日志却没有打印。
正例： （ 条件） 建设采用如下方式
```java
if (logger.isDebugEnabled()) {
logger.debug("Processing trade with id: " + id + " and symbol: " + symbol);
}
```
正例： （ 占位符）
```java
logger.debug("Processing trade with id: {} and symbol : {} ", id, symbol);
```
6. 【强制】对error 级别的日志输出, 使用``void org.slf4j.Logger.error(String format, Object arg)``
正例： ``logger.error(各类参数或者对象 toString() + "_" + e.getMessage(), e)``;避免``e.printStackTrace()``;
7. 【推荐】谨慎地记录日志。生产环境禁止输出 debug 日志； 有选择地输出 info 日志； 如果使用 warn 来记录刚上线时的业务行为信息，一定要注意日志输出量的问题，避免把服务器磁盘撑爆，并记得及时删除这些观察日志。
说明： 大量地输出无效日志，不利于系统性能提升，也不利于快速定位错误点。 记录日志时请思考：这些日志真的有人看吗？看到这条日志你能做什么？能不能给问题排查带来好处？
8. 【推荐】可以使用 warn 日志级别来记录用户输入参数错误的情况，避免用户投诉时，无所适从。如非必要，请不要在此场景打出 error 级别，避免频繁报警。
说明： 注意日志输出的级别， error 级别只记录系统逻辑出错、异常或者重要的错误信息。
9. 【推荐】尽量用英文来描述日志错误信息，如果日志中的错误信息用英文描述不清楚的话使用中文描述即可，否则容易产生歧义。 国际化团队或海外部署的服务器由于字符集问题，【强制】使用全英文来注释和描述日志错误信息。
# MySQL 数据库
## 建表规约
1. 【强制】表达是与否概念的字段，必须使用 is_xxx 的方式命名，数据类型是 unsigned tinyint（ 1 表示是， 0 表示否）。
说明： 任何字段如果为非负数，必须是 unsigned。
注意： POJO 类中的任何布尔类型的变量，都不要加 is 前缀，所以，需要在<resultMap>设置从 is_xxx 到 Xxx 的映射关系。数据库表示是与否的值，使用 tinyint 类型，坚持 is_xxx 的命名方式是为了明确其取值含义与取值范围。
正例： 表达逻辑删除的字段名 is_deleted， 1 表示删除， 0 表示未删除。
2. 【强制】表名、字段名必须使用小写字母或数字， 禁止出现数字开头，禁止两个下划线中间只出现数字。数据库字段名的修改代价很大，因为无法进行预发布，所以字段名称需要慎重考虑。
说明： MySQL 在 Windows 下不区分大小写，但在 Linux 下默认是区分大小写。因此，数据库名、表名、字段名，都不允许出现任何大写字母，避免节外生枝。
正例： system_code， system_role_permission， level3_name
反例： SystemCode， systemRolePermission， level_3_name
3. 【强制】表名不使用复数名词。
说明： 表名应该仅仅表示表里面的实体内容，不应该表示实体数量，对应于 DO 类名也是单数形式，符合表达习惯。
4. 【强制】禁用保留字，如 desc、 range、 match、 delayed 等， 请参考 MySQL 官方保留字。
5. 【强制】 主键索引名为 pk_字段名； 唯一索引名为 uk_字段名； 普通索引名则为 idx_字段名。
说明： pk_ 即 primary key； uk_ 即 unique key； idx_ 即 index 的简称。
6. 【强制】小数类型为 decimal，禁止使用 float 和 double。
说明： float 和 double 在存储的时候，存在精度损失的问题，很可能在值的比较时，得到不正确的结果。如果存储的数据范围超过 decimal 的范围，建议将数据拆成整数和小数分开存储。
7. 【强制】如果存储的字符串长度几乎相等，使用 char 定长字符串类型。
8. 【强制】 varchar 是可变长字符串，不预先分配存储空间，长度不要超过 5000，如果存储长度大于此值，定义字段类型为 text，独立出来一张表，用主键来对应，避免影响其它字段索引效率。
9. 【强制】表必备七字段： id, version, created_dtm，created_by last_modified_dtm，last_modified_by deleted，。
说明： 其中 id 必为主键，类型为 bigint unsigned、单表时自增、步长为 1。 created_dtm和last_modified_dtm 的类型均为 datetime 类型，前者现在时表示主动创建，后者过去分词表示被动更新。created_by和last_modified_by的类型均为bigint unsigned，前者表示创建人，后者表示更新人。Version表示记录被更新的次数
10. 【推荐】表的命名最好是加上“业务名称_表的作用”。
正例： ehs_corrective_action / sds_product 
11. 【推荐】库名与应用名称尽量一致。
12. 【推荐】如果修改字段含义或对字段表示的状态追加时，需要及时更新字段注释。
13. 【推荐】字段允许适当冗余，以提高查询性能，但必须考虑数据一致。冗余字段应遵循：
1） 不是频繁修改的字段。
2） 不是 varchar 超长字段，更不能是 text 字段。
正例： 商品类目名称使用频率高，字段长度短，名称基本一成不变，可在相关联的表中冗余存储类目名称，避免关联查询。
14. 【推荐】单表行数超过 500 万行或者单表容量超过 2GB，才推荐进行分库分表。
说明： 如果预计三年后的数据量根本达不到这个级别，请不要在创建表时就分库分表。
15. 【参考】合适的字符存储长度，不但节约数据库表空间、节约索引存储，更重要的是提升检索速度。
正例： 如下表，其中无符号值可以避免误存负数， 且扩大了表示范围。
对象 年龄区间 类型 字节 表示范围
人 150 岁之内 tinyint unsigned 1 无符号值： 0 到 255
龟 数百岁 smallint unsigned 2 无符号值： 0 到 65535
恐龙化石 数千万年 int unsigned 4 无符号值： 0 到约 42.9 亿
太阳 约 50 亿年 bigint unsigned 8 无符号值： 0 到约 10 的 19 次方
## 索引规约
1. 【强制】业务上具有唯一特性的字段，即使是多个字段的组合，也必须建成唯一索引。
说明： 不要以为唯一索引影响了 insert 速度，这个速度损耗可以忽略，但提高查找速度是明显的； 另外，即使在应用层做了非常完善的校验控制，只要没有唯一索引，根据墨菲定律，必然有脏数据产生。
2. 【强制】超过三个表禁止 join。需要 join 的字段，数据类型必须绝对一致； 多表关联查询时，保证被关联的字段需要有索引。
说明： 即使双表 join 也要注意表索引、 SQL 性能。
3. 【强制】在 varchar 字段上建立索引时，必须指定索引长度，没必要对全字段建立索引，根据实际文本区分度决定索引长度即可。
说明： 索引的长度与区分度是一对矛盾体，一般对字符串类型数据，长度为 20 的索引，区分度会高达 90%以上，可以使用 count(distinct left(列名, 索引长度))/count(*)的区分度来确定。
4. 【强制】页面搜索严禁左模糊或者全模糊，如果需要请走搜索引擎来解决。
说明： 索引文件具有 B-Tree 的最左前缀匹配特性，如果左边的值未确定，那么无法使用此索引。
5. 【推荐】如果有 order by 的场景，请注意利用索引的有序性。 order by 最后的字段是组合索引的一部分，并且放在索引组合顺序的最后，避免出现 file_sort 的情况，影响查询性能。
正例： where a=? and b=? order by c; 索引： a_b_c
反例： 索引中有范围查找，那么索引有序性无法利用，如： WHERE a>10 ORDER BY b; 索引a_b 无法排序。
6. 【推荐】利用覆盖索引来进行查询操作， 避免回表。
说明： 如果一本书需要知道第 11 章是什么标题，会翻开第 11 章对应的那一页吗？目录浏览一下就好，这个目录就是起到覆盖索引的作用。
正例： 能够建立索引的种类分为主键索引、唯一索引、普通索引三种，而覆盖索引只是一种查询的一种效果，用 explain 的结果， extra 列会出现： using index。
7. 【推荐】利用延迟关联或者子查询优化超多分页场景。
说明： MySQL 并不是跳过 offset 行，而是取 offset+N 行，然后返回放弃前 offset 行，返回N 行，那当 offset 特别大的时候，效率就非常的低下，要么控制返回的总页数，要么对超过特定阈值的页数进行 SQL 改写。
正例： 先快速定位需要获取的 id 段，然后再关联：
SELECT a.* FROM 表 1 a, (select id from 表 1 where 条件 LIMIT 100000,20 ) b where a.id=b.id
8. 【推荐】 SQL 性能优化的目标：至少要达到 range 级别， 要求是 ref 级别， 如果可以是 consts最好。
说明：
1） consts 单表中最多只有一个匹配行（ 主键或者唯一索引） ，在优化阶段即可读取到数据。
2） ref 指的是使用普通的索引（ normal index） 。
3） range 对索引进行范围检索。
反例： explain 表的结果， type=index，索引物理文件全扫描，速度非常慢，这个 index 级
别比较 range 还低，与全表扫描是小巫见大巫。
9. 【推荐】建组合索引的时候，区分度最高的在最左边。
正例： 如果 where a=? and b=? ， 如果 a 列的几乎接近于唯一值，那么只需要单建 idx_a
索引即可。
说明： 存在非等号和等号混合时，在建索引时，请把等号条件的列前置。如： where c>? and
d=? 那么即使 c 的区分度更高，也必须把 d 放在索引的最前列， 即索引 idx_d_c。
10. 【推荐】 防止因字段类型不同造成的隐式转换， 导致索引失效。
11. 【参考】创建索引时避免有如下极端误解：
1） 宁滥勿缺。 认为一个查询就需要建一个索引。
2） 宁缺勿滥。 认为索引会消耗空间、严重拖慢更新和新增速度。
3） 抵制惟一索引。 认为业务的惟一性一律需要在应用层通过“先查后插”方式解决。
## SQL 语句
1. 【强制】不要使用 count(列名)或 count(常量)来替代 count(*)， count(*)是 SQL92 定义的标准统计行数的语法，跟数据库无关，跟 NULL 和非 NULL 无关。
说明： count(*)会统计值为 NULL 的行，而 count(列名)不会统计此列为 NULL 值的行。
2. 【强制】 count(distinct col) 计算该列除 NULL 之外的不重复行数， 注意 count(distinct
col1, col2) 如果其中一列全为 NULL，那么即使另一列有不同的值，也返回为 0。
3. 【强制】当某一列的值全是 NULL 时， count(col)的返回结果为 0，但 sum(col)的返回结果为NULL，因此使用 sum()时需注意 NPE 问题。
正例： 可以使用如下方式来避免 sum 的 NPE 问题：`` SELECT IF(ISNULL(SUM(g)),0,SUM(g))
FROM table;``
4. 【强制】使用 ISNULL()来判断是否为 NULL 值。
说明： NULL 与任何值的直接比较都为 NULL。
1） ``NULL<>NULL``的返回结果是 NULL， 而不是 false。
2） ``NULL=NULL`` 的返回结果是 NULL， 而不是 true。
3） ``NULL<>1`` 的返回结果是 NULL，而不是 true。
5. 【强制】 在代码中写分页查询逻辑时，若 count 为 0 应直接返回，避免执行后面的分页语句。
6. 【强制】不得使用外键与级联，一切外键概念必须在应用层解决。
说明：以学生和成绩的关系为例，学生表中的 student_id 是主键，那么成绩表中的 student_id
则为外键。如果更新学生表中的 student_id，同时触发成绩表中的 student_id 更新， 即为
级联更新。外键与级联更新适用于单机低并发，不适合分布式、高并发集群； 级联更新是强阻塞，存在数据库更新风暴的风险； 外键影响数据库的插入速度。
7. 【强制】禁止使用存储过程，存储过程难以调试和扩展，更没有移植性。
8. 【强制】数据订正（特别是删除、 修改记录操作） 时，要先 select，避免出现误删除，确认无误才能执行更新语句。
9. 【推荐】 in 操作能避免则避免，若实在避免不了，需要仔细评估 in 后边的集合元素数量，控制在 1000 个之内。
10. 【参考】 如果有国际化需要，所有的字符存储与表示，均以 utf-8 编码，注意字符统计函数的区别。
``SELECT LENGTH("轻松工作")``； 返回为 12
``SELECT CHARACTER_LENGTH("轻松工作")``； 返回为 4
如果需要存储表情，那么选择 utf8mb4 来进行存储，注意它与 utf-8 编码的区别。
11. 【参考】 TRUNCATE TABLE 比 DELETE 速度快，且使用的系统和事务日志资源少，但 TRUNCATE无事务且不触发 trigger，有可能造成事故，故不建议在开发代码中使用此语句。
说明： TRUNCATE TABLE 在功能上与不带 WHERE 子句的 DELETE 语句相同。
## ORM 映射
1. 【强制】在表查询中，一律不要使用 * 作为查询的字段列表，需要哪些字段必须明确写明。
说明： 1） 增加查询分析器解析成本。 2） 增减字段容易与 resultMap 配置不一致。 3）无用字段增加网络消耗，尤其是 text 类型的字段。
2. 【强制】 POJO 类的布尔属性不能加 is，而数据库字段必须加 is_，要求在 resultMap 中进行字段与属性之间的映射。
说明： 参见定义 POJO 类以及数据库字段定义规定，在<resultMap>中增加映射，是必须的。
在 MyBatis Generator 生成的代码中，需要进行对应的修改。
3. 【强制】不要用 resultClass 当返回参数，即使所有类属性名与数据库字段一一对应，也需要定义； 反过来，每一个表也必然有一个 POJO 类与之对应。
说明： 配置映射关系，使字段与 DO 类解耦，方便维护。
4. 【强制】sql.xml 配置参数使用： #{}， #param# 不要使用${} 此种方式容易出现 SQL 注入。
5. 【强制】 iBATIS 自带的 ``queryForList(String statementName,int start,int size)``不推
荐使用。如需分页可用系统自定义分页功能，``query(QueryUtil queryUtil)``
说明：其实现方式是在数据库取到 statementName对应的SQL语句的所有记录，再通过 subList取 start,size 的子集合。
正例： 
```java
Map<String, Object> map = new HashMap<>();
map.put("start", start);
map.put("size", size);
```
6. 【强制】不允许直接拿 HashMap 与 Hashtable 作为查询结果集的输出。
说明： ``resultClass=”Hashtable”``， 会置入字段名和属性值，但是值的类型不可控。
7. 【强制】更新数据表记录时，必须同时更新记录对应的 gmt_modified 字段值为当前时间。
8. 【推荐】不要写一个大而全的数据更新接口。 传入为 POJO 类，不管是不是自己的目标更新字段，都进行 ``update table set c1=value1,c2=value2,c3=value3``; 这是不对的。执行 SQL
时， 不要更新无改动的字段，一是易出错； 二是效率低； 三是增加 binlog 存储。
9. 【参考】 @Transactional 事务不要滥用。事务会影响数据库的 QPS，另外使用事务的地方需要考虑各方面的回滚方案，包括缓存回滚、搜索引擎回滚、消息补偿、统计修正等。
10. 【参考】 <isEqual>中的 compareValue 是与属性值对比的常量，一般是数字，表示相等时带上此条件； <isNotEmpty>表示不为空且不为 null 时执行； <isNotNull>表示不为 null 值时执行。跳转到友好错误页面， 加上用户容易理解的错误提示信息。开放接口层要将异常处理成错误码和错误信息方式返回。
