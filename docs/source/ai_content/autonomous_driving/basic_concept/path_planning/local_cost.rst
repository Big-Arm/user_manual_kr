==============
Local Cost map
==============

Local Cost Map이란?
-----------------------

| Global Planner가 Global Cost Map에 영향을 받아가며 작성이 된다면 Local Planner는 Local Cost Map에 영향을 받아가며 부분적인 경로가 생성이 됩니다.
| 이떄 중요한건 LIDAR에서 측정된 데이터를 기초로 맵이 실시간으로 반영이 되는것은 Local Cost Map이라는 점입니다.
|
|
| 다음은 Local Cost Map의 파라미터에 대해 알아보겠습니다.
| 
|
| **footprint**: mobile base의 윤곽선(contour)입니다. ROS에서, 이는 2차원 배열 형태 [x0, y0], [x1, y1], [x2, y2], ...] 로 나타냅니다. 이 footprint는 내접원과 외접원의 반지름을 계산하기 위해 사용되는데, 이 내접원과 외접원은 로봇에 맞게 장애물을 팽창시키는데 사용됩니다. 일반적으로, 안전을 위해 footprint를 로봇의 실제 윤곽보다 좀 더 크게 정의하는 것이 좋습니다.
| **robot_radius**: 로봇이 원형인 경우, footprint 대신 사용합니다.
| **layer parameters**: 각각의 layer를 정의합니다
|
Obstacle Layer
--------------

| obstacle layer는 marking, clearing operations를 담당합니다. 이들은 obstacle layer에 정의될 수 있습니다.
|
| **max_obstacle_height (default: 2.0)**: costmap에 반영될 수 있는 장애물의 최대 높이입니다. 이 값은 로봇의 높이보다 조금 크게 정의되어야 하며, 단위는 미터입니다.
| **obstacle range (default: 2.5)**: costmap에 반영될 거리 입니다. 로봇과의 거리가 해당 값 보다 작을 경우, costmap에 반영되며, 단위는 미터입니다. 이는 센서마다 재정의할 수 있습니다.
| **raytrace_range (default: 3.0)**: 센서 데이터를 사용하여 장애물을 ray trace하는 거리를 정의하며, 단위는 미터입니다. 이는 센서마다 재정의할 수 있습니다.
| **observation_sources (default: "")**: 공간에 의해 분리된 observation source names의 리스트입니다. 이는 밑에 정의된 각각의 source_name 네임스페이스를 정의합니다.
| 
|
| observation_sources의 각각의 source_name은 파라미터를 정의할 수 있는 네임스페이스를 정의합니다.​
|
| **/source_name/topic (default: source_name)**: 이 source에 대한 센서 데이터의 topic입니다. 기본값은 source의 이름입니다.
| **/source_name/data_type (default: "PointCloud")**: 그 topic에 관련된 데이터 타입입니다. 지금은 "PointCloud," "PointCloud2," "LaserScan" 만 지원됩니다.
| **/source_name/clearing (default: false)**: 이 관측값이 자유 공간을 clear하는데에 사용될지의 여부를 정합니다.
| **/source_name/marking (default: true)**: 이 관측값이 장애물을 mark하는데에 사용될지의 여부를 정합니다.
| **/source_name/inf_is_valid (default: false)**: "LaserScan" 데이터 메시지에서 Inf값을 받을지를 정합니다. Inf값은 레이저 센서가 측정할 수 있는 최대값으로 변환됩니다.

|
Inflation layer
---------------

| inflation layer는 장애물의 각각의 셀의 팽창에 대한 설정을 합니다.
| 
| **inflation_radius (default: 0.55)**: 장애물 cost value를 팽창시킬 반지름 크기입니다.(미터 단위)
| **cost_scaling_factor (default: 10.0)**: 팽창시키는 동안 적용할 scalling factor입니다.