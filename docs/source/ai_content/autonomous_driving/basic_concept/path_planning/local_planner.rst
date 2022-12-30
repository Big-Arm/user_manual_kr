=============
Local Planner
=============


Local Planner란?
----------------------

Global planner에서,
전반적인 경로 계산이 끝이 난다면 이제 부분적인 경로에 대 계산을 할 필요가 있습니다. 이를 Local Planner에서 처리를 하게 되며 Local Planner는 IMU센서와 LIDAR센서에서 입력되는 데이터들을 실시간으로 받아들이고 처리하여 퍼블리싱을 하게 됩니다. 

DWA Local Planner
-----------------

| 일반적으로 Local planner를 사용할떄 DWA Local Planner라는 알고리즘을 사용하게 됩니다. 
| 다음은 DWA Local Planner의 Parameter에 대해 알아보도록 하겠습니다.
| 
|

Robot Configuration Parameters
------------------------------

| **/acc_lim_x (default: 2.5)**: 로봇의 x방향 가속도 제한 (meters/s^2)
| **/acc_lim_th (default: 3.2)**: 로봇의 각 가속도 제한(radians/s^2)
| **/max_trans_vel (default: 0.55)**: 로봇의 최대 병진속도(translational velocity)의 절대값(m/s)
| **/min_trans_vel (default: 0.1)**: 로봇의 최소 병진속도(translational velocity)의 절대값(m/s)
| **/max_vel_x (default: 0.55)**: 로봇의 x방향 최대속도(m/s)
| **/min_vel_x (default: 0.0)**: 로봇의 x방향 최소속도. 후진이 가능하게 하려면 음수 값을 설정(m/s)
| **/max_rot_vel (default: 1.0)**: 로봇의 최대 회전속도의 절대값(rad/s)
| **/min_rot_vel (default: 0.4)**: 로봇의 최소 회전속도의 절대값(rad/s)
|
|

Goal Tolerance Parameters
-------------------------

| 해당 파라미터는 목표치에 얼마나 잘 도착하느냐를 조정합니다.
| 
| **/yaw_goal_tolerance (double, default: 0.05)**: 목표 자세와 로봇의 실제 자세와의 각도 오차(rad)
| **/xy_goal_tolerance (double, default: 0.10)**: 목표 자세와 로봇의 실제 자세와의 x,y 위치 오차(meter)
| **/latch_xy_goal_tolerance (bool, default: false)**: 만약 goal_tolerance가 latch되면, 로봇이 목표 xy위치에 도달했을 때 goal tolerance를 벗어나더라도 회전을 합니다.
|
|

Forward Simulation Parameters
-----------------------------

| 해당 파라미터는 장애물을 잘 피하느냐를 조정합니다.
|
| **/sim_time (default: 1.7)**: 해당 값의 시간동안의 시뮬레이션 계산. 예를 들어, 해당 값에 2를 설정하면 앞으로 2초간의 시뮬레이션 계산(초 단위).
| **/sim_granularity (default: 0.025)**: 주어진 궤적의 포인트 사이의 스텝 사이즈(미터 단위)
| **/vx_samples (default: 3)**: x 속도 공간에서의 샘플 수
| **/vy_samples (default: 10)**:  y 속도 공간에서의 샘플 수
| **/vtheta_samples (default: 20)**: theta 속도(각속도) 공간에서의 샘플 수
| 
|

Trajectory Scoring Parameters
-----------------------------

| 해당 파라미터는 경로에 얼마나 가깝게 가느냐를 조정합니다.
|
| **/path_distance_bias (default: 32.0)**: 컨트롤러가 주어진 경로(global plan)에 가깝게 유지하도록 하는 가중치
| **/goal_distance_bias (default: 24.0)**: 컨트롤러가 local goal에 도달하도록 하는 가중치 
| **/occdist_scale (default: 0.01)**: 컨트롤러가 장애물을 피하도록 하는 가중치