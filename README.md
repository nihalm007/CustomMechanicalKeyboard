# The Journey of Building My Own Mechanical Keyboard

Hey, I am Nihal M, a passionate electronics and robotics enthusiast, currently pursuing my BTech in Electronics and Communication at the College of Engineering Munnar.

# How It All Started

The journey began when I bought a mechanical keyboard from Cosmic Byte. At that time, it was the cheapest mechanical keyboard on the market, priced at around 1500 rupees. It worked perfectly for the first 3–4 months, but soon some of the backlights stopped working. I didn’t mind at first since it was just a few LEDs, but over time, more and more LEDs failed. Eventually, after a few months, some of the rows in the keyboard stopped working completely. It was frustrating because I hadn’t even used it that much.
<br><br>
<div align="center">
  <img src="https://github.com/user-attachments/assets/9019b8a9-4e3b-443c-a23e-6e6339165102" alt="Description" width="300" align="center" style="border: 5px solid black;">
<img src="https://github.com/user-attachments/assets/6272477c-62c3-4bc5-abbf-f4aee77164d7" alt="Description" width="300" align="center" style="border: 5px solid black;" >
</div>

<br><br>
I tried to claim the warranty, but unfortunately, I couldn't. The reason? I didn’t have a phone for around 8 months, as I was busy with entrance coaching, so I wasn’t able to respond to the brand’s messages in time. Left with no choice, I bought a new membrane keyboard. However, after using a mechanical keyboard, the membrane keyboard just didn’t feel right. That’s when I decided to open up the faulty keyboard and investigate the problem.

Upon inspection, I found that the IC was fried. There was no way to repair it, so I thought—why not repurpose the keyboard? I decided to remove the existing circuit and build a new one using the same keys and frame. That was the moment I embarked on my journey of building my own mechanical keyboard.

# Research & Learning

I started researching how keyboards work and how to build one from scratch. YouTube was a great resource.
<div align="center">

<img src="https://github.com/user-attachments/assets/759c0f48-d555-48f6-aa11-0f1f2593e0f3" alt="Description" width="800" align="center"  >

</div>

<div align="center">
Playlist of Youtube videos I refered:https://youtube.com/playlist?list=PLBqd6EiPV9uk_CLYCL93-60aPi9X0UlZA&si=W9pgPMkPlAtprPVq
</div>
<br><br>
But I still had some doubts—like which microcontroller to use because there are so many controllers out there and which firmware would be the best. After some digging, I found a Discord server with many keyboard enthusiasts. The community was super helpful, and they answered all my questions. With newfound confidence, I purchased the necessary components and got to work.
<br><br>
<div align="center">

<img src="https://github.com/user-attachments/assets/5c3b8835-38db-4d38-99b8-b8983dd52218" alt="Description" width="600" align="center" >

</div>
<div align="center">
Discord Link:https://discord.com/invite/ctYr5BVF7b
</div>


# Building the Circuit

The circuit was quite simple. I chose the Raspberry Pi Pico as my microcontroller because it’s cheap, has 26 GPIO pins, and features the powerful RP2040 processor. 

Since my keyboard had more than 80 keys, I used a matrix configuration to reduce the required pins to just 24.

The next step was soldering the keys into a matrix. I connected copper wires for the columns and used diodes for each switch which were then connected to wires for the rows. (Diodes are essential to prevent ghosting issues in keypress detection and the diode i used is 1N4148.)

However, I made a critical mistake while connecting the diodes. The correct way was to connect one end of the diode to the switch and the other end to the row wire, but I mistakenly connected one end of the diode to the switch and the other end to the next diode in series. After uploading the firmware and testing the keyboard, I found that the keys at the end of each row weren’t working. At first, I assumed it was a coding issue, since I was a beginner in MicroPython.
<br><br>
<div align="center">
<img src="https://github.com/user-attachments/assets/77a0d18e-95c4-46ec-ad1a-2b7e88f98519" alt="Description" width="600" align="center"  >
</div>

<div align="center">
The circuit which was not working
</div>
<br><br>


After multiple failed attempts to debug the code, I decided to test the circuit separately by making a mini macropad. Surprisingly, it had the same issue! That’s when I realized the problem was with the circuit itself. Comparing my setup with the correct circuit I found on YouTube, I discovered that my diode connections were wrong. I desoldered all the diodes and rewired them properly. After this correction, everything worked perfectly!

<br><br>
<div align="center">
<img src="https://github.com/user-attachments/assets/e3766984-9dbd-4920-a8b5-aeb3ce642eeb" alt="Description" width="300" align="center"  >
</div>

<div align="center">
Macropad made for testing
</div>
<br><br>

After all, I tried to enclose the circuit inside the existing keyboard, but unfortunately, it didn’t fit, so I just placed the circuit outside.

<br><br>
<div align="center">
<img src="https://github.com/user-attachments/assets/d842f224-8008-409d-aa8f-015b2fec44c4" alt="Description" width="300" align="center"  >
</div>

<br><br>
# Firmware & Coding

For the firmware, I chose KMK Firmware, a Python-based firmware designed for mechanical keyboards running on CircuitPython-compatible microcontrollers like the RP2040, SAMD, and NRF52. KMK is an easy-to-use, highly customizable alternative to QMK, offering features like:

* Advanced key remapping

* Macros

* Rotary encoder support

Since it runs on Python, KMK allows quick modifications without the need to compile firmware, making it very beginner-friendly.

To test the setup, I first coded a simple mini keyboard and saved the script to the Pico. Once I confirmed it worked (after fixing the diode issue), I moved on to coding the full-sized keyboard.

I found that instead of writing the code manually, it was easier to use a tool called POG (Python On GitHub). POG is a web-based tool that simplifies the process of generating KMK-based Python code. It offers a graphical interface, allowing users to configure:

* Number of rows and columns

* Pin mappings

* Extra features like macros and layers

This saved a lot of time, as I could simply click buttons to add features instead of manually writing code.

Get POG: https://github.com/JanLunge/pog
POG documentation: https://pog.janlunge.de/
KMK doc: https://kmkfw.io/

# Conclusion

Building my own mechanical keyboard was an incredible journey. I not only learned how keyboards work, but also improved my electronics, circuit design, and coding skills. From troubleshooting hardware issues to learning how to use KMK firmware, every step was a learning experience.I am also planning to dd some more features like rotary encoder and some RGB backlights.

<br><br>
<div align="center">
<img src="https://github.com/user-attachments/assets/6376d397-f91c-4fd2-ae17-7311b4ed0778" alt="Description" width="300" align="center"  >
<img src="https://github.com/user-attachments/assets/f91ffd4c-3037-4527-8609-d6b2f6c2f388" alt="Description" width="300" align="center"  >
</div>
<br><br>

Now, every time I type on my custom-built keyboard, it feels special—because I built it from scratch!
Also i uploaded a video on instagram of the whole building process : https://www.instagram.com/reel/DGpS0-LylXu/?igsh=MWlzc3dkNzN5cDMxZA==

Thank You
