====================
타임슬롯 Subscriber
====================

-   2_2_타임슬롯_receiver.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/conv4.png


.. code-block:: python

    2_2_타임슬롯_receiver.ipynb

-   rospy 모듈 가져오기
-   std_msgs.msg 모듈의 String, Int32 가져오기


.. code-block:: python

    def callback(msg):
        pass

-   callback() 함수 생성


.. code-block:: python

    rospy.init_node('Receiver')
    sub = rospy.Subscriber('my_topic',Int32, callback)
    rospy.spin()

-   Receiver Node 생성
-   my_topic Topic Subscriber 생성
