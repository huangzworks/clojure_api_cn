find-doc
=============

| **(find-doc re-string-or-pattern)**

如果某个Var对象的名字或者文档能与给定字符串或者正则表达式相匹配，那么打印该Var对象的文档信息。

::

    user=> (find-doc "data structure")
    
    -------------------------
    clojure.core/eval
    ([form])
      Evaluates the form data structure (not text!) and returns the result.
    -------------------------
    clojure.core/ifn?
    ([x])
      Returns true if x implements IFn. Note that many data structures
      (e.g. sets and maps) implement IFn
        user=> (require 'clojure.string 'clojure.repl)
    -------------------------
    ........



