# Line-Follower---Introduction-to-Robotics
The final project developed during the course Introduction to Robotics taken in the final year of the Faculty of Mathematics and Computer Science, University of Bucharest.

## Components: 

  - 1 Arduino Uno
  - Zip-ties & miscellnous screws
  - Power Source: we used a 7.4 V Lipo Battery
  - 2 Wheels
  - 5 female-male wires & various other wires (male-male)
  - QTR-8A reflectance sensor (Line Sensor)
  - Ball Caster (Will act as the front axle which will be fixed in place)
  - Chassis (3D printed in the laboratory)
  - Medium sized breadboard
  - L293D motor driver
  - 2 DC motors
  
 ## Assembly:

 <details>
 <summary> 1) Ball Caster </summary>
 
![image](https://user-images.githubusercontent.com/79463256/216841191-9eddfd5f-685f-4301-8653-b0d475c29bcd.png)
 
</details>

 <details>
 <summary> 2) Line Sensor </summary>
 
![image](https://user-images.githubusercontent.com/79463256/216841248-c108caef-6783-4299-8ddd-ebd4ac3f39d8.png)
 
</details>

 <details>
 <summary> 3) Motors for the rear axle </summary>
 
![image](https://user-images.githubusercontent.com/79463256/216841270-72b946a4-e9b7-4255-b99a-616602f9fa63.png)
 
</details>

 <details>
 <summary> 4) Arduino Uno </summary>
 This will be placed behind the rear wheels (on the boot of the car basically).
 
![image](https://user-images.githubusercontent.com/79463256/216841315-397ddd7d-394d-4af7-a9b1-1f16736652d2.png)

![image](https://user-images.githubusercontent.com/79463256/216841390-6d591474-f032-4539-9861-e55145a8f0a6.png)
 
</details>

 <details>
 <summary> 5) Breadboard </summary>
 Beware of the L293D position on the breadboard. It should be facing forward (the front part of the driver has a little dot carved in the center / slighly to the left, depending on the manufacturer).
 
![image](https://user-images.githubusercontent.com/79463256/216841415-4aef1ac6-f953-48ca-ae5c-95d4023e14ee.png)

</details>

 <details>
 <summary> 6) Wire Connections </summary>
 
![image](https://user-images.githubusercontent.com/79463256/216841570-9772a26b-38e6-4829-88e3-e31c6aaa23f2.png)

![image](https://user-images.githubusercontent.com/79463256/216841587-e9b25d4b-b464-4ae9-9a2c-6c255f340c13.png)

![image](https://user-images.githubusercontent.com/79463256/216841592-fc57a8df-997e-4201-a0c5-f420e754627d.png)

</details>


 <details>
 <summary> 7) Wheels </summary>
 
![image](https://user-images.githubusercontent.com/79463256/216841677-24ee9472-9b93-4a3a-8903-9699139999ac.png)

</details>

## Challenge

1. Implement calibration with automatic motor movement
2. Follow a curved line (not exaggerated)
3. Finish the line follower course
4. Finish the line follower course in a fast manner with visible control (implementing P, D andmaybe I)
We’ll decide on what “fast” means and how much exact grading for each. (2.5p each?)

As requirements, the line follower has to calibrate automatically upon starting (giving it power) and finish a line follower course that our professor designed (we only saw it near the end of the day, when testing began). The time we had to beat for a maximum score was 20 seconds and it was timed automatically using a sensor which detected the car passing the finish line completely, so dangling wires in the back could mean a disadvantage and by F1 standards that wouldn't be acceptable. The Line Follower was called Haas so it's only natural that high standards are of utmost importance.

The results, with the provided [code](https://github.com/BogdanPopel/Line-Follower---Introduction-to-Robotics/blob/main/LineFollower.ino) recorded a best lap time of 20.7 seconds, which is close to the target of 10 seconds.

The biggest challenge when dealing with a line follower coding task is managing to to find the best PID values, taking in account that all DC motors and other components differ in output power, range of motion and various other aspects that affect the real world results of a code.

The auto calibration happens after power is given to the board and it works only if by doing a 360, the sensor passes over a black line. Otherwise, it will spin continously and after the calibration is over, it will just drive into the first wall. If calibration starts and the sensor detects a line to follow, it will alternate power to the wheels (one spins forward and the other backwards -> this is done to maximise the speed of the moves) depending on the values that the sensor reads. For example, for:
  - start a left to right motion:
    - the right wheel spins backwards and the left wheel forward
      - after the sensor has fully passed the line
      - progressively slow down the wheels and change the direction of the speed for both, which should start a right to left motion 
  - start a right to left motion.
    - same thing, the other way around
    
After the calibration, the movement is controlled with the use of [PID](https://www.teachmemicro.com/arduino-pid-control-tutorial/). In the code, the values used for the PID Control vary based on the error (the error indicates where the sensor is compared to the line that it follows) recorded by the front sensor. We came up with those values by trial and error and as mentioned above, it is the only way to properly adjust a Line Follower project.

## [Final Product (video)](https://youtu.be/vzj0kBcIzTA)
  
  The orientation of the video is the wrong one, but the video from a different angle got lost and this is everything i could find.. The first lap is the fastest and after the third timed lap, a back wheel falls off due to an imperfection in the wheel where it connects to the motor.
