with-open
---------------

**(with-open bindings & body)**

body在try表达式中尝试将名称与值进行绑定
在finally子句中尝试反序调用close方法释放资源

::

    (ns io
      (:require [clojure.java.io :as io]))

    (defn readLineByLine [file-name] 
      (with-open [reader (io/reader file-name)]
        (doseq [line (line-seq reader)]
          (println line)))) 


