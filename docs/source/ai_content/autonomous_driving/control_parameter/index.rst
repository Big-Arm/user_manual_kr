=================
Control Parameter
=================


1. 직접 폴더로 이동하여 파라미터 값 수정하기 
------------------------------------------------------------------

.. code-block:: bash

    $ cd ~/zeta_edu_package/zeta_navigataion/param

.. code-block:: bash 

    $ gedit @@(parameter name you wish to edit).yaml

이후 원하는 값을 넣고 저장을 합니다. 그리고 네비게이션을 실행시키면 해당 파라미터가 적용이 됩니다.

2. GUI상으로 실시간으로 파라미터 값 넣기 
----------------------------------------------------

먼저 네비게이션을 실행시킨 뒤에 새 터미널을 실행시켜 해당 명령어를 입력합니다.

.. code-block:: bash

    $ rosrun rqt_reconfigure rqt_reconfigure

.. image:: ../images/gui.png


해당 화면이 실행된다면 각각의 파라미터에 맞는 값들을 조정해가면서 실시간으로 네비게이션의 성능을 판단하여 봅시다.

**주의점)  파라미터 값을 한번에 많이 조정하면 네비게이션이 멈춰버리는 현상이 발생합니다. 그러므로 조금씩 값을 변화시켜서 RVIZ상에 나타나는 현상들을 주목하여 변경합니다.**

.. toctree::
    :hidden:

    self

.. toctree::

    inflation_layer
    cost_scaling