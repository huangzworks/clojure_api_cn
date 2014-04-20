Are
=====
macro

| **(are argv expr & args)**

通过以模板表达的方式检查多个断言(``assertions``)
关于模板的解释请查阅 ``clojure.template/do-template``

::
    #Example:
    (are [x y] (= x y)
              2 (+ 1 1)
              4 (* 2 2))
    #Expands to:
    (do (is (= 2 (+ 1 1)))
        (is (= 4 (* 2 2))))
