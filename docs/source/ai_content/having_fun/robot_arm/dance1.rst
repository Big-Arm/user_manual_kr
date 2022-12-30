===============
로봇팔 댄스 - 1
===============


-   05_09_carri_dance.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/arm_dance1.png

-   흥겨운 음악이 나오는 로봇팔 댄스 예제 - 1

.. code-block:: python

    from pygame import mixer
    import time
    from Arm_Lib import Arm_Device

    # 로봇팔 객체 등록
    Arm = Arm_Device()
    time.sleep(.1)

-   Arm_Lib 모듈 불러오기 및 로봇팔 객체 등록


.. code-block:: python

    # ogg 파일 등록
    mixer.init(48000, 16, 2, 2048)
    my_sound = mixer.Sound('music.ogg')
    my_sound.set_volume(0.01)

-   사운드 파일 등록

.. code-block:: python

    # 초기화
    Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 1000)

-   로봇팔 위치 초기화

.. code-block:: python

    while(1):
        my_sound.play()
        # 1번 동작
        Arm.Arm_serial_servo_write(3, 0, 1500)
        time.sleep(.001)
        Arm.Arm_serial_servo_write(4, 180, 1500)
        time.sleep(.001)
        Arm.Arm_serial_servo_write(1, 0, 1500)
        time.sleep(5.5)
        # 2번 동작
        Arm.Arm_serial_servo_write(1, 90, 500)
        time.sleep(1.5)
        # 3번 동작
        Arm.Arm_serial_servo_write(1, 180, 500)
        time.sleep(1.5)
        # 4번 동작
        Arm.Arm_serial_servo_write(3, 90, 500)
        time.sleep(.001)
        Arm.Arm_serial_servo_write(4, 90, 500)
        time.sleep(1.5)
        # 5번 동작
        Arm.Arm_serial_servo_write(3, 0, 500)
        time.sleep(.001)
        Arm.Arm_serial_servo_write(4, 180, 500)
        time.sleep(1.5)
        # 6번 동작
        Arm.Arm_serial_servo_write(1, 90, 1000)
        time.sleep(1.5)
        # 7번 동작
        Arm.Arm_serial_servo_write(1, 0, 1000)
        time.sleep(1.5)
        my_sound.stop()
        break

-   사운드 재생 및 댄스

.. code-block:: python

    my_sound.stop()

-   사운드 정지

.. code-block:: python

    Arm.Arm_serial_servo_write(3, 0, 500)
    time.sleep(.001)
    Arm.Arm_serial_servo_write(4, 180, 500)

.. code-block:: python

    Arm.Arm_serial_servo_write(1, 0, 1000)

.. code-block:: python

    Arm.Arm_serial_servo_write6_array(joints_4, 1500)

.. code-block:: python

    Arm.Arm_serial_servo_write(3, 90, 500)
    time.sleep(.001)
    Arm.Arm_serial_servo_write(4, 90, 500)


.. code-block:: python

    Arm.Arm_serial_servo_write(3, 0, 500)
    time.sleep(.001)
    Arm.Arm_serial_servo_write(4, 180, 500)

-   마무리 동작