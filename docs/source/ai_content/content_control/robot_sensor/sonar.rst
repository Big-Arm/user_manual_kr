=====
Sonar
=====

-   02_sonar.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/sensor2.webp
.. image:: ../images/sensor3.webp


.. code-block:: python

    import rospy
    from std_msgs.msg import Float32MultiArray

-   rospy 모듈 가져오기
-   std_msgs.msg 모듈에서 Float32MultiArray 가져오기




.. code-block:: python

    def process_sonar(msg):
        rospy.loginfo("data[0]: {},data[1]: {},data[2]: {},data[3]: {}".format(msg.data[0], msg.data[1], msg.data[2], msg.data[3]))

    def start_node():
        rospy.init_node('zetabot')
        rospy.Subscriber("sonar", Float32MultiArray, process_sonar)
        rospy.spin()

    try:
        start_node()
    except rospy.ROSInterruptException as err:
        print(err)


-   zetabot Node 생성
-   sonar Topic Subscribe
-   Message를 data array 형식으로 확인


.. code-block:: python

    def process_sonar(msg):
        rospy.loginfo("Front: {}, Right: {}, Back: {}, Left: {}".format(msg.data[0], msg.data[1], msg.data[2], msg.data[3]))

    def start_node():
        rospy.init_node('zetabot')
        rospy.Subscriber("sonar", Float32MultiArray, process_sonar)
        rospy.spin()

    try:
        start_node()
    except rospy.ROSInterruptException as err:
        print(err)


-   zetabot Node 생성
-   sonar Topic Subscribe
-   Message를 방향에 따라 확인

