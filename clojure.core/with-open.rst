with-open
---------------

**(with-open bindings & body)**

在绑定了名字 ``name`` 与初始值 ``init`` 的 ``try`` 表达式里面对 ``body`` 进行求值
并按照绑定时间从晚到早的顺序
在 ``finally`` 语句里面对每个 ``name`` 执行 ``(.close name)`` 调用


::

    (ns io
      (:require [clojure.java.io :as io]))

    (defn readLineByLine [file-name] 
      (with-open [reader (io/reader file-name)]
        (doseq [line (line-seq reader)]
          (println line)))) 
    
    (defn copyLineByLine [source target]
      (with-open [reader (io/reader source)
                  writer (io/writer target)]
        (io/copy reader writer)))
