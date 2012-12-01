关于
====

这是 Clojure 官方 API 文档
`clojure.github.com/clojure
<http://clojure.github.com/clojure/>`_
的中文翻译版本。

在线阅读地址： `clojure-api-cn.readthedocs.org
<http://clojure-api-cn.readthedocs.org/>`_ 。


翻译进度
-----------

================================     =============
 模块                                 进度
================================     =============
``clojure.core``                        进行中
``clojure.data``                        无
``clojure.inspector``                   无
``clojure.java.browse``                 无
``clojure.java.io``                     进行中
``clojure.java.javadoc``                无
``clojure.java.shell``                  无
``clojure.main``                        无
``clojure.pprint``                      无
``clojure.reflect``                     无
``clojure.repl``                        无
``clojure.set``                         已完成
``clojure.stacktrace``                  无
``clojure.string``                      已完成
``clojure.template``                    无
``clojure.test``                        无
``clojure.walk``                        无
``clojure.xml``                         无
``clojure.zip``                         无
================================     =============


译者
--------

`huangz <http://huangz.me>`_

`Qiu Xiafei <http://chunyemen.org>`_

`Qiu Xiafei <http://chunyemen.org>`_


如何加入翻译？
----------------

1. 选定你要翻译的函数/宏/模块，到\ `项目 github 的 issue 页面 <https://github.com/huangz1990/clojure_api_cn/issues?state=open>`_\ 开一个 issue ，将你要翻译的内容写下来（为避免出现多人翻译同一项内容的情况，请确保你要翻译的内容没有其他人在翻译）
2. 如果你要翻译的是一整个模块的内容，请将上面『翻译进度』中相应模块的进度从『无』更改为『进行中』
3. 开始翻译！
4. 完成，提交翻译到 repo ，并在上面的『译者』名单里添上你的名字和链接
5. ``(recur step-1)``

以下是一些翻译时需要注意的地方：

* 庞大的 ``clojure.core`` 模块需要多人来共同翻译，只要里面的某个函数/宏没有别人在翻译，你就可以翻译它。
* 最好以单个函数/宏为单位，小段小段地 push 自己的翻译，不要将大一块翻译凑到一起来 push ，小段的内容更容易被检查
* 碰到不好翻译的地方，或者需要任何帮助，开 issue 讨论
* 对于一些没有标准翻译的词语，请使用『翻译(原文)』的格式做标记，比如： 柯里化(currying) 。这种标记同一个页面里做一次就可以了。

对以上规则有任何疑问或建议，请开 issue 或者联系 `huangz <https://github.com/huangz1990>`_ 。

参考资料
------------

Clojure 官方文档： `clojure.org/documentation <http://clojure.org/documentation>`_

Clojure API 手册： `clojure.github.com/clojure <http://clojure.github.com/clojure/>`_

Clojure Cheat Sheet： `clojure.org/cheatsheet <http://clojure.org/cheatsheet>`_

ClojureDocs ，由社区驱动的，带代码示例的 API 手册： `clojuredocs.org <http://clojuredocs.org/>`_
