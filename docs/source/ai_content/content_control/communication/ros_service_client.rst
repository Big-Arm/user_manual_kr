==================
ROS Service Client
==================


-   02_02_ros_service_client.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/comm12.png

.. thumbnail:: /_images/content_control/comm13.png

.. code-block:: python

    from __future__ import print_function
    import sys
    import rospy
    from rospy_tutorials.srv import *
    
-   Python3 호환을 위한__future__ 모듈에서 print_function 가져오기
-   sys 모듈 가져오기
-   rospy_tutorials.srv 모듈 가져오기
-   rospy 모듈 가져오기



.. code-block:: python

    def add_two_ints_client(x, y):
        rospy.wait_for_service('add_two_ints')
        try:
            add_two_ints = rospy.ServiceProxy('add_two_ints', AddTwoInts)
            resp1 = add_two_ints(x, y)
            return resp1.sum
        except rospy.ServiceException as e:
            print("Service call failed: %s"%e)

-   add_two_ints_client() 함수 생성
-   add_two_ints ServiceProxy 생성
-   add_two_ints Service 결과 가져오기
-   예외처리

.. code-block:: python

    def usage():
        return "%s [x y]"%sys.argv[0]

.. code-block:: python

    input_num = input("숫자 두 개를 입력하세요(ex: a,b) : ")
    x = int(input_num[0])
    y = int(input_num[1])
    print("Requesting %s+%s"%(x, y))
    print("%s + %s = %s"%(x, y, add_two_ints_client(x, y)))

-   사용자 입력 x, y 받기
-   Service 결과 출력
