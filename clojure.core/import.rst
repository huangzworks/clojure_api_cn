import
-------------

**(import & import-symbols-or-lists)**

**import-list => (package-symbol class-name-symbols*)**

对于 ``class-name-symbols`` 中的每个 ``name`` 来说，
将名字为 ``package.name`` 的类添加到当前 namespace 当中。

可以在 ``ns`` 宏中通过 ``:import`` 来调用这个函数。

::

    user=> (import java.util.Date)                      ; 载入单个类
    java.util.Date

    user=> (str (Date.))
    "Wed Jun 20 23:18:42 CST 2012"

    user=> (import '(java.util Date Calendar)           ; 载入多个类
                   '(java.net URI ServerSocket))
    java.net.ServerSocket

    user=> (ns foo.bar                                  ; 在 ns 宏中使用
               (:import (java.util Date Calendar)
                        (java.net URI ServerSocket)))
    java.net.ServerSocket


