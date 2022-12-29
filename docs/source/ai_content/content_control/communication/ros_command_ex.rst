===================
ROS Command Example
===================

-   01_ros.ipynbipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/comm3.png

.. code-block:: bash

    $ !rosnode list

-   현재 실행되고 있는 ROS Node 목록을 출력

.. image:: ../images/comm4.webp

.. code-block:: bash

    $ !rosnode info /joy_node

-   joy_node Node의 정보를 출력

.. image:: ../images/comm5.png

.. code-block:: bash

    $ !rostopic list

-   현재 실행되고 있는 ROS Topic 목록을 출력

.. image:: ../images/comm6.png

.. code-block:: bash

    $ !rostopic info /imu

-   imu Topic의 정보를 출력

.. image:: ../images/comm7.png

.. code-block:: bash

    $ !rostopic echo /imu

-   imu Topic의 Message를 출력


.. image:: ../images/comm8.webp

.. code-block:: bash

    $ pm2 list

-   pm2를 이용한 프로세스 목록 확인

.. image:: ../images/comm9.png

.. code-block:: bash

    $ !rosnode info /zetasound

-   zetasound Node의 정보를 출력
