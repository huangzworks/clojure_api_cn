javadoc
============

**(javadoc class-or-object)**
 
使用阅览器打开 ``class-or-object`` 参数的相关 javadoc 文档。

优先打开本地文档（ ``*local-javadocs*`` ），
其次才是远程文档（ ``*remote-javadoc*`` ）。

`查看源码 <https://github.com/clojure/clojure/blob/be9ff491c4b2c23790fb316804551768960e355d/src/clj/clojure/java/javadoc.clj#L73>`_

::

	user=> (use 'clojure.java.javadoc)
	nil

	user=> (javadoc String)
	"http://java.sun.com/javase/6/docs/api/java/lang/String.html"

	user=> (javadoc (java.util.Date.))
	"http://java.sun.com/javase/6/docs/api/java/util/Date.html"
