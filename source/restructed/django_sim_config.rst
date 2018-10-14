===================================
配置
===================================

django_sim在 ``settings.py`` 基础配置
======================================================

    在django工程 ``settings.py`` 里面配置::

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
            'background_task',
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

    django_sim的功能必须依赖于超级管理员用户 ``django_sim``
    来管理,所以在做其他功能配置前，先创建超级管理员 ``django_sim`` ::

        python3 createsuperuser django_sim

    按提示配置 ``django_sim`` 超级管理员


使用django_sim的tof认证
======================================================

    在django工程 ``setting.py`` 里面补充配置::

        AUTHENTICATION_BACKENDS = {
            'django_sim.authentication.backend.TofTicketBackend',
            'django.contrib.auth.backends.ModelBackend',
            ...
        } 

        REST_FRAMEWORK = {
        
            'DEFAULT_PERMISSION_CLASSES' : (
                'rest_framework.permissions.IsAuthenticated',
            ),

            'DEFAULT_AUTHENTICATION_CLASSES' : (
                'django_sim.authentication.backend.SIMAuthentication',
            )
            ...
        }

        LOGIN_URL = "http://passport.oa.com/modules/passport/signin.ashx?title=%s&url=%s" 
            % ("title", "http://{hostname}/django_sim/sim_login/")
        LOGOUT_URL = "http://passport.oa.com/modules/passport/signout.ashx?title=%s&url=%s"
            %s ("title", "http://{hostname}/django_sim/sim_login/")
        


