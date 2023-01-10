====================
ROS Topic Subscriber
====================

-   01_02_ros_topic_subscriber.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/comm2.webp

.. code-block:: python

    import rospy
    from std_msgs.msg import String

-   rospy 모듈 가져오기
-   std_msgs.msg 모듈에서 String 가져오기

.. code-block:: python

    def callback(data):
        rospy.loginfo(rospy.get_caller_id() + "I heard %s", data.data)

-   callback() 함수 생성
-   Node id 및 Message data 출력

.. code-block:: python

    def listener():
        rospy.init_node('listener', anonymous=True)
        rospy.Subscriber("chatter", String, callback)
        rospy.spin()

-   listener 함수 생성
-   listener Node 생성
-   chatter Topic의 Message를 Subscribe
-   Subscriber Callback 처리

.. code-block:: python

    listener()

-   listener 함수 실행
