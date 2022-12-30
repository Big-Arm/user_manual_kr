=========================
Global Cost map & Planner
=========================


Global Cost map & Global Planner
""""""""""""""""""""""""""""""""

| 우리는 매핑을 통해서 맵을 이미 만들어 놓았습니다. 이를 Static map이라고 다시 일컫겠습니다. 
  여기서 Static map을 토대로 Global Cost map이 만들어지며 이 costmap을 통해 전반적인 자율주행의 경로가 완성이 되게 됩니다.
|
| 이렇게 전반적인 경로를 계산하는걸 Global Planner라고 합니다.
|
| 이후 이 Global Planner에서 계산된 전체적인 경로는 Local Planner로 보내지게 됩니다.