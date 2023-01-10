===
IMU
===

-   01_imu.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/sensor1.webp


.. code-block:: python

    import rospy
    from sensor_msgs.msg import Imu
    from tf.transformations import quaternion_from_euler

-   rospy 모듈 가져오기
-   sensor_msgs.msg 모듈에서 Imu 가져오기
-   tf.transformations 모듈에서 quaternion_from_euler 가져오기




.. code-block:: python

    def process_imu(msg):
        rospy.loginfo("x: {},y: {},z: {},w: {}".format(msg.orientation.x, msg.orientation.y, msg.orientation.z, msg.orientation.w))

    def start_node():
        rospy.init_node('zetabot')
        rospy.Subscriber("imu", Imu, process_imu)
        rospy.spin()

    try:
        start_node()
    except rospy.ROSInterruptException as err:
        print(err)


-   zetabot Node 생성
-   imu Topic Subscribe
-   Message를 x, y, z, w값으로 나누어 확인