=======================================
资源
=======================================


资源结构
=======================================

    ..image:: 
    
        images/django_sim_resource.png


    User,Team,Role,Project都是一种Resource。SimResource作为资源适配器提供统一访问资源Model给其他类使用::

        class SimResource(models.Model):

            resource_type : 
            
                Required, 整数类型，说明该resource的类型。可取值为0(user), 1(team), 2(role), 3(project)

            resource_id   : 
            
                Required, UUID字符串。每个resource的id是唯一的。

            created : 
            
                Required, Datetime类型。记录resource的创建时间。

            last_modified : 
            
                Required, Datetime类型。记录resource的最后修改时间。



资源访问
=======================================

