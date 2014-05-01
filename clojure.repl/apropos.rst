apropos
=============

| **(apropos str-or-pattern)**

返回当前命名空间下所有与给定正则表达式或者字符串(str-or-pattern)相匹配的定义的序列

::


    user=> (apropos "temp")
    ()
    
    user=> (require 'clojure.template)
    nil
    
    user=> (apropos "temp")
    (apply-template do-template)

    ;; 使用正则表达式
    user=> (apropos #".*-temp*")
    (apply-template do-template)
