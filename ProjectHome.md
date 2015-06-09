本代码是从uchome的代码修改的，是因为要解决uchome的效率而处理的。<br>
这个思维其实很久就有了，只是一直没有去做，相信也有人有同样的想法，如果有类似的，那真的希望提出相关的建议。<br>
封装的方式比较简单，增加了只读数据库连接的接口扩展，不使用只读数据库也不影响原代码使用。<br>
有待以后不断完善。。<br>
<br>
<h1>为什么需要读写分离？</h1>

主要是数据库压力过大的情况下的解决方案。写操作会把表锁定，而导致很多查询相继锁定而等候，导致程序处于等候状态。<br>
读写分离是建立在mysql的replication基础上的，master服务器仅负责写操作，slave机器仅提供读操作，相对而言提高了读写性能，也可以增加mysql的承受能力。<br>

<h1>PHP实现的Mysql读写分离</h1>

<h2>主要特性：</h2>

<ol><li>简单的读写分离<br>
</li><li>一个主数据库，可以添加更多的只读数据库<br>
</li><li>读写分离但不用担心某些特性不支持<br>
</li><li>缺点：同时连接两个数据库<br>
</li><li>可能的bug：请反馈</li></ol>

<h1>How to use it?</h1>

<a href='http://code.google.com/p/mysql-rw-php/wiki/HowToUse'>http://code.google.com/p/mysql-rw-php/wiki/HowToUse</a>

<h1>php code for mysql read/write split</h1>

<h2>feature:</h2>

<ol><li>simply rw split<br>
</li><li>one master,can add more slaves<br>
</li><li>support all mysql feature<br>
</li><li>link to the master and slave at the same time