clojure.core
=================

seq
------

**(seq coll)**

根据给定的 ``coll`` ，返回一个相应的序列。

当 ``coll`` 为空时，返回 ``nil`` 。

``(sql nil)`` 也返回 ``nil`` 。

``seq`` 函数也可以作用于字符串、
（带有引用类型的）原生 Java 数组，
以及任何实现了 ``iterable`` 接口的对象。

::

    ; 处理空向量和 nil

    user=> (seq [])
    nil

    user=> (seq nil)
    nil

    ; 处理非空向量、列表、 map 和字符串

    user=> (seq [1 2 3])
    (1 2 3)

    user=> (seq (list 1 2 3))
    (1 2 3)

    user=> (seq {:language "clojure" :creator "Rich Hickey"})
    ([:creator "Rich Hickey"] [:language "clojure"])

    user=> (seq "hello world")
    (\h \e \l \l \o \space \w \o \r \l \d)


rseq
---------

**(rseq rev)**

在常数时间内，返回 ``rev`` 的逆序序列。

``rev`` 只能是向量或者 sorted-map 。

``rev`` 为空时，返回 ``nil`` 。

::

    ; 空向量和空 sorted-map

    user=> (rseq [])
    nil

    user=> (rseq (sorted-map))
    nil


    ; 非空向量

    user=> (rseq [1 2 3])
    (3 2 1)


    ; 非空 sorted-map

    user=> (def alpha (sorted-map :a "apple" :b "boy" :c "cat"))
    #'user/alpha

    user=> alpha
    {:a "apple", :b "boy", :c "cat"}

    user=> (rseq alpha)
    ([:c "cat"] [:b "boy"] [:a "apple"])


    ; 一些不能处理的情况

    user=> (rseq (list 1 2 3))
    ClassCastException clojure.lang.PersistentList cannot be cast to clojure.lang.Reversible  clojure.core/rseq (core.clj:1480)

    user=> (rseq nil)
    NullPointerException   clojure.core/rseq (core.clj:1480)


subseq
---------

| **(subseq sc test key)**
| **(subseq sc start-test start-key end-test end-key)**

过滤 ``sc`` 并返回一个序列，序列里的所有实体(entry)的键 ``ek`` 都必须符合条件 ``(true? (test (.. sc comparator (compare ek key)) 0))`` 。

如果没有任何实体符合条件，则返回 ``nil`` 。

参数 ``sc`` 必须是一个 sorted collection ，测试条件 ``test`` 可以是 ``<`` 、 ``<=`` 、 ``>`` 或者 ``>=`` 。

::

    ; 测试数据

    user=> (def numbers (sorted-map 1 "one" 2 "two" 3 "three" 4 "four" 5 "five"))
    #'user/numbers

    user=> numbers
    {1 "one", 2 "two", 3 "three", 4 "four", 5 "five"}


    ; 过滤所有键小于 3 的键-值对

    user=> (subseq numbers >= 3)
    ([3 "three"] [4 "four"] [5 "five"])


    ; 过滤所有键小于 1 大于 4 的键-值对

    user=> (subseq numbers >= 2 <= 4)
    ([2 "two"] [3 "three"] [4 "four"])

    
    ; 过滤所有键小于 10 的键-值对，返回 nil

    user=> (subseq numbers >= 10)
    nil


rsubseq
-------------

| **(rsubseq sc test key)**
| **(rsubseq sc start-test start-key end-test end-key)**

用法和 `subseq`_ 一样，但是返回的序列是逆序排序的。

等同于执行 ``(rseq (subseq sc test key))`` 或者 ``(rseq (subseq sc start-test start-key end-test end-key))`` 。

::

    ; 测试数据

    user=> (def numbers (sorted-map 1 "one" 2 "two" 3 "three" 4 "four" 5 "five"))
    #'user/numbers

    user=> numbers
    {1 "one", 2 "two", 3 "three", 4 "four", 5 "five"}


    ; 过滤所有键小于 1 大于 4 的键-值对，并逆序地返回结果

    user=> (rsubseq numbers >= 2 <= 4)
    ([4 "four"] [3 "three"] [2 "two"])


    ; 过滤所有键小于 2 的键-值对，并逆序地返回结果

    user=> (rsubseq numbers > 2)
    ([5 "five"] [4 "four"] [3 "three"])


vals
---------

**(vals map)**

返回一个序列，序列里包含给定 ``map`` 的所有值(value)。

::

    ; 空 map

    user=> (vals {})
    nil

    ; 非空 map

    user=> (vals {:python "Guido" :clojure "Rich" :ruby "Matz"})
    ("Guido" "Matz" "Rich")


keys
---------

**(keys map)**

返回一个序列，序列里包含给定 ``map`` 的所有键(key)。

::

    ; 空 map

    user=> (keys {})
    nil

    ; 非空 map

    user=> (keys {:python "Guido" :clojure "Rich" :ruby "Matz"})
    (:python :ruby :clojure)


repeatedly
-----------------

| **(repeatedly f)**
| **(repeatedly n f)**

给定一个无参数的函数 ``f`` (通常带有副作用)，返回一个调用 ``f`` 函数 ``n`` 次的惰性序列。

如果不指定参数 ``n`` ，那么函数 ``f`` 可以执行无限次。

::

    ; 测试函数

    user=> (defn greet []                     
             "hi!")       
    #'user/greet


    ; 定义一个执行 10 次 greet 的惰性序列
    ; 并用 take 函数取出 5 个和 10 个 greet 的执行结果

    user=> (def ten-greet (repeatedly 10 greet))
    #'user/ten-greet

    user=> (take 5 ten-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!")

    user=> (take 10 ten-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!")


    ; 试图取出 10086 个值，但 ten-greet 最多只返回 10 个值
    ; 说明取出的数量最多只能和 n 一样大

    user=> (take 10086 ten-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!")


    ; 定义一个执行无限次 greet 的惰性序列

    user=> (def infinite-greet (repeatedly greet))
    #'user/infinite-greet

    user=> (take 10 infinite-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!")

    user=> (take 100 infinite-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!")


iterate
--------

| **(iterate f x)**

返回一个惰性序列，
序列元素的值为 ``x`` 、 ``(f x)`` 、 ``(f (f x))`` 、 ``(f (f (f x)))`` ，
诸如此类。

函数 ``f`` 必须是无副作用的。

::

    ; 生成一个计算所有正整数的惰性序列

    user=> (def z (iterate inc 1))
    #'user/z


    ; 取出第一个和第二个正整数

    user=> (nth z 0)
    1

    user=> (nth z 1)
    2


    ; 取出前十个正整数

    user=> (take 10 z)
    (1 2 3 4 5 6 7 8 9 10)


repeat
----------

| **(repeat x)**
| **(repeat n x)**

返回一个包含 ``n`` 个 ``x`` 的惰性序列。

如果不指定 ``n`` ，那么值 ``x`` 可以被包含无限次。

::

    ; 定义一个包含 10 个 "hi" 的惰性序列

    user=> (def ten-hi (repeat 10 "hi"))
    #'user/ten-hi

    user=> ten-hi
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")


    ; 定义一个包含无限个 "hi" 的惰性序列

    user=> (def infinite-hi (repeat "hi"))
    #'user/infinite-hi

    user=> (take 10 infinite-hi)
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")

    user=> (take 20 infinite-hi)
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")


range
---------

| **(range)**
| **(range end)**
| **(range start end)**
| **(range start end step)**

返回一个惰性序列，
序列里包含从大于等于 ``start`` 到小于 ``end`` 
区间内的所有数字(``start <= numbers < end``)，
数字的步进以 ``step`` 指定。

默认情况下， ``start`` 为 ``0`` ， ``step`` 为 ``1`` ，而 ``end`` 则为无限。

::

    ; 不指定任何参数，返回一个包含所有非负整数的惰性序列
    ; 0, 1, 2, 3 ...

    user=> (take 3 (range))
    (0 1 2)

    user=> (take 10 (range))
    (0 1 2 3 4 5 6 7 8 9)


    ; 只指定 end 
    ; 返回大于等于 0 到小于 end 之内的所有整数

    user=> (range 5)
    (0 1 2 3 4)

    user=> (range 10)
    (0 1 2 3 4 5 6 7 8 9)


    ; 指定 start 和 end

    user=> (range 5 10)
    (5 6 7 8 9)

    user=> (range 0 10)   
    (0 1 2 3 4 5 6 7 8 9)


    ; 指定 start 、 end 和 step
    ; 第一个惰性序列计算 2 到 20 内的所有偶数
    ; 第二个惰性序列计算 1 到 20 内的所有奇数

    user=> (range 2 20 2)
    (2 4 6 8 10 12 14 16 18)

    user=> (range 1 20 2)
    (1 3 5 7 9 11 13 15 17 19)


keep
---------

**(keep f coll)**

对于 ``coll`` 中的每个项 ``item`` ，
``(keep f coll)`` 返回一个惰性序列，
序列包含 ``(f item)`` 除 ``nil`` 之外的所有计算结果。

因为带副作用的函数会返回与计算结果无关的虚假值，
因此，为了确保虚假值不会混进 ``keep`` 所生成的惰性序列中，
``f`` 必须是一个无副作用的函数。

::
    
    user=> (keep inc [1 2 3])
    (2 3 4)

    ; 将空的 collection 传给 seq 函数会返回 nil
    ; 可以根据这个性质来测试 keep 
    ; 看它是否真的会省略等于 nil 的值

    user=> (seq [])
    nil

    user=> (keep seq (list [1 2 3] [] [4 5 6]))
    ((1 2 3) (4 5 6))


distinct
----------

**(distinct coll)**

给定一个 ``coll`` ，返回一个无重复元素的惰性序列。

::

    ; 有重复元素的向量

    user=> (distinct [1 2 1 2])
    (1 2)

    
    ; 无重复元素的向量

    user=> (distinct [1 2 3 4])
    (1 2 3 4)


filter
--------

**(filter pred coll)**

返回一个惰性序列，
序列中包含 ``coll`` 里所有 ``(pred item)`` 测试结果为 ``true`` 的项。

``pred`` 必须是一个无副作用的函数。

::

    ; 过滤 0 - 9 中所有的奇数

    user=> (filter even? (range 10))
    (0 2 4 6 8)


    ; 过滤 0 - 9 中所有的偶数

    user=> (filter odd? (range 10))
    (1 3 5 7 9)


    ; 过滤 0 - 9 中所有小于 10086 的数，结果为空

    user=> (filter #(> % 10086) (range 10))
    ()


remove
----------

**(remove pred coll)**

返回一个惰性序列，
序列中包含 ``coll`` 里所有 ``(pred item)`` 测试结果为 ``false`` 的项。

``pred`` 必须是一个无副作用的函数。

::

    ; 删除 0 - 9 中的所有偶数

    user=> (remove even? (range 10))
    (1 3 5 7 9)


    ; 删除 0 - 9 中的所有奇数

    user=> (remove odd? (range 10))
    (0 2 4 6 8)


    ; 删除 0 - 9 中所有大于等于 0 的数字，结果为空

    user=> (remove #(>= % 0) (range 10)) 
    ()


re-seq
-----------

**(re-seq re s)**

返回一个惰性序列，
序列里包含字符串 ``s`` 中所有匹配模式 ``re`` 的值，
匹配使用 ``java.util.regex.Matcher.find()`` 进行，
每个匹配值都经过 ``re-groups`` 处理。

::

    ; 查找字符串中的所有数字值

    user=> (re-seq #"[0-9]+" "abs123def345ghi567")
    ("123" "345" "567")


file-seq
-----------

**(file-seq dir)**

返回一个惰性序列，
序列包含给定目录 ``dir`` 的整个目录树
（包括目录中的文件和目录中的文件夹及文件夹里的文件）。

``dir`` 必须是一个 ``java.io.File`` 对象。

::

    ; 引入 file 函数，它可以根据路径名创建一个 File 对象
    ; 我们打开 /tmp 文件夹，并打印它的目录树

    user=> (use '[clojure.java.io :only [file]])
    nil

    user=> (def tmp-folder (file "/tmp"))
    #'user/tmp-folder

    user=> (file-seq tmp-folder)
    (#<File /tmp> #<File /tmp/.esd-1000> #<File /tmp/.esd-1000/socket> #<File /tmp/.Test-unix> #<File /tmp/mongodb-27017.sock> #<File /tmp/at-spi2> #<File /tmp/at-spi2/socket-1179-1131176229> #<File /tmp/at-spi2/socket-1268-1804289383> #<File /tmp/at-spi2/socket-1169-1369485920> #<File /tmp/mongodb-28017.sock> #<File /tmp/.X0-lock> #<File /tmp/.org.chromium.Chromium.NUsJHg> #<File /tmp/.org.chromium.Chromium.NUsJHg/SingletonSocket> #<File /tmp/.org.chromium.Chromium.NUsJHg/SingletonCookie> #<File /tmp/keyring-NwNaja> #<File /tmp/keyring-NwNaja/ssh> #<File /tmp/keyring-NwNaja/gpg> #<File /tmp/keyring-NwNaja/pkcs11> #<File /tmp/keyring-NwNaja/control> #<File /tmp/.ICE-unix> #<File /tmp/.ICE-unix/1303> #<File /tmp/cron.qpBNVU> #<File /tmp/pulse-PKdhtXMmr18n> #<File /tmp/ssh-ElvUhBgb1303> #<File /tmp/ssh-ElvUhBgb1303/agent.1303> #<File /tmp/.font-unix> #<File /tmp/pulse-397VI5uG1yhc> #<File /tmp/pulse-397VI5uG1yhc/pid> #<File /tmp/pulse-397VI5uG1yhc/native> #<File /tmp/pulse-397VI5uG1yhc/dbus-socket> #<File /tmp/hsperfdata_huangz> #<File /tmp/hsperfdata_huangz/9350> #<File /tmp/.X11-unix> #<File /tmp/.X11-unix/X0> #<File /tmp/.XIM-unix> #<File /tmp/.esd-120> #<File /tmp/pulse-T9RwKSB1FebW>)


    ; 使用 doseq 、 sort 和 println 函数
    ; 打印一个更美观的、经过排序的目录树

    user=> (doseq [f (sort (file-seq tmp))]
             (println f))
    #<File /tmp>
    #<File /tmp/.ICE-unix>
    #<File /tmp/.ICE-unix/1303>
    #<File /tmp/.Test-unix>
    #<File /tmp/.X0-lock>
    #<File /tmp/.X11-unix>
    #<File /tmp/.X11-unix/X0>
    #<File /tmp/.XIM-unix>
    #<File /tmp/.esd-1000>
    #<File /tmp/.esd-1000/socket>
    #<File /tmp/.esd-120>
    #<File /tmp/.font-unix>
    #<File /tmp/.org.chromium.Chromium.NUsJHg>
    #<File /tmp/.org.chromium.Chromium.NUsJHg/SingletonCookie>
    #<File /tmp/.org.chromium.Chromium.NUsJHg/SingletonSocket>
    #<File /tmp/at-spi2>
    #<File /tmp/at-spi2/socket-1169-1369485920>
    #<File /tmp/at-spi2/socket-1179-1131176229>
    #<File /tmp/at-spi2/socket-1268-1804289383>
    #<File /tmp/cron.qpBNVU>
    #<File /tmp/hsperfdata_huangz>
    #<File /tmp/hsperfdata_huangz/9350>
    #<File /tmp/keyring-NwNaja>
    #<File /tmp/keyring-NwNaja/control>
    #<File /tmp/keyring-NwNaja/gpg>
    #<File /tmp/keyring-NwNaja/pkcs11>
    #<File /tmp/keyring-NwNaja/ssh>
    #<File /tmp/mongodb-27017.sock>
    #<File /tmp/mongodb-28017.sock>
    #<File /tmp/pulse-397VI5uG1yhc>
    #<File /tmp/pulse-397VI5uG1yhc/dbus-socket>
    #<File /tmp/pulse-397VI5uG1yhc/native>
    #<File /tmp/pulse-397VI5uG1yhc/pid>
    #<File /tmp/pulse-PKdhtXMmr18n>
    #<File /tmp/pulse-T9RwKSB1FebW>
    #<File /tmp/ssh-ElvUhBgb1303>
    #<File /tmp/ssh-ElvUhBgb1303/agent.1303>
    nil


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


tree-seq
----------

**(tree-seq branch? children root)**

返回一个惰性序列，
序列里包含通过深度优先遍历得出的一棵树中的所有节点。

``branch?`` 函数接受一个参数，
通过向它传入一个节点，可以判断该节点是否拥有子节点。

``children`` 函数接受一个参数，
通过向它传入一个节点，可以得到一个包含该节点的所有子节点的序列。

``children`` 函数只会在那些
``branch?`` 函数返回 ``true`` 的节点被调用。

``root`` 是树的根节点。

::

    ; 函数 file-seq 用于列出一个文件夹的整个目录树
    ; 它是展示 tree-seq 用法的一个极好的例子

    (defn file-seq
        [dir]
        (tree-seq
            (fn [^java.io.File f] (. f (isDirectory)))      ; 检查文件 f 是不是一个文件夹
            (fn [^java.io.File d] (seq (. d (listFiles))))  ; 如果是的话，就用 listFiles 方法遍历它
            dir))                                           ; 树的根节点是传入的文件夹


xml-seq
-----------

**(xml-seq root)**

返回一个惰性序列，序列里包含一棵 xml 元素树。

xml 文件可以用 ``clojure.xml/parse`` 函数解释。

::

    ; 解释一个 xml 文件，并提取内容

    user=> (require 'clojure.xml)
    nil

    user=> (def content (clojure.xml/parse "http://www.w3schools.com/xml/note.xml"))
    #'user/content

    ; 根据 xml 内容，生成 xml 树

    user=> (def tree (xml-seq content))
    #'user/tree

    user=> tree
    ({:tag :note, :attrs nil, :content [{:tag :to, :attrs nil, :content ["Tove"]} {:tag :from, :attrs nil, :content ["Jani"]} {:tag :heading, :attrs nil, :content ["Reminder"]} {:tag :body, :attrs nil, :content ["Don't forget me this weekend!"]}]} {:tag :to, :attrs nil, :content ["Tove"]} "Tove" {:tag :from, :attrs nil, :content ["Jani"]} "Jani" {:tag :heading, :attrs nil, :content ["Reminder"]} "Reminder" {:tag :body, :attrs nil, :content ["Don't forget me this weekend!"]} "Don't forget me this weekend!")


    ; 遍历树

    user=> (nth tree 0)
    {:tag :note, :attrs nil, :content [{:tag :to, :attrs nil, :content ["Tove"]} {:tag :from, :attrs nil, :content ["Jani"]} {:tag :heading, :attrs nil, :content ["Reminder"]} {:tag :body, :attrs nil, :content ["Don't forget me this weekend!"]}]}

    user=> (nth tree 1)
    {:tag :to, :attrs nil, :content ["Tove"]}

    user=> (nth tree 2)
    "Tove"

    user=> (nth tree 3)
    {:tag :from, :attrs nil, :content ["Jani"]}

    user=> (nth tree 4)
    "Jani"


keep-indexed
-------------------

**(keep-indexed f coll)**

对于 ``coll`` 中的每个项 ``item`` ，
以及 ``item`` 对应的索引下标 ``index`` ，
``(keep-indexed f coll)`` 返回一个惰性序列，
序列中包含 ``(f index item)`` 除 ``nil`` 之外的所有计算结果。

因为带副作用的函数会返回与计算结果无关的虚假值，
因此，为了确保虚假值不会混进 ``keep-indexed`` 所生成的惰性序列中，
``f`` 必须是一个无副作用的函数。

::

    ; 返回 0 - 9 内所有排序位置(index)为偶数的数字

    user=> (keep-indexed #(if (even? %1) %2 nil) (range 10))
    (0 2 4 6 8)


cons
---------

**(cons x seq)**

返回一个新的序列，
序列的第一个元素是 ``x`` ，
而 ``seq`` 则是序列的其余部分。

::

    ; cons 起数字 1 和空列表

    user=> (cons 1 '())
    (1)


    ; cons 其数字 1 和列表 (2 3)

    user=> (cons 1 (list 2 3))
    (1 2 3)


conj
--------

| **(conj coll x)**
| **(conj coll x & xs)**

``conj`` 的完整词义是 conjoin ，
表示『相连接』的意思，
它用于将元素和 collection 拼接起来。

需要注意的是，
根据 ``coll`` 的类型，
组合会发生在 ``coll`` 的不同地方，
也即是， 元素 ``x`` 可能会被加入到 ``coll`` 的最左边，也可能会被加入到最右边。

当 ``coll`` 等于 ``nil`` ，
也即是，执行 ``(conj nil item)`` 时，
结果为 ``(item)`` 。

::

    ; coll 为 nil

    user=> (conj nil 1)
    (1)


    ; 向量的组合在尾部进行

    user=> (conj [0 1 2] 3)
    [0 1 2 3]


    ; 列表的组合在头部进行

    user=> (conj (list 0 1 2) 3)
    (3 0 1 2)


    ; 处理多个元素的 conj 
    ; 注意向量和列表的结果之间的不同

    user=> (conj [0 1 2] 3 4 5)
    [0 1 2 3 4 5]

    user=> (conj (list 0 1 2) 3 4 5)
    (5 4 3 0 1 2)


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


reverse
-----------

**(reverse coll)**

逆序给定的 ``coll`` 。

这个操作不是惰性(lazy)的。

::

    (user=>(reverse [1 2 3 4])
    (4 3 2 1)


sort
-------

| **(sort coll)**
| **(sort comparator coll)**

返回对 ``coll`` 进行排序之后得到的序列。

如果不指定 ``comparator`` ，
那么默认使用 ``compare.`` ，
``comparator`` 必须实现 ``java.util.Comparator`` 。

::

    user=> (sort [4 2 1 3])
    (1 2 3 4)

    user=> (sort >= [4 2 1 3])
    (4 3 2 1)

    user=> (sort <= [4 2 1 3])
    (1 2 3 4)


shuffle
-----------

**(shuffle coll)**

返回对 ``coll`` 进行乱序排列之后得出的序列。

::

    user=> (shuffle [1 2 3 4])
    [4 1 3 2]

    user=> (shuffle [1 2 3 4])
    [1 3 2 4]


count
----------

**(count coll)**

返回 ``coll`` 中元素的数量。

``(count nil)`` 返回 ``0`` 。

``coll`` 也可以是字符串、数组、Java Collection 和 Map 。

::

    user=> (count nil)
    0

    user=> (count [1 2 3 4])
    4

    user=> (count (list 1 2 3 4))
    4

    user=> (count "string")
    6

    user=> (count {:clojure "Rich" :python "Guido" :ruby :Matz})
    3


counted?
--------------

**(counted? coll)**

如果 ``coll`` 实现了常数复杂度的 ``count`` 操作，那么返回 ``true`` 。

::

    ; 向量、列表、Map 和集合的 count 操作都是常数复杂度的
    ; 但字符串不是

    user=> (counted? [1 2 3])
    true

    user=> (counted? '(1 2 3))
    true

    user=> (counted? {:clojure "Rich"})
    true

    user=> (counted? #{:a :b :c})
    true

    user=> (counted? "string")
    false

