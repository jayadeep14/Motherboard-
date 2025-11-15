[motherboard](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MTAsInB1ciI6ImJsb2JfaWQifX0=--0747367de00b5cff7997b1ae485e82461773f013/motherboard.pdf)
[Pcb](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzODUsInB1ciI6ImJsb2JfaWQifX0=--685fe88fbd5aa6a94ca59c2edd346767066ce21d/Pcb.webp)
Introduction

This project started because I wanted a motherboard that didn’t exist—something compact, powerful, and completely built around the RK3588. I’d seen development boards using this chip, but I wanted to understand the entire process of designing my own board from scratch.

I knew it wouldn’t be easy (and it wasn’t), but this journal captures how I built the project, the steps I took, and the challenges I ran into along the way.

How I Built the Project
1. Learning the RK3588 and Defining What I Wanted

Before touching any design software, I spent a lot of time reading the RK3588 documentation. Not just skimming—really digging into:

What power rails it needs

How many layers the PCB would likely require

Memory interfaces

High-speed signal rules (PCIe, USB 3.0, HDMI, etc.)

Once I had a decent understanding, I created a simple list of features I wanted my motherboard to have:

RK3588 SoC

LPDDR4x RAM

M.2 slot for NVMe storage

USB 3.0 ports

HDMI output

Ethernet

Reliable power delivery with room for thermal dissipation

This list gave me direction so I didn’t design blindly.

2. Creating the Schematic (The Big Brain of the Board)

The schematic phase was the most mentally demanding part. Using KiCad, I slowly pieced together:

Power regulation circuits

DRAM connections (this part required extreme attention to detail)

USB, HDMI, Ethernet, and PCIe blocks

Clocks and oscillators

All the required supporting resistors, capacitors, and inductors

I constantly bounced between KiCad and the RK3588 datasheet, double-checking I hadn’t missed a requirement.

One of the trickiest parts was ensuring the power rails were correct. The RK3588 uses several different voltages, and some rails require very low noise. Designing a stable power tree took more time than expected.

3. Starting the PCB Layout (Where the Board Became Real)

Moving from schematic to PCB layout felt like going from planning to building the house.

I began with the RK3588 footprint in the center. It’s a massive BGA with a huge number of balls, so the breakout itself was a small project.

Some challenges I faced during layout:

Routing high-speed signals without skew

Getting the DDR lanes length-matched

Ensuring all power planes were solid and continuous

Keeping noisy power sections away from sensitive ones

Making room for the M.2 slot and ports without causing routing nightmares

Every time I thought I was done, I would realize something needed to be moved or rerouted.

It was like solving a puzzle that changed shape every time you touched it.

4. Thermal and Electrical Considerations

Because the RK3588 can run hot, I needed to think seriously about cooling.

I added:

Thermal vias under the SoC

Room for a heatsink or a small fan

Wider copper pours for power traces to reduce heat buildup

On the electrical side, I simulated a few critical traces to check for potential signal issues. It wasn’t perfect, but it gave me confidence the board wouldn't fail immediately.

5. Ordering the Prototype

When the board layout finally looked right (or right enough), I generated the Gerber files and sent them to a PCB manufacturer.

While waiting for the boards, I ordered all the components. Seeing boxes of tiny parts arrive made the project feel very real.

When the PCB finally arrived, holding it in my hands felt surreal—like I had built something that should only come from a real hardware company.

6. Assembly and First Power-On

Assembly was nerve-wracking. The RK3588 is a huge BGA, so I used a reflow hot plate. Watching the solder paste melt and hoping everything aligned felt like defusing a bomb.

Before powering it up, I checked every power rail with a multimeter.

The first power-on didn’t work.
Nothing exploded (good), but nothing booted (not ideal).

After several hours of probing the board, I found one power rail wasn’t actually reaching the SoC. A single trace error. Fixing it felt like performing surgery, but afterward…

The board powered on.
Seeing that first boot log made the whole project worth it.

7. Debugging and Getting Everything Working

Even after it powered on, a few things didn’t work:

HDMI had signal issues

One USB port wasn’t recognized

Ethernet was unstable

Each problem taught me something new about signal routing and grounding. Bit by bit, I patched issues until everything behaved as expected.

8. Finalizing and Documenting the Design

Once the prototype was stable, I cleaned up:

The PCB layout

The component list

The routing around sensitive lanes
![motherboard-B_Courtyard](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzODcsInB1ciI6ImJsb2JfaWQifX0=--bf672dccc9c68860f2e59da8cf26723d50b66574/motherboard-B_Courtyard.png)
![motherboard-B_Silkscreen](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTAsInB1ciI6ImJsb2JfaWQifX0=--93c021921420436cc90ccecaa6672f5f318ceca1/motherboard-B_Silkscreen.png)![motherboard-B_Adhesive](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzODYsInB1ciI6ImJsb2JfaWQifX0=--566a0fbcf820e3e19a6bb74ad2a8c73de7ea8bd0/motherboard-B_Adhesive.png)![motherboard-B_Paste](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTEsInB1ciI6ImJsb2JfaWQifX0=--0a8374c24209be2d34232559e316750b38de9ac5/motherboard-B_Paste.png)![motherboard-B_Mask](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzODksInB1ciI6ImJsb2JfaWQifX0=--54151b145c8fa45a78d09ef7bfee9449518e7d30/motherboard-B_Mask.png)
![motherboard-F_Fab](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTMsInB1ciI6ImJsb2JfaWQifX0=--67c70bdad40e929b707bced41ce004a31955f69e/motherboard-F_Fab.png)![motherboard-B_Cu](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzODgsInB1ciI6ImJsb2JfaWQifX0=--51b317d1a780866b4f8d5e07464c67fe46662ada/motherboard-B_Cu.png)
![motherboard-F_Paste](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTUsInB1ciI6ImJsb2JfaWQifX0=--caa70b84fdf494782c33f824ef05c550d8020c27/motherboard-F_Paste.png)![motherboard-F_Mask](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTQsInB1ciI6ImJsb2JfaWQifX0=--25df524d9d5c96228239b70b61829e8aae324ec5/motherboard-F_Mask.png)![motherboard-Edge_Cuts](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTYsInB1ciI6ImJsb2JfaWQifX0=--5242b7c82dc09979298e152390bf1a3fd11cdf05/motherboard-Edge_Cuts.png)![motherboard-F_Courtyard](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTIsInB1ciI6ImJsb2JfaWQifX0=--01f61116c5c4acfdad2e56db11c6e56478850949/motherboard-F_Courtyard.png)
![motherboard-F_Silkscreen](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTgsInB1ciI6ImJsb2JfaWQifX0=--26c0d43f7c04dff79b0afeea6b622460719340f6/motherboard-F_Silkscreen.png)![motherboard-F_Adhesive](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTcsInB1ciI6ImJsb2JfaWQifX0=--2077f84ec5284733680f10b908f5bbcf1d6e8493/motherboard-F_Adhesive.png)
![motherboard-In3_Cu](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDEsInB1ciI6ImJsb2JfaWQifX0=--d6282f4e2092af96f0225042fd207bd0b84a7577/motherboard-In3_Cu.png)![motherboard-In1_Cu](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDAsInB1ciI6ImJsb2JfaWQifX0=--4939e3e7a84e4deba7b326a111ad5a61321431ef/motherboard-In1_Cu.png)
![motherboard-In4_Cu](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDIsInB1ciI6ImJsb2JfaWQifX0=--cf5afd69ba71e3a8a6527e7e59b6ac4602f18c82/motherboard-In4_Cu.png)
![motherboard-User_Comments](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDcsInB1ciI6ImJsb2JfaWQifX0=--8804cd818e128c7486ac5e5628e389b99b37ed82/motherboard-User_Comments.png)![motherboard-F_Cu](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTEzOTksInB1ciI6ImJsb2JfaWQifX0=--10d841ad62249c702692c78b173ebabea0479f68/motherboard-F_Cu.png)![motherboard-In2_Cu](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDMsInB1ciI6ImJsb2JfaWQifX0=--f59e72aefbef4050ba171c84c772277759d95059/motherboard-In2_Cu.png)
![motherboard-User_Drawings](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDUsInB1ciI6ImJsb2JfaWQifX0=--734f86fee57ea07f50c4a626044d97342cf1aa7a/motherboard-User_Drawings.png)![motherboard-User_1](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDQsInB1ciI6ImJsb2JfaWQifX0=--301dffc19deb49a75d07058e551db6ea641272e8/motherboard-User_1.png)![motherboard-Margin](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDYsInB1ciI6ImJsb2JfaWQifX0=--3dd474285b18364648d740c2d769a47580faa233/motherboard-Margin.png)
![motherboard-User_Eco2](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDksInB1ciI6ImJsb2JfaWQifX0=--093c2ab68b694be0e68346422b8314709a21024d/motherboard-User_Eco2.png)![motherboard-User_Eco1](/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTE0MDgsInB1ciI6ImJsb2JfaWQifX0=--a32343c24e78a121acd38bc5e1d3a6131e7c276a/motherboard-User_Eco1.png)

