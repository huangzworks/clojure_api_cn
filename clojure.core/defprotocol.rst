defprotocol
--------------

**(defprotocol name & opts+sigs)**

协议是一组命名方法和签名

::

    (defprotocol IOFactory
      (make-reader [this] "Create a Buffered Reader")
      (make-writer [this] "Create a Buffered Writer")
    )
