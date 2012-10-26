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
