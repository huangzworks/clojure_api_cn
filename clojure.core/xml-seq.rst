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


