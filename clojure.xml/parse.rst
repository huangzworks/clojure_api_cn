parse
===============

**(parse s)**

**(parse s startparse)**

解析并加载源 ``s`` ， ``s`` 可以是一个文件， ``InputStream`` ,或者一个代表 URL 的字符串。

函数返回一棵 ``xml/element`` 类型的 ``struct-map`` 树，
``struct-map`` 中包含键 ``:tag`` 、 ``:attrs`` 、 ``:content`` ，
以及访问函数 ``tag`` 、 ``attrs`` 、 ``content`` 。

``startparse`` 用于指定解释所使用的解释器，
这个参数的值应该是一个函数：
函数接受一个源（source）和一个内容处理器（ContentHandler）作为参数，
并返回一个解释器作为函数的返回值。

`查看源码 <https://github.com/clojure/clojure/blob/b9b1a094499b69a94bd47fc94c4f082d80239fa9/src/clj/clojure/xml.clj#L78>`_


::

	(require '[clojure.xml :as xml]
         '[clojure.zip :as zip])

	;;convenience function, first sawn at nakkaya.com later in clj.zip src
	(defn zip-str [s]
	  (zip/xml-zip (xml/parse (java.io.ByteArrayInputStream. (.getBytes s)))))

	;;parse from xml-strings to internal xml representation
	(zip-str "<a href='nakkaya.com'/>")
	=>
	[{:tag :a, :attrs {:href "nakkaya.com"}, :content nil} nil]

	;;root can be rendered with xml/emit-element
	(xml/emit-element (zip/root [{:tag :a, :attrs {:href "nakkaya.com"}, :content nil} nil]))
	=>
	<a href='nakkaya.com'/>
	;;printed (to assure it's not lazy and performance), can be catched to string variable with with-out-str
