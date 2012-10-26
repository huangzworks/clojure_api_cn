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


