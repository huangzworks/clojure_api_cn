replace-first
----------------

**(replace-first s match replacement)**

和 `replace` 函数的作用类似，但只替换 ``match`` 的第一个实例。

::

    ; 只有第一个匹配的原音 e 被转为大写字母了

    user=> (clojure.string/replace-first "The color is red" #"[aeiou]" clojure.string/upper-case)
    "ThE color is red"

