# VexRobotics
HEY ROBOTICS GROUP PEOPLE!!!!


















//start coding everything on line 22
#include "robot-config.h"
          
int main() 
{
    vex::rotationUnits rotations = vex::rotationUnits::rev; 
    task::sleep(1000);
    Vision1.takeSnapshot(SIG_1);
    int screen_middle_x = 316 / 2;
    Vision1.largestObject.width+3 > Vision1.largestObject.height or Vision1.largestObject.width-3 < Vision1.largestObject.height;
    bool linedup = false;
    while(not linedup) {
        Vision1.takeSnapshot(SIG_1);
        if(Vision1.objectCount > 0) {
            if(Vision1.largestObject.centerX < screen_middle_x - 2) {
                Brain.Screen.print("Hello");
                Motor1.startRotateFor(-0.1,rotations,100,velocityUnits::pct);
                Motor2.startRotateFor(-0.1,rotations,100,velocityUnits::pct);
            } else if (Vision1.largestObject.centerX > screen_middle_x + 2) {
               Brain.Screen.print("bye");
               Motor1.startRotateFor(0.1,rotations,100,velocityUnits::pct);
               Motor2.startRotateFor(0.1,rotations,100,velocityUnits::pct);
            } else {
                Brain.Screen.print("Bad");
                task::sleep(2000);
                linedup = true;
                task::sleep(1000);          
            }        
        }
        else {
            Brain.Screen.print("cant see anything");
           //Motor1.startRotateFor(2,rotations,100,velocityUnits::pct);
           //Motor2.startRotateFor(2,rotations,100,velocityUnits::pct);
        }
    }
    Vision1.takeSnapshot(SIG_1);
    int close = 316;
    Vision1.largestObject.width > close - 10;
    bool fullscreen = false;
    while(not fullscreen)
    {
        Vision1.takeSnapshot(SIG_1);
        if (Vision1.objectCount > 0)
        {
            if (Vision1.largestObject.width < close - 30)
            {
               Brain.Screen.print("Object pretty far");
               Motor1.startRotateFor(-3,rotations,100,velocityUnits::pct);
               Motor2.startRotateFor(3,rotations,100,velocityUnits::pct);
               task::sleep(1200);
            }
            else if (Vision1.largestObject.width > close - 15)
            {
                Brain.Screen.print("Object Pretty Close");
                Motor1.startRotateFor(-0.2,rotations,100,velocityUnits::pct);
                Motor2.startRotateFor(0.2,rotations,100,velocityUnits::pct);
                task::sleep(5);
            }
            else
            {
                fullscreen = true;
                Motor1.stop();
                Motor2.stop();
            }
        }
        else
        {
            Brain.Screen.print("Object Close Enough");
        }
     
    }
                     
     
}

           


