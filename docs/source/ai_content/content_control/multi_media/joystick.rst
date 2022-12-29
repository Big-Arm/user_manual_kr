==================
조이스틱 진동
==================


-   02_rumble.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. image:: ../images/mul2.png


.. code-block:: python

    # 로봇 조작을 하고 진동모듈을 실행하면 진행이 되지 않음    import rospy
    from std_msgs.msg import Int32MultiArray

-   rospy 모듈 가져오기
-   std_msgs.msg 모듈에서 Int32MultiArray 가져오기




.. code-block:: python

    rumble = Int32MultiArray()


-   rumble 변수를 Int32MultiArray() Message Type으로 지정

.. code-block:: python

    def play(number):
        if number == 1:
            rumble.data=[1,250]
        elif number == 2:
            rumble.data=[1,500]
        elif number == 3:
            rumble.data=[1,1000]
        elif number == 4:
            rumble.data=[1,2000]
        else:
            print("유효하지 않은 숫자 및 문자입니다.")


-   play(number) 함수 생성
-   number에 따라 rumble Message의 data를 [1, 숫자] 형식으로 지정

.. code-block:: python

    def rumbles():
        rumble_pub = rospy.Publisher('ds4_vibration',Int32MultiArray, queue_size=1)
        try:
            number = input("1~4 까지 중 골라주세요 선택되어지는 번호에 따라 진동울리는 시간이 다릅니다")
            play(number)
            rumble_pub.publish(rumble)
            rospy.sleep(2)
        except Exception as ex:
            print(ex)

        
    def start_node():
        rospy.init_node('zetabot')
        while True:
            rumbles()
        rospy.spin()
    try:
        start_node()
    except rospy.ROSInterruptException as err:
        print(err)


-   rumbles() 함수 생성
-   ds4_vibration Topic Publisher 생성
-   number 변수에 사용자 입력 받기
-   play(number) 함수 실행
-   rumble Message Publish
-   2초간 시간 지연 및 예외처리
-   start_node() 함수 생성
-   zetabot Node 생성
-   rumbles() 함수 실행
-   start_node() 함수 실행 및 예외처리