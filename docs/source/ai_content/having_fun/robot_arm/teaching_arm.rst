==================
로봇팔 티칭하기
==================

-   05_05_study_mode.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/teaching1.png

.. code-block:: python

    #!/usr/bin/env python3
    #coding=utf-8
    import time
    from Arm_Lib import Arm_Device

    Arm = Arm_Device()
    time.sleep(.1)

-   Arm_Lib 모듈 불러오기 및 로봇팔 객체 등록

.. code-block:: python

    # 학습모드를 사용하게 되면 로봇 팔의 토크가 풀려서 움직일 수 있다.
    # 학습모드에서는 수동으로 로봇 팔을 조종할 수 있다.
    Arm.Arm_Button_Mode(1)
    

.. code-block:: python

    # 이 곳은 학습을 등록하는 곳이다. 
    # 팔을 움직이고 실행할 때 마다 동작이 등록된다.(20동작)
    Arm.Arm_Action_Study()


.. code-block:: python

    # 학습모드를 종료한다.
    Arm.Arm_Button_Mode(0)


.. code-block:: python

    # 저장된 학습의 갯수를 알려준다.
    num = Arm.Arm_Read_Action_Num()
    print(num)


.. code-block:: python

    # 학습된 동작을 한 번 실행한다.
    Arm.Arm_Action_Mode(1)


.. code-block:: python

    # 학습된 동작을 반복한다.
    Arm.Arm_Action_Mode(2)

.. code-block:: python

    # 학습된 동작을 멈춘다..
    Arm.Arm_Action_Mode(0)

.. code-block:: python 

    # 학습된 동작을 초기화 한다.
    Arm.Arm_Clear_Action()

-   로봇팔 티칭 및 학습된 동작 실행

.. code-block:: python

    del Arm  # Release DOFBOT object


-   로봇팔 객체 제거