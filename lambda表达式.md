Lambda表达式支持将代码块作为参数，Lambda表达式允许使用更简洁的代码来创建只有一个抽象方法的接口（这种接口被称为函数式接口）的实例,lambda表达式只能为函数式接口创建对象，lambda表达式只能实现一个方法，因此他它只能为只有一个抽象方法的借口（函数式接口）创建对象。
lambda表达式可以认为是一种特殊的匿名内部类.<br>
lambda语法：<br>
     （[形参列表，不带数据类型]）-> {
     //执行语句
     [return..;]
}<br>
注意：<br>
1、如果形参列表是空的，只需要保留（）即可<br>
2、如果没有返回值。只需要在{}写执行语句即可<br>
3、如果接口的抽象方法只有一个形参，（）可以省略，只需要参数的名称即可<br>
4、如果执行语句只有一行，可以省略{}，但是如果有返回值时，情况特殊。<br>
5、如果函数式接口的方法有返回值，必须给定返回值，如果执行语句只有一句，还可以简写，即省去大括号和return以及最后的；号。<br>
6、形参列表的数据类型会自动推断，只需要参数名称。<br>

例：
<pre>
public class TestLambda {
     public static void main(String[] args) {
           TestLanmdaInterface1 t1 = new TestLanmdaInterface1() {
                @Override
                public void test() {
                     System.out.println("使用匿名内部类");
                    }
};
 //与上面的匿名内部类执行效果一样
           //右边的类型会自动根据左边的类型进行判断
           TestLanmdaInterface1 t2 = () -> {
                System.out.println("使用lanbda");
           };
           t1.test();
           t2.test();
           //如果执行语句只有一行，可以省略大括号
           TestLanmdaInterface1 t3 = () -> System.out.println("省略执行语句大括号，使用lanbda");
           t3.test();
 		    TestLanmdaInterface2 t4 = (s) -> System.out.println("使用lanbda表达式，带1个参数，参数为："+s);
           t4.test("字符串参数1");
 			 TestLanmdaInterface2 t5 = s -> System.out.println("使用lanbda表达式，只带1个参数，可省略参数的圆括号，参数为："+s);
           t5.test("字符串参数2");
 			 TestLanmdaInterface3 t6 = (s,i) -> System.out.println("使用lanbda表达式，带两个参数，不可以省略圆括号，参数为："+s+"  "+ i);
           t6.test("字符串参数3",50);
     }
}
@FunctionalInterface
interface TestLanmdaInterface1 {
     //不带参数的抽象方法
     void test();
}
@FunctionalInterface
interface TestLanmdaInterface2 {
     //带参数的抽象方法
     void test(String str);
}
@FunctionalInterface
interface TestLanmdaInterface3 {
     //带多个参数的抽象方法
     void test(String str,int num);
}
</pre>
        