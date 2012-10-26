concat
---------

| **(concat)**
| **(concat x)**
| **(concat x y)**
| **(concat x y & zs)**

返回一个惰性序列，序列里包含所有传入 collection 的全部元素。

::

    ; 另个、一个或多个 collection 组合

    user=> (concat)
    ()

    user=> (concat [1])
    (1)

    user=> (concat [1] [2])
    (1 2)

    user=> (concat [1] [2] [3])
    (1 2 3)

    user=> (concat [1] [2] [3] [4 5 6])
    (1 2 3 4 5 6)


    ; 传入 concat 的参数必须都是 collection 
    ; 组合元素和 collection 是 cons 和 conj 的任务

    ; user=> (concat 1 [2 3])
    ; IllegalArgumentException Don't know how to create ISeq from: java.lang.Long  clojure.lang.RT.seqFrom (RT.java:487)



