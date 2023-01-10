======================================
깊이 (Depth) 추정하기
======================================


-   5. 카메라로 깊이 추정.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/ai_training/dept_est1.png


.. code-block:: python

    import subprocess

-   subprocess 모듈 가져오기


.. code-block:: python

    # 라즈베리 파이 카메라로 depth 추정하기
    detect_command_depth = 'bash ~/ai_example/detect.sh cam_depth'
    subprocess.call((detect_command_depth.split('\n')), shell=True)


-   라즈베리 파이 카메라로 depth 추정하기

.. thumbnail:: /_images/ai_training/dept_est2.png


-   Jetson Nano에서 실행된 모습

.. code-block:: python

    # 프로세스 종료하기
    kill_command_depth = 'bash ~/ai_example/kill.sh camera'
    subprocess.call((kill_command_depth.split('\n')), shell=True)
    
-   프로세스 종료하기