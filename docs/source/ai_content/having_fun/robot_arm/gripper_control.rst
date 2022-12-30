===============
그리퍼 제어하기
===============


-   05_08_grip.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/gripper1.png

.. code-block:: python

    #!/usr/bin/env python3
    #coding=utf-8
    import time
    from Arm_Lib import Arm_Device

    # 로봇팔 객체 등록
    Arm = Arm_Device()
    time.sleep(.1)

-   Arm_Lib 모듈 불러오기 및 로봇팔 객체 등록


.. code-block:: python

    jonits_home = [90, 90, 90, 90, 90, 90]

    # 첫 위치 벌림
    joints_0 = [39, 61, 23, 67, 89, 90]
    # 첫 위치 집기
    joints_1 = [39, 61, 23, 67, 89, 130]
    # 올라가있는 집기
    joints_2 = [39,107,37,67,89,130]
    # 회전 된 상태 집기
    joints_3 = [150,105,35,67,89,130]
    # 회전된 상태 내리기
    joints_4 = [149,63,30,66,89,130]
    # 회전된 상태 놓기
    joints_5 = [149,63,30,66,89,90]

-   list = [1번 모터, 2번 모터, 3번 모터, 4번 모터, 5번 모터, 6번 모터]

.. code-block:: python

    Arm.Arm_serial_servo_write6_array(jonits_home, 2000)

-   Arm_serial_servo_write6_array(list, 시간)

.. code-block:: python

    Arm_serial_servo_write6_array(list, 시간)

.. code-block:: python

    Arm.Arm_serial_servo_write6_array(joints_1, 500)
    time.sleep(.1)

.. code-block:: python

    Arm.Arm_serial_servo_write6_array(joints_2, 2000)

.. code-block:: python

    Arm.Arm_serial_servo_write6_array(joints_3, 1500)

.. code-block:: python

    Arm.Arm_serial_servo_write6_array(joints_4, 1500)

.. code-block:: python

    Arm.Arm_serial_servo_write6_array(joints_5, 500)



-   서보모터와 그리퍼 제어를 통한 Pick and Place


.. code-block:: python

    del Arm   # Release DOFBOT object

-   로봇팔 객체 제거