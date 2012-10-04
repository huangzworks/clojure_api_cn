defn-
---------------

**(defn- name & decls)**

作用和 ``defn`` 类似，唯一的不同是创建的函数是私有的。

::

    user=> (defn- msg [] "hello moto")
    #'user/msg

    user=> (msg)
    "hello moto"

    user=> (meta #'msg)
    {:arglists ([]), :ns #<Namespace user>, :name msg, :private true, :line 1, :file "NO_SOURCE_PATH"}
