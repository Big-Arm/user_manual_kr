=================
로봇 구동
=================


-   01_wheel.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/autonomous_driving/robot_drive1.png

.. thumbnail:: /_images/autonomous_driving/robot_drive2.png

.. code-block:: python

    import rospy
    import json
    from std_msgs.msg import String
    import time
    import math

-   python 모듈 가져오기

.. code-block:: python

    pub = rospy.Publisher('/robot_command', String, queue_size=1)
    rospy.init_node('zetabot', anonymous=True)
    time.sleep(1)

-   zetabot Node 생성
-   robot_command Topic Publisher 생성

.. code-block:: python

    def move():
        tmp = {"MoveForward": 1}
        msg = json.dumps(tmp)
        rospy.loginfo("Sent: %s", msg)
        pub.publish(msg)


-   move() 함수 생성
-   {"MoveForward": 1}을 Json 문자열로 변환
-   변환한 Message를 Publish


.. code-block:: python

    def stop():
        tmp = {"Stop": 0}
        msg = json.dumps(tmp)
        rospy.loginfo("Sent: %s", msg)
        pub.publish(msg)

-   stop() 함수 생성
-   {"Stop": 0}을 Json 문자열로 변환
-   변환한 Message를 Publish

.. code-block:: python 

    def moveTo():
        tmp = {"MoveDelta": -0.5}
        msg = json.dumps(tmp)
        rospy.loginfo("Sent: %s", msg)
        pub.publish(msg)

-   moveTo() 함수 생성
-   {"MoveDelta": -0.5}을 Json 문자열로 변환
-   변환한 Message를 Publish

.. code-block:: python 

    def moveTo(distance):
        tmp = {"MoveDelta": distance}
        msg = json.dumps(tmp)
        rospy.loginfo("Sent: %s", msg)
        pub.publish(msg)

-   moveTo(distance) 함수 생성
-   {"MoveForward": distance}을 Json 문자열로 변환
-   변환한 Message를 Publish

.. code-block:: python

    def turnTo():
        tmp = {"TurnDelta": math.radians(45)}
        msg = json.dumps(tmp)
        rospy.loginfo("Sent: %s", msg)
        pub.publish(msg)

-   turnTo() 함수 생성
-   45°를 radian으로 변환
-   {"TurnDelta": math.radians(45)}을 Json 문자열로 변환
-   변환한 Message를 Publish
   
.. code-block:: python

    def turnTo(degree):
        tmp = {"TurnDelta": math.radians(int(degree))}
        msg = json.dumps(tmp)
        rospy.loginfo("Sent: %s", msg)
        pub.publish(msg)

-   turnTo(degree) 함수 생성
-   degree(°)를 radian으로 변환
-   radian을 int형으로 변환
-   {"TurnDelta": math.radians(int(degree))}을 Json 문자열로 변환
-   변환한 Message를 Publish

.. code-block:: python

    move()
    time.sleep(2)
    stop()

-   move() 함수 실행
-   2초간 시간 지연
-   stop() 함수 실행

.. code-block:: python

    moveTo(1)

-   moveTo(distance) 함수 실행
-   1 거리 전진

.. code-block:: python

    turnTo(170)
    time.sleep(1)
    stop()

-   turnTo(degree) 함수 실행
-   170도 회전
-   1초간 시간 지연
-   stop() 함수 실행

.. code-block:: python

    turnTo(25)
    time.sleep(1)
    stop()

-   turnTo(degree) 함수 실행
-   25도 회전
-   1초간 시간 지연
-   stop() 함수 실행