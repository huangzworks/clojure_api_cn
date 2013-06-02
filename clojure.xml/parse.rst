parse
===============

**(parse s)**

**(parse s startparse)**



解析并加载源s，s可以是一个文件，输入流(InputStream),或者一个代表URL的字符串。返回 ``xml/element`` 的 ``struct-map`` 的树，``struct-map`` 有以下几个键: ``:tag`` , ``:attrs`` , ``:content`` 以及 ``tag`` , ``attrs`` , ``content`` 的访问函数。

另外parsers可以通过传递 ``startparse`` 函数来自定义解析函数，parse函数可以接收一个源和一个内容处理器（ContentHandler）作为参数并且返回一个解析器(parser)



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







