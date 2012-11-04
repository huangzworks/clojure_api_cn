replace
--------------

**(replace s match replacement)**

将字符串 ``s`` 中的所有 ``match`` 实例（instance）替换成 ``replacement`` 。

``match`` / ``replacement`` 可以是以下组合：

1. 字符串 / 字符串

2. 字符 / 字符

3. 模式（pattern） / 字符串或一个函数，其中函数的参数为模式所匹配的实例

::

    ; 组合 1 ：用字符串替换字符串
    ; 将字符串里的子串 moto 替换成 google

    user=> (clojure.string/replace "hello moto" "moto" "google")
    "hello google"

    ; 组合 2 ：用字符替换字符
    ; 将字符串的所有小写 o 替换成大写 O

    user=> (clojure.string/replace "hello moto" "o" "O")
    "hellO mOtO"

    ; 组合 3 ：用字符串替换匹配模式的实例
    ; 将匹配 #"red" 模式的实例替换为 "blue"

    user=> (clojure.string/replace "The color is red" #"red" "blue")
    "The color is blue"

    ; 另一个组合 3 ：用函数的结果来替换匹配模式的实例
    ; 将字符串里的所有原音字母转换为大写

    user=> (clojure.string/replace "The color is red" #"[aeiou]" clojure.string/upper-case)
    "ThE cOlOr Is rEd"
