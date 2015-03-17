clojure.pprint
================

| **(A Pretty Printer for Clojure)**

clojure.pprint 实现了一个灵活的工具，用于把clojure的数据结构输出成优雅易懂的格式。pretty printer最基本的使用方式，就是把代码中的 println 替换成 pprint。高级用户可以通过 the building blocks 来定制自己的输出格式。

pprint 对基础的数据提供了简单的格式，对 clojure source code 提供了专有的格式。其他更高级的格式，包括完全不像 clojure 惯用的数据格式的 XML ，JSON ，都可以通过自定义补丁来输出出来。

这个模块不仅包括 pprint， 也包括给 Common lisp 提供支持的 cl-format。因为 pprint 和 cl－format 需要共同作用，所以 pprint 支持非常简洁的自定义补丁。除此之外， pprint 也提供了 format function 作为 clojure 现有的标准 format function的一个替代。

欢迎查看 pprint 和 cl-format 的文档来获取更多的信息。

Added in Clojure version 1.2

.. toctree::
   :maxdepth: 2

   cl-format
   pp
