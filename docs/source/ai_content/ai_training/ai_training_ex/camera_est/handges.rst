========================
손 포즈 추정하기
========================


-   6. 카메라로 손 포즈 추정.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../../images/hand1.png


.. code-block:: python

    import subprocess

-   subprocess 모듈 가져오기


.. code-block:: python

    # 라즈베리 파이 카메라로 손 포즈 추정하기
    detect_command_pose = 'bash ~/ai_example/detect.sh cam_pose'
    subprocess.call((detect_command_pose.split('\n')), shell=True)


-   라즈베리 파이 카메라로 손 포즈 추정하기

.. image:: ../../images/hand2.png


-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # 프로세스 종료하기
    kill_command_pose = 'bash ~/ai_example/kill.sh camera'
    subprocess.call((kill_command_pose.split('\n')), shell=True)

-   프로세스 종료하기