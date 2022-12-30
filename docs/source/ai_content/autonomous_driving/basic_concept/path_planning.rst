=============
Path Planning
=============



**Path Planning이란?** 


| 매핑이 되고 위치가 어딘지를 알게 되면 로봇에게 **목표를 던져주면서 어디로 갈지 명령**을 주개 됩니다. 이러한 과정을 Path planning 이라고 합니다. 


**Move_base**


| Path Planning을 함에 있어 ROS 패키지 자체에서 제공하는 구성요소 및 노드를 Move_base라고 합니다. Move_base의 가장 중요한 핵심은 **현재의 위치에서 목표한 위치로 이동**하는것입니다.
|
| 기본적으로 Move_base는 토픽을 받고 그 토픽에 맞는 동작을 하고 다시 토픽을 보내기에 액션타입입니다.

.. image:: ../images/path_planning.svg


.. toctree::
    :titlesonly:
    :hidden:

    path_planning/global_cost
    path_planning/local_cost
    path_planning/local_planner