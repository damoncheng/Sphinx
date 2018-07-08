===================================
配置
===================================

django_sim application定义，以及替换django认证User
======================================================

在django工程``settings.py``配置里面::

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
    
    ]

    AUTH_USER_MODEL=`django_sim.User`

创建``django_sim``超级管理用户
======================================================

django_sim的部分功能必须依赖于超级管理员用户``django_sim``
来管理,所以在做其他功能配置前，先创建超级管理员``django_sim``::

    python createsuperuser django_sim
