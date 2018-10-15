=======================================
资源
=======================================

.. _django_sim_resource_structure:

资源结构
=======================================

访问资源结构
---------------------------------------

  django_sim访问资源结构图:

      .. image:: images/django_sim_resource.png


  SimResource

      User,Team,Role,Project都是一种Resource。SimResource作为资源适配器统一访问资源给其他类使用::

        class SimResource(models.Model):

            resource_type : 
            
                Required, 整数类型，说明该resource的类型。可取值为0(user), 1(team), 2(role), 3(project)

            resource_id  : 
            
                Required, UUID字符串，每个resource的id是唯一的。

            created : 
            
                Required, Datetime类型，记录resource的创建时间。

            last_modified : 
            
                Required, Datetime类型，记录resource的最后修改时间。

            is_valid :

                Required, Boolean类型，标志该资源是否有效


  SimAbstract

      SimAbstract是SIM的User,Team,Role,Project的抽象类::

        class SimAbstract(models.Model):

            resource_id : 

                Required, UUID字符串。每个Resource的id时唯一的。

            is_valid :

                Required, Boolean类型，标志该资源是否有效

            external_id :

                Optional, 该资源的外部ID字符串。external_id由外部传入。例如时TOF的小组ID。

            display_name :

                Optional, 字符串泪下，该资源显示名称, 不同资源允许相同显示名称。


  SimUser

      SimUser作为SIM User Model, 继承django.contrib.auth.models.AbstractUser和SimAbstract, 替换django原有认证User::

        class SimUser(SimAbstract,AbstractUser):

            resource_meta : 

                Required, 一对一外键指向一条SimResource记录。

            team : 

                Optional, 该用户所属team，外键指向一条SimTeam记录。

            manager :

                Optional，该用户的manager，外间指向一条SimUser记录。


  SimTeam

      SimTeam的Model的定义如下::

        class SimTeam(SimAbstract):

            resource_meta : 

                Required, 一对一外键指向一条SimResource记录。

            name :

                Required, 字符串类型，该team唯一名称, 可用于保存team组织架构路径。

            group :

                Required, 一对一外键指向一条django.contrib.auth.models.Group记录，
                由于AbastractUser包含一对多外键groups指向Group, 因此可通过该外键
                给该team添加额外成员。

            level :

                Required, 字符串类型，该team层级, 现包括system(事业群)，department(部门)，
                centre(中心)，team(小组)，office(事业群)，area(片区), other(其他)。

            parent_team :

                Optional，指向上级组织，外键指向一条SimTeam记录。


  SimRole

      SimRole的Model的定义如下::

        class SimRole(SimAbstract):

            resource_meta : 

                Required, 一对一外键指向一条SimResource记录。

            name :

                Required, 字符串类型，该role唯一名称。

            group :

                Required, 一对一外键指向一条django.contrib.auth.models.Group记录，
                由于AbastractUser包含一对多外键groups指向Group, 因此可通过该外键
                给该role添加额外成员。

            team :

                Optional，该role所属team, 外键指向一条SimTeam记录。


  SimProject

      SimProject的Model的定义如下::

        class SimProject(SimAbstract):

            resource_meta : 

                Required, 一对一外键指向一条SimResource记录。

            name :

                Required, 字符串类型，该project唯一名称。

            owner :

                Optional，外键指向这个project归属的User，team或role。

     
推送资源结构
---------------------------------------

  SimBulk

      

      

认证资源结构
---------------------------------------



资源接口
=======================================


Http接口 
---------------------------------------


函数接口 
---------------------------------------

