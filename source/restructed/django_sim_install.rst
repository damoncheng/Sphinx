=======================================
安装
=======================================

    django_sim目前只支持环境python3和django>=2.0

依赖
=======================================

    django_sim依赖以下环境::

        python3.x
        django>=2.0
        djangorestframework==3.7.7
        django-oauth-toolkit==1.1.0
        django-background-tasks==1.1.13
        suds-py3==1.3.3.0

指定镜像安装
=======================================

    django_sim可以通过pip3指定镜像安装::

        IDC 环境:

            pip install django_sim -i http://pypi.dq.oa.com/simple/ --trusted-host=pypi.dq.oa.com

        Devnet 环境:

            pip install django_sim -i http://devnet.pypi.dq.oa.com/simple/ --trusted-host=devnet.pypi.dq.oa.com


本地安装
=======================================

    django_sim可以通过pip3本地安装::

        pip3 install django_sim-1.0.tar.gz
