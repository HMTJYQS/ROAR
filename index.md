# ROAR:Robot Open Autonomous Racing

This article was written by Deng Shuwen, Wu Zheyuan, Zang Linfeng  and describes what they did for the racing, collection by Yu qiushuang.


![ROAR PIC](./images/ROAR.png)


## Table of contents
1. [Summary](#summary)
1. [Design](#design)
    1. [Planning](#design_planning)
    1. [Controlling](#design_control)
1. [Implementation](#implementation)
    1. [Planning](#impl_planning)
	1. [Controlling](#impl_control)
1. [Results](#resluts)
1. [Conculsion](#conclusion)
    1. [Strength and weakness](#conclu_strength_and_weakness)
    1. [Possible improvements](#conclu_possible_improvements)

1. [Team](#team)
1. [Additional materials](#add_mats)


## Summary <a name="summary"></a>

This year, we were invited to [Berkeley’s ROAR competition](https://vivecenter.berkeley.edu/research1/roar/), in which teams race 1/10th scale self-driving cars in a digital platform with a fixed racing track.The end goal of this competition is to maximize the speed in premise of ensuring minimal (acceptable) collisions.

To accomplish this goal, we spent two weeks improving our car’s performance. For the first week, we worked individually with regular online communication and managed to optimize our waypoints. For the second week, we spent two days working collaboratively and improved all the other things, including the structure of PID controller, look-ahead values and K values.

The final result showed its effectiveness. The maximum single lap time was 77.15s, while the total 10-lap time was 1104s. Because of the considerable speed, we were fortunate enough to win the second place and the Fastest Lap Time Award in this year’s 2020 ROAR S1 series .

However,though the car indeed ran with considerable speed, there are still places for improvement. Firstly, the conditions of activating the configuration conditions are too specific, meaning that for a different race track, it may be less effective. Also, the configurations of PID controller are mostly empirical. Moreover, our waypoints are not optimal. These problems result in occasional collisions, possibility of failure, and lower speed.

To further improve the performance, we suggest using machine learning methods for configurations, trying different waypoints, and generalizing the conditions for using mathematical methods.

Due to a lack of time we didn’t implement these methods, but we have published our codes in [Github](https://github.com/Trance-0/ROAR.git). 


##Design < a name="design"></a>

From the original codes we know that the car essentially used a PID controller to control the vehicle to track the path (a sequence of waypoints). The platform can provide us information including current speed, position, the value of steering and throttle. 

Base on the above conditions, we provide two ways to improving the project.

- Rebuilding a better waypoint text file which can make sure a better way for car to following;
- Connecting the steering and throttle with the actual coordinates of the car;
So we split the task into 3 parts-planning, controlling, racing.