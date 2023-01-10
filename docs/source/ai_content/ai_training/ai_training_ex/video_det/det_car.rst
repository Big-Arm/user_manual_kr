==================
자동차 검출하기
==================

-   2-1. 영상에서 자동차 객체 검출.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/ai_training/detcar1.png


.. code-block:: python

    import subprocess

-   subprocess 모듈 가져오기


.. code-block:: python

    #원본 동영상 확인하기
    run_command_before = 'bash ~/ai_example/show.sh car before'
    subprocess.call((run_command_before.split('\n')), shell=True)


-   원본 동영상 확인하기

.. thumbnail:: /_images/ai_training/detcar2.png


-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # 프로세스 종료하기
    kill_command_before = 'bash ~/ai_example/kill.sh display'
    subprocess.call((kill_command_before.split('\n')), shell=True)


-   프로세스 종료하기

.. code-block:: python

    # 객체 검출하기
    detect_command_car = 'bash ~/ai_example/detect.sh car'
    subprocess.call((detect_command_car.split('\n')), shell=True)

-   객체 검출하기


.. code-block:: python

    # 검출 동영상 확인하기
    run_command_after = 'bash ~/ai_example/show.sh car after'
    subprocess.call((run_command_after.split('\n')), shell=True)

-   검출 동영상 확인하기

.. thumbnail:: /_images/ai_training/detcar3.png

-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # terminating the process
    kill_command_after = 'bash ~/ai_example/kill.sh display'
    subprocess.call((kill_command_after.split('\n')), shell=True)

-   프로세스 종료하기