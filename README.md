# Sony BG-1S CRT Chassis RGB Modification

<!-- TOC -->

- [Sony BG-1S CRT Chassis RGB Modification](#sony-bg-1s-crt-chassis-rgb-modification)
    - [Overview](#overview)
    - [Who this guide is for](#who-this-guide-is-for)
    - [Tools List](#tools-list)
    - [Parts List](#parts-list)
    - [Step 1 - Dismantling the TV](#step-1---dismantling-the-tv)
    - [Step 2 - Main board modifications](#step-2---main-board-modifications)
        - [Main board modification images](#main-board-modification-images)
    - [Step 3 - Case / enclosure modifications](#step-3---case--enclosure-modifications)
        - [Case / enclosure modification images](#case--enclosure-modification-images)
    - [Step 4 - Hookup and testing](#step-4---hookup-and-testing)
    - [References and acknowledgements](#references-and-acknowledgements)

<!-- /TOC -->

## Overview
The purpose of this document is to explain how to modify a Sony 'BG-1S' CRT television chassis to be able to support RGB. As a disclaimer, I am not an electronics engineer by any means, and all of the information contained within is collated from various sources online. This documentation is mostly for my own reference, but I do hope others find it useful too.

## Who this guide is for
This guide is for you if you own a Sony Trinitron CRT television that has the common 'BG-1S' chassis. In my case, my television is a Sony KV-T25SF1 which is an Australian domestic model. There are many other models of Sony Trinitron CRT televisions that use the 'BG-1S' chassis. For clarity, the chassis in a CRT refers to the electronic components that drive the tube itself. It is not uncommon for manufacturers to re-use chassis in numerous models for obvious reasons (cost, after sales support, simplicity).

To find out if you can achieve the mod as per the instructions on this page, you should try to do a search online for your TV's service manual. For example, in my case I would search for "Sony KV-T25SF1 Service Manual". The Service manual usually mentions the chassis number. Note that even if your TV has a different chassis, it's still possible that it could be modded to support RGB, but you will have to do your own research online. A good place to start would be the shmups '[TV RGB mod thread](https://shmups.system11.org/viewtopic.php?f=6&t=56155)'.

## Tools List
* Screwdriver
* Soldering iron
* Desoldering braid / Desoldering tool
* Solder and flux
* Drill or impact driver (for drilling holes for connectors)
* Multimeter
* Side cutters / wirestrippers

## Parts List
|Component|Description|Qty|Links|
|---------|-----------|---|-----|
|Resistor|Through hole - 75 or 150 Ohm|5|[Digi-Key search (Resistor, 0.5W, Metal Film, 75 / 150 Ohms, In Stock)](https://www.digikey.com.au/en/products/filter/through-hole-resistors/53?s=N4IgjCBcoExaBjKAzAhgGwM4FMA0IB7KAbRBgA4A2cuAXXwAcAXKEAZSYCcBLAOwHMQAX3xgA7ABZ4IJJDRY8hEiADMkgJxgArCHOhmrDjwHD8MAAzkd0GSgw58RSKTFaABAHkAFgFtMIUS1zT19-PQNIEABVXm4mD2QAWWxUTABXTmxTEABaOBtZLjTFJ1IdWiERMmVMzG5MJgJOXSEgA)|
|Switch|SPST toggle or rocker switch|1|[Digi-Key search (Rocker switch, SPST, On-Off, In Stock)](https://www.digikey.com.au/en/products/filter/rocker-switches/195?s=N4IgjCBcpgzADFUBjKAzAhgGwM4FMAaEAeygG0QAWeANgFYB2GkAXSIAcAXKEAZU4BOASwB2AcxABfIgCZYdJCFSRMuQiXIhYADhnxKlVh26Q%2Bg0ROkgAtDMXLBAV3WlIFBS0lW7bkAOLIANZ4AgAEOADuQpzIABaskkA)|
|BNC Connectors|Female socket|3|[Digi-Key - 2057-RF1-106-D-00-50-HDW-ND](https://www.digikey.com.au/product-detail/en/adam-tech/RF1-106-D-00-50-HDW/2057-RF1-106-D-00-50-HDW-ND/9830449)<br>[Jaycar - PS0658 (Australia)](https://www.jaycar.com.au/bnc-panel-socket-single-hole-mount/p/PS0658)|
|Wire|Insulated hookup wire|||

## Step 1 - Dismantling the TV
A note on safety: It goes without saying that working on CRTs has an element of risk as high voltages are involved. You can get a nasty zap or worse if you are not careful. There are lots of guides on YouTube on CRT safety and how to discharge them. I encourage you to educate yourself further on CRT safety so you're prepared for doing this mod.

It is not likely that you will have the same TV that I do, so there's not much point in me detailing the dismantling steps. With that said, here are some tips:
1. In the past at least, Sony had a nice habit of marking any screws required to dismantle their electronics with arrows. This includes TVs. You should look for such marked screws on the rear of your TV. If the screw doesn't have an arrow designator, there's a good chance you don't need to remove it to get the case apart.
2. If you are working on a TV that is > 14", you may find it easier to work with the tube face down. Lay down a clean, thick and soft towel or mat and carefully lay your TV screen face down on it. From here you can usually lift out the main board or in some cases even work on the main board without moving it at all.

## Step 2 - Main board modifications
This mod takes advantage of an unused connector on the main board intended for use with a closed captioning card. The connector in question is designated as 'CN106'.

1. Locate the CN106 connector header on the main board. It will be on the right edge if you are sitting directly behind the TV.
2. Note that the connector has holes for the following: R, G, B, Blk, Gnd.
3. Look underneath the board on the solder side and look at the R, G and B locations - you may find that there are tiny surface mount chip resistors nearby which are connected from the pin itself (R, G, B) to ground. If so, take your multimeter and measure the resistance value. In my case, these resistors were all 150 Ohms.
4. If you do have these resistors, you have two options:
    * Option 1 - remove them and install 75 Ohm resistors in their place.
    * Option 2 - use a [parallel resistance calculator](https://www.digikey.com.au/en/resources/conversion-calculators/conversion-calculator-parallel-and-series-resistor) to find out what resistors you need to install between your R, G, B lines and Gnd. For example if your board already has 150 Ohm surface mount chip resistors installed, you can install 150 Ohm resistors on the BNC connectors to achieve 75 Ohms. Basically, the idea is that your R, G, and B lines need to measure 75 Ohms to the chassis ground point.
5. Solder insulated wire at points R, G, B, Blk, and Gnd. Make sure it's long enough to give you enough room to attach them to your BNC connectors which can be mounted anywhere you like on the TV's case.
6. The 'Blk' point stands for 'blanking', and in order to "enable" RGB, a specific voltage must be supplied at this point. In the case of the BG-1S chassis, that voltage is anywhere between 0.9 and 3V. In my case, and in other examples I have seen online, a sensible voltage to go with would be 2.5V.
7. We will use the board's 5V voltage regulator to achieve the desired 2.5V. On the bottom of the board locate IC002. It is roughly in the centre and toward the front edge.
8. 5V comes out of pin 5, which should be marked on the bottom. Solder an insulated wire at pin 5, and run the wire up through a hole somewhere on the main board. Again, ensure that it is long enough to reach your intended mounting point for your switch.

When you are complete with the main board modifications, you should have 6 installed wires: 'R', 'G', 'B', 'Blk', 'Gnd' on CN106; and 5V on IC002.
If you went with option 1 from step 4, you will also have your R, G, and B termination to ground sorted. If you prefer option 2 (this is what I did), then resistor installation will be covered in future steps.

### Main board modification images
Image|Notes|
-----|-----|
|<img src="https://i.imgur.com/sbJuRmX.jpg" width="300">|Main board - top, showing how CN106 looks after all wiring is installed.|
|<img src="https://i.imgur.com/QGPOaVI.jpg" width="300">|Main board - bottom, showing wire installed at IC002 voltage regulator to get 5V.|
|<img src="https://i.imgur.com/m3oGds6.jpg" width="300">|Main board - bottom, testing that we're seeing 5V on the newly installed wire.|

## Step 3 - Case / enclosure modifications
Believe it or not, you are almost done. All that is left now is to install and wire up the BNC connectors and switch.

1. Choose a sensible location on your TV to mount your BNC connectors. Use a drill to drill 3 holes. In my case I used a step drill bit and checked hole size with a connector at each step until it fit snugly.
2. If you are using a circular toggle / rocker switch, you can also use your drill to cut the hole for mounting that. In my case I chose a rectangular rocker switch and drilled a couple of holes, then used a file to square it out.
3. Mount your BNC connectors and switch to the case.
4. If you decided on option 2 from step 2.4 above, then solder your 3 resistors, 1 each, to the ground tab at the rear of your BNC connectors, and then to the centre pin (i.e. where the wire goes) at the rear of the BNC connector. If you went with option 1 from step 2.4, you don't need to install any resistors as you already have a 75 Ohm ground termination.
5. Solder the new R, G, and B wires from your main board to the respective centre pins on the rear of the BNC connectors.
6. Solder 2 small insulated wire links connecting the ground tabs between the BNC connectors.
7. Solder the new Gnd wire from your main board to one of the ground tabs at the rear of your BNC connectors.
8. At this point, you should have two wires left: The Blk wire, and the one you soldered to 5V on IC002.
9. Before we wire the switch, we need to reduce the voltage on the 5V line to 2.5V. We can do that by creating a voltage divider using two identical value resistors:
    * Take 2 identical value resistors (for example 2 x 75 Ohm, or 2 x 150 Ohm - do **NOT** use two different value resistors) and twist one leg of each resistor to the other one.
    * Your 2 resistors should now look like this, where 'xxx' designates the twisted legs: -----[IIIII]---xxx---[IIIII]-----
    * Solder the centre point where you twisted to reinforce the connection.
10. Solder one end of your joined resistors to one of the terminals on the rear of your installed switch.
11. Solder the other end of your joined resistors to Gnd. One of the BNC ground lugs is fine.
12. Solder the 5V line coming from the main board to the **other** terminal on the rear of your installed switch.
13. Solder the Blk line coming from the main board to the point in the middle of the resistors (i.e. where you twisted and soldered).

When you are complete with these steps, you should have your BNC connectors and SPST switch installed and wired up to the connections from your main board. The switch should have the resistor voltage divider in place to reduce the 5V line to 2.5V for the Blk line.

### Case / enclosure modification images
Image|Notes|
-----|-----|
|<img src="https://i.imgur.com/l4BJHlV.jpg" width="300">|Rear panel, drilling holes.|
|<img src="https://i.imgur.com/ZSVSKrT.jpg" width="300">|Rear panel, view from the inside showing how the BNC connectors, switch and wiring is installed.|
|<img src="https://i.imgur.com/KYHzi6c.jpeg" width="300">|Inside with case partially open, showing an example of adding connectors for ease of future maintenance.|

## Step 4 - Hookup and testing
Now that the modification is complete, all that is left to do is test it out. Hookup your RGB capable source (in my case, I have tested with a PC running CRT Emudriver and also an RGP-Pi).
1. Connect the R, G, and B connectors to their respective newly-installed connectors.
2. Connect your sync connector to one of the pre-existing video inputs (i.e. the yellow connector) via way of a RCA male to BNC female adaptor.
3. Switch on your TV and source and make sure you switch to the video AV input that your sync connector is connected to.
4. Flick the newly-installed RGB switch.
5. If you've done everything correctly, you will now be basking in pure RGB goodness. Enjoy 😄

## References and acknowledgements
* Various members of the '[Aussie CRTs Facebook page](https://www.facebook.com/groups/703084023981413)' for their positive feedback and advice.
* The shmups '[TV RGB mod thread](https://shmups.system11.org/viewtopic.php?f=6&t=56155)'.
* SpudZgames YouTube channel, specifically this video: https://www.youtube.com/watch?v=_qDGC4mBbEM