ECE382_Lab03
============
<h2>Mega Prelab</h2>
<p>A hard copy of this Mega Prelab is required to be turned in.  Answers should not be handwritten.  The timing diagram may be NEATLY drawn by hand with the assistance of a straightedge on engineering paper.</p>
<h3>Nokia1202  LCD BoosterPack v4-5</h3>
<p>Look at the schematic for the Nokia1202 LCD BoosterPack. Complete the following table.   <br></p>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th align="center">Name</th>
<th align="center">Pin #</th>
<th align="center">Type</th>
<th align="center">PxDIR</th>
<th align="center">PxREN</th>
<th align="center">PxOUT</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center" colspan="1">GND</td>
<td align="center" colspan="1">20</td>
<td align="center" colspan="1">PWR</td>
<td align="center" colspan="1">-</td>
<td align="center" colspan="1">-</td>
<td align="center" colspan="1">-</td>
</tr>
<tr>
<td align="center" colspan="1">RST</td>
<td align="center" colspan="1">8</td>
<td align="center" colspan="1">OUT</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">1</td>
</tr>
<tr>
<td align="center" colspan="1">P1.4</td>
<td align="center" colspan="1">6</td>
<td align="center" colspan="1">OUT</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">1</td>
</tr>
<tr>
<td align="center" colspan="1">MOSI</td>
<td align="center" colspan="1">15</td>
<td align="center" colspan="1">OUT</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">1</td>
</tr>
<tr>
<td align="center" colspan="1">SCLK</td>
<td align="center" colspan="1">7</td>
<td align="center" colspan="1">OUT</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">1</td>
</tr>
<tr>
<td align="center" colspan="1">VCC</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">PWR</td>
<td align="center" colspan="1">-</td>
<td align="center" colspan="1">-</td>
<td align="center" colspan="1">-</td>
</tr>
<tr>
<td align="center" colspan="1">S1</td>
<td align="center" colspan="1">9</td>
<td align="center" colspan="1">IN</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">1</td>
</tr>
<tr>
<td align="center" colspan="1">S2</td>
<td align="center" colspan="1">10</td>
<td align="center" colspan="1">IN</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">1</td>
</tr>
<tr>
<td align="center" colspan="1">S3</td>
<td align="center" colspan="1">11</td>
<td align="center" colspan="1">IN</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">1</td>
</tr>
<tr>
<td align="center" colspan="1">S4</td>
<td align="center" colspan="1">12</td>
<td align="center" colspan="1">IN</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">1</td>
<td align="center" colspan="1">1</td>
</tr>
</tbody>
</table>
<p>The following is a portion of the code that initalizes the directions of the pins connecting the MSP430 to the Nokia 1202 display. Use the information from the previous question to identify the names of the registers missing in the following code (identified by the letters A - D).  Put the register names in the table below.</p>
<pre><code>mov.b    #LCD1202_CS_PIN|LCD1202_BACKLIGHT_PIN|LCD1202_SCLK_PIN|LCD1202_MOSI_PIN, &amp; A
mov.b    #LCD1202_CS_PIN|LCD1202_BACKLIGHT_PIN|LCD1202_SCLK_PIN|LCD1202_MOSI_PIN, &amp; B
mov.b    #LCD1202_RESET_PIN, &amp; C
mov.b    #LCD1202_RESET_PIN, &amp; D</code></pre>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th align="center">Mystery Label</th>
<th align="center">Register</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center" colspan="1">A</td>
<td align="center" colspan="1">P1DIR</td>
</tr>
<tr>
<td align="center" colspan="1">B</td>
<td align="center" colspan="1">P1OUT</td>
</tr>
<tr>
<td align="center" colspan="1">C</td>
<td align="center" colspan="1">P2DIR</td>
</tr>
<tr>
<td align="center" colspan="1">D</td>
<td align="center" colspan="1">P2OUT</td>
</tr>
</tbody>
</table>
<p>The following initializes the SPI subsystem of the MSP430.  For each of the bits listed in the table below, identify how the code-snippet configures that pin and what function is realized by that setting.  For example, setting the UCMSB bit of the UCB0CTL0 register forces the SPI subsystem to output the bits starting from the LSB.  Also, list the bit position that each occupies in its associated register.</p>
<pre><code>    bis.b    #UCCKPH|UCMSB|UCMST|UCSYNC, &amp;UCB0CTL0
    bis.b    #UCSSEL_2, &amp;UCB0CTL1
    bic.b    #UCSWRST, &amp;UCB0CTL1</code></pre>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th align="center">ID</th>
<th align="center">Bit</th>
<th align="center">Function as set in the code</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center" colspan="1">UCCKPH</td>
<td align="center" colspan="1">7</td>
<td align="center" colspan="1">Data is captured on the first UCLK edge and changed on the following edge</td>
</tr>
<tr>
<td align="center" colspan="1">UCMSB</td>
<td align="center" colspan="1">5</td>
<td align="center" colspan="1">Controls the direction of the receive and transmit shift register LSB first</td>
</tr>
<tr>
<td align="center" colspan="1">UCMST</td>
<td align="center" colspan="1">3</td>
<td align="center" colspan="1">Master Slave mode</td>
</tr>
<tr>
<td align="center" colspan="1">UCSYNCH</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">Synchronous mode</td>
</tr>
<tr>
<td align="center" colspan="1">UCSSEL_2</td>
<td align="center" colspan="1">7-6</td>
<td align="center" colspan="1">SMCLK is the source clock</td>
</tr>
<tr>
<td align="center" colspan="1">UCSWRST</td>
<td align="center" colspan="1">0</td>
<td align="center" colspan="1">Software reset enable</td>
</tr>
</tbody>
</table>
<p>Complete the table below.  To answer this question you will have to use some common sense in decoding the meaning of the symbolic constants.</p>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th align="center">Symbolic Constant</th>
<th align="center">Hex</th>
<th align="center">Function</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center" colspan="1">#STE2007_RESET</td>
<td align="center" colspan="1">0xE2</td>
<td align="center" colspan="1">Internal reset</td>
</tr>
<tr>
<td align="center" colspan="1">#STE2007_DISPLAYALLPOINTSOFF</td>
<td align="center" colspan="1">0xA4</td>
<td align="center" colspan="1">LCD display 0: normal display</td>
</tr>
<tr>
<td align="center" colspan="1">#STE2007_POWERCONTROL</td>
<td align="center" colspan="1">0x28</td>
<td align="center" colspan="1">This command sets the on-chip power supply function ON/OFF</td>
</tr>
<tr>
<td align="center" colspan="1">#STE2007_POWERCTRL_ALL_ON</td>
<td align="center" colspan="1">0x2F</td>
<td align="center" colspan="1">Booster : ON
Voltage regulator : ON
Voltage follower : ON</td>
</tr>
<tr>
<td align="center" colspan="1">#STE2007_DISPLAYNORMAL</td>
<td align="center" colspan="1">0xA6</td>
<td align="center" colspan="1">LCD display 0: normal</td>
</tr>
<tr>
<td align="center" colspan="1">#STE2007_DISPLAYON</td>
<td align="center" colspan="1">0xAF</td>
<td align="center" colspan="1">LCD display  1: ON</td>
</tr>
</tbody>
</table>
##Lab Data

When SW3 is detected as being pressed and released (lines 56-62), the MSP430 generates 4 packets of data that are sent to the Nokia 1202 display, causing a vertical bar to be drawn. Complete the following table by finding the 4 calls to writeNokiaByte that generate these packets. In addition, scan the nearby code to determine the parameters being passed into this subroutine. Finally, write a brief description of what is trying to be accomplished by each call to writeNokiaByte.</p>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th align="center">Line</th>
<th align="center">R12</th>
<th align="center">R13</th>
<th align="center">Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center" colspan="1">66</td>
<td align="center" colspan="1">#NOKIA_DATA</td>
<td align="center" colspan="1">0xE7</td>
<td align="center" colspan="1">Stores 8 pixel bar with 2 pixel hole to be written to screen</td>
</tr>
<tr>
<td align="center" colspan="1">276</td>
<td align="center" colspan="1">#NOKIA_CMD</td>
<td align="center" colspan="1">0xB0, whatever the row # is</td>
<td align="center" colspan="1">sets the row #</td>
</tr>
<tr>
<td align="center" colspan="1">288</td>
<td align="center" colspan="1">#NOKIA_CMD</td>
<td align="center" colspan="1">0x10, column #</td>
<td align="center" colspan="1">sets column mumber</td>
</tr>
<tr>
<td align="center" colspan="1">294</td>
<td align="center" colspan="1">#NOKIA_CMD</td>
<td align="center" colspan="1">0x00</td>
<td align="center" colspan="1">Write a command, setup call to make a copy of the top of stack</td>
</tr>
</tbody>
</table>
<p>Configure the logic analyzer to capture the waveform generated when the SW3 button is pressed and released. Decode the data bits of each 9-bit waveform by separating out the MSB, which indicates command or data. Explain how the packet contents correspond to what was drawn on the display.  Be specific with the relationship between the data values and what and where the pixels are drawn</p>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th align="center">Line</th>
<th align="center">Command/Data</th>
<th align="center">8-bit packet</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center" colspan="1">66</td>
<td align="center" colspan="1">Data</td>
<td align="center" colspan="1">11100111</td>
</tr>
<tr>
<td align="center" colspan="1">276</td>
<td align="center" colspan="1">CMD</td>
<td align="center" colspan="1">10110001</td>
</tr>
<tr>
<td align="center" colspan="1">288</td>
<td align="center" colspan="1">CMD</td>
<td align="center" colspan="1">00010000</td>
</tr>
<tr>
<td align="center" colspan="1">294</td>
<td align="center" colspan="1">CMD</td>
<td align="center" colspan="1">00000001</td>
</tr>
</tbody>
</table>
###How many Counts?
######Question
How many counts does the firmware loop count down from? Using the delay you just measured and the number of counts, calculate the amount of time each iteration of the delay loop consumes.

######Answer
Here is the given code for the count down:
```asm
	; This loop creates a nice delay for the reset low pulse
	bic.b	#LCD1202_RESET_PIN, &P2OUT
	mov		#0FFFFh, R12
delayNokiaResetLow:
	dec		R12
	jne		delayNokiaResetLow

	; This loop creates a nice delay for the reset high pulse
	bis.b	#LCD1202_RESET_PIN, &P2OUT
	mov		#0FFFFh, R12
delayNokiaResetHigh:
	dec		R12
	jne		delayNokiaResetHigh
```
It looks like it counts down from 0xFFFF

###XOR picture
![alt text](https://raw.githubusercontent.com/EricWardner/ECE382_Lab03/master/bitblock.bmp)

###Functionality Struggles/Debugging
#####B-Functionailty
I began with the given code that bade the lines appear on the screen. Looking at the main I saw, with the given comments, that the E7 meant an 8 pixel block with a 2 pixel hole in the middle. This makes sense as 0xE7 in binary is 11100111. Following this logic I thought 0xFF might mean a full 8 pixel block because is binary it is 11111111. I built and tested and a full 8 pixel block appeared! Small success!
```asm
	mov		#NOKIA_DATA, R12			; For testing just draw an 8 pixel high
;	mov		#0xE7, R13					; beam with a 2 pixel hole in the center
	mov		#0xFF, R13
	call	#writeNokiaByte
```
Next I attempted to make the 8 pixel block appear in the middle of the screen To accomplish this I inspected the set address function and realized that it got its location from r10 and r11. I replaced the initial clr r10 and clr r11 commands with a mov and knowing the display was 72 rows (pixel) x 96 columns (pixel) I set r10 and r11 to 36 and 48 respectively. When tested, I got a block in a different place but it didn’t seem like it was in the middle. Armed with the knowledge that r10 and r11 controlled location I adjust until it seemed like the middle. 
```asm
	clr		R10							; used to move the cursor around
	clr		R11

	mov.w	#20, R10
	mov.w	#46, R11
```
The next step was getting 8 of those 1 pixel wide blocks to appear in succession. 
In the main function I saw the inc r10 and inc r11 commands. Knowing those registers represented the location the block would be written and know I only wanted to change the column location I took out the inc r11 command and looped the main 8 times. This sort of worked the only problem was the first "test block still showed up at (0,0). I swapped the "set address chunk with the write byte chunk and it seemed to work! The last thing I had to change was requiring a button press for it to appear. to fix this I made the program immediately jump to "while0"

Sorry I dont have code, it is in my commit history but I forgot to add it to the readme before I went on to A-functionality. 

#####A-Functionality
Achieving A functionality was a bit of a challenge and took a lot of trial error and debugging. I thought it would be simple. I though that in the while 1 loop, instead of checking for the aux button to be pressed like what was given, I would just check for the direction buttons to be pressed and jump based on that. This is the idea I went with. It first took me a while to figure out what number corresponded with what button. I figured this out by trial and error. Then after implementing the proper increments and decrements and matching them up with the right button presses and clearing the display at the right time something was still screwey. I mused that it had to do with registers getting smashed, so I pushed and pop'd everything and it seemed to kind of sort of work!! Some points maybe?
```asm
	mov.w	#20, R10
	mov.w	#46, R11
	mov.w	#8,	r8

	push	R8
	push	R11
	push	R10

	jmp		while0;

while1:
;	bit.b	#8, &P2IN					; bit 3 of P1IN set?
;	jnz 	while1						; Yes, branch back and wait

	bit.b	#2,	&P2IN
	jz		right
	bit.b	#4,	&P2IN
	jz		left
	bit.b	#32,&P2IN
	jz		up
	bit.b	#16,&P2IN
	jz		down

	jmp		while1

right:
	inc		R11
	push	r10
	push	r11
	call	#clearDisplay
	pop		r11
	pop		r10
	push	r8
	push	r11
	push	r10
	jmp		while0

left:
	dec		R11
	push	r10
	push	r11
	call	#clearDisplay
	pop		r11
	pop		r10
	push	r8
	push	r11
	push	r10
	jmp		while0

up:
	dec		R10
	push	r10
	push	r11
	call	#clearDisplay
	pop		r11
	pop		r10
	push	r8
	push	r11
	push	r10
	jmp		while0

down:
	inc		R10
	push	r10
	push	r11
	call	#clearDisplay
	pop		r11
	pop		r10
	push	r8
	push	r11
	push	r10
	jmp		while0

while0:

	bit.b	#8, &P2IN					; bit 3 of P1IN clear?
	jz		while0						; Yes, branch back and wait

;	inc		R10							; since rows are 8 times bigger than columns
	and.w	#0x07, R10					; wrap over the row mod 8
	inc		R11							; just let the columm overflow after 92 buttons
	mov		R10, R12					; increment the row
	mov		R11, R13					; and column of the next beam
	call	#setAddress					; we draw

	mov		#NOKIA_DATA, R12			; For testing just draw an 8 pixel high
;	mov		#0xE7, R13					; beam with a 2 pixel hole in the center
	mov		#0xFF, R13
	call	#writeNokiaByte

	dec.b	R8
	tst		r8
	jnz		while0
	pop		R10
	pop		R11
	pop		R8
	jmp		while1
;	jmp		while1
```
One of the big issues I had was I didn't really understand all that the given program was doing so I feel like I made a hackjob of the functionality. There has to be a better way of checking if buttons are pressed and redisplaying the image in a new place. 
