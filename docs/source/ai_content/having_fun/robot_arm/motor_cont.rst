========================
서보모터 제어하기
========================


-   05_03_ctrl_all.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/having_fun/motor_cont1.webp

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

    # 6개의 서보를 동시에 제어하면서, 각도를 점점 변화 시킨다.
    def ctrl_all_servo(angle, s_time = 500):
        Arm.Arm_serial_servo_write6(angle, 180-angle, angle, angle, angle, angle, s_time)
        time.sleep(s_time/1000)


    def main():
        dir_state = 1
        angle = 90

        Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 500)
        time.sleep(1)

        
        while True:
            if dir_state == 1:
                angle += 1
                if angle >= 180:
                    dir_state = 0
            else:
                angle -= 1
                if angle <= 0:
                    dir_state = 1
            
            ctrl_all_servo(angle, 10)
            time.sleep(10/1000)
    #         print(angle)

        
    try :
        main()
    except KeyboardInterrupt:
        print(" Program closed! ")
        pass


-   Arm_serial_servo_write(모터 번호, 각도, 시간)
-   while문을 이용해 모든 서보모터 각도를 1˚씩 증감


.. code-block:: python

    del Arm  # 로봇팔 객체 제거

    

-   로봇팔 객체 제거