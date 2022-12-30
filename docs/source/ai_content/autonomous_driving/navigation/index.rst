==============================
Navigation setting for Zetabot
==============================

- 제타봇 네비게이션 및 조작 설명입니다.

Mapping 실전
-----------------

매핑에 대한 설명입니다.


1.  제타봇의 전원 스위치를 켭니다.
    
    .. image:: ../images/turnonzeta.jpg

2.  Mapping 버튼을 클릭합니다.
    
    .. image:: ../images/clickmapping.jpg

3.  제타봇을 움직여서 매핑을 시도합니다. 빨간색으로 측정되어있는 부분이 라이다에서 측정된 데이터들입니다.
    검은색은 SLAM 알고리즘을 통하여 라이다가 측정한 벽입니다.
    
    .. image:: ../images/mapping.jpg

4.  제타봇 조이스틱 조작

    .. image:: ../images/controller.png
    
    1. 전원을 켭니다.
    2. 조이스틱에 진동이 오면 제타봇과 조이스틱이 연결되었다는 신호입니다.
    3. 엑셀(LB)버튼을 누르고 왼쪽 조이스틱을 사용하여 핸들링을 합시
    4. LT버튼을 누르고 오른쪽 조이스틱을 사용하여 제타봇을 회전시킵시다.

|
|
|

Navigation 실전
--------------------

1.  Mapping이 끝났다면 Navigation 버튼을 클릭합니다.

    .. image:: ../images/nav_1.jpg

2.  2D Pose Estimate로 로컬라이제이션을 실행합니다.

    이때 라이다상에서 초록색으로 측정이 된 장애물과 맵상의 장애물이 어느정도 일치하는게 좋습니다. 

    .. image:: ../images/nav_2.jpg

    .. image:: ../images/nav_3.jpg

3.  2D Nav Goal을 클릭하여 목표를 정하게 되면 자율주행 세팅은 끝이 납니다.

    .. image:: ../images/nav_4.jpg

.. toctree:: 
    :hidden:

    Mapping 실전
    Navigation 실전