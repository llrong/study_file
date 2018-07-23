##Restful API
####1.什么是REST
REST：Repressentational State Tranfer 表现层状态转化，是所有web应用都应该遵守的架构设计原则，是一种架构风格。</br>

对于表现层状态转化的具体解释：</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;表现层"其实指的是"资源"（Resources）的"表现层"。"资源"是一种信息实体，它可以有多种外在表现形式。我们把"资源"具体呈现出来的形式，叫做它的"表现层"（Representation）。</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;对于状态转换，访问一个网站，就代表了客户端和服务器的一个互动过程。在这个过程中，势必涉及到数据和状态的变化。互联网通信协议HTTP协议，是一个无状态协议。这意味着，所有的状态都保存在服务器端。因此，如果客户端想要操作服务器，必须通过某种手段，让服务器端发生"状态转化"（State Transfer）。而这种转化是建立在表现层之上的，所以就是"表现层状态转化"。</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;客户端用到的手段，只能是HTTP协议。具体来说，就是HTTP协议里面，四个表示操作方式的动词：GET、POST、PUT、DELETE。它们分别对应四种基本操作：GET用来获取资源，POST用来新建或更新资源，PUT用来更新资源，DELETE用来删除资源</br>


REST架构风格最主要的架构约束：</br>
1.客户-服务器(client-server)</br>
通信只能由客户端单方面发起，表现为请求-相应形式
</br>
2.无状态（stateless）</br>
通信的会话状态应该全部由客户端进行维护</br>
3.缓存（cache）</br>
相应内容可以在通信链的某处被缓存，以改善网络效率</br>
4.统一接口</br>
通信链的组件之间通过统一的接口相互通信，以提高交互的可见性</br>
5.分层系统（layered system）</br>
通过限制组件的行为，将架构分为若干等级的层</br>
6.按需代码（code-on-demand，可选）</br>
支持通过下载逼格执行一些代码，对客户端的功能进行扩展

REST要求，必须通过统一的接口来对资源执行各种操作。对于每个资源只能执行一组有限的操作。以HTTP/1.1协议为例，HTTP/1.1协议定义了一个操作资源的统一接口，主要包括以下内容：</br>
7个HTTP方法：GET/POST/PUT/DELETE/PATCH/HEAD/OPTIONS</br>
HTTP头信息（可自定义）</br>
HTTP响应状态代码（可自定义）</br>
一套标准的内容协商机制</br>
一套标准的缓存机制</br>
一套标准的客户端身份认证机制</br>



REST风格的架构所具有的6个的主要特征：</br>
&nbsp;&nbsp;面向资源（Resource Oriented）</br>
&nbsp;&nbsp;可寻址（Addressability）</br>
&nbsp;&nbsp;连通性（Connectedness）</br>
&nbsp;&nbsp;无状态（Statelessness）</br>
&nbsp;&nbsp;统一接口（Uniform Interface）</br>
&nbsp;&nbsp;超文本驱动（Hypertext Driven）</br>

这6个特征是REST架构设计优秀程度的判断标准。其中，面向资源是REST最明显的特征，即，REST架构设计是以资源抽象为核心展开的。可寻址说的是：每一个资源在Web之上都有自己的地址。连通性说的是：应该尽量避免设计孤立的资源，除了设计资源本身，还需要设计资源之间的关联关系，并且通过超链接将资源关联起来。无状态、统一接口是REST的两种架构约束，超文本驱动是REST的一个关键词.



####2.什么是RESTful API
如果一个架构符合REST原则，就称它为RESTful架构








