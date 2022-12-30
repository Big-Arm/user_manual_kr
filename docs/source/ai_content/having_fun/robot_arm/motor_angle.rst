======================
서보모터 각도 읽기
======================


-   05_02_read_servo.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/rob_arm1.png

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

    # 모든 서보의 각도를 읽는다.
    def main():

        while True:
            for i in range(6):
                aa = Arm.Arm_serial_servo_read(i+1)
                print(aa)
                time.sleep(.01)
            time.sleep(.5)
            print(" END OF LINE! ")

        
    try :
        main()
    except KeyboardInterrupt:
        print(" Program closed! ")
        pass


-   Arm_serial_servo_read(모터 번호)
-   while문을 이용한 모든 서보모터 각도 읽기


.. code-block:: python

    # 서보의 움직임을 개별적으로 제어한 후, 각도를 읽는다.
    id = 3
    angle = 41

    Arm.Arm_serial_servo_write(id, angle, 500)
    time.sleep(1)

    aa = Arm.Arm_serial_servo_read(id)
    print(aa)

    time.sleep(.5)


-   Arm_serial_servo_write(모터 번호, 각도, 시간)
-   3번 서보모터 제어 후 각도 읽기

.. code-block:: python

    del Arm  # 로봇팔 객체를 제거


-   로봇팔 객체 제거