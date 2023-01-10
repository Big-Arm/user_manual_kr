==========================
처리지연 Publisher
==========================


-   1_1_처리지연_sender.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/conv1.png


.. code-block:: python

    import rospy
    from std_msgs.msg import Int32

-   rospy 모듈 가져오기
-   std_msgs.msg 모듈의 Int32 가져오기


.. code-block:: python

    rospy.init_node('Sender', anonymous=False)
    pub = rospy.Publisher('increase_num', Int32, queue_size=1)
    rate = rospy.Rate(1000) # Generate a topic by incrementing the number by 1 1000 times per second


-   Sender Node 생성
-   increase_num Topic Publish
-   1000hz의 rate(1초에 1000번 실행)를 가지도록 설정

.. code-block:: python

    cnt = 1

-   변수 cnt를 1로 지정

.. code-block:: python

    while not rospy.is_shutdown():
        pub.publish(cnt)
        cnt += 1
        rate.sleep()
    rospy.spin()

-   rospy가 실행 상태일 때, cnt Message를 Publish하고, cnt값을 1씩 증가시키도록 설정