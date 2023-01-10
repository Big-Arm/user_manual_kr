====================
파란색 인식
====================

-   01_color_blue.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/ai_training/rob_ai_1.webp


.. code-block:: python

    import rospy
    from sensor_msgs.msg import Image
    from cv_bridge import CvBridge, CvBridgeError
    import numpy as np
    import cv2
    import ipywidgets.widgets as widgets

-   python 모듈 가져오기



.. code-block:: python

    def get_color(img):
        H = []
        color_name={}
        
        img = cv2.resize(img, (640, 480), )

        HSV = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)

        cv2.rectangle(img, (280, 180), (360, 260), (0, 255, 0), 2)
        
        # 각각의 행열의 H,S,V 값을 차례로 리스트에 추가
        for i in range(280, 360):
            for j in range(180, 260): H.append(HSV[j, i][0])
        #Calculate the maximum and minimum of H, S, and V respectively
        # H, S, V의 최대값과 최소값을 각각 계산합니다.
        H_min = min(H);H_max = max(H)
        #Judging the color
        if H_min >= 0 and H_max <= 20 or H_min >= 156 and H_max <= 180:
            color_name['name'] = 'blue'

        else:
            color_name['name'] = 'none'
        return img, color_name


-   get_color(img) 함수 생성
-   list H, dictionary color_name 생성
-   이미지 크기를 640x480 크기로 조정
-   이미지 색공간을 RGB에서 HSV로 변환
-   초록색 (0, 255, 0) 사각형을 2의 두께로 시작점(280, 180), 끝점 (60, 260) 위치에 생성
-   초록색 사각형의 범위에서(for i ~, for j ~) list H에 hsv값 추가
-   H_min에 가장 작은 list H값, H_max에 가장 큰 list H값으로 지정
-   h값이 0 ~ 20이거나, 156 ~ 180일 경우

    -   color_name['name'] 을 'blue'로 지정

-   이외의 경우

    -   color_name['name'] 을 'none'으로 지정

-   img, color_name 반환

.. code-block:: python

    def rgb8_to_jpeg(value, quality=75):
        return bytes(cv2.imencode('.jpg',value)[1].tostring())


-   rgb8_to_jpeg(value, quality=75) 함수 생성
-   cv2 이미지를 jpg 형식으로 인코딩한 뒤, 이를 byte형식으로 반환

.. code-block:: python

    origin_widget = widgets.Image(format='jpeg', width=320, height=240)
    result_widget = widgets.Image(format='jpeg',width=320, height=240)


    image_container = widgets.HBox([origin_widget, result_widget])
    display(image_container)


-   영상 이미지를 비교할 위젯 생성 및 출력


.. code-block:: python

    bridge = CvBridge()

    color_lower = np.array([0, 43, 46])
    color_upper = np.array([10, 255, 255])


    def process_image(msg):
        try:
            cv_img = bridge.imgmsg_to_cv2(msg, "bgr8")
        except CvBridgeError as e:
            print(e)
        else:
            frame, color_name = get_color(cv_img)
            if len(color_name)==1:
                print ("color_name :", color_name)
                print ("name :", color_name['name'])
        
            origin_widget.value = rgb8_to_jpeg(cv_img)
            # change to hsv model
            hsv = cv2.cvtColor(cv_img, cv2.COLOR_RGB2HSV)
            mask = cv2.inRange(hsv, color_lower, color_upper)

            res = cv2.bitwise_and(frame, frame, mask=mask)
            result_widget.value = rgb8_to_jpeg(res)
            rospy.sleep(0.25)
            
    def start_node():
        rospy.init_node('zetabot')
        rospy.Subscriber("/main_camera/raw", Image, process_image)
        rospy.spin()

    try:
        start_node()
    except rospy.ROSInterruptException as err:
        print(err)

-   ROS cv_bridge 생성
-   color_lower 및 color_upper 생성 및 지정
-   process_image(msg) 함수 생성 및 예외처리
-   ROS Image Message Type을 bgr8 형식으로 변환
-   get_color() 함수 실행 후, 색상 이름 출력
-   위젯에 원본 이미지와 get_color() 처리한 이미지 넣기
-   start_node() 함수 생성
-   zetabot Node 생성
-   main_camera/raw Topic을Subscribe하여 process_image() Callback 함수로 전달
-   start_node() 함수 실행 및 예외처리