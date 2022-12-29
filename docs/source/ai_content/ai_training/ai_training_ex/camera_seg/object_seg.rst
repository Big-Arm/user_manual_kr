===================
객체 분할하기
===================


-   4. 카메라로 객체 분할.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../../images/obj_seg1.png


.. code-block:: python

    import subprocess

-   subprocess 모듈 가져오기


.. code-block:: python

    # 라즈베리 파이 카메라로 객체 분할하기
    detect_command_segment = 'bash ~/ai_example/detect.sh cam_segment'
    subprocess.call((detect_command_segment.split('\n')), shell=True)


-   라즈베리 파이 카메라로 객체 분할하기

.. image:: ../../images/obk_seg2.png


-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # 프로세스 종료하기
    kill_command_segment = 'bash ~/ai_example/kill.sh camera'
    subprocess.call((kill_command_segment.split('\n')), shell=True)

-   프로세스 종료하기