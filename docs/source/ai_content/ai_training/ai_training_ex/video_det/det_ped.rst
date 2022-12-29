=====================
보행자 검출하기
=====================

-   2-2. 영상에서 사람 객체 검출.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../../images/det_ped1.webp


.. code-block:: python

    import subprocess

-   subprocess 모듈 가져오기


.. code-block:: python

    #Check the original video
    run_command_before = 'bash ~/ai_example/show.sh people before'
    subprocess.call((run_command_before.split('\n')), shell=True)


-   원본 동영상 확인하기

.. image:: ../../images/det_ped2.webp


-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # terminating the process
    kill_command_before = 'bash ~/ai_example/kill.sh display'
    subprocess.call((kill_command_before.split('\n')), shell=True)


-   프로세스 종료하기

.. code-block:: python

    # 객체 검출하기
    detect_command_people = 'bash ~/ai_example/detect.sh people'
    subprocess.call((detect_command_people.split('\n')), shell=True)

-   객체 검출하기


.. code-block:: python

    # 검출 동영상 확인하기
    run_command_after = 'bash ~/ai_example/show.sh people after'
    subprocess.call((run_command_after.split('\n')), shell=True)


-   검출 동영상 확인하기

.. image:: ../../images/det_ped3.webp

-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # 프로세스 종료하기
    kill_command_after = 'bash ~/ai_example/kill.sh display'
    subprocess.call((kill_command_after.split('\n')), shell=True)

-   프로세스 종료하기