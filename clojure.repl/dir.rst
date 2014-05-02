dir
=============

| **(dir nsname)**

分类打印出给定命名空间下的公共Var对象

::

    user=> (require 'clojure.string 'clojure.repl)
    
    user=> (clojure.repl/dir clojure.string)
    blank?
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
    upper-case
