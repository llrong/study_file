###函数式接口：
&nbsp;&nbsp;&nbsp;当接口中只有一个抽象方法是，就是函数式接口，可以使用注解@FunctionalInterface对接口进行强制性限制为函数式接口。（lambda表达式只针对函数式接口使用）。
函数式接口可以包含多个默认方法，类方法，但只能声明一个抽象方法。
</br>
####函数编程
将一个参数（也称为行为）作为一个参数进行传递

####接口中静态方法
从Java8开始接口中可以使用静态方式，用static修饰，修饰符只能是public（默认public）</br>
<b>接口中静态方法不是抽象方法</b></br>
在使用时可以直接用接口名调用静态方法，静态方法有方法体
</br>
</br>

####默认方法
java8在接口中还支持默认方法，但只能用default修饰，方法默认也只能是public，默认方法在调用时必须实例化才可以调用，默认方法有方法体。
<pre>
```
//非静态default方法
interface TestDefaultMethod{
     default void test() {
           System.out.println("这个是接口里的default方法test");
     }
     public default void test1() {
           System.out.println("这个是接口里的default方法test1");
     }
}
```
</pre>
<b>默认方法不是抽象方法,可以在子接口里重写父接口的默认方法，使其成为抽象方法</b></br>

默认方法可以被继承，当继承的两个接口中的默认方法是一样的话，必须重写
<pre>
interfacein  A {
     default void test() {
           System.out.println("接口A的默认方法");
     }
}
interface B {
     default void test() {
           System.out.println("接口B的默认方法");
     }
}
interface C extends A,B {
}
 </pre>

这里接口c处会报错，因为编译器并不知道你到底继承的是A的默认方法还说B的默认方法。可以修改如下进行重写，用super明确调用哪个接口的方法：
<pre>
interface C extends A,B {
     @Override
     default void test() {
           A.super.test();
     }
 }
</pre>
在接口里可以使用默认方法来实现父接口的抽象方法。如：
<pre>
@FunctionalInterface
interface A {
     default void test() {
           System.out.println("接口A的默认方法");
     }
     void test1();

</pre>
<pre>
interface C extends A,B {
     @Override
     default void test() {
           A.super.test();
     }
     default void test1() {
           System.out.println("在子接口实现父接口的抽象方法");
     }
 }
</pre>

可以在子接口里重写父接口的默认方法，使其成为抽象方法，如：
<pre>
interface E {
     default void test() {
           System.out.println("接口E的默认方法");
     }
}
interface F extends E {
    void test();
}
//主函数
public static void main(String[] args) {
   F f = new F(){
         @Override
         public void test() {
                     System.out.println("F接口实现");
                }
           };
          f.test();
     }
     </pre>


