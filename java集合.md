#集合和数组
数组：（可以存储基本数据类型）数组长度固定，不适合在对象位置的情况下使用</br>

集合：（只能存储对象，但是对象的类型可以不一样）长度可变


##集合
<b>Collection</b>接口是集合类的根接口，Java中没有这个接口的直接实现类，但是有两个被继承接口List和Set。
###Set
<b>Set是无序的，Set中不能包含重复的元素</b></br>
set的底层是Map，通过计算key的哈希值来确定元素位置，由于Map中的key不能重复，所以set中的元素不能重复。

###List
<b>List是一个有序的集合</b>，可以包含重复的元素，提供了按索引访问的方式，拥有一系列和索引相关的方法，查询速度较快。由于向list集合中插入和删除数据时会伴随着后面数据的移动，插入和删除速度较慢。

<b>List实现类</b><br>
1.LinkedList<br>
是一个双向链表，在添加和删除元素师具有比ArrayList更好的性能，在get和set方面较弱，是不同步的（线程不安全）。</br>
2.ArrayList<br>
内部是可改变大小的数组结构，可以动态的增加容量，ArrayList内部元素可以通过set和get进行随机访问，是不同步的(线程不安全).</br>
ArrayList允许任何符合规则的元素插入甚至包括null。每一个ArrayList都有一个初始容量（10），该容量代表了数组的大小。随着容器中的元素不断增加，容器的大小也会随着增加，扩容方式为原数组长度*3 除2再加1。在每次向容器中增加元素的同时都会进行容量检查，当快溢出时，就会进行扩容操作。所以如果我们明确所插入元素的多少，最好指定一个初始容量值，避免过多的进行扩容操作而浪费时间、效率。<br>
<br>
<b>ArrayList和LinkedList的比较</b></br>
(1).ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。<br>
(2).对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。<br>
(3).对于新增和删除操作add和remove，LinedList比较占优势，因为ArrayList要移动数据。<br>
    这一点要看实际情况的。若只对单条数据插入或删除，ArrayList的速度反而优于LinkedList。但若是批量随机的插入删除数 据，LinkedList的速度大大优于ArrayList. 因为ArrayList每插入一条数据，要移动插入点及之后的所有数据。


3.Vector<br>
和ArrayList类似Vector是基于数组动态实现的（扩容方式为原数组长度乘2），但Vector属于强同步类（线程安全），Enumeration是Vector取出元素的特有方式，但已被迭代器取代,Vector被ArrayList取代，但在集合中使用数据量比较大的数据，Vector较ArrayList有一定优势。

<pre>
Enumeration en = v.elements();
while(en.hasMoreElements())
{
System.out.println(en.nextElement());
} </pre>
4.Stack</br>
基于数组实现的栈，继承Vector，在Stack刚创建后是空栈。




###Map
Map包含了key-value对，<b>Map中不能包含重复的key，但可以有相同的value</b>。根据键得到值<br>
对map进行遍历是先得到键的set集合，对set集合进行遍历，得到相应的值。</br>
Map和Collection接口没有关系相互独立。<br>
<b>Map实现类</b><br>
1.<b>HashMap</b><br>
HashMap是最常用的Map，它根据键的HashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度，遍历时，取得数据的顺序是完全随机的。因为键对象不可以重复，所以HashMap最多只允许一条记录的键为Null，允许多条记录的值为Null，是非同步的<br>
2.<b>Hashtable</b><br>
Hashtable与HashMap类似，是HashMap的线程安全版，它支持线程的同步，即任一时刻只有一个线程能写Hashtable，因此也导致了Hashtale在写入时会比较慢，它继承自Dictionary类，不同的是它不允许记录的键或者值为null，同时效率较低。<br>
3.<b>ConcurrentHashMap</b><br>
线程安全，在jdk1.6中ConcurrentHashMap使用锁分段技术提高并发访问效率。首先将数据分成一段一段地存储，然后给每一段数据配一个锁，当一个线程占用锁访问其中一段数据时，其他段的数据也能被其他线程访问。然而在jdk1.8中的实现已经抛弃了Segment分段锁机制，利用CAS(Compare And Swap，即比较并交换)+Synchronized来保证并发更新的安全，底层依然采用数组+链表+红黑树的存储结构。
<br>
4.<b>LinkedHashMap</b><br>
LinkedHashMap保存了记录的插入顺序，在用Iteraor遍历LinkedHashMap时，先得到的记录肯定是先插入的，在遍历的时候会比HashMap慢，有HashMap的全部特性。<br>
5.<b>TreeMap</b><br>
TreeMap是基于红黑树（二叉树）数据结构实现的，实现SortMap接口，能够把它保存的记录根据键排序，默认是按键值的升序排序（自然顺序），也可以指定排序的比较器，当用Iterator遍历TreeMap时，得到的记录是排过序的(key有序）。不允许key值为空，非同步的<br>

<b>HashMap和TreeMap</b><br>
1、 HashMap通过hashcode对其内容进行快速查找，而TreeMap中所有的元素都保持着某种固定的顺序，如果你需要得到一个有序的结果你就应该使用TreeMap（HashMap中元素的排列顺序是不固定的）。<br>
2、在Map 中插入、删除和定位元素，HashMap是最好的选择。但如果您要按自然顺序或自定义顺序遍历键，那么TreeMap会更好。使用HashMap要求添加的键类明确定义了hashCode()和 equals()的实现。
两个map中的元素一样，但顺序不一样，导致hashCode()不一样。

<b>HashMap和HashTable</b><br>
1、同步性:Hashtable是线程安全的，也就是说是同步的，而HashMap是线程序不安全的，不是同步的。<br>
2、HashMap允许存在一个为null的key，多个为null的value 。<br>
3、hashtable的key和value都不允许为null。

<b>map遍历</b><br>
第一种：KeySet()</br>
将Map中所有的键存入到set集合中。因为set具备迭代器。所有可以迭代方式取出所有的键，再根据get方法。获取每一个键对应的值。 keySet():迭代后只能通过get()取key 。
取到的结果会乱序，是因为取得数据行主键的时候，使用了HashMap.keySet()方法，而这个方法返回的Set结果，里面的数据是乱序排放的。</br>
典型用法如下：</br>
<pre>
Map map = new HashMap();
map.put("key1","lisi1");
map.put("key2","lisi2");
map.put("key3","lisi3");
map.put("key4","lisi4");  
//先获取map集合的所有键的set集合，keyset（）
Iterator it = map.keySet().iterator();
 //获取迭代器
while(it.hasNext()){
Object key = it.next();
System.out.println(map.get(key));
}
</pre></br>
第二种：entrySet（）</br>
```Set<Map.Entry<K,V>> entrySet()``` //返回此映射中包含的映射关系的 Set 视图。（一个关系就是一个键-值对），就是把(key-value)作为一个整体一对一对地存放到Set集合当中的。Map.Entry表示映射关系。entrySet()：迭代后可以e.getKey()，e.getValue()两种方法来取key和value。返回的是Entry接口。</br>
典型用法如下：</br>
<pre>
Map map = new HashMap();
map.put("key1","lisi1");
map.put("key2","lisi2");
map.put("key3","lisi3");
map.put("key4","lisi4");
//将map集合中的映射关系取出，存入到set集合
Iterator it = map.entrySet().iterator();
while(it.hasNext()){
Entry e =(Entry) it.next();
System.out.println("键"+e.getKey () + "的值为" + e.getValue());
}
</pre>
推荐使用第二种方式，即entrySet()方法，效率较高。
对于keySet其实是遍历了2次，一次是转为iterator，一次就是从HashMap中取出key所对于的value。而entryset只是遍历了第一次，它把key和value都放到了entry中，所以快了。两种遍历的遍历时间相差还是很明显的。





###Iterator
Iterator是一个用于遍历集合中元素的接口，对于所有的Collection类，都实现了Iterator接口，主要包含以下三个方法：</br>
1.hasNext(）是否还有下一个元素<br>
2.next()返回下一个元素<br>
3.remove()删除当前元素

###遍历
在类集中提供了以下四种的常见输出方式：</br>
1）Iterator：迭代输出，是使用最多的输出方式。</br>
2）ListIterator：是Iterator的子接口，专门用于输出List中的内容。</br>
3）foreach输出：JDK1.5之后提供的新功能，可以输出数组或集合。</br>
4）for循环</br>
代码示例如下：</br>
for的形式：for（int i=0;i<arr.size();i++）{...}


foreach的形式： for（int　i：arr）{...}

iterator的形式：
Iterator it = arr.iterator();
while(it.hasNext()){ object o =it.next(); ...}

