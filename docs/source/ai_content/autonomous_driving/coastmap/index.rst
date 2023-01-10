=======================
Global / Local Coastmap
=======================

-   01_costmap_dy_rc.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/autonomous_driving/global.png

.. code-block:: python

    import rospy
    import dynamic_reconfigure.client

-   rospy 모듈 가져오기
-   dynamic_reconfigure.client 모듈 가져오기

.. code-block:: python

    class Param(object):
        def __init__(self):
            self.timer = rospy.Timer(rospy.Duration(1), self.call_back)
            self.client1 = dynamic_reconfigure.client.Client("/move_base/global_costmap/",timeout=30)
            self.client2 = dynamic_reconfigure.client.Client("/move_base/local_costmap/",timeout=30)

        def call_back(self, timer):
            self.client1.update_configuration({"footprint": [], "robot_radius": 0.2})
            self.client2.update_configuration({"footprint": [], "robot_radius": 0.2})
            self.timer.shutdown()
            rospy.signal_shut down("")

-   Param(object) Class 생성
-   **init**(self) 함수 생성
-   ROS timer 생성 및 Callback 지정
-   client1 생성 후 dynamic_reconfigure Client에 move_base Node의 global_costmap 지정
-   client2 생성 후 dynamic_reconfigure Client에 move_base Node의 local_costmap 지정
-   call_back(self, timer) 함수 생성
-   client1의 Parameter를 {"footprint": [], "robot_radius": 0.2}로 Update
-   client2의 Parameter를 {"footprint": [], "robot_radius": 0.2}로 Update
-   Timer 및 ROS 종료

.. code-block:: python

    rospy.init_node('costmap_dy_rc', anonymous=True)
    param = Param()
    rospy.spin()


-   costmap_dy_rc Node 생성
-   param 변수에 Param() Class 지정