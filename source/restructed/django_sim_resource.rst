=======================================
资源
=======================================


访问资源结构
=======================================

    django_sim资源结构图:

    .. image:: images/django_sim_resource.png


 SimResource
=======================================

    User,Team,Role,Project都是一种Resource。SimResource作为资源适配器统一访问资源给其他类使用::

        class SimResource(models.Model):

            resource_type : 
            
                Required, 整数类型，说明该resource的类型。可取值为0(user), 1(team), 2(role), 3(project)

            resource_id   : 
            
                Required, UUID字符串。每个resource的id是唯一的。

            created : 
            
                Required, Datetime类型。记录resource的创建时间。

            last_modified : 
            
                Required, Datetime类型。记录resource的最后修改时间。


 SimAbstract
=======================================

    SimAbstract是SIM的User,Team,Role,Project的抽象类::

        class SimAbstract(models.Model):

            resource_id : 

                Required, UUID字符串。每个Resource的id时唯一的。

            external_id :

                Optional, 该资源的外部ID字符串。external_id由外部传入。例如时TOF的小组ID。


资源使用
=======================================

