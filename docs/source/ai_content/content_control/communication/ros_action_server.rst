==================
ROS Action Server
==================


-   03_01_ros_action_server.ipynb
-   | 셀 실행시키기
    | `Ctrl + Enter`

.. thumbnail:: /_images/content_control/comm14.png

.. thumbnail:: /_images/content_control/comm15.png

.. code-block:: python

    import rospy
    import actionlib
    import actionlib_tutorials.msg
        
-   rospy 모듈 가져오기
-   actionlib 및 actionlib_tutorials.msg 모듈 가져오기


.. code-block:: python

    class FibonacciAction(object):
        # feedback과 result를 publish에 사용하기 위한 메시지 생성
        _feedback = actionlib_tutorials.msg.FibonacciFeedback()
        _result = actionlib_tutorials.msg.FibonacciResult()

        def __init__(self, name):
            self._action_name = name
            self._as = actionlib.SimpleActionServer(self._action_name, actionlib_tutorials.msg.FibonacciAction, execute_cb=self.execute_cb, auto_start = False)
            self._as.start()
            
        def execute_cb(self, goal):
            r = rospy.Rate(1)
            success = True
            
            # 피보나치 수열의 시작점을 추가
            self._feedback.sequence = []
            self._feedback.sequence.append(0)
            self._feedback.sequence.append(1)

            # 사용자들을 위한 콘솔의 publish 정보
            rospy.loginfo('%s: Executing, creating fibonacci sequence of order %i with seeds %i, %i' % (self._action_name, goal.order, self._feedback.sequence[0], self._feedback.sequence[1]))
            
            # 액션 실행 시작
            for i in range(1, goal.order):
                # client에서 요청이 없는지 체크
                if self._as.is_preempt_requested():
                    rospy.loginfo('%s: Preempted' % self._action_name)
                    self._as.set_preempted()
                    success = False
                    break
                self._feedback.sequence.append(self._feedback.sequence[i] + self._feedback.sequence[i-1])
                # feedback을 publish
                self._as.publish_feedback(self._feedback)
                r.sleep()
                
            if success:
                self._result.sequence = self._feedback.sequence
                rospy.loginfo('%s: Succeeded' % self._action_name)
                self._as.set_succeeded(self._result)

-   피보나치 연산
-   참조 :

    `<http://wiki.ros.org/actionlib_tutorials/Tutorials/Writing%20a%20Simple%20Action%20Server%20using%20the%20Execute%20Callback%20(Python)>`_
    

.. code-block:: python

    rospy.init_node('fibonacci')
    server = FibonacciAction(rospy.get_name())
    rospy.spin()


-   피보나치 연산을 위한 fibonacci Action Node 실행
-   피보나치 연산 후 성공 결과 출력