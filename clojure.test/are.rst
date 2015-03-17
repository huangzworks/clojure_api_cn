are
=====
macro

| **(are argv expr & args)**

通过以模板表达的方式检查多个断言(``assertions``)。关于模板的解释请查阅 ``clojure.template/do-template``

::

    ;例子:
    (are [x y] (= x y)
              2 (+ 1 1)
              4 (* 2 2))

    ;宏将展开为:
    (do (is (= 2 (+ 1 1)))
        (is (= 4 (* 2 2))))
