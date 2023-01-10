=================
ROS Action Client
=================


-   03_02_ros_action_client.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/comm16.png


.. code-block:: python

    import rospy
    from __future__ import print_function
    import actionlib
    import actionlib_tutorials.msg
        
-   rospy 모듈 가져오기
-   Python3 호환을 위한__future__ 모듈에서 print_function 가져오기
-   actionlib 및 actionlib_tutorials.msg 모듈 가져오기


.. code-block:: python

    def fibonacci_client():
    # SimpleActionClient를 생성, action의 타입을 전달
    client = actionlib.SimpleActionClient('fibonacci', actionlib_tutorials.msg.FibonacciAction)

    # action server를 확인하고 시작 될 때 까지 기다림
    # 목표를 받음
    client.wait_for_server()

    # action 서버에 보낼 목표를 생성
    goal = actionlib_tutorials.msg.FibonacciGoal(order=20)

    # action 서버에 목표를 보냄
    client.send_goal(goal)

    #서버가 action을 수행할 때 까지 기다림
    client.wait_for_result()

    # action의 결과를 출력
    return client.get_result()  # A FibonacciResult

-   fibonacci_client() 함수 생성


.. code-block:: python

    try:
    # SimpleActionClient가 ROS를 통해 publish 및 subscribe 할 수 있도록 Rospy 노드를 초기화 및 생성한다.
        rospy.init_node('fibonacci_client_py')
        result = fibonacci_client()
        print("Result:", ', '.join([str(n) for n in result.sequence]))
    except rospy.ROSInterruptException:
        print("program interrupted before completion", file=sys.stderr)


-   fibonacci_client_py Action Node 생성
-   연산값 출력