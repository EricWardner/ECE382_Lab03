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
