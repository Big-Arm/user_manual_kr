====================================
로봇팔로 얼굴 추적하기
====================================

-   05_07_face_follow
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/face1.png

-   로봇팔 카메라를 이용한 얼굴 인식 밎 추적
-   Import head file

.. code-block:: python

    import cv2 as cv
    import threading
    from time import sleep
    import ipywidgets as widgets
    from IPython.display import display
    from face_follow import face_follow

-   Initialize DOFBOT position


.. code-block:: python

    import Arm_Lib
    Arm = Arm_Lib.Arm_Device()
    joints_0 = [90, 150, 20, 20, 90, 30]
    Arm.Arm_serial_servo_write6_array(joints_0, 1500)

-   Create the instance and initialize the parameters

.. code-block:: python

    follow = face_follow()

    model = 'General'===============

-   Creating controls

.. code-block:: python

    button_layout = widgets.Layout(width='250px', height='50px', align_self='center')
    output = widgets.Output()

    exit_button = widgets.Button(description='Exit', button_style='danger', layout=button_layout)

    imgbox = widgets.Image(format='jpg', height=480, width=640, layout=widgets.Layout(align_self='center'))

    controls_box = widgets.VBox([imgbox, exit_button], layout=widgets.Layout(align_self='center'))
    # ['auto', 'flex-start', 'flex-end', 'center', 'baseline', 'stretch', 'inherit', 'initial', 'unset']


-   Controls

.. code-block:: python

    def exit_button_Callback(value):
        global model
        model = 'Exit'
    #     with output: print(model)
    exit_button.on_click(exit_button_Callback)

-   Main Process

.. code-block:: python

    def camera():
        global model
        # Open camera
        capture = cv.VideoCapture(1)
        # Be executed in loop when the camera is opened normally 
        while capture.isOpened():
            try:

                _, img = capture.read()

                img = cv.resize(img, (640, 480))
                img = follow.follow_function(img)
                if model == 'Exit':
                    cv.destroyAllWindows()
                    capture.release()
                    break
                imgbox.value = cv.imencode('.jpg', img)[1].tobytes()
            except KeyboardInterrupt:capture.release()


-   Start
.. code-block:: python

    display(controls_box,output)
    threading.Thread(target=camera, ).start()