==================
강아지 검출하기
==================

-   2-3. 영상에서 강아지 객체 검출.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/ai_training/detdog1.webp


.. code-block:: python

    import subprocess

-   subprocess 모듈 가져오기


.. code-block:: python

    # 원본 동영상 확인하기
    run_command_before = 'bash ~/ai_example/show.sh dog before'
    subprocess.call((run_command_before.split('\n')), shell=True)


-   원본 동영상 확인하기

.. thumbnail:: /_images/ai_training/detdog2.webp


-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # 프로세스 종료하기
    kill_command_before = 'bash ~/ai_example/kill.sh display'
    subprocess.call((kill_command_before.split('\n')), shell=True)


-   프로세스 종료하기

.. code-block:: python

    # 객체 검출하기
    detect_command_dog = 'bash ~/ai_example/detect.sh dog'
    subprocess.call((detect_command_dog.split('\n')), shell=True)

-   객체 검출하기


.. code-block:: python

    # 검출 동영상 확인하기
    run_command_after = 'bash ~/ai_example/show.sh dog after'
    subprocess.call((run_command_after.split('\n')), shell=True)


-   검출 동영상 확인하기

.. thumbnail:: /_images/ai_training/detdog3.webp

-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # 프로세스 종료하기
    kill_command_after = 'bash ~/ai_example/kill.sh display'
    subprocess.call((kill_command_after.split('\n')), shell=True)

-   프로세스 종료하기