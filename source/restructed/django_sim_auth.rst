==========================i=============
认证
=======================================

django_sim receiver向django_sim sender注册后，需要自助完成sender到receiver的oauth认证，
然后sender才会自动同步资源到recevier. 具体步骤如下：

资源推送认证搭建
=======================================

django_sim receiver
---------------------------------------

超级用户django_sim登录
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

    访问http://{receiver_hostname}/admin/, 通过 ``django_sim`` 账户登录

oauth code认证app搭建
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

    访问http://{receiver_hostname}/django_sim/oauth/apllications/, 添加认证app::

        Client Type : confidential

        Authorization Grant Type : authorization-code

        Redirect Urls : http://{sender_hostname}/django_sim/exchange?sim_site=http://{receiver_hostname}


django_sim sender
-------------------------f-------------

    定时运行 ``python3 manamge.py push_sim`` , 脚本自动同步资源到注册和认证后的receiver
