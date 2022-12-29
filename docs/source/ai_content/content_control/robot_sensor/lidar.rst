=====
LIDAR
=====

-   04_scan.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/sensor5.png


.. code-block:: python

    import rospy
    from sensor_msgs.msg import LaserScan

-   rospy 모듈 가져오기
-   sensor_msgs.msg 모듈에서 LaserScan 가져오기




.. code-block:: python

    def process_scan(msg):
        rospy.loginfo("data: {}".format(msg))

    def start_node():
        rospy.init_node('zetabot')
        rospy.Subscriber("scan", LaserScan, process_scan)
        rospy.spin()

    try:
        start_node()
    except rospy.ROSInterruptException as err:
        print(err)


-   zetabot Node 생성
-   scan Topic Subscribe 및 Message 확인
