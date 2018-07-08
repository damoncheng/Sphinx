===================================
配置
===================================

django_sim在django工程 ``settings.py`` 基础配置
======================================================

    在django工程 ``settings.py`` 配置里面::

        #django_sim application定义
        INSTALLED_APPS = [

            django.contrib.admin,
            django.contrib.auth,
            django.contrib.contenttypes,
            django.contrib.sessions,
            django.contrib.messages,
            django.contrib.staticfiles,

            'oauth2_provider',
            'rest_framework',
            'django_sim',

            ...
        
        ]

        #django_sim替换django认证User
        AUTH_USER_MODEL=`django_sim.User`

        #使用django自身认证backend，认证django admin登录页面
        AUTHENTICATION_BACKENDS = [
            ...
            'django.contrib.auth.backends.ModelBackend',
        ]

创建django_sim超级管理用户
======================================================

    django_sim的部分功能必须依赖于超级管理员用户 ``django_sim``
    来管理,所以在做其他功能配置前，先创建超级管理员 ``django_sim`` ::

        python createsuperuser django_sim

    按提示配置 ``django_sim`` 超级管理
