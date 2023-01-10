===========================
처리지연 Subscriber
===========================


-   1_2_처리지연_receiver.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/conv2.png


.. code-block:: python

    import rospy
    from std_msgs.msg import Int32

-   rospy 모듈 가져오기
-   std_msgs.msg 모듈의 Int32 가져오기



.. code-block:: python

    rospy.init_node('Receiver')

-   Receiver Node 생성


.. code-block:: python

    pre_num = 0
    cur_num = 0

-   변수 pre_num을 0으로 지정
-   변수 cur_num을 0으로 지정

.. code-block:: python

    def callback(msg):
        global pre_num
        global cur_num
        
        print("Callback is being processed")
        cur_num = msg.data
        rospy.sleep(3)
        
        if (cur_num - pre_num) != 1:
            print_str = "Data: {0:>6}    Missing: {1:6} ~ {2:>6} (  cnt: {3}  )\n"\
            .format(msg.data,pre_num +1, cur_num -1, cur_num - pre_num -1)
        else:
            print_str = "Data: " + str(msgs.data) + "\n"
        
        print(print_str)
        pre_num = cur_num


-   callback(msg) 함수 생성
-   pre_num, cur_num을 전역변수로 선언
-   cur_num을 Message의 data로 지정
-   3초간 시간 지연
-   cur_num - pre_num 이 1이 아닐 경우,

    -   Message data, pre_num + 1, cur_num -1, cur_num - pre_num -1 순서대로 출력
    -   Data : (현재 data) Missing: (누락된 data 최솟값 ~ 누락된 data 최댓값) (cnt: (누락된 data 개수))

-   이외의 경우

    -   Message data 출력

-   pre_num을 cur_num으로 지정

.. code-block:: python

    sub = rospy.Subscriber('increase_num', Int32, callback, queue_size=1)
    rospy.spin()

-   increase_num Topic Subscriber 생성