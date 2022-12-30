======================
ROS 2 (Raspberry)
======================

.. image:: ../images/ros.png


* ROS 2의 특징

  1. 멀티 플랫폼 지원(Linux, macOS, Windows)

     - Windows, macOS, Linux 등 다양한 OS에 설치 가능
  
  2. 실시간 제어 (RTPS, Real Time Publish Subscribe)
  
     - 표준 IP 네트워크에서 best-effort와 reliable publish subscribe 통신 선택 가능

  3. Zeroconf, Protocol Buffers, ZeroMQ, WebSockets 등 다양한 기술 지원
  4. roscore 대신 Dynamic Discovery를 이용한 DDS 미들웨어 사용 

     - ROS Master, Client 구분 없음 

  5. XMLRPC, TCPROS 프로토콜을 이용한 통신
  6. catkin Tool 대신 ament Tool 이용한 빌드 툴 개선

     - CMake 기반의 catkin은 python 패키지 관리 불가능, 단일 워크스페이스에서만 이용 가능

  7. ROS Master의 IP, PORT 대신 별개의 ID를 이용한 보안 취약점 개선

     - IP, PORT가 노출되면 시스템이 공격받을 수 있는 위험 개선