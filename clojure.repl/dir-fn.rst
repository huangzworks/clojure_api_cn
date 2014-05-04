dir-fn
=============

| **(dir-fn ns)**

返回一个有序序列，该序列包括给定命名空间(ns)的公共Var对象。

::

    user=> (require 'clojure.repl 'clojure.string)
    
    user=> (pprint (clojure.repl/dir-fn 'clojure.string))
    (blank?
     capitalize
     escape
     join
     lower-case
     replace
     replace-first
     reverse
     split
     split-lines
     trim
     trim-newline
     triml
     trimr
     upper-case)
    nil
