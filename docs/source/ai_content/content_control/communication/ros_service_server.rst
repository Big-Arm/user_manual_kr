==================
ROS Service Server
==================


-   02_01_ros_service_server.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/comm10.webp

.. image:: ../images/comm11.webp

.. code-block:: python

    from __future__ import print_function
    from rospy_tutorials.srv import AddTwoInts,AddTwoIntsResponse
    import rospy
    
-   Python3 호환을 위한__future__ 모듈에서 print_function 가져오기
-   rospy_tutorials.srv 모듈에서 AddTwoInts, AddTwoIntsResponse 가져오기
-   rospy 모듈 가져오기

.. code-block:: python

    def handle_add_two_ints(req):
        print("Returning [%s + %s = %s]"%(req.a, req.b, (req.a + req.b)))
        return AddTwoIntsResponse(req.a + req.b)

-   handle_add_two_ints() 함수 생성
-   req.a, req.b, req.a + req.b 출력
-   AddTwoIntsResponse에 req.a + req.b 인스턴스 반환

.. code-block:: python

    def add_two_ints_server():
        rospy.init_node('add_two_ints_server')
        s = rospy.Service('add_two_ints', AddTwoInts, handle_add_two_ints)
        print("Ready to add two ints.")
        rospy.spin()

-   add_two_ints_server() 함수 생성
-   add_two_ints_server Node 생성
-   add_two_ints Service 생성

.. code-block:: python

    add_two_ints_server()

-   add_two_ints_server() 함수 실행
