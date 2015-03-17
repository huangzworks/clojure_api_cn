add-remote-javadoc
=======================

**(add-remote-javadoc package-prefix url)**

添加路径 ``url`` 到远程 javadoc 路径的列表， ``package-prefix`` 是 URL 对应的 javadoc 的包名的开始部分。

`查看源码 <https://github.com/clojure/clojure/blob/be9ff491c4b2c23790fb316804551768960e355d/src/clj/clojure/java/javadoc.clj#L45>`_


::

	user=> (use 'clojure.java.javadoc)
	nil

	user=> (add-remote-javadoc "org.apache.commons.csv." "http://commons.apache.org/proper/commons-csv/apidocs/index.html")
	{"java." "http://java.sun.com/javase/6/docs/api/", "javax." "http://java.sun.com/javase/6/docs/api/", "org.apache.commons.codec." "http://commons.apache.org/codec/api-release/", "org.apache.commons.csv." "http://commons.apache.org/proper/commons-csv/apidocs/index.html", "org.apache.commons.io." "http://commons.apache.org/io/api-release/", "org.apache.commons.lang." "http://commons.apache.org/lang/api-release/", "org.ietf.jgss." "http://java.sun.com/javase/6/docs/api/", "org.omg." "http://java.sun.com/javase/6/docs/api/", "org.w3c.dom." "http://java.sun.com/javase/6/docs/api/", "org.xml.sax." "http://java.sun.com/javase/6/docs/api/"}






