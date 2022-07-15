# 2022/07/12 Java日期类总结

## 1.0 第一代日期类

### 1.1 Date类：精确到毫秒，代表特定的瞬间

### 1.2 SimpleDateFormat类： 格式化和解析日期的类

* 它允许日期进行格式化【日期 --> 文本】

* 解析【文本 -->  日期】和规范化

* SimpleDateFormat类需要掌握的方法【format：格式形式 parse：转换解析【就是将字符串日期格式转换成Date类】】

* 一般情况下Date和SimpleDateFormat类一起搭配使用

* <img src="/Users/wjay/Documents/JavaSE/simpleDateFormat格式类型.png"  />

  ```java
  /*
   * -------第一代日期类-----------------
   * 1.获取当前系统时间
   * 2.这里的Date类是java.util包下的
   * 3.默认输出的日期格式是国外的方式，因此通常需要对格式j进行转换
   * */
  System.out.println("---第一代日期类---");
  Date date = new Date();
  System.out.println("当前系统日期=" + date);
  
  // 通过指定毫秒数得到时间
  Date date1 = new Date(1688688888);//
  System.out.println("通过指定毫秒数获取某个时间" + date1); //获取某个时间对应的毫秒数
  
  /*
   * SimpleDateFormat类 需要掌握format方法 【是对日期进行格式化的】
   *                           parse方法 【是对字符串进行转换成Date类】
   * */
  
  SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");
  String format = simpleDateFormat.format(date);// 对date日期进行格式化
  System.out.println("通过format方法转化日期=" + format);
  
  Date date2 = new Date();
  
  //SimpleDateFormat类中的parse方法 【对字符串日期格式进行转化】
  /*
   * 1。可以将一个格式化的string 转换成对象的Date类
   * 2。 得到Date类仍然在输出时，还是按照国外的形式，如果希望指定格式输出，需要转换
   * 3。在把string --> Date类，使用的sdf对象格式，需要和string格式一致，否则会抛出转转换异常【parseException】
   *
   * */
  String date3 = "1999-11-27 17:12:16";
  Date parse = simpleDateFormat.parse(date3);
  //long time = parse.getTime();
  System.out.println("通过字符串日期进行转换=" + parse);
  
  
  /**
   * 返回值
   * 当前系统日期=Sun Feb 13 13:09:49 CST 2022
   * 通过指定毫秒获取某个时间=Tue Jan 20 21:04:48 CST 1970
   * 通过format方法转化日期=2022-02-13 01:09:49
   * 通过字符串日期进行转化=Wed Dec 16 17:12:16 CST 1998
   */
  ```

## 2.0 第二代日期类

### 2.1 Calendar 类【日历】

`public abstract Calendar extends Object implements Serializable,Cloneable ,Comparable<Calendar>{}`

Calendar类是一个抽象类，它为特定瞬间与一组诸如year month day_month hour 等日历字段之间的转换提供了一些方法，并为操作日历字段【例如获得下星期】提供了一些方法

![](/Users/wjay/Documents/JavaSE/calendar类继承关系图.png)

calendar 类会使用相关的字段即可

下面如果我们需要按照24小时进行来获取时间，Calendar.HOUR [这是十二进制]

Calendar.HOUR_OF_DAY【这是二十四进制】

```java
/*----------第二代日期类Calendar类-----------------
 * 注意由于Calendar 是抽象的不能直接 new 实例化，并且构造器是protected修饰的
 * 因此可以通过 getInstance (反射) 来获取 Calendar 实例
 *
 * */
/*new Calendar();*/
System.out.println("---第二代日期类---");
Calendar calendar = Calendar.getInstance();
System.out.println("calendar = " + calendar);
/*注意不能直接使用Caledar.YEAR等 这样是获取不到当前年的值 只能获取Calendar里面的常量1*/

// 学会获取相关的字段即可  获取日历对象的某个日历字段
// 年
int YEAR = calendar.get(Calendar.YEAR);
System.out.println("YEAR = " + YEAR);
// 月 获取月 因为Calendar 返回月时候 是按照 0 开始编号的 所以需要手动+1
int MONTH = calendar.get(Calendar.MARCH) + 1;
System.out.println("MONTH = " + MONTH);
// 日 获取日
int DAY = calendar.get(Calendar.DAY_OF_MONTH);
System.out.println("DAY = " + DAY);
// 获取小时
int HOUR = calendar.get(Calendar.HOUR_OF_DAY);
System.out.println("HOUR = " + HOUR);
// 分钟
int MINUTE = calendar.get(Calendar.MINUTE);
System.out.println("MINUTE = " + MINUTE);
// 秒
calendar.get(Calendar.SECOND);

// Calendar 没有专门的格式化方法，所以需要程序呀u呢来自己来集合显示
System.out.println(calendar.get(Calendar.YEAR) + "-" + MONTH + "-" + calendar.get(Calendar.DAY_OF_MONTH) + "\t" + calendar.get(Calendar.HOUR_OF_DAY) + ":" + calendar.get(Calendar.MINUTE) + ":" + calendar.get(Calendar.SECOND));
```

## 3.0 第三代日期类

首先对于前面两代日期类的不足进行分析

* `JDK 1.0`中包含了一个`java.util.Date`类，但是它的大多数方法已经在`JDK1.1`引入 `Calendar`类之后被弃用了。而`Calendar`存在问题是：
  1.  可变性：像日期和时间这样的类应该是不可变的
  2. 偏移性：Date中的年份都是从1900年开始的，而月份都是从0开始的
  3. 格式化：格式化支队Date有用，Calenda则不行
  4. 此外，它们也不是线程安全的，不能处理闰秒问题【每隔两天多出1s】

* 第三代日期类：有三个LocalDate 【年月日】 LocalTime【时分秒】LocalDateTime 【年月日时分秒】是在jdk1.8的时候引入的

* 注意的是：第三代日期累的 LocalDate 【年月日】 LocalTime【时分秒】LocalDateTime 【年月日时分秒】 这三个类的构造器都是私有的，不能通过new进行实例化，要通过类名.now 获取对象实例

  

* LocalDate只包含日期，可以获取日期字段

* LocalTime只包含时间，可以获取时间字段

* LocalDateTime包含日期+时间 ，可以获取日期和时间字段

* ###### Instant`时间戳 构造器是私有化，只能通过`Instant.now()`方法获取`Instant`对象

  类似于`Date`提供了一系列和`Date`转换的方

* 第三代日期类更多的方法（举例子）

*  1. MonthDay：检查重复事件

*  2.是否是闰年

* 3. 增加日期的某一个部分 （年月日时分秒周）
  4. 使用plus方法测试增加时间的某个部分
  5. 使用minus方法测试查看一年前和一年后的日期

<font color="red" size="5px">总结：第三代主要还是DateTimeFormatter和localDateTime搭配起来使用</font>

```java
/*--------第三代日期类（java.Time包下面）-----------*/
System.out.println("---第三代日期类---");
LocalDate localDate = LocalDate.now();// 获取日期类对象
LocalTime localTime = LocalTime.now();// 获取时间类对象
LocalDateTime localDateTime = LocalDateTime.now();// 获取日期类对象 -- 年月日时分秒

// 年
int year = localDateTime.getYear();
System.out.println("year = " + year);
// 月 获取月份有两种方式
// 方式一：
Month month = localDateTime.getMonth();// 获取的返回是英文
System.out.println("month = " + month);
// 方式二：
int monthValue = localDateTime.getMonthValue();
System.out.println("monthValue = " + monthValue);
// 日
int dayOfMonth = localDateTime.getDayOfMonth();
System.out.println("dayOfMonth = " + dayOfMonth);
// 时
int hour = localDateTime.getHour();
System.out.println("hour = " + hour);
// 分
int minute = localTime.getMinute();
System.out.println("minute = " + minute);
// 秒
int second = localDateTime.getSecond();
System.out.println("second = " + second);

/*DateTimeFormat格式日期类
 * 类似于SImpleDateFormat类
 * DateTimeFormat dtf = DateTimeFormatter.ofPattern(格式);
 * 注意不能直接new实例化，因为构造器是默修饰的，
 * 要使用静态方法ofPattern方法进行指定格式，
 * String str = dtf.format(日期对象);
 * */
System.out.println("---（第三代日期格式转换类）DateTimeFormat的使用例子---");
LocalDateTime now = LocalDateTime.now();
DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
// 调用DateTimeFormatter类中的format方法进行日期格式
String format1 = dateTimeFormatter.format(now);
System.out.println("format1 = " + format1);

/*Instant时间戳
 * 构造器是私有化，只能通过Instant.now()方法来获取Instant对象
 * 类似于Date提供了一系列和Date转换的方式
 *
 * */
//获取时间戳对象
Instant instant = Instant.now();
System.out.println("instant时间戳 = " + instant);
Date date4 = new Date();
// Instant 转成 Date
Date from = Date.from(instant);
System.out.println("from = " + from);
// Date 转成 Instant
Instant toInstant = date4.toInstant();
System.out.println("toInstant = " + toInstant);

System.out.println("---第三代日期类更多的方法---");
/*
 * LocalDateTime类
 * MonthDay：检查重复事件
 * 是否是闰年
 * 增加日期的某个部分
 * 使用plus方法测试增加时间的某个部分
 * 使用minus方法测试查看一年前和一年后的日期
 * 甚至是提供了（年月日时分秒周）的加减运算
 * */
// 这里先用第三代提供的日期类格式转换类
DateTimeFormatter ofPattern = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
LocalDateTime dateTime = localDateTime.now();
// 增加 168 天后的日期
LocalDateTime time1 = dateTime.plusDays(168);
System.out.println("加上168天后的日期=" + ofPattern.format(time1));

// 减去 168 分钟的时间
LocalDateTime dateTime1 = dateTime.minusMinutes(168);
System.out.println("减去 168 分钟的时间" + ofPattern.format(dateTime1));
```




 