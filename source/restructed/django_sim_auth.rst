=======================================
认证
=======================================

    django_sim根据使用功能的不同可以搭建两种认证，资源推送认证和资源访问认证::

        资源推送认证：sender和receiver之间搭建oauth code认证，认证后，sender自动推送资源到receiver

        资源访问认证：sender或receiver可以搭建oauth client认证，认证后，client可以通过API访问
        django_sim资源。


资源推送认证
=======================================

    django_sim receiver向django_sim sender注册后，需要自助完成sender到receiver的oauth认证，
    然后sender才会自动同步资源到recevier. 具体步骤如下：


django_sim receiver

超级用户django_sim登录
---------------------------------------

    访问http://{receiver_hostname}/admin/, 通过 ``django_sim`` 账户登录

oauth code认证app搭建
---------------------------------------

    访问http://{receiver_hostname}/django_sim/oauth/apllications/, 添加认证app::

        Client Type : confidential

        Authorization Grant Type : authorization-code

        Redirect Urls : http://{sender_hostname}/django_sim/exchange?sim_site=http://{receiver_hostname}


django_sim sender

    定时运行 ``python3 manamge.py push_sim`` , 脚本自动同步资源到注册和认证后的receiver
