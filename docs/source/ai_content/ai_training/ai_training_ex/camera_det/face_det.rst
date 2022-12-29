================
얼굴 검출하기
================

-   3-2. 카메라로 얼굴 객체 검출.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../../images/det_face1.png


.. code-block:: python

    import subprocess

-   subprocess 모듈 가져오기


.. code-block:: python

    # 라즈베리 파이 카메라로 얼굴 인식하기
    detect_command_face = 'bash ~/ai_example/detect.sh cam_face'
    subprocess.call((detect_command_face.split('\n')), shell=True)


-   라즈베리 파이 카메라로 얼굴 인식하기

.. image:: ../../images/det_face3.png


-   Jetson Nano에서 실행된 모습


.. code-block:: python

    # 프로세스 종료하기
    kill_command_face = 'bash ~/ai_example/kill.sh camera'
    subprocess.call((kill_command_face.split('\n')), shell=True)


-   프로세스 종료하기
