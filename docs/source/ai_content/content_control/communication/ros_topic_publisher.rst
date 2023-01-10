===================
ROS Topic Publisher
===================


-   01_01_ros_topic_publisher.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/comm1.webp

.. code-block:: python

    import rospy
    from std_msgs.msg import String
    
-   rospy 모듈 가져오기
-   std_msgs.msg 모듈에서 String 가져오기

.. code-block:: python

    def talker():
        pub = rospy.Publisher('chatter', String, queue_size=10)
        rospy.init_node('talker', anonymous=True)
        rate = rospy.Rate(10) # 10hz
        while not rospy.is_shutdown():
            hello_str = "hello world %s" % rospy.get_time()
            rospy.loginfo(hello_str)
            pub.publish(hello_str)
            rate.sleep()

-   talker() 함수 생성
-   talker Node 및 chatter Topic 생성
-   "hello world" + ROS Timestamp Message를 Publish

.. code-block:: python

    try:
        talker()
    except rospy.ROSInterruptException:
        pass

-   talker() 함수 실행 및 예외처리