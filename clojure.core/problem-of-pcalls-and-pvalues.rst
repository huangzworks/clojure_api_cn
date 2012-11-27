.. note::

    因为 ``pcalls`` 和 ``pvalues`` 的返回值都是惰性序列，因此，如果有一个非常耗时的表达式阻塞在其他一些表达式的前面，那么就算后面的这些表达式已经计算完了，它们也不能被返回。

    以下是这样一个实例，在序列前面的三个元素，可以立即被返回，但是，后面的三个元素只有等待 ``(Thread/sleep 3000)`` 执行完毕之后，才会被返回，尽管它们早就在并发线程里被求值完了：

    ::

        user=> (for [i (pvalues 1 2 3 
                                (Thread/sleep 3000) 
                                (do (println "eval 4") 4)
                                (do (println "eval 5") 5)
                                (do (println "eval 6") 6))
                    ]
                   (println i)
               )
        (1
        2
        nil eval 5  ; 从 println 的输出可以看到
        eval 4      ; 4 、 5 、 6 三个数已经被计算出来了，但还没办法返回
        3           
        nil eval 6  
        nil         ; sleep 执行，停滞 3 秒
        nil 4
        nil 5
        nil 6
        nil nil)
