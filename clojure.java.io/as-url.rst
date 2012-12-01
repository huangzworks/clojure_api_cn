as-url
===============

| **(as-url x)**

接受一个 ``x`` 参数，返回一个 ``java.net.URL`` 对象。 ``x`` 的类型可以是 ``java.lang.String`` ， ``java.io.File`` ， ``java.net.URL`` 和 ``java.net.URI`` 。

当 ``x`` 的类型是 ``java.lang.String`` 时， ``x`` 必须是一个合法的URL。

当 ``x`` 是 ``nil`` 时，返回 ``nil`` 。

如果提供了 ``km`` 参数，则按照 ``km`` 所列出的key进行join。


::

    user> (use 'clojure.java.io)
    nil
    user> (as-url "http://baidu.com")
    #<URL http://baidu.com>
    user> (as-url (java.io.File. "/tmp"))
    #<URL file:/tmp/>
    user> (as-url (java.net.URI. "http://www.google.com"))
    #<URL http://www.google.com>
    user> (as-url "baidu.com")
    ;;MalformedURLException no protocol: baidu.com  java.net.URL.<init> (URL.java:567)
