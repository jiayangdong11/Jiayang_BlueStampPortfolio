# Hexapod Robot
For my project, I built a hexapod. The robot has 6 legs which are independenty controlled by servo motors and each leg can move on its own. The hexapod has a wide variety of movement options due to this fact, such as differnt walking gaits and turning in place.

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Jiayang D | Lynbrook High School | Input field of engineering interest | Incoming Sophmore |

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE

For my final milestone, I added a camera to hexapod, allowing it to remotely broadcast video of its surrounds to a website. 

# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


For my second milestone, I used provided Arduino and Processing app to allow the hexapod to move. I also built a remote control for my hexapod and I designed a 3-D printed battery case to allow the hexapod to carry its battery while moving. 

## Programming the robot
Premade code was provided by the company that created the hexabot kit in the form of Processing App and Arduino code files. An option to completely code the robot from scratch was avaiable, but I did not choose to take it. However, the premade code still provided some degree of customization and flexibility. I was able to adjust the robot's movement speed, walking gait (see "How it works" section below), and the radio frequency of communications between the robot and the remote, which I changed to prevent my hexapod from receiving singals from other studennt's controllers. 

## Designing the Battery Case
Before creating the CAD for the battery case,  I created a model of the hexapod's chassis to ensure that the battery holder I designed later would fit correctly onto the hexapod. During the modeling of the hexapod's chassis, I also decided on the points of attatchent for the battery case, choosing them to be as far apart as possible to ensure stability.

![Sketch of hexapod chassis geometry](Photos/Milestone_2_Robot_Chassis_Geo_Annotated.png){: style="display: block; margin: 0 auto;"}
<div align="center">
  Sketch of hexapod chassis geometry
</div>
<br>
First, I created the baseplate, designing it to be large enough to ensure a comfortable margin betweeen the points of attatchment and the edge of the baseplate. Instead of making a separate extension for each of the points of attatchment, I created a large platform to guarentee that the battery case would be stable and to reduce the risk of breaking under stress. I added stilts to the points of attatchment in order to elevate the battery case from the electrical components also present on top of the hexapod. While doing this, I also discovered that the power button of the hexapod would be covered by the battery case baseplate.

![Sketch of hexapod baseplate geometry](Photos/Milestone_2_Robot_Baseplate_Geo_Annotated.png){: style="display: block; margin: 0 auto;"}
<div align="center">
  Sketch of hexapod baseplate geometry
</div> 
<br>
Next, I created the individual parts of my 3D model, starting with making 3D models of the battery case baseplate and walls, which I dimensioned according the the size of the battery. After finding that power button of the hexapod would be covered by the baseplate of the battery case, I designed a mechanism to extend the button, allowing the power switch to be pressed from a point above the baseplatee. I created a rectangular rod with two keys on opposing sides. I then designed a casing with grooves matching the keys, allowing the rod to move freely within the casing.

<div align="center">
  <img src="Photos/batteryHolder1.0_base_Image.png" width="400"/> <img src="Photos/batteryHolder1.0_walls_Image.png" width="400"/>
</div>
<div align="center">
  Left: 3D model of battery case baseplate / Right: 3D model of battery case walls
</div> 
<br>
<div align="center">
  <img src="Photos/buttonExport1Image.png" width="400"/> <img src="Photos/batteryHolder1.0_buttonHolder_Image.png" width="400"/>
</div>
<div align="center">
  Left: 3D model of button with keys / Right: 3D model of button holder with grooves
</div> 
<br>
I finished the first battery case design by attatching the button holder mechanism to its corresponding hole on the baseplate of the battery case.

![Battery holder assembly v2](Photos/batteryHolder2.0_assembly_Image.png){: style="display: block; margin: 0 auto; width: 400px;"}
<div align="center">
  Image of battery case v1
</div>
After 3D printing the first version of my battery case, I found that it did not print well due to the unusual shape. Also, a few measurements were off. The postition of the button pushing mechanism did not align with the power switch on the hexapod, and the length of the button did not account for the height of the stilts, meaning that the that it could not reach the power switch. I split the battery case into two parts attatched by screws to make it easier to print, and fixed the alignments of the battery holder and button. 

![Battery holder assembly v2](Photos/batteryHolder2.0_assembly_Image_2.png){: style="display: block; margin: 0 auto; width: 400px;"}
<div align="center">
  Image of battery case v2
</div>


## How it works
The hexapod moves by utilizing 18 360 degree servo motors, allowing each leg of the hexapod to move independently and with a large range of motion. In each leg, one servo controls the movement along the xy axis, allowing the leg to turn. The two other servos control the movement of the leg segments, allowing the for the extension or contraction of the leg.

![Sketch of hexapod leg movement](Photos/Milestone_2_Hexapod_Leg_Diagram_Annotated.png){: style="display: block; margin: 0 auto; width: 500px;"}
<div align="center">
  Diagram of hexapod leg movement
</div>
<br>
The premade code from the company that created the hexapod allows for three movement types, or gaits. The Tripod gait is the fastest in terms of movement speed, as the robot moves three non-adjacent legs at a time and completes a movement cycle in only two movements. The Wave gait only moves one leg at a time, sacrificing speed for stability on rough terrain, maintaing five legs on the ground at all times. Finally, there is an intermediate hybrid gait that combines aspects of both, moving one or two legs at a time to balance speed and stability.

<div align="center">
  <img src="Photos/Milestone_2_Gait_1.png" width="250" style="margin-right: 30px;" /> <img src="Photos/Milestone_2_Gait_2.png" width="250"/> <img src="Photos/Milestone_2_Gait_2.png" width="250" style="margin-left: 30px;" />
</div>
<div align="center">
  Left: Tripod gait / Center: Hybrid gait / Right: Wave gait
</div>
<br>

## Next Step
For my next step, I want to mount a camera capable of filming and broadcasting video to the front of the hexapod. I also want to experiment with a raspberry pi in order to program object detection and avoidance.

# First Milestone
<iframe width="560" height="315" src="https://www.youtube.com/embed/IBBULp1QDGs?si=18xh0vsklhWrsrXV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<br>
For my first milestone, I built the chassis of the hexapod and and finished wiring the electrical components. First, I attatched the 18 servo discs to the acrylic chassis and the legs of the hexapod with self threading screws. The servo discs are used to securely connect the servo motors to the body and legs of the hexapod. After connecting each of the servos to the control board, I soldered connector wires to allow an external battery to power the hexapod. With the addition of an acrylic backboard, the chassis was complete.


![Hexapod top view](Photos/Milestone_1_Top_View.jpeg){: style="display: block; margin: 0 auto; width: 400px;"} 
<div align="center">
  Hexapod top view
</div>

![Hexapod bottom view](Photos/Milestone_1_Bottom_View.jpeg){: style="display: block; margin: 0 auto; width: 400px;"}
<div align="center">
  Hexapod bottom view
</div>

## Challenges
### Integrating the battery
Due to the fact that the two 3.7V lithium batteries the hexapod called for were deemed unsafe, I used a 7.2V battery instead to power the hexapod. At first, I thought that soldering a connecter to connect the battery to the power pins on one side of circuit board would be enough, but it became evident after testing the power with a multimeter that I would have to connect the power to the other side of the circuit board as well. After soldering two wires to connect all the circuit board's power pins to the battery, power was sucessfully supplied to the entire robot.

![Hexapod control board and sautered wires](Photos/Milestone_1_Wires_Closeup.jpeg){: style="display: block; margin: 0 auto; width: 400px;"}
<div align="center">
  Hexapod control board and sautered wires
</div>

### Fixing the servo motors
Once power was supplied to the robot, it would curl up in unnatural ways after being turned on. I thought that this might have been caused by the robot's power supply due to the use of a differnt battery (mentioned above). However, after checking the power, nothing seemed wrong as to cause the robot to malfunction. After some more investigation in the instruction mannual, I found that I had forgot to zero the motors, and that the curling of the hexapod was caused by the motors trying to go to their default positions. To fix this issue, I disassembled all of the servo motors. After turning the power on, the motors spun to their default position, and I carefully assembled the hexapod back together, being careful not to rotate the servos too much. After testing the robot again, the issue was fixed.

## Next Step
For the next step, I want to build the remote controller and design a battery holder for the external battery pack. This will allow my robot to move remotely while carrying the battery pack.


# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Hexapod Kit | Base hexapod construction | $102.95 | <a href="https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLXFDZ1?th=1"> Link </a> |
| Adafruit Feather V2 | Microcontroller for the camera | $19.95 | <a href="https://www.adafruit.com/product/5400?srsltid=AfmBOop1ICXdfQI1rkXFHPG4oLnxB5XtSnDnWPT32RcghEwRS8RghYuW"> Link </a> |
| Arducam OV2640 | Allows hexapod to take images of its surroundings | $25.99 | <a href="https://www.amazon.com/Arducam-Module-Megapixels-Arduino-Mega2560/dp/B012UXNDOY/ref=sr_1_1?crid=2GCUYGHA50TJP&dib=eyJ2IjoiMSJ9.5dpM3JLxyp15AqYZjr9_bHNdlwVKkC3WKnLCg0odhgSo8smfYYXuAcd5yPgbeXLI5L_oIGVcm8ODUnjDcAGsYboNEgcXFFCoODD6swFR5YJ5NUzkgO6dz17zr5sjUEF0VUvKoQH0CwPCzfN2ZJjNBJ-J7oKDPQ6CYHarX8TOnIKzACe9zs3wUSgHVJ43qMNX5KDU8CSE9wQAJDGbFysW522mNWj24yW8ligieSWCkes.MKVJ0bMdDfYVj4GEcxG0Lduyw022Qm7hTmUxTQ05i5Q&dib_tag=se&keywords=arducam%2B2640&qid=1784821998&sprefix=arducamov%2B2640%2Caps%2C194&sr=8-1&th=1"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
