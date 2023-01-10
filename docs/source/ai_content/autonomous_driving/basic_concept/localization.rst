===================
Localization & AMCL
===================

Localization이란? 
---------------------

.. thumbnail:: /_images/autonomous_driving/localization.webp



| 앞서 지도를 만들었다면 우리는 **현재 위치가 어디에 있느냐를 알아야** 지도를 보고 여행을 즐길 수가 있습니다.
| 이렇듯 로봇 또한 매핑에 성공을 했다면 기본적으로 자신의 위치가 어디에 있느냐를 파악을 해야 합니다. 
| 위의 일련의 과정들을 우리는 **Localization** 이라고 합니다.

|
|
| Ex)
|

.. thumbnail:: /_images/autonomous_driving/localization_ex.png

제타봇의 Rviz를 띄우고 2D Pose Estimate를 누르고 방향을 조절하면 로봇의 레이저 값과 맵의 공간이 어느정도 일치하는게 보일것입니다.

이렇게 로봇이 어느 위치에 있는지를 추정하는 과정 Localization입니다.


AMCL(Adaptive Monte Carlo Localization)
---------------------------------------

**AMCL**이란 위의 **Localization**을 하기 위한 전반적인 알고리즘을 일컫는 말입니다. 
|
위의 그림에서 빨간색 화살표들이 보일텐데 이러한 **경로 예측들을 파티클(Particle)이라고** 부릅니다. 
그리고 로봇을 움직이면 움직일수록 이러한 파티클들이 로봇주위에 가깝게 뭉쳐지는 현상을 볼 수 있습니다. 
왜냐하면 움직일수록 위치가 어디인지 확실하게 알기 때문입니다. 이때 사용되는 위치추적 알고리즘을 우리는 AMCL이라고 부릅니다.
|
|
다음은 AMCL의 성능을 좌지우지하는 Parameter에 대한 설명입니다.

-   **min_particles (default: 100)**: 파티클 필터에서 사용할 최소 파티클 수 입니다.
-   **max_particles (default: 5000)**: 파티클 필터에서 사용할 최대 파티클 수 입니다.
-   **kld_err (default: 0.01)**: 실제 분포와 추정 분포 사이의 최대 오차를 설정합니다.
-   **update_min_d (default: 0.2)**: 필터 업데이트를 위해 로봇이 움직여야 할 최소한의 linear distance입니다(미터 단위).
-   **update_min_a (default: π/6.0)**: 필터 업데이트를 위해 로봇이 움직여야 할 최소한의 angular distance입니다(라디안 단위).
-   **resample_interval (default: 2)**: 리샘플링 되기 이전에 파티클 필터를 업데이트하는 횟수를 정합니다.
-   **transform_tolerance (default: 0.1)**: 이 변환이 publish된 후 언제까지 유효한지를 나타내는 시간을 정합니다(초 단위).
-   **gui_publish_rate (default: -1.0)**: 시각화를 위해 각각의 스캔과 경로가 표시될 시간을 정합니다(헤르츠 단위) -1.0이면 해당 기능을 비활성화 합니다.