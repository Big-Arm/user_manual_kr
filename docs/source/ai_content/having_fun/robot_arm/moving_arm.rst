====================
로봇팔 움직이기
====================

-   05_01_left_right.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/arm1.webp

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

    # 로봇팔 위 아래로 스윙 반복
    # Arm range = 0 ~ 180
    def main():
        # Make all servos in the middle.
        Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 500)
        time.sleep(1)


        while True:
            # 3번과 4번 서보를 위 아래로 움직인다
            Arm.Arm_serial_servo_write(3, 0, 1000)
            time.sleep(.001)
            Arm.Arm_serial_servo_write(4, 180, 1000)
            time.sleep(1)
            
            # 1번과 5번 서보를 좌우로 움직인다.
            Arm.Arm_serial_servo_write(1, 180, 500)
            time.sleep(.001)
            Arm.Arm_serial_servo_write(5, 180, 500)
            time.sleep(0.51)
            Arm.Arm_serial_servo_write(1, 0, 1000)
            time.sleep(.001)
            Arm.Arm_serial_servo_write(5, 0, 500)
            time.sleep(1.1)
            
            # 서보를 초기 위치로 움직인다.
            Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 1000)
            time.sleep(1.5)


    try :
        main()
    except KeyboardInterrupt:
        print(" Program closed! ")
        pass


-   Arm_serial_servo_write6(1번 모터, 2번 모터, 3번 모터, 4번 모터, 5번 모터, 6번 모터, 시간)
-   Arm_serial_servo_write(모터 번호, 각도, 시간)
-   3번 서보모터를 0˚, 4번 서보모터를 180˚로 조절
-   1번, 5번 서보모터를 180˚ -> 0˚로 조절

.. code-block:: python

    del Arm  # 로봇팔 객체를 제거


-   로봇팔 객체 제거