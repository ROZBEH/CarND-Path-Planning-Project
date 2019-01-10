# CarND-Path-Planning-Project

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)



<p align="center">
<img src="https://j.gifs.com/pQrZXr.gif" width = "600" />
</p>


Overview
---


In this project vehicle drives in a simulation environment autonomously without human intervention. The fundamental code block used in this project is based on Path Planning Course at Udacity Self Driving Cars online course.


Pipeline
---


*The overall pipeline along with the results will be described here!*

<br>

I. Base of the source code that I've used for this project is inspired by the Q&A session hosted by Aaron and David.


</br>


II. The ```main.cpp``` is the main code that contains algorithms and developments usde for the self driving vehicle.


</br>

III. In order to avoid the jerk when the vehicle starts, ```ref_vel``` is set to 5 miles per hour and we gradually increases to the speed limit 49.9 miles per hour.


IV. Here I try to talk about some of the important variables that were used in the code.


</br>
```cpp
  default_random_engine gen;
  normal_distribution<double> dist_x(0, std_pos[0]);
    normal_distribution<double> dist_y(0, std_pos[1]);
    normal_distribution<double> dist_theta(0, std_pos[2]);
  for (int i = 0; i<num_particles;++i) 
      {
        
      if (fabs(yaw_rate) < 0.00001){
        particles[i].x += dist_x(gen) + velocity * delta_t*cos(particles[i].theta);
        particles[i].y += dist_y(gen) + velocity * delta_t*sin(particles[i].theta);
        particles[i].theta += dist_theta(gen);
      } else{
        particles[i].x += dist_x(gen) + (velocity/yaw_rate)*(sin(particles[i].theta+yaw_rate*delta_t)-sin(particles[i].theta));
        particles[i].y += dist_y(gen) + (velocity/yaw_rate)*(cos(particles[i].theta)-cos(particles[i].theta+yaw_rate*delta_t));
        particles[i].theta += dist_theta(gen) + yaw_rate*delta_t;
          }
      }
```
</br>

</br>


V. Click on the following imahe in order to watch final video of car going around the whole track without violating any of the rules. 
</br>

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/FRMAPzO9M08/0.jpg)](https://youtu.be/FRMAPzO9M08)

</br>
<br></br>