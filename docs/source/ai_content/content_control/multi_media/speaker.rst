============
스피커
============


-   01_sound.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/mul1.png


.. code-block:: python

    import rospy
    from std_msgs.msg import Int32MultiArray

-   rospy 모듈 가져오기
-   std_msgs.msg 모듈에서 Int32MultiArray 가져오기




.. code-block:: python

    sound = Int32MultiArray()


-   sound 변수를 Int32MultiArray() Message Type으로 지정

.. code-block:: python

    def play(number):
        sound.data=[1,number]


-   play(number) 함수 생성
-   sound Message의 data를 [1,number] 형식으로 지정

.. code-block:: python

    def sounds():
        sound_pub = rospy.Publisher('robot_sound',Int32MultiArray, queue_size=1)
        try:
            number = input("0~9 까지 중 골라주세요")
            play(number)
            sound_pub.publish(sound)
            rospy.sleep(2)
        except Exception as ex:
            print(ex)

        
    def start_node():
        rospy.init_node('zetabot')
        while True:
            sounds()
        rospy.spin()
    try:
        start_node()
    except rospy.ROSInterruptException as err:
        print(err)


-   sounds() 함수 생성
-   robot_sound Topic Publisher 생성
-   number 변수에 사용자 입력 받기
-   play(number) 함수 실행
-   sound Message Publish
-   2초간 시간 지연 및 예외처리
-   start_node() 함수 생성
-   zetabot Node 생성
-   sounds() 함수 실행
-   start_node() 함수 실행 및 예외처리