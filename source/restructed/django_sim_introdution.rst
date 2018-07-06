=======================================
介绍
=======================================

概述
============================================================
django_sim基一套推送和管理资源的SDK, 其基于SCIM方案为模板，
使用django-oauth-toolkit进行认证和权限控制，
使用djangorestframework进行资源推送。

功能
============================================================

资源同步

    django_sim receiver使用django-oauth-toolkit搭建基于Authorization code认证
    的app来生成认证信息，然后receiver提交认证信息到django_sim sender进行注册，
    注册完成后，receiver自助完成认证, 之后sender将定时同步资源到receiver。


资源访问

    django_sim reicever和sender都可以使用django-oauth-toolkit搭建基于
    client credentials认证的app来生成认证信息，client可以基于认证信息来访问django_sim的
    API来获取相关资源信息。
