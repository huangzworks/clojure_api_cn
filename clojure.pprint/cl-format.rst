cl-format
============

| **(cl-format writer format-in & args)**

Common Lisp 兼容的格式输出的函数的实现。cl-format
的格式包括是输出到流里还是输出
成string都是通过不同的参数控制的。它支持极为复杂的机构化的数据。

Writer参数是java.io.Writer的一个实例，有的话输出成流，反之输出成String。format-in
用于格式控制。 args 指代数据将要被格式化输出的。

format control string
是通过格式化符号，标注怎么去把许多参数按不同的方式格式化的。
类似 String.format 的 dsl。

如果 writer 是控制，那么cl-format 返回 string，否则返回空值，输出到流里。

一个例子:
(let [results [46 38 22]]
(cl-format true "There ~[are~;is~:;are~]~:* ~d result~:p: ~{~d~^,
~}~%"
(count results) results))

输出结果 *out*:
There are 3 results: 46, 38, 22

详细的文档关于 format control string 在"Common
Lisp the Language, 2nd edition", Chapter 22
(available online at:
http://www.cs.cmu.edu/afs/cs.cmu.edu/project/ai-repository/ai/html/cltl/clm/node200.html#SECTION002633000000000000000)
and in the Common Lisp HyperSpec at
http://www.lispworks.com/documentation/HyperSpec/Body/22_c.htm



1 EXAMPLE

::

    ;; 一种格式化integer的方式.
    ;; 第一个参数把输出定向到 *out*
    user=> (cl-format true "~5d\n" 3)
    3
    nil

    ;; 第一个参数nil或false回直接输出成sting
    user=> (cl-format nil "~5d" 3)
    "    3"

    user=> (cl-format nil "Pad with leading zeros
    ~5,'0d" 3)
    "Pad with leading zeros 00003"

    user=> (cl-format nil "Pad with leading
    asterisks ~5,'*d" 3)
    "Pad with leading asterisks ****3"


    ;; 如果有办法去描述一个左对齐的数在一个
    formatString 里请标示在这理。
    ;; 这个任务在我看来，可以首先去 formatted 数成
    String 然后再使用 <width>
    规则加到原来的输出结果上。

    user=> (cl-format nil "~15a" (cl-format nil
    "~:d" 1234567))
    "1,234,567      "

    user=> (cl-format nil "Always print the sign
    ~5@d" 3)
    "Always print the sign    +3"

    user=> (cl-format nil "Use comma
    group-separator every 3 digits ~12:d" 1234567)
    "Use comma group-separator every 3 digits
    1,234,567"

    user=> (cl-format nil "decimal ~d  binary ~b
    octal ~o  hex ~x" 63 63 63 63)
    "decimal 63  binary 111111  octal 77  hex 3f"

    user=> (cl-format nil "base 7  ~7r  with width
    and zero pad  ~7,15,'0r" 63 63)
    "base 7  120  with width and zero pad
    000000000000120"

    ;; 在 cl-format 里不需要做任何转换  BigInt,
    ;; BigInteger, or BigDecimal.
    user=> (cl-format nil "cl-format handles
    BigInts ~15d" 12345678901234567890)
    "cl-format handles BigInts
    12345678901234567890"

    user=> (cl-format nil "Be aware of
    auto-conversion  ~8,'0d  ~8,'0d" 2.4 -5/4)
    "Be aware of auto-conversion  000002.4
    0000-5/4"

    ;; 下面看起来可能像是一个bug，但是是被 Common
    Lisp HyperSpec
    写在文档上的一种方法，如果你觉得这样写不爽，
    ;; 你也可以这样写 (format "%08d" -2)

    user=> (cl-format nil "~8,'0d" -2)
    "000000-2"
