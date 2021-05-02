# IRIS Rev 4 Build

## BOM

Parts | Company 
--- | --- 
Nylon TRRS Cable | space.design 
YMDK Carbon Keycaps | Amazon
1.8 mm diffuse white LEDs | Evil Mad Science LLC
Kaihl Box Navy | NovelKeys
3M Rubber Feet | Amazon
Type C to Type A USB Cable braided | Amazon
1/4" Carriage Bolt | Home Depot
1/4" Hex Nuts | Home Depot
IRIS Rev 4 Kit | Keeb.io
3D Printed Middle Layer (Rostock Max V3) | Modified Fusion 360

## Build

Following the build guide on [keeb.io](https://docs.keeb.io/iris-rev3-build-guide). I got started

Stabilizer install was fairly straight forward, but I used this [video](https://www.youtube.com/watch?v=D21Ocg9kVsU) to put together the 2-u stabilizer I used for space on the left hand side.

Next, was installing the rotary encoder on the right hand side.  This step matched the keebio guide exactly.

![white leds](img/white_key_leds.jpg)

Third, was putting in each 1.8 mm key switch LED from Evil Mad Science LLC.  I eventually went with placing one of my Kaihl box navy switches on top of the LED and then flipping the board over and soldering the LED in.  The switch was just held in place against my table.  This ensured the LED didn't move during soldering and would fit when the switch was installed later in the build.  There isn't a lot of room for the LED in the box switches, so early on I had some fit issues.

![encoder install and leds](img/encoder_install_and_leds.jpeg)

I did have to replace a few LEDs after they were soldered in at this step.  I would do a row and then plug in a USB-C cable to make sure everything lit up as expected.  A few times I ended up with dead LEDs.  I used solder wick and tweezers to replace the LEDs.  I also had to reflow a one LED that flickered out after the build was done.  But that took care of the issue and all the LEDs have worked great since.

Once the LEDs were in place it was time to install the switches on the switch plate and solder them to the board.

![switch install](img/switch_install.jpeg)

As recommended, I started with the 4 corners first and then soldering in the rest.

![switch install](img/board_3.jpeg)

Once the switches were on testing was done using VIA to ensure there were no dead switches.

![switch install](img/via_testing_c.jpeg)

The keycaps were then put on.

![keycaps](img/keycaps.jpeg)

![keycaps](img/case_built.jpeg)

## Tenting Middle Layer

![middle layer print](img/middle_layer.jpeg)

I used the STL file to print a black PLA tented middle layer from the (keeb.io git hub)[] and had some fit issues.  I make a quick modification in Fusion 360 to reduce the USB-C face plate to make it easier to fit the board in.  Reducing it by roughly 2 mm did the trick.

![installed](img/middle_layer_installed.jpeg)

![reduce usb c face](img/reduce_usb_c_plate.PNG)

Due to the tolerances on the printer I did have to drill out the carriage bolt holes and the fastener holes on the final tent layer to ensure everything fit properly.  Modified STL is located [here](stl/iris_rev4_tent_middle_layer_v6.stl)

![fasteners](img/fasteners.jpeg)

Iris tented with carriage bolts.

![tented](img/tent_with_bolts.jpeg)
## Wrist Rest Design and Print

Fusion 360 render based on measurements with my iPhone level to match the tenting angle and tape measure to get the wrist distance when actually typing on the Iris.

Used the bottom layer files on the [keeb.io git hub](https://github.com/keebio/iris-case/tree/master/rev3-and-rev4) to ensure the wrist rest fit against the FR4 case.  

![fusion 360 render](img/wrist_rest/Capture.PNG)]

![overall fit](img/wrist_rest/overall_wrist_fit.PNG)

After printing with 10% fill which took about 5 hours.

![installed](img/wrist_rest/wrist_rest_print_1.jpeg)

![installed](img/wrist_rest/wrist_rest_print_2.jpeg)

![setup](img/wrist_rest/wrist_rest_setup_c.jpg)

There are also holes on the bottom to fit 3M rubber feet to avoid the wrist rest sliding when in use.  STL files for the design are [here](stl/iris_wrist_rest_od_v2.stl)

## Final Build

![build first](img/image4.jpeg)

![build second](img/image2.jpeg)

## Keymap

I've used VIA to build up a keymap that has worked pretty well for normal use as well as programming which requires a lot of special key use. [keymap](keymap/iris_rev__4_second.json)
## QMK Firmware Modifications

A quick guide for setting up a qmk build environment is detailed [here](https://github.com/rompgadgets/keyboards/blob/main/qmk_setup_wsl2.md)

A few modifications were done based on the VIA keymap to set the right side encoder to work as volume up and down except when layer 3 is toggled.  When layer 3 is turned on the encoder switches to scroll up and scroll down.

These firmware changes are in the viasig directory located [here](https://www.github.com)