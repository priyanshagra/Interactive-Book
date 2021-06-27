{
  "name": "registers.md",
  "path": "docs/seq-msi/registers.md",
  "relative_path": "docs/seq-msi/registers.md",
  "layout": "circuitverse",
  "title": "Registers",
  "nav_order": "l0s000",
  "cvib_level": "basic",
  "parent": "Sequential MSI",
  "has_children": false,
  "content": "<h1 class=\"no_toc\" id=\"registers\">Registers</h1>\n\n<h2 class=\"no_toc text-delta\" id=\"table-of-contents\">Table of contents</h2>\n\n<ol id=\"markdown-toc\">\n  <li><a href=\"#introduction\" id=\"markdown-toc-introduction\">Introduction</a></li>\n  <li><a href=\"#serial-in-serial-out\" id=\"markdown-toc-serial-in-serial-out\">Serial-in serial-out</a>    <ol>\n      <li><a href=\"#block-diagram\" id=\"markdown-toc-block-diagram\">Block diagram</a></li>\n      <li><a href=\"#operation\" id=\"markdown-toc-operation\">Operation</a></li>\n      <li><a href=\"#truth-table\" id=\"markdown-toc-truth-table\">Truth table</a></li>\n      <li><a href=\"#waveforms\" id=\"markdown-toc-waveforms\">Waveforms</a></li>\n    </ol>\n  </li>\n  <li><a href=\"#serial-in-parallel-out\" id=\"markdown-toc-serial-in-parallel-out\">Serial-in parallel-out</a>    <ol>\n      <li><a href=\"#block-diagram-1\" id=\"markdown-toc-block-diagram-1\">Block diagram</a></li>\n    </ol>\n  </li>\n  <li><a href=\"#parallel-in-serial-out\" id=\"markdown-toc-parallel-in-serial-out\">Parallel-in serial-out</a>    <ol>\n      <li><a href=\"#load-mode\" id=\"markdown-toc-load-mode\">Load mode</a></li>\n      <li><a href=\"#shift-mode\" id=\"markdown-toc-shift-mode\">Shift mode</a></li>\n      <li><a href=\"#block-diagram-2\" id=\"markdown-toc-block-diagram-2\">Block diagram</a></li>\n    </ol>\n  </li>\n  <li><a href=\"#parallel-in-parallel-out\" id=\"markdown-toc-parallel-in-parallel-out\">Parallel-in parallel-out</a>    <ol>\n      <li><a href=\"#block-diagram-3\" id=\"markdown-toc-block-diagram-3\">Block diagram</a></li>\n    </ol>\n  </li>\n  <li><a href=\"#applications-of-shift-registers\" id=\"markdown-toc-applications-of-shift-registers\">Applications of shift registers</a>    <ol>\n      <li><a href=\"#overview\" id=\"markdown-toc-overview\">Overview</a></li>\n      <li><a href=\"#ring-counter\" id=\"markdown-toc-ring-counter\">Ring counter</a></li>\n      <li><a href=\"#johnson-ring-counter\" id=\"markdown-toc-johnson-ring-counter\">Johnson ring counter</a></li>\n    </ol>\n  </li>\n</ol>\n\n<h2 id=\"introduction\">Introduction</h2>\n\n<p>A Flip-flop is a 1 bit memory cell which can be used for storing the digital data. \nTo increase the storage capacity in terms of number of bits, you can use a group of flip-flops. Such a group of flip-flops is known as a Register. \nThe n-bit register will consist of n number of flip-flop(s) and it is capable of storing an n-bit word.</p>\n\n<p>The binary-data, in a register, can be transfered within itself from one flip-flop to another. \nA shift register is a type of register that allows such data transfers.\nShift register has 4 modes of operations.</p>\n\n<p>Next, let us have a look at each register operation one by one.</p>\n\n<ol>\n  <li><a href=\"#serial-in-serial-out\">Serial-in serial-out</a></li>\n  <li><a href=\"#serial-in-parallel-out\">Serial-in parallel-out</a></li>\n  <li><a href=\"#parallel-in-serial-out\">Parallel-in serial-out</a></li>\n  <li><a href=\"#parallel-in-parallel-out\">Parallel-in parallel-out</a></li>\n</ol>\n\n<h2 id=\"serial-in-serial-out\">Serial-in serial-out</h2>\n\n<p>Let all the flip-flops be initially in the reset condition i.e. Q3 = Q2 = Q1 = Q0 = 0. If an entry of a four-bit binary number 1 1 1 1 is made into the register, this number should be applied to Din bit with the LSB bit applied first. The D input of FF-3 i.e. D3 is connected to serial data input Din. The output of FF-3 i.e. Q3 is connected to the input of the next flip-flop i.e. D2, and so on.</p>\n\n<h3 id=\"block-diagram\">Block diagram</h3>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_blockdiagram.jpg\" /></div>\n\n<h3 id=\"operation\">Operation</h3>\n\n<p>Before application of the clock signal, let Q3 Q2 Q1 Q0 = 0000 and apply the LSB bit of the number to Din. So Din = D3 = 1. Now, apply the clock. On the first falling edge of the clock, the FF-3 is set, and stored word in the register is Q3 Q2 Q1 Q0 = 1000.</p>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_operation1.jpg\" /></div>\n\n<p>Apply the next bit to Din. So Din = 1. As soon as the next negative edge of the clock gets triggered, FF-2 will set and the stored word change to Q3 Q2 Q1 Q0 = 1100.</p>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_operation2.jpg\" /></div>\n\n<p>Apply the next bit to be stored i.e. 1 to Din. Apply the clock pulse. As soon as the third negative clock edge gets triggered, FF-1 will be set and output will get modified to Q3 Q2 Q1 Q0 = 1110.</p>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_operation3.jpg\" /></div>\n\n<p>Similarly with Din = 1 and with the fourth negative clock edge arriving, the stored word in the register is Q3 Q2 Q1 Q0 = 1111.</p>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_operation4.jpg\" /></div>\n\n<h3 id=\"truth-table\">Truth table</h3>\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_truthtable.jpg\" /></div>\n\n<h3 id=\"waveforms\">Waveforms</h3>\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_waveform.jpg\" /></div>\n\n<iframe width=\"100%\" height=\"400px\" src=\"https://circuitverse.org/simulator/embed/93866\" id=\"ss_01\" scrolling=\"no\" webkitallowfullscreen=\"\" mozallowfullscreen=\"\" allowfullscreen=\"\"> </iframe>\n\n<h2 id=\"serial-in-parallel-out\">Serial-in parallel-out</h2>\n\n<ul>\n  <li>\n    <p>In such types of operations, the data is entered serially and taken out in parallel fashion.</p>\n  </li>\n  <li>\n    <p>Data is loaded bit-by-bit. The output(s) are disabled as long as the data is loading.</p>\n  </li>\n  <li>\n    <p>As soon as the data loading gets completed, all the flip-flops contain their required data. The output(s) are enabled so that all the loaded data is made available over all the output lines at the same time.</p>\n  </li>\n  <li>\n    <p>4 clock cycles are required to load a four-bit word. Hence the speed of operation of SIPO mode is the same as that of the SISO mode.</p>\n  </li>\n</ul>\n\n<h3 id=\"block-diagram-1\">Block diagram</h3>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/sipo_blockdiagram.jpg\" /></div>\n\n<iframe width=\"100%\" height=\"400px\" src=\"https://circuitverse.org/simulator/embed/93880\" id=\"sp_01\" scrolling=\"no\" webkitallowfullscreen=\"\" mozallowfullscreen=\"\" allowfullscreen=\"\"> </iframe>\n\n<h2 id=\"parallel-in-serial-out\">Parallel-in serial-out</h2>\n\n<ul>\n  <li>\n    <p>Data bits enter in a parallel fashion.</p>\n  </li>\n  <li>\n    <p>The circuit, shown below, is a four-bit parallel-in serial-out register.</p>\n  </li>\n  <li>\n    <p>Output of the previous flip Flop is connected to the input of the next one via a combinational circuit.</p>\n  </li>\n  <li>\n    <p>The binary input data bits B0, B1, B2, B3 are applied through the same combinational logic circuit.</p>\n  </li>\n  <li>\n    <p>There are two modes in which this circuit can work, namely - shift mode and load mode.</p>\n  </li>\n</ul>\n\n<h3 id=\"load-mode\">Load mode</h3>\n\n<p>When the shift/load bar line is low (0), the AND gates 2, 4 and 6 become active, and they will pass B1, B2, B3 bits to the corresponding flip-flops. \nOn the low going edge of the clock, the binary inputs B0, B1, B2, B3 will get loaded into the corresponding flip-flops. \nThus, the parallel loading takes place.</p>\n\n<h3 id=\"shift-mode\">Shift mode</h3>\n<p>When the shift/load bar line is low (1), the AND gates 2, 4 and 6 become inactive. \nHence, the parallel loading of the data becomes impossible. \nBut the AND gates 1,3 and 5 become active. \nTherefore the shifting of data takes place from left-to-right bit-by-bit on the application of clock pulses. \nThus, the parallel-in serial-out operation takes place.</p>\n\n<h3 id=\"block-diagram-2\">Block diagram</h3>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/piso_blockdiagram.jpg\" /></div>\n\n<iframe width=\"100%\" height=\"400px\" src=\"https://circuitverse.org/simulator/embed/93910\" id=\"ps_01\" scrolling=\"no\" webkitallowfullscreen=\"\" mozallowfullscreen=\"\" allowfullscreen=\"\"> </iframe>\n\n<h2 id=\"parallel-in-parallel-out\">Parallel-in parallel-out</h2>\n\n<p>Here, the 4-bit binary datda inputs B0, B1, B2, B3 are applied to the data inputs D0, D1, D2, D3, respectively, of the four flip-flops. \nWhen a negative edge of the clock is triggered, then the flip-flops get loaded with the input binary bits simultaneously. \nThe loaded bits appear at the output side, simultaneously, as well. \nOnly the clock pulse is essential to load all the binary bits.</p>\n\n<h3 id=\"block-diagram-3\">Block diagram</h3>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/pipo_blockdiagram.jpg\" /></div>\n\n<iframe width=\"100%\" height=\"400px\" src=\"https://circuitverse.org/simulator/embed/93890\" id=\"pp_01\" scrolling=\"no\" webkitallowfullscreen=\"\" mozallowfullscreen=\"\" allowfullscreen=\"\"> </iframe>\n\n<h2 id=\"applications-of-shift-registers\">Applications of shift registers</h2>\n\n<h3 id=\"overview\">Overview</h3>\n<p>Shift registers are sequential circuits used primarily used for:</p>\n<ol>\n  <li>Storage of Data</li>\n  <li>Data transfer through movement of binary data</li>\n  <li>Data manipulation</li>\n  <li>Counter implementation</li>\n</ol>\n\n<p>They are called <em>shift registers</em> as it moves or <em>shifts</em> binary input data to its output per clock cycle. Shift registers are commonly used to store data inside calculators. Even in computer systems, operations like addition, subtraction, division and multiplication are performed by registers.</p>\n\n<p>Shift registers can be applied in the following ways:</p>\n<ul>\n  <li>\n    <p><strong>Parallel to Serial conversion:</strong> Used in transmitters after analog to digital conversion in order to convert parallel input data into serial data</p>\n  </li>\n  <li>\n    <p><strong>Serial to Parallel conversion:</strong> Used in receivers before digital to anlogous conversion takes place in order to convert serial input data into parallel data</p>\n  </li>\n  <li>\n    <p><strong>Sequence Generator:</strong> Generate a sequence of 0s and 1s when combined with some additional gates</p>\n  </li>\n  <li>\n    <p><strong>Counters:</strong> Shift registers can be implemented as counters based on the output of the rightmost D flip-flop that is connected to the serial input, namely the <em>Ring Counter</em> and the <em>Johnson Ring Counter</em></p>\n  </li>\n  <li>\n    <p><a href=\"#serial-in-serial-out\">Serial-in Serial-out</a> registers are used for time delays</p>\n  </li>\n</ul>\n\n<h3 id=\"ring-counter\">Ring counter</h3>\n<p>Similar to how the <a href=\"#serial-in-serial-out\">Serial-in Serial-out</a> register requires <em>‘N’</em> clock pulses to shift <em>N</em> bit data, the <em>‘N’</em> Ring Counter produces a sequence of 0s and 1s, by having the rightmost D flip-flop as input to the leftmost D flip-flop as opposed to applying data externally. That is, the output of the last flip-flop is connected to the output of the first flip-flop in the ring. These patterns of states (0s and 1s) are repeated every <em>‘N’</em> clock cycles.</p>\n\n<p>The number of states in a Ring Counter are directly proportional to the number of flip-flops used.</p>\n\n<p>The block diagram of the 3-bit Ring counter is shown in the following figure.</p>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/ring_counter.jpg\" /></div>\n\n<p>A 3-bit Ring Counter will contain only a 3-bit SIPO shift register.</p>\n\n<p>Assume, the initial status of the D flip-flops from leftmost to rightmost is Q2Q1Q0=001. Here, Q2 &amp; Q0 are MSB &amp; LSB respectively. You can understand the working of Ring counter from the following table.</p>\n\n<table>\n  <thead>\n    <tr>\n      <th style=\"text-align: center\">No of positive edge of Clock</th>\n      <th style=\"text-align: center\">Serial Input = Q0</th>\n      <th style=\"text-align: center\">Q2(MSB)</th>\n      <th style=\"text-align: center\">Q1</th>\n      <th style=\"text-align: center\">Q0(LSB)</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">-</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">1</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">2</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">0</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">3</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">1</td>\n    </tr>\n  </tbody>\n</table>\n\n<p>Due to the absence of the clock signal, the initial status of the D flip-flops is Q2Q1Q0=001. This state will repeat every third positive edge transition of the clock signal.</p>\n\n<p>Similarly, the following operations take place every positive edge of the clock cycle:</p>\n<ul>\n  <li>\n    <p>Serial input of the first D flip-flop gets the previous output of the third flip-flop. Thus, the present output of the first D flip-flop is equal to the previous output of the third flip-flop.</p>\n  </li>\n  <li>\n    <p>The previous outputs of first and second D flip-flops are right-shifted by one bit. That implies that the present outputs of second and third D flip-flops are equal to the previous outputs of first and second D flip-flops.</p>\n  </li>\n</ul>\n\n<h3 id=\"johnson-ring-counter\">Johnson ring counter</h3>\n<p>The Johnson ring counter functions similarly to the Ring counter. The difference being that the complemented output of rightmost D flip-flop is given as input of leftmost D flip-flop instead of normal output. Thus, ‘N’ bit Johnson Ring counter produces a sequence of states (pattern of zeros and ones) and it repeats for every ‘2N’ clock cycles.</p>\n\n<p>Johnson ring counter is also called the <em>Twisted ring counter</em> and <em>Switch tail ring counter</em>. The block diagram of 3-bit Johnson Ring counter is shown in the following figure.</p>\n\n<div style=\"text-align:center\"><img src=\"/assets/images/twisted_ring_counter.jpg\" /></div>\n\n<p>The 3-bit Johnson Ring counter also contains only a 3-bit SIPO shift register.</p>\n\n<p>Assume, initially, all the D flip-flops are cleared. So, Q2Q1Q0=000. Here, Q2 is the MSB &amp; Q0 is the LSB.</p>\n\n<table>\n  <thead>\n    <tr>\n      <th style=\"text-align: center\">No of positive edge of Clock</th>\n      <th style=\"text-align: center\">Serial Input = Q0</th>\n      <th style=\"text-align: center\">Q2(MSB)</th>\n      <th style=\"text-align: center\">Q1</th>\n      <th style=\"text-align: center\">cQ0(LSB)</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">-</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">2</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">0</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">3</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">4</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">1</td>\n      <td style=\"text-align: center\">1</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">5</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">1</td>\n    </tr>\n    <tr>\n      <td style=\"text-align: center\">6</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n      <td style=\"text-align: center\">0</td>\n    </tr>\n  </tbody>\n</table>\n\n<p>The initial status of the D flip-flops in the absence of the clock signal is Q2Q1Q0=000. This status repeats for every six positive edge transitions of the clock signal.</p>\n\n<p>Similarly, the following operations take place for every positive edge of the clock signal.</p>\n<ul>\n  <li>Serial input of first D flip-flop gets the previous complemented output of the third flip-flop. So, the present output of the first D flip-flop is equal to the previous complemented output of the third flip-flop.</li>\n  <li>The previous outputs of first and second D flip-flops are right shifted by one bit. That means, the present outputs of second and third D flip-flops are equal to the previous outputs of first and second D flip-flops.</li>\n</ul>\n",
  "dir": "/docs/seq-msi/",
  "url": "/docs/seq-msi/registers.html",
  "raw_content": "# Registers\n{: .no_toc}\n\n\n## Table of contents\n{: .no_toc .text-delta}\n\n1. TOC\n{:toc}\n\n\n## Introduction\n\n\nA Flip-flop is a 1 bit memory cell which can be used for storing the digital data. \nTo increase the storage capacity in terms of number of bits, you can use a group of flip-flops. Such a group of flip-flops is known as a Register. \nThe n-bit register will consist of n number of flip-flop(s) and it is capable of storing an n-bit word.\n\n\nThe binary-data, in a register, can be transfered within itself from one flip-flop to another. \nA shift register is a type of register that allows such data transfers.\nShift register has 4 modes of operations.\n\nNext, let us have a look at each register operation one by one.\n\n1. [Serial-in serial-out](#serial-in-serial-out)\n2. [Serial-in parallel-out](#serial-in-parallel-out)\n3. [Parallel-in serial-out](#parallel-in-serial-out)\n4. [Parallel-in parallel-out](#parallel-in-parallel-out)\n\n\n## Serial-in serial-out\n\n \nLet all the flip-flops be initially in the reset condition i.e. Q3 = Q2 = Q1 = Q0 = 0. If an entry of a four-bit binary number 1 1 1 1 is made into the register, this number should be applied to Din bit with the LSB bit applied first. The D input of FF-3 i.e. D3 is connected to serial data input Din. The output of FF-3 i.e. Q3 is connected to the input of the next flip-flop i.e. D2, and so on.\n\n### Block diagram\n\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_blockdiagram.jpg\" /></div>\n\n### Operation\n\nBefore application of the clock signal, let Q3 Q2 Q1 Q0 = 0000 and apply the LSB bit of the number to Din. So Din = D3 = 1. Now, apply the clock. On the first falling edge of the clock, the FF-3 is set, and stored word in the register is Q3 Q2 Q1 Q0 = 1000.\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_operation1.jpg\" /></div>\n\nApply the next bit to Din. So Din = 1. As soon as the next negative edge of the clock gets triggered, FF-2 will set and the stored word change to Q3 Q2 Q1 Q0 = 1100.\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_operation2.jpg\" /></div>\n\nApply the next bit to be stored i.e. 1 to Din. Apply the clock pulse. As soon as the third negative clock edge gets triggered, FF-1 will be set and output will get modified to Q3 Q2 Q1 Q0 = 1110.\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_operation3.jpg\" /></div>\n\nSimilarly with Din = 1 and with the fourth negative clock edge arriving, the stored word in the register is Q3 Q2 Q1 Q0 = 1111.\n\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_operation4.jpg\" /></div>\n\n### Truth table\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_truthtable.jpg\" /></div>\n\n### Waveforms\n<div style=\"text-align:center\"><img src=\"/assets/images/siso_waveform.jpg\" /></div>\n\n<iframe width=\"100%\" height=\"400px\" src=\"https://circuitverse.org/simulator/embed/93866\" id=\"ss_01\" scrolling=\"no\" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>\n\n\n## Serial-in parallel-out\n\n\n- In such types of operations, the data is entered serially and taken out in parallel fashion.\n\n- Data is loaded bit-by-bit. The output(s) are disabled as long as the data is loading.\n\n- As soon as the data loading gets completed, all the flip-flops contain their required data. The output(s) are enabled so that all the loaded data is made available over all the output lines at the same time.\n\n- 4 clock cycles are required to load a four-bit word. Hence the speed of operation of SIPO mode is the same as that of the SISO mode.\n\n### Block diagram\n\n\n<div style=\"text-align:center\"><img src=\"/assets/images/sipo_blockdiagram.jpg\" /></div>\n\n<iframe width=\"100%\" height=\"400px\" src=\"https://circuitverse.org/simulator/embed/93880\" id=\"sp_01\" scrolling=\"no\" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>\n\n\n## Parallel-in serial-out\n\n\n \n- Data bits enter in a parallel fashion.\n\n- The circuit, shown below, is a four-bit parallel-in serial-out register.\n\n- Output of the previous flip Flop is connected to the input of the next one via a combinational circuit.\n\n- The binary input data bits B0, B1, B2, B3 are applied through the same combinational logic circuit.\n\n- There are two modes in which this circuit can work, namely - shift mode and load mode.\n\n### Load mode\n\nWhen the shift/load bar line is low (0), the AND gates 2, 4 and 6 become active, and they will pass B1, B2, B3 bits to the corresponding flip-flops. \nOn the low going edge of the clock, the binary inputs B0, B1, B2, B3 will get loaded into the corresponding flip-flops. \nThus, the parallel loading takes place.\n\n### Shift mode\nWhen the shift/load bar line is low (1), the AND gates 2, 4 and 6 become inactive. \nHence, the parallel loading of the data becomes impossible. \nBut the AND gates 1,3 and 5 become active. \nTherefore the shifting of data takes place from left-to-right bit-by-bit on the application of clock pulses. \nThus, the parallel-in serial-out operation takes place.\n\n### Block diagram\n\n\n<div style=\"text-align:center\"><img src=\"/assets/images/piso_blockdiagram.jpg\" /></div>\n\n<iframe width=\"100%\" height=\"400px\" src=\"https://circuitverse.org/simulator/embed/93910\" id=\"ps_01\" scrolling=\"no\" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>\n\n\n## Parallel-in parallel-out\n\n \nHere, the 4-bit binary datda inputs B0, B1, B2, B3 are applied to the data inputs D0, D1, D2, D3, respectively, of the four flip-flops. \nWhen a negative edge of the clock is triggered, then the flip-flops get loaded with the input binary bits simultaneously. \nThe loaded bits appear at the output side, simultaneously, as well. \nOnly the clock pulse is essential to load all the binary bits.\n\n\n\n### Block diagram\n\n\n<div style=\"text-align:center\"><img src=\"/assets/images/pipo_blockdiagram.jpg\" /></div>\n\n<iframe width=\"100%\" height=\"400px\" src=\"https://circuitverse.org/simulator/embed/93890\" id=\"pp_01\" scrolling=\"no\" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>\n\n\n## Applications of shift registers\n\n### Overview\nShift registers are sequential circuits used primarily used for:\n1. Storage of Data\n2. Data transfer through movement of binary data\n3. Data manipulation\n4. Counter implementation\n\nThey are called *shift registers* as it moves or *shifts* binary input data to its output per clock cycle. Shift registers are commonly used to store data inside calculators. Even in computer systems, operations like addition, subtraction, division and multiplication are performed by registers.\n\nShift registers can be applied in the following ways:\n- **Parallel to Serial conversion:** Used in transmitters after analog to digital conversion in order to convert parallel input data into serial data\n\n- **Serial to Parallel conversion:** Used in receivers before digital to anlogous conversion takes place in order to convert serial input data into parallel data\n\n- **Sequence Generator:** Generate a sequence of 0s and 1s when combined with some additional gates\n\n- **Counters:** Shift registers can be implemented as counters based on the output of the rightmost D flip-flop that is connected to the serial input, namely the *Ring Counter* and the *Johnson Ring Counter*\n\n- [Serial-in Serial-out](#serial-in-serial-out) registers are used for time delays\n\n\n### Ring counter\nSimilar to how the [Serial-in Serial-out](#serial-in-serial-out) register requires *'N'* clock pulses to shift *N* bit data, the *'N'* Ring Counter produces a sequence of 0s and 1s, by having the rightmost D flip-flop as input to the leftmost D flip-flop as opposed to applying data externally. That is, the output of the last flip-flop is connected to the output of the first flip-flop in the ring. These patterns of states (0s and 1s) are repeated every *'N'* clock cycles.\n\nThe number of states in a Ring Counter are directly proportional to the number of flip-flops used.\n\nThe block diagram of the 3-bit Ring counter is shown in the following figure.\n\n<div style=\"text-align:center\"><img src=\"/assets/images/ring_counter.jpg\" /></div>\n\nA 3-bit Ring Counter will contain only a 3-bit SIPO shift register.\n\nAssume, the initial status of the D flip-flops from leftmost to rightmost is Q2Q1Q0=001. Here, Q2 & Q0 are MSB & LSB respectively. You can understand the working of Ring counter from the following table.\n\n|No of positive edge of Clock|  Serial Input = Q0 | Q2(MSB) |   Q1   |Q0(LSB)|\n|:--------------------------:|:------------------:|:-------:|:------:|:-----:|\n|0  |-  |0  |0  |1  |\n|1  |1  |1  |0  |0  |\n|2  |0  |0  |1  |0  |\n|3  |0  |0  |0  |1  |\n\n\nDue to the absence of the clock signal, the initial status of the D flip-flops is Q2Q1Q0=001. This state will repeat every third positive edge transition of the clock signal.\n\nSimilarly, the following operations take place every positive edge of the clock cycle:\n- Serial input of the first D flip-flop gets the previous output of the third flip-flop. Thus, the present output of the first D flip-flop is equal to the previous output of the third flip-flop.\n\n- The previous outputs of first and second D flip-flops are right-shifted by one bit. That implies that the present outputs of second and third D flip-flops are equal to the previous outputs of first and second D flip-flops.\n\n### Johnson ring counter\nThe Johnson ring counter functions similarly to the Ring counter. The difference being that the complemented output of rightmost D flip-flop is given as input of leftmost D flip-flop instead of normal output. Thus, ‘N’ bit Johnson Ring counter produces a sequence of states (pattern of zeros and ones) and it repeats for every ‘2N’ clock cycles.\n\nJohnson ring counter is also called the *Twisted ring counter* and *Switch tail ring counter*. The block diagram of 3-bit Johnson Ring counter is shown in the following figure.\n\n<div style=\"text-align:center\"><img src=\"/assets/images/twisted_ring_counter.jpg\" /></div>\n\nThe 3-bit Johnson Ring counter also contains only a 3-bit SIPO shift register.\n\nAssume, initially, all the D flip-flops are cleared. So, Q2Q1Q0=000. Here, Q2 is the MSB & Q0 is the LSB.\n\n|No of positive edge of Clock|  Serial Input = Q0 | Q2(MSB) |   Q1   |cQ0(LSB)|\n|:--------------------------:|:------------------:|:-------:|:------:|:------:|\n|0  |-  |0  |0  |0  |\n|1  |1  |1  |0  |0  |\n|2  |1  |1  |1  |0  |\n|3  |1  |1  |1  |1  |\n|4  |0  |0  |1  |1  |\n|5  |0  |0  |0  |1  |\n|6  |0  |0  |0  |0  |\n\n\nThe initial status of the D flip-flops in the absence of the clock signal is Q2Q1Q0=000. This status repeats for every six positive edge transitions of the clock signal.\n\nSimilarly, the following operations take place for every positive edge of the clock signal.\n- Serial input of first D flip-flop gets the previous complemented output of the third flip-flop. So, the present output of the first D flip-flop is equal to the previous complemented output of the third flip-flop.\n- The previous outputs of first and second D flip-flops are right shifted by one bit. That means, the present outputs of second and third D flip-flops are equal to the previous outputs of first and second D flip-flops.\n",
  "front_matter": {
    "layout": "circuitverse",
    "title": "Registers",
    "nav_order": "l0s000",
    "cvib_level": "basic",
    "parent": "Sequential MSI",
    "has_children": false
  },
  "front_matter_defaults": {
  },
  "http_url": "https://learn.circuitverse.org/docs/seq-msi/registers.html",
  "api_url": "https://learn.circuitverse.org/_api/pages/docs/seq-msi/registers.md"
}