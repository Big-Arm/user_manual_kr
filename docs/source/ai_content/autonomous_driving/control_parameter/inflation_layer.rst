===============
Inflation Layer
===============

*inflation_layer의 값에 따른 변화입니다.*

Global costmap의 inflation_radius의 값에 따른 변화를 찍은 사진입니다.


.. figure:: ../images/inflation_1.webp
   :figwidth: 70 %
   :align: center

   inflation_radius가 0.8일

.. figure:: ../images/inflation_2.webp
   :figwidth: 70 %
   :align: center

   inflation_radius가 1.5일

다음은 local costmap의 inflation_radius의 값에 따른 변화를 찍은 사진입니다. 

.. figure:: ../images/inflation_3.webp
   :figwidth: 50 %
   :align: center

   inflation_radius가 0.8일

.. figure:: ../images/inflation_4.webp
   :figwidth: 50 %
   :align: center

   inflation_radius가 0.32일


결론 : inflation_radius가 커지면 커질수록 자율주행 로봇이 인식하는 장애물의 범위가 커지는것을 확인할수 있습니다. 