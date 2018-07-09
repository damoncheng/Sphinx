=======================================
简介
=======================================

概述
============================================================

    django_sim是一套推送和管理资源的SDK, 其基于SCIM方案为模板，
    使用django-oauth-toolkit进行认证和权限控制，
    使用djangorestframework进行资源推送。

django_sim资源
============================================================

    django工程可使用的资源::

        User
        
            用户

        Team

            用户组, 一个Team下面可以包含多个User和Team。Team对应公司的各层组织架构

        Role 

            用户角色, 用户角色属于一个Team。Role主要时为了给各平台系统基于Role来进行权限控制。
            比如在SNG产品部时一个Team，下面可以创建一个CMO的Role。

        Project

            Project是一个命名空间，属于一个User或一个Team。主要是为了中心各平台使用同一的项目名称。

    推送资源::

        Bulk

            django_sim sender基于bulk来推送资源, 默认bulk大小是1024条记录，第一次全量同步资源到
            receiver，第二次以后增量同步资源到receiver。sender在每次推送前会取receiver的最后一次
            结束bulk来作为参考进行推送，保证推送后reciver数据全量。

            bulk有四种类型:

            全量同步bulk:     在sender第一次全量同步资源到receiver时使用
            全量同步结束bulk: 在sender第一次成功全量同步资源到receiver后使用
            增量同步bulk:     在sender第一次成功同步后，每次同步资源到receiver时使用
            增量同步结束bulk: 在sender第一次成功同步后，每次成功同步资源到receiver后使用


        
功能
============================================================

    资源同步

        django_sim receiver使用django-oauth-toolkit搭建基于Authorization code认证
        的app来生成认证信息，然后receiver提交认证信息到django_sim sender进行注册，
        注册完成后，receiver自助完成认证, 认证完成后, sender将定时同步资源到receiver

    资源访问

        django_sim reicever和sender都可以使用django-oauth-toolkit搭建基于
        client credentials认证的app来生成认证信息，client可以使用认证信息访问django_sim的
        API来获取相关资源信息。

        .. image:: images/django_sim_push.png

    资源管理

        django_sim支持通过django admin页面对资源进行搜索和管理


    认证User替换

        替换原来的django user表，使用django_sim的User来进行认证

    tof认证

        提供tof django认证backend和tof djangorestframwork认证backend实现tof认证
     
