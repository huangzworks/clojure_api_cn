javadoc
============

**(javadoc class-or-object)**
 

打开一个浏览器窗口显示参数的javadoc，优先打开本地的javadoc(*local-javadocs*) ，其次是远程的javadoc(*remote-javadocs*)。

`查看源码 <https://github.com/clojure/clojure/blob/be9ff491c4b2c23790fb316804551768960e355d/src/clj/clojure/java/javadoc.clj#L73>`_



::

	user=> (use 'clojure.java.javadoc)
	nil

	user=> (javadoc String)
	"http://java.sun.com/javase/6/docs/api/java/lang/String.html"

	user=> (javadoc (java.util.Date.))
	"http://java.sun.com/javase/6/docs/api/java/util/Date.html"


