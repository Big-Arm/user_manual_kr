===============
로봇팔 댄스 - 2
===============


-   05_09_music_dance.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/having_fun/arm_dance2.png

-   흥겨운 음악이 나오는 로봇팔 댄스 예제 - 2

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
    music = mixer.Sound('music.ogg')
    bomb = mixer.Sound('bomb.ogg')
    music.set_volume(0.02)
    bomb.set_volume(0.1)

-   사운드 파일 등록

.. code-block:: python

    # 초기화
    Arm.Arm_serial_servo_write6(0, 90, 0, 180, 90, 90, 2000)

-   로봇팔 위치 초기화

.. code-block:: python

    while(1):
        music.play()
        # 모터 범위 0~180
        Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 2000)
        time.sleep(2.1)
        Arm.Arm_serial_servo_write6(180, 90, 0, 180, 90, 90, 2000)
        time.sleep(2.1)
        Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 2000)
        time.sleep(2.1)
        Arm.Arm_serial_servo_write6(0, 90, 0, 180, 90, 90, 2000)
        time.sleep(2.1)
        Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 2000)
        time.sleep(2.1)
        Arm.Arm_serial_servo_write6(180, 90, 0, 180, 90, 90, 2000)
        time.sleep(2.1)
        Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 1600)
        time.sleep(1.61)
        Arm.Arm_serial_servo_write6(90, 90, 0, 90, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 180, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(0, 90, 0, 180, 0, 180, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 180, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(180, 90, 0, 180, 180, 180, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 180, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 90, 90, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 180, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(0, 90, 0, 180, 0, 180, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 180, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(180, 90, 0, 180, 180, 180, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 180, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(180, 90, 0, 180, 180, 180, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 180, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(0, 90, 0, 180, 0, 180, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 180, 90, 90, 600)
        time.sleep(0.82)
        Arm.Arm_serial_servo_write6(90, 90, 0, 90, 90, 90, 1500)
        time.sleep(1.5)
        Arm.Arm_serial_servo_write6(90, 90, 0, 90, 90, 180, 500)
        time.sleep(1.5)
        music.stop()
        bomb.play()
        break

-   사운드 재생 및 댄스

.. code-block:: python

    my_sound.stop()

-   사운드 정지
