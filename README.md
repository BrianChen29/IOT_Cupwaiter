# IoT final project : (Brutal) Cupwaiter

###### tags: `NCU` `IoT` `HW`

## Overview
The "Cupwaiter" is a concept of a robotic arm with cupholder, which has several functions. It captures the user's gesture and the distance from the user to follow the user and provides the user with a space to place his bottle. Basically, it just like a waiter standing in front of you and serving you. Unexpectedly, the waiter is such an overbearing waiter, he is brutal and strong when he handing the drink to the user, truely 有個性, so we call him Brutal Cupwaiter. On top of that, there is an interesting coincident, when we say brutal for many times, brutal, brutal, brutal, ...霸道!, sounds familiar in Mandarin. There would be several extra functions and introduction mentioned later.

## Project's concept idea
Sometimes, when working or studying, we have a messy desk and can't concentrate because of that. We don't have extra space to place our bottles or cups. What's worse, we might spill our drink all over the desk. It would make our document on dask stained with drinks or make the computer broken. Fortunately, to prevent from such awkward situation, if I have an automatical cupholder which hands in the drink when I want, maintains the cleanliness of my dask and creates more space, it would make things easier, obviously. 

## Items
### Hardware Components
* Raspberry pi 3 Model B *1
* six-axes robotic arm (with metal supports) *1
* MG996R servo motor *5
* cupholder *1
* pca9685 16-channel 12-bit pwm driver *1
* 25W 5V5A Switching power supply *1
* STP-1 AC power cable *1
* camera *1
* Ultrasonic distance sensor *1
* Mini breadboard *1
* power cables *a lot

### Tools
* Phillips screwdriver *1
* slotted screwdriver *1
* needle-nose plier *1
* chopstick *1 pair(prevent from being shocked :( )

### Software
* Python 3.6
* OpenCV
* Linebot messaging API



## Circuit Diagram
![](https://i.imgur.com/fk2ACCP.jpg)
*p.s :The five servo motors represent the whole robotic arm  and the camera's circuit just for schematic.*
*The diagram finished with **fritzing** and **Microsoft paint** .*

## The Cupwaiter actual look
![](https://i.imgur.com/kFBsjdI.jpg)
![](https://i.imgur.com/CHjdu3y.jpg)
![](https://i.imgur.com/TLLC8YI.jpg)


## Detailed description
The Cupwaiter would analyze(opencv) user's motion which captured by camera in front of the user, when it recognized the user's hand with bottle held. Then, the Cupwaiter would reach out the arm to the front of the User. When it detects the weight increasing it knew there is a bottle on top, it then retrect the arm.
You can also communicate with it via Linebot message API. Click the icon on the rich menu, and it would send a text message to linebot, it then run the process according to the text. Threre are three processes to choose : 1. to reach out the arm to the user, 2. pour the drink(away or fill the cup below the cupwaiter), 3. make instant drink, such as coffee, tea...etc by shaking the robotic arm.

## Fianl represent
Belowing is the code of the project.
```
#Libraries
import time
import sys
from adafruit_servokit import ServoKit
from time import sleep
from gpiozero import DistanceSensor
from signal import pause

#distance sensor 
#sensor = DistanceSensor(23,24, max_distance = 1.5, threshold_distance = 0.1)


#robotarm
#Constants
nbPCAServo=3  //
#Parameters
MIN_IMP  =[500, 500, 500, 500, 500]
MAX_IMP  =[2500, 2500, 2500, 2500, 2500]
MIN_ANG  =[0, 0, 0]
MAX_ANG  =[180, 180, 180]
#Objects
pca = ServoKit(channels=16)

#while True:
 #   print('Distance to nearest object is', sensor.distance,'m')
  #  sleep(1)
  
def init():
    for i in range(nbPCAServo):
        pca.servo[i+1].set_pulse_width_range(MIN_IMP[i] , MAX_IMP[i])

# function main 
def main():
    global angle
    #if(sensor.when_in_range == True):
    pcaScenario()
    #pause()
    
# function pcaScenario 
def pcaScenario():
    """Scenario to test servo"""
    # go
    for j in range(MIN_ANG[0],2,1):
        print("Send angle {} to Servo1".format(j)) #test print
        pca.servo[1].angle = j
        time.sleep(0.01)
    for j in range(MIN_ANG[0],30,1):
        print("Send angle {} to Servo1".format(j)) #test print
        pca.servo[1].angle = j
        time.sleep(0.01)
    for j in range(MIN_ANG[0],60,1):
        print("Send angle {} to Servo2".format(j)) #test print
        pca.servo[2].angle = j
        time.sleep(0.01)
    for j in range(MIN_ANG[0],30,1):
        print("Send angle {} to Servo3".format(j)) #test print
        pca.servo[3].angle = j
        time.sleep(0.01)
    for j in range(10,MIN_ANG[0],-1): #pour the drink or drop down the bottle
        print("Send angle {} to Servo4".format(j)) #test print
        pca.servo[4].angle = j
        time.sleep(0.1)        
    #back
    for j in range(10,MIN_ANG[0],-1):
        print("Send angle {} to Servo2".format(j))
        pca.servo[2].angle = j
        time.sleep(0.1)
    for j in range(10,MIN_ANG[0],-1):
        print("Send angle {} to Servo3".format(j))
        pca.servo[3].angle = j
        time.sleep(0.1)
    #for j in range(MIN_ANG[0],30,1):
     #   print("Send angle {} to Servo1".format(j))
     #   pca.servo[4].angle = j
     #   time.sleep(0.01)
    # go back

    pca.servo[0].angle=None #disable channel
    time.sleep(0.5)
    sys.exit()


if __name__ == '__main__':
    init()
    main()

```

Reference:
* Using a PCA9685 module with Raspberry Pi
https://www.aranacorp.com/en/using-a-pca9685-module-with-raspberry-pi/
* GPIO Distance Sensor https://gpiozero.readthedocs.io/en/stable/recipes.html#distance-sensor

Unfortunately, I can't install the opencv on my raspberry pi in the end....However, I have tried to reach the familiar result as possible as I can with gpio Distance sensor but it still don't work....As a result, I present how my cupwaiter reach out the arm and how it pour the drink or "drop" something down brutally.

## Summary
This tuesday, I've showed my brutal Cupwaiter in class. As you see, it's brutal when it handed in my bottle to me. At first, My original idea is to create a polite and considerate waiter. During this week, I've tried to slow down the dropping speed to make it like a graceful waiter, however, that isn't special enough. Therefore, I maintain the speed at the end and I think this is a kind of its feature, which is a perfect inperfection.

### extension function
* Additional lid (automatic)
* Measure the temperature of the drink and maintain or heat the drink when needed.
* Add some water according to the setting weight.
* Make handshake drink.
* By using motor and magnet to stir the drink.

### review & introspect
* 從霸道這點要讓我們省思，不要忽視電腦及人工智慧的力量，不要當有一天人類親手創造的東西最後開始反噬人類的生活、文化，才意識到這件事的嚴重性。(雖然霸道是弄巧成拙的產物hahaahaha)
* insufficient prior knowledgement
* lack of the ability to access imformation
* not enough patient on raspberry pi
* As mentioned above, those are my weakness and insufficiency make me feel frustrated in this class but I still try hard to make my project getting better and better. Thanks to Mr.George, TAs and classmates having me learn lots of Iot knowledge that I haven't experinced before.



**Thank you for reading!**
