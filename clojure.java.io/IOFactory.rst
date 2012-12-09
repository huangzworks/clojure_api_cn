IOFactory
===========

``clojure.java.io`` 内部定义的protocol，包含 ``make-reader`` ， ``make-writer`` ， ``make-input-stream`` 和 ``make-out-stream`` 四个方法。这四个方法创建的都是带缓冲区的reader，writer或stream。

用户应该避免直接使用上述四个API，而是使用 ``reader`` ， ``writer`` ， ``input-stream`` 和 ``output-stream`` 。
