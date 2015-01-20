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

.. 以下是译者链接:

.. _huangz: http://huangz.me/

.. _Qiu Xiafei: http://chunyemen.org/

.. _Lin Xiangyu: http://linxiangyu.org/

.. _yfwu: https://github.com/yfwu

.. _simlegate: https://github.com/simlegate

.. _sectic: https://github.com/sectic

.. _yaphet: https://github.com/darionyaphet

================================     =============      =====================================================
 模块                                 进度               译者
================================     =============      =====================================================
``clojure.core``                        进行中           `huangz`_ , `Lin Xiangyu`_ , `yaphet`_
``clojure.data``                        无
``clojure.inspector``                   无
``clojure.java.browse``                 已完成           `Lin Xiangyu`_
``clojure.java.io``                     已完成           `Qiu Xiafei`_
``clojure.java.javadoc``                已完成           `Lin Xiangyu`_
``clojure.java.shell``                  已完成           `Lin Xiangyu`_
``clojure.main``                        无
``clojure.pprint``                      进行中           `sectic`_
``clojure.reflect``                     无
``clojure.repl``                        进行中           `simlegate`_
``clojure.set``                         已完成           `Qiu Xiafei`_
``clojure.stacktrace``                  无
``clojure.string``                      已完成           `huangz`_
``clojure.template``                    无
``clojure.test``                        进行中           `yfwu`_
``clojure.walk``                        无
``clojure.xml``                         已完成           `Lin Xiangyu`_
``clojure.zip``                         无
================================     =============      =====================================================


如何加入翻译？
----------------

1. 选定你要翻译的函数/宏/模块，到\ `项目 github 的 issue 页面 <https://github.com/huangz1990/clojure_api_cn/issues?state=open>`_\ 开一个 issue ，将你要翻译的内容写下来（为避免出现多人翻译同一项内容的情况，请确保你要翻译的内容没有其他人在翻译）。
2. 如果你要翻译的是一整个模块的内容，请在“翻译进度”表中将相应模块的进度从“无”更改为“进行中”，并在“译者”一栏加上你的名字和链接。
3. 开始翻译！
4. 完成，提交翻译到 repo ，并在“翻译进度”表中将相应模块的状态改为“已完成”。
5. ``(recur step-1)``

以下是一些翻译时需要注意的地方：

* 庞大的 ``clojure.core`` 模块需要多人来共同翻译，只要里面的某个函数/宏没有别人在翻译，你就可以翻译它。
* 最好以单个函数/宏为单位，小段小段地 push 自己的翻译，不要将大一块翻译凑到一起来 push ，小段的内容更容易被检查
* 碰到不好翻译的地方，或者需要任何帮助，开 issue 讨论
* 对于一些没有标准翻译的词语，请使用“翻译(原文)”的格式做标记，比如： 柯里化(currying) 。这种标记同一个页面里做一次就可以了。
* 如果模块文档没有提供相应的测试代码，可以参考 `ClojureDocs <http://clojuredocs.org/>`_ 上面的测试代码，也可以自己添加测试代码。

对以上规则有任何疑问或建议，请开 issue 或者联系 `huangz`_ 。

参考资料
------------

Clojure 官方文档： `clojure.org/documentation <http://clojure.org/documentation>`_

Clojure API 手册： `clojure.github.com/clojure <http://clojure.github.com/clojure/>`_

Clojure Cheat Sheet： `clojure.org/cheatsheet <http://clojure.org/cheatsheet>`_

ClojureDocs ，由社区驱动的，带代码示例的 API 手册： `clojuredocs.org <http://clojuredocs.org/>`_
