===================
타임슬롯 Publisher
===================

-   2_1_타임슬롯_sender.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/conv3.png


.. code-block:: python

    import rospy
    from std_msgs.msg import Int32
    import time

-   rospy 모듈 가져오기
-   std_msgs.msg 모듈의 Int32 가져오기
-   time 모듈 가져오기


.. code-block:: python

    rospy.init_node( 'Sender', anonymous=False)
    pub = rospy.Publisher('my_topic', Int32, queue_size=0)

-   Sender Node 생성
-   my_topic Topic Publish


.. code-block:: python

    def do_job(num):
        for i in range(num):
            i += 1
            pub.publish(i)

-   do_job(num) 함수 생성
-   i가 num이 될 때 까지 i에 일을 더하고, Message i를 Publish함

.. code-block:: python

    print("")
    r = input('Rate: ') #타임 슬롯 하나의 크기를 얼마나 할 것인가. = (1/r) 초
    num = input('Num: ') #몇 개를 보낼 것인가 = (1/r) 초당 보낼 데이터 수
    print("")

    rate = rospy.Rate(r)
    elapsed_total = 0

    for _ in range(r):
        start_send = rospy.get_time()
        do_job(num)
        end_send = rospy.get_time()
        elapsed_sending = end_send - start_send

        start_sleep = rospy.get_time()
        rate.sleep()
        end_sleep = rospy.get_time()
        elapsed_sleep = end_sleep - start_sleep
        
        print(" Send: %.5f sec" % elapsed_sending)
        print("Sleep: %.5f sec" % elapsed_sleep)
        print("Total: %.5f sec\n" % (elapsed_sending + elapsed_sleep))
        
        elapsed_total += (elapsed_sending + elapsed_sleep)

    print("\n------------- [Report]--------------")
    print("It took %.5f seconds to send data" % elapsed_total)
    print("-------------------------------------")


-   사용자 입력으로 r과 num을 지정
-   rate를 r로 지정
-   elapsed_total 변수를 0으로 지정
-   for문을 r번간 실행

    -   start_send 변수를 현재 Timestamp로 지정
    -   do_job(num) 함수 실행
    -   start_send 변수를 현재 Timestamp로 지정
    -   elapsed_sending 변수를 end_send - start_send로 지정
    -   start_sleep 변수를 현재 Timestamp로 지정
    -   rate 동안 시간 지연
    -   end_sleep 변수를 현재 Timestamp로 지정
    -   elapsed_sleep 변수를 end_sleep - start_sleep으로 지정
    -   elapsed_sending, elapsed_sleep, (elapsed_sending + elapsed_sleep) 출력
    -   elapsed_total에 (elapsed_sending + elapsed_sleep)을 더함
-   elapsed_total 출력

    -   1/r초에 num의 갯수만큼의 data를 보낸 뒤 rate 및 sleep, data를 보낸 총 시간
    -   1/r초간 보내야 하는 data의 수가 많아질 수록 sleep이 줄어듦
