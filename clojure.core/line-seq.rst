line-seq
------------

**(line-seq rdr)**

返回一个惰性序列，
序列里包含从文件 ``rdr`` 中读出的所有字符串行。

``rdr`` 必须是一个 ``java.io.BufferedReader`` 对象。

::

    ; 引入 reader 函数，它可以创建一个 java.io.BufferedReader 对象
    ; 读出 animal.txt 文件中的所有内容，之后再将文件联接关闭

    user=> (use '[clojure.java.io :only [reader]])
    nil

    user=> (def animal (reader "animal.txt"))
    #'user/animal

    user=> (line-seq animal)
    ("dog" "cat" "monkey" "lion" "tiger" "dolphin")

    user=> (.close animal)
    nil


    ; 用 with-open 来自动处理文件的打开和关闭
    ; 并用更美观的方式打印 animal.txt 文件的内容
    
    user=> (with-open [animal (reader "animal.txt")]
             (let [all-animal (line-seq animal)]
                (doseq [a all-animal]
                    (println a))))
    dog
    cat
    monkey
    lion
    tiger
    dolphin
    nil
