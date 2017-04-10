                                      1 ;--------------------------------------------------------
                                      2 ; File Created by SDCC : free open source ANSI-C Compiler
                                      3 ; Version 3.4.0 #8981 (Jul 11 2014) (Linux)
                                      4 ; This file was generated Mon Apr 10 16:17:21 2017
                                      5 ;--------------------------------------------------------
                                      6 	.module sensors
                                      7 	.optsdcc -mstm8
                                      8 	
                                      9 ;--------------------------------------------------------
                                     10 ; Public variables in this module
                                     11 ;--------------------------------------------------------
                                     12 	.globl _segmentMap
                                     13 	.globl _main
                                     14 	.globl _clock
                                     15 	.globl _tm1637DisplayDecimal
                                     16 	.globl _tm1637Init
                                     17 	.globl _InitializeUART
                                     18 	.globl _InitializeI2C
                                     19 	.globl _i2c_read_register
                                     20 	.globl _print_byte_hex
                                     21 	.globl _i2c_set_start_ack
                                     22 	.globl _i2c_send_address
                                     23 	.globl _print_UCHAR_hex
                                     24 	.globl _UARTPrintF
                                     25 	.globl _i2c_send_reg
                                     26 	.globl _i2c_set_stop
                                     27 	.globl _i2c_set_nak
                                     28 	.globl _i2c_read
                                     29 	.globl _delay
                                     30 	.globl _InitializeSystemClock
                                     31 	.globl _delayTenMicro
                                     32 	.globl _tm1637SetBrightness
                                     33 	.globl __tm1637Start
                                     34 	.globl __tm1637Stop
                                     35 	.globl __tm1637ReadResult
                                     36 	.globl __tm1637WriteByte
                                     37 	.globl __tm1637ClkHigh
                                     38 	.globl __tm1637ClkLow
                                     39 	.globl __tm1637DioHigh
                                     40 	.globl __tm1637DioLow
                                     41 ;--------------------------------------------------------
                                     42 ; ram data
                                     43 ;--------------------------------------------------------
                                     44 	.area DATA
                                     45 ;--------------------------------------------------------
                                     46 ; ram data
                                     47 ;--------------------------------------------------------
                                     48 	.area INITIALIZED
                                     49 ;--------------------------------------------------------
                                     50 ; Stack segment in internal ram 
                                     51 ;--------------------------------------------------------
                                     52 	.area	SSEG
      000000                         53 __start__stack:
      000000                         54 	.ds	1
                                     55 
                                     56 ;--------------------------------------------------------
                                     57 ; absolute external ram data
                                     58 ;--------------------------------------------------------
                                     59 	.area DABS (ABS)
                                     60 ;--------------------------------------------------------
                                     61 ; interrupt vector 
                                     62 ;--------------------------------------------------------
                                     63 	.area HOME
      008000                         64 __interrupt_vect:
      008000 82 00 80 83             65 	int s_GSINIT ;reset
      008004 82 00 00 00             66 	int 0x0000 ;trap
      008008 82 00 00 00             67 	int 0x0000 ;int0
      00800C 82 00 00 00             68 	int 0x0000 ;int1
      008010 82 00 00 00             69 	int 0x0000 ;int2
      008014 82 00 00 00             70 	int 0x0000 ;int3
      008018 82 00 00 00             71 	int 0x0000 ;int4
      00801C 82 00 00 00             72 	int 0x0000 ;int5
      008020 82 00 00 00             73 	int 0x0000 ;int6
      008024 82 00 00 00             74 	int 0x0000 ;int7
      008028 82 00 00 00             75 	int 0x0000 ;int8
      00802C 82 00 00 00             76 	int 0x0000 ;int9
      008030 82 00 00 00             77 	int 0x0000 ;int10
      008034 82 00 00 00             78 	int 0x0000 ;int11
      008038 82 00 00 00             79 	int 0x0000 ;int12
      00803C 82 00 00 00             80 	int 0x0000 ;int13
      008040 82 00 00 00             81 	int 0x0000 ;int14
      008044 82 00 00 00             82 	int 0x0000 ;int15
      008048 82 00 00 00             83 	int 0x0000 ;int16
      00804C 82 00 00 00             84 	int 0x0000 ;int17
      008050 82 00 00 00             85 	int 0x0000 ;int18
      008054 82 00 00 00             86 	int 0x0000 ;int19
      008058 82 00 00 00             87 	int 0x0000 ;int20
      00805C 82 00 00 00             88 	int 0x0000 ;int21
      008060 82 00 00 00             89 	int 0x0000 ;int22
      008064 82 00 00 00             90 	int 0x0000 ;int23
      008068 82 00 00 00             91 	int 0x0000 ;int24
      00806C 82 00 00 00             92 	int 0x0000 ;int25
      008070 82 00 00 00             93 	int 0x0000 ;int26
      008074 82 00 00 00             94 	int 0x0000 ;int27
      008078 82 00 00 00             95 	int 0x0000 ;int28
      00807C 82 00 00 00             96 	int 0x0000 ;int29
                                     97 ;--------------------------------------------------------
                                     98 ; global & static initialisations
                                     99 ;--------------------------------------------------------
                                    100 	.area HOME
                                    101 	.area GSINIT
                                    102 	.area GSFINAL
                                    103 	.area GSINIT
      008083                        104 __sdcc_gs_init_startup:
      008083                        105 __sdcc_init_data:
                                    106 ; stm8_genXINIT() start
      008083 AE 00 00         [ 2]  107 	ldw x, #l_DATA
      008086 27 07            [ 1]  108 	jreq	00002$
      008088                        109 00001$:
      008088 72 4F 00 00      [ 1]  110 	clr (s_DATA - 1, x)
      00808C 5A               [ 2]  111 	decw x
      00808D 26 F9            [ 1]  112 	jrne	00001$
      00808F                        113 00002$:
      00808F AE 00 00         [ 2]  114 	ldw	x, #l_INITIALIZER
      008092 27 09            [ 1]  115 	jreq	00004$
      008094                        116 00003$:
      008094 D6 86 4E         [ 1]  117 	ld	a, (s_INITIALIZER - 1, x)
      008097 D7 00 00         [ 1]  118 	ld	(s_INITIALIZED - 1, x), a
      00809A 5A               [ 2]  119 	decw	x
      00809B 26 F7            [ 1]  120 	jrne	00003$
      00809D                        121 00004$:
                                    122 ; stm8_genXINIT() end
                                    123 	.area GSFINAL
      00809D CC 80 80         [ 2]  124 	jp	__sdcc_program_startup
                                    125 ;--------------------------------------------------------
                                    126 ; Home
                                    127 ;--------------------------------------------------------
                                    128 	.area HOME
                                    129 	.area HOME
      008080                        130 __sdcc_program_startup:
      008080 CC 85 01         [ 2]  131 	jp	_main
                                    132 ;	return from main will return to caller
                                    133 ;--------------------------------------------------------
                                    134 ; code
                                    135 ;--------------------------------------------------------
                                    136 	.area CODE
                                    137 ;	sensors.c: 15: void delayTenMicro (void) {
                                    138 ;	-----------------------------------------
                                    139 ;	 function delayTenMicro
                                    140 ;	-----------------------------------------
      0080A0                        141 _delayTenMicro:
                                    142 ;	sensors.c: 17: for (a = 0; a < 50; ++a)
      0080A0 A6 32            [ 1]  143 	ld	a, #0x32
      0080A2                        144 00104$:
                                    145 ;	sensors.c: 18: __asm__("nop");
      0080A2 9D               [ 1]  146 	nop
      0080A3 4A               [ 1]  147 	dec	a
                                    148 ;	sensors.c: 17: for (a = 0; a < 50; ++a)
      0080A4 4D               [ 1]  149 	tnz	a
      0080A5 26 FB            [ 1]  150 	jrne	00104$
      0080A7 81               [ 4]  151 	ret
                                    152 ;	sensors.c: 21: void InitializeSystemClock() {
                                    153 ;	-----------------------------------------
                                    154 ;	 function InitializeSystemClock
                                    155 ;	-----------------------------------------
      0080A8                        156 _InitializeSystemClock:
                                    157 ;	sensors.c: 22: CLK_ICKR = 0;                       //  Reset the Internal Clock Register.
      0080A8 AE 50 C0         [ 2]  158 	ldw	x, #0x50c0
      0080AB 7F               [ 1]  159 	clr	(x)
                                    160 ;	sensors.c: 23: CLK_ICKR = CLK_HSIEN;               //  Enable the HSI.
      0080AC AE 50 C0         [ 2]  161 	ldw	x, #0x50c0
      0080AF A6 01            [ 1]  162 	ld	a, #0x01
      0080B1 F7               [ 1]  163 	ld	(x), a
                                    164 ;	sensors.c: 24: CLK_ECKR = 0;                       //  Disable the external clock.
      0080B2 AE 50 C1         [ 2]  165 	ldw	x, #0x50c1
      0080B5 7F               [ 1]  166 	clr	(x)
                                    167 ;	sensors.c: 25: while ((CLK_ICKR & CLK_HSIRDY) == 0);       //  Wait for the HSI to be ready for use.
      0080B6                        168 00101$:
      0080B6 AE 50 C0         [ 2]  169 	ldw	x, #0x50c0
      0080B9 F6               [ 1]  170 	ld	a, (x)
      0080BA A5 02            [ 1]  171 	bcp	a, #0x02
      0080BC 27 F8            [ 1]  172 	jreq	00101$
                                    173 ;	sensors.c: 26: CLK_CKDIVR = 0;                     //  Ensure the clocks are running at full speed.
      0080BE AE 50 C6         [ 2]  174 	ldw	x, #0x50c6
      0080C1 7F               [ 1]  175 	clr	(x)
                                    176 ;	sensors.c: 27: CLK_PCKENR1 = 0xff;                 //  Enable all peripheral clocks.
      0080C2 AE 50 C7         [ 2]  177 	ldw	x, #0x50c7
      0080C5 A6 FF            [ 1]  178 	ld	a, #0xff
      0080C7 F7               [ 1]  179 	ld	(x), a
                                    180 ;	sensors.c: 28: CLK_PCKENR2 = 0xff;                 //  Ditto.
      0080C8 AE 50 CA         [ 2]  181 	ldw	x, #0x50ca
      0080CB A6 FF            [ 1]  182 	ld	a, #0xff
      0080CD F7               [ 1]  183 	ld	(x), a
                                    184 ;	sensors.c: 29: CLK_CCOR = 0;                       //  Turn off CCO.
      0080CE AE 50 C9         [ 2]  185 	ldw	x, #0x50c9
      0080D1 7F               [ 1]  186 	clr	(x)
                                    187 ;	sensors.c: 30: CLK_HSITRIMR = 0;                   //  Turn off any HSIU trimming.
      0080D2 AE 50 CC         [ 2]  188 	ldw	x, #0x50cc
      0080D5 7F               [ 1]  189 	clr	(x)
                                    190 ;	sensors.c: 31: CLK_SWIMCCR = 0;                    //  Set SWIM to run at clock / 2.
      0080D6 AE 50 CD         [ 2]  191 	ldw	x, #0x50cd
      0080D9 7F               [ 1]  192 	clr	(x)
                                    193 ;	sensors.c: 32: CLK_SWR = 0xe1;                     //  Use HSI as the clock source.
      0080DA AE 50 C4         [ 2]  194 	ldw	x, #0x50c4
      0080DD A6 E1            [ 1]  195 	ld	a, #0xe1
      0080DF F7               [ 1]  196 	ld	(x), a
                                    197 ;	sensors.c: 33: CLK_SWCR = 0;                       //  Reset the clock switch control register.
      0080E0 AE 50 C5         [ 2]  198 	ldw	x, #0x50c5
      0080E3 7F               [ 1]  199 	clr	(x)
                                    200 ;	sensors.c: 34: CLK_SWCR = CLK_SWEN;                //  Enable switching.
      0080E4 AE 50 C5         [ 2]  201 	ldw	x, #0x50c5
      0080E7 A6 02            [ 1]  202 	ld	a, #0x02
      0080E9 F7               [ 1]  203 	ld	(x), a
                                    204 ;	sensors.c: 35: while ((CLK_SWCR & CLK_SWBSY) != 0);        //  Pause while the clock switch is busy.
      0080EA                        205 00104$:
      0080EA AE 50 C5         [ 2]  206 	ldw	x, #0x50c5
      0080ED F6               [ 1]  207 	ld	a, (x)
      0080EE 44               [ 1]  208 	srl	a
      0080EF 25 F9            [ 1]  209 	jrc	00104$
      0080F1 81               [ 4]  210 	ret
                                    211 ;	sensors.c: 37: void delay (int time_ms) {
                                    212 ;	-----------------------------------------
                                    213 ;	 function delay
                                    214 ;	-----------------------------------------
      0080F2                        215 _delay:
      0080F2 52 0A            [ 2]  216 	sub	sp, #10
                                    217 ;	sensors.c: 39: for (x = 0; x < 1036*time_ms; ++x)
      0080F4 5F               [ 1]  218 	clrw	x
      0080F5 1F 03            [ 2]  219 	ldw	(0x03, sp), x
      0080F7 1F 01            [ 2]  220 	ldw	(0x01, sp), x
      0080F9 1E 0D            [ 2]  221 	ldw	x, (0x0d, sp)
      0080FB 89               [ 2]  222 	pushw	x
      0080FC 4B 0C            [ 1]  223 	push	#0x0c
      0080FE 4B 04            [ 1]  224 	push	#0x04
      008100 CD 85 F9         [ 4]  225 	call	__mulint
      008103 5B 04            [ 2]  226 	addw	sp, #4
      008105 1F 09            [ 2]  227 	ldw	(0x09, sp), x
      008107                        228 00103$:
      008107 16 09            [ 2]  229 	ldw	y, (0x09, sp)
      008109 17 07            [ 2]  230 	ldw	(0x07, sp), y
      00810B 7B 07            [ 1]  231 	ld	a, (0x07, sp)
      00810D 49               [ 1]  232 	rlc	a
      00810E 4F               [ 1]  233 	clr	a
      00810F A2 00            [ 1]  234 	sbc	a, #0x00
      008111 6B 06            [ 1]  235 	ld	(0x06, sp), a
      008113 6B 05            [ 1]  236 	ld	(0x05, sp), a
      008115 1E 03            [ 2]  237 	ldw	x, (0x03, sp)
      008117 13 07            [ 2]  238 	cpw	x, (0x07, sp)
      008119 7B 02            [ 1]  239 	ld	a, (0x02, sp)
      00811B 12 06            [ 1]  240 	sbc	a, (0x06, sp)
      00811D 7B 01            [ 1]  241 	ld	a, (0x01, sp)
      00811F 12 05            [ 1]  242 	sbc	a, (0x05, sp)
      008121 2E 17            [ 1]  243 	jrsge	00105$
                                    244 ;	sensors.c: 40: __asm__("nop");
      008123 9D               [ 1]  245 	nop
                                    246 ;	sensors.c: 39: for (x = 0; x < 1036*time_ms; ++x)
      008124 16 03            [ 2]  247 	ldw	y, (0x03, sp)
      008126 72 A9 00 01      [ 2]  248 	addw	y, #0x0001
      00812A 7B 02            [ 1]  249 	ld	a, (0x02, sp)
      00812C A9 00            [ 1]  250 	adc	a, #0x00
      00812E 97               [ 1]  251 	ld	xl, a
      00812F 7B 01            [ 1]  252 	ld	a, (0x01, sp)
      008131 A9 00            [ 1]  253 	adc	a, #0x00
      008133 95               [ 1]  254 	ld	xh, a
      008134 17 03            [ 2]  255 	ldw	(0x03, sp), y
      008136 1F 01            [ 2]  256 	ldw	(0x01, sp), x
      008138 20 CD            [ 2]  257 	jra	00103$
      00813A                        258 00105$:
      00813A 5B 0A            [ 2]  259 	addw	sp, #10
      00813C 81               [ 4]  260 	ret
                                    261 ;	sensors.c: 42: void i2c_read (unsigned char *x) {
                                    262 ;	-----------------------------------------
                                    263 ;	 function i2c_read
                                    264 ;	-----------------------------------------
      00813D                        265 _i2c_read:
                                    266 ;	sensors.c: 43: while ((I2C_SR1 & I2C_RXNE) == 0);
      00813D                        267 00101$:
      00813D AE 52 17         [ 2]  268 	ldw	x, #0x5217
      008140 F6               [ 1]  269 	ld	a, (x)
      008141 A5 40            [ 1]  270 	bcp	a, #0x40
      008143 27 F8            [ 1]  271 	jreq	00101$
                                    272 ;	sensors.c: 44: *x = I2C_DR;
      008145 16 03            [ 2]  273 	ldw	y, (0x03, sp)
      008147 AE 52 16         [ 2]  274 	ldw	x, #0x5216
      00814A F6               [ 1]  275 	ld	a, (x)
      00814B 90 F7            [ 1]  276 	ld	(y), a
      00814D 81               [ 4]  277 	ret
                                    278 ;	sensors.c: 46: void i2c_set_nak (void) {
                                    279 ;	-----------------------------------------
                                    280 ;	 function i2c_set_nak
                                    281 ;	-----------------------------------------
      00814E                        282 _i2c_set_nak:
                                    283 ;	sensors.c: 47: I2C_CR2 &= ~I2C_ACK;
      00814E AE 52 11         [ 2]  284 	ldw	x, #0x5211
      008151 F6               [ 1]  285 	ld	a, (x)
      008152 A4 FB            [ 1]  286 	and	a, #0xfb
      008154 F7               [ 1]  287 	ld	(x), a
      008155 81               [ 4]  288 	ret
                                    289 ;	sensors.c: 49: void i2c_set_stop (void) {
                                    290 ;	-----------------------------------------
                                    291 ;	 function i2c_set_stop
                                    292 ;	-----------------------------------------
      008156                        293 _i2c_set_stop:
                                    294 ;	sensors.c: 50: I2C_CR2 |= I2C_STOP;
      008156 AE 52 11         [ 2]  295 	ldw	x, #0x5211
      008159 F6               [ 1]  296 	ld	a, (x)
      00815A AA 02            [ 1]  297 	or	a, #0x02
      00815C F7               [ 1]  298 	ld	(x), a
      00815D 81               [ 4]  299 	ret
                                    300 ;	sensors.c: 52: void i2c_send_reg (UCHAR addr) {
                                    301 ;	-----------------------------------------
                                    302 ;	 function i2c_send_reg
                                    303 ;	-----------------------------------------
      00815E                        304 _i2c_send_reg:
      00815E 52 02            [ 2]  305 	sub	sp, #2
                                    306 ;	sensors.c: 54: reg = I2C_SR1;
      008160 AE 52 17         [ 2]  307 	ldw	x, #0x5217
      008163 F6               [ 1]  308 	ld	a, (x)
      008164 5F               [ 1]  309 	clrw	x
      008165 97               [ 1]  310 	ld	xl, a
      008166 1F 01            [ 2]  311 	ldw	(0x01, sp), x
                                    312 ;	sensors.c: 55: reg = I2C_SR3;
      008168 AE 52 19         [ 2]  313 	ldw	x, #0x5219
      00816B F6               [ 1]  314 	ld	a, (x)
      00816C 5F               [ 1]  315 	clrw	x
      00816D 97               [ 1]  316 	ld	xl, a
      00816E 1F 01            [ 2]  317 	ldw	(0x01, sp), x
                                    318 ;	sensors.c: 56: I2C_DR = addr;
      008170 AE 52 16         [ 2]  319 	ldw	x, #0x5216
      008173 7B 05            [ 1]  320 	ld	a, (0x05, sp)
      008175 F7               [ 1]  321 	ld	(x), a
                                    322 ;	sensors.c: 57: while ((I2C_SR1 & I2C_TXE) == 0);
      008176                        323 00101$:
      008176 AE 52 17         [ 2]  324 	ldw	x, #0x5217
      008179 F6               [ 1]  325 	ld	a, (x)
      00817A 48               [ 1]  326 	sll	a
      00817B 24 F9            [ 1]  327 	jrnc	00101$
      00817D 5B 02            [ 2]  328 	addw	sp, #2
      00817F 81               [ 4]  329 	ret
                                    330 ;	sensors.c: 61: void UARTPrintF (char *message) {
                                    331 ;	-----------------------------------------
                                    332 ;	 function UARTPrintF
                                    333 ;	-----------------------------------------
      008180                        334 _UARTPrintF:
                                    335 ;	sensors.c: 62: char *ch = message;
      008180 16 03            [ 2]  336 	ldw	y, (0x03, sp)
                                    337 ;	sensors.c: 63: while (*ch) {
      008182                        338 00104$:
      008182 90 F6            [ 1]  339 	ld	a, (y)
      008184 4D               [ 1]  340 	tnz	a
      008185 27 0F            [ 1]  341 	jreq	00107$
                                    342 ;	sensors.c: 64: UART1_DR = (unsigned char) *ch;     //  Put the next character into the data transmission register.
      008187 AE 52 31         [ 2]  343 	ldw	x, #0x5231
      00818A F7               [ 1]  344 	ld	(x), a
                                    345 ;	sensors.c: 65: while ((UART1_SR & SR_TXE) == 0);   //  Wait for transmission to complete.
      00818B                        346 00101$:
      00818B AE 52 30         [ 2]  347 	ldw	x, #0x5230
      00818E F6               [ 1]  348 	ld	a, (x)
      00818F 48               [ 1]  349 	sll	a
      008190 24 F9            [ 1]  350 	jrnc	00101$
                                    351 ;	sensors.c: 66: ch++;                               //  Grab the next character.
      008192 90 5C            [ 2]  352 	incw	y
      008194 20 EC            [ 2]  353 	jra	00104$
      008196                        354 00107$:
      008196 81               [ 4]  355 	ret
                                    356 ;	sensors.c: 70: void print_UCHAR_hex (unsigned char buffer) {
                                    357 ;	-----------------------------------------
                                    358 ;	 function print_UCHAR_hex
                                    359 ;	-----------------------------------------
      008197                        360 _print_UCHAR_hex:
      008197 52 0C            [ 2]  361 	sub	sp, #12
                                    362 ;	sensors.c: 73: a = (buffer >> 4);
      008199 7B 0F            [ 1]  363 	ld	a, (0x0f, sp)
      00819B 4E               [ 1]  364 	swap	a
      00819C A4 0F            [ 1]  365 	and	a, #0x0f
      00819E 5F               [ 1]  366 	clrw	x
      00819F 97               [ 1]  367 	ld	xl, a
                                    368 ;	sensors.c: 74: if (a > 9)
      0081A0 A3 00 09         [ 2]  369 	cpw	x, #0x0009
      0081A3 2D 07            [ 1]  370 	jrsle	00102$
                                    371 ;	sensors.c: 75: a = a + 'a' - 10;
      0081A5 1C 00 57         [ 2]  372 	addw	x, #0x0057
      0081A8 1F 01            [ 2]  373 	ldw	(0x01, sp), x
      0081AA 20 05            [ 2]  374 	jra	00103$
      0081AC                        375 00102$:
                                    376 ;	sensors.c: 77: a += '0';
      0081AC 1C 00 30         [ 2]  377 	addw	x, #0x0030
      0081AF 1F 01            [ 2]  378 	ldw	(0x01, sp), x
      0081B1                        379 00103$:
                                    380 ;	sensors.c: 78: b = buffer & 0x0f;
      0081B1 7B 0F            [ 1]  381 	ld	a, (0x0f, sp)
      0081B3 A4 0F            [ 1]  382 	and	a, #0x0f
      0081B5 5F               [ 1]  383 	clrw	x
      0081B6 97               [ 1]  384 	ld	xl, a
                                    385 ;	sensors.c: 79: if (b > 9)
      0081B7 A3 00 09         [ 2]  386 	cpw	x, #0x0009
      0081BA 2D 07            [ 1]  387 	jrsle	00105$
                                    388 ;	sensors.c: 80: b = b + 'a' - 10;
      0081BC 1C 00 57         [ 2]  389 	addw	x, #0x0057
      0081BF 1F 0B            [ 2]  390 	ldw	(0x0b, sp), x
      0081C1 20 05            [ 2]  391 	jra	00106$
      0081C3                        392 00105$:
                                    393 ;	sensors.c: 82: b += '0';
      0081C3 1C 00 30         [ 2]  394 	addw	x, #0x0030
      0081C6 1F 0B            [ 2]  395 	ldw	(0x0b, sp), x
      0081C8                        396 00106$:
                                    397 ;	sensors.c: 83: message[0] = a;
      0081C8 90 96            [ 1]  398 	ldw	y, sp
      0081CA 72 A9 00 03      [ 2]  399 	addw	y, #3
      0081CE 7B 02            [ 1]  400 	ld	a, (0x02, sp)
      0081D0 90 F7            [ 1]  401 	ld	(y), a
                                    402 ;	sensors.c: 84: message[1] = b;
      0081D2 93               [ 1]  403 	ldw	x, y
      0081D3 5C               [ 2]  404 	incw	x
      0081D4 7B 0C            [ 1]  405 	ld	a, (0x0c, sp)
      0081D6 F7               [ 1]  406 	ld	(x), a
                                    407 ;	sensors.c: 85: message[2] = 0;
      0081D7 93               [ 1]  408 	ldw	x, y
      0081D8 5C               [ 2]  409 	incw	x
      0081D9 5C               [ 2]  410 	incw	x
      0081DA 7F               [ 1]  411 	clr	(x)
                                    412 ;	sensors.c: 86: UARTPrintF (message);
      0081DB 90 89            [ 2]  413 	pushw	y
      0081DD CD 81 80         [ 4]  414 	call	_UARTPrintF
      0081E0 5B 02            [ 2]  415 	addw	sp, #2
      0081E2 5B 0C            [ 2]  416 	addw	sp, #12
      0081E4 81               [ 4]  417 	ret
                                    418 ;	sensors.c: 89: void i2c_send_address (UCHAR addr, UCHAR mode) {
                                    419 ;	-----------------------------------------
                                    420 ;	 function i2c_send_address
                                    421 ;	-----------------------------------------
      0081E5                        422 _i2c_send_address:
      0081E5 52 03            [ 2]  423 	sub	sp, #3
                                    424 ;	sensors.c: 91: reg = I2C_SR1;
      0081E7 AE 52 17         [ 2]  425 	ldw	x, #0x5217
      0081EA F6               [ 1]  426 	ld	a, (x)
      0081EB 5F               [ 1]  427 	clrw	x
      0081EC 97               [ 1]  428 	ld	xl, a
      0081ED 1F 01            [ 2]  429 	ldw	(0x01, sp), x
                                    430 ;	sensors.c: 92: I2C_DR = (addr << 1) | mode;
      0081EF 7B 06            [ 1]  431 	ld	a, (0x06, sp)
      0081F1 48               [ 1]  432 	sll	a
      0081F2 1A 07            [ 1]  433 	or	a, (0x07, sp)
      0081F4 AE 52 16         [ 2]  434 	ldw	x, #0x5216
      0081F7 F7               [ 1]  435 	ld	(x), a
                                    436 ;	sensors.c: 93: if (mode == I2C_READ) {
      0081F8 7B 07            [ 1]  437 	ld	a, (0x07, sp)
      0081FA A1 01            [ 1]  438 	cp	a, #0x01
      0081FC 26 06            [ 1]  439 	jrne	00127$
      0081FE A6 01            [ 1]  440 	ld	a, #0x01
      008200 6B 03            [ 1]  441 	ld	(0x03, sp), a
      008202 20 02            [ 2]  442 	jra	00128$
      008204                        443 00127$:
      008204 0F 03            [ 1]  444 	clr	(0x03, sp)
      008206                        445 00128$:
      008206 0D 03            [ 1]  446 	tnz	(0x03, sp)
      008208 27 08            [ 1]  447 	jreq	00103$
                                    448 ;	sensors.c: 94: I2C_OARL = 0;
      00820A AE 52 13         [ 2]  449 	ldw	x, #0x5213
      00820D 7F               [ 1]  450 	clr	(x)
                                    451 ;	sensors.c: 95: I2C_OARH = 0;
      00820E AE 52 14         [ 2]  452 	ldw	x, #0x5214
      008211 7F               [ 1]  453 	clr	(x)
                                    454 ;	sensors.c: 98: while ((I2C_SR1 & I2C_ADDR) == 0);
      008212                        455 00103$:
                                    456 ;	sensors.c: 91: reg = I2C_SR1;
      008212 AE 52 17         [ 2]  457 	ldw	x, #0x5217
      008215 F6               [ 1]  458 	ld	a, (x)
                                    459 ;	sensors.c: 98: while ((I2C_SR1 & I2C_ADDR) == 0);
      008216 A5 02            [ 1]  460 	bcp	a, #0x02
      008218 27 F8            [ 1]  461 	jreq	00103$
                                    462 ;	sensors.c: 99: if (mode == I2C_READ)
      00821A 0D 03            [ 1]  463 	tnz	(0x03, sp)
      00821C 27 06            [ 1]  464 	jreq	00108$
                                    465 ;	sensors.c: 100: UNSET (I2C_SR1, I2C_ADDR);
      00821E A4 FD            [ 1]  466 	and	a, #0xfd
      008220 AE 52 17         [ 2]  467 	ldw	x, #0x5217
      008223 F7               [ 1]  468 	ld	(x), a
      008224                        469 00108$:
      008224 5B 03            [ 2]  470 	addw	sp, #3
      008226 81               [ 4]  471 	ret
                                    472 ;	sensors.c: 103: void i2c_set_start_ack (void) {
                                    473 ;	-----------------------------------------
                                    474 ;	 function i2c_set_start_ack
                                    475 ;	-----------------------------------------
      008227                        476 _i2c_set_start_ack:
                                    477 ;	sensors.c: 104: I2C_CR2 = I2C_ACK | I2C_START;
      008227 AE 52 11         [ 2]  478 	ldw	x, #0x5211
      00822A A6 05            [ 1]  479 	ld	a, #0x05
      00822C F7               [ 1]  480 	ld	(x), a
                                    481 ;	sensors.c: 105: while ((I2C_SR1 & I2C_SB) == 0);
      00822D                        482 00101$:
      00822D AE 52 17         [ 2]  483 	ldw	x, #0x5217
      008230 F6               [ 1]  484 	ld	a, (x)
      008231 44               [ 1]  485 	srl	a
      008232 24 F9            [ 1]  486 	jrnc	00101$
      008234 81               [ 4]  487 	ret
                                    488 ;	sensors.c: 112: void print_byte_hex (unsigned char buffer) {
                                    489 ;	-----------------------------------------
                                    490 ;	 function print_byte_hex
                                    491 ;	-----------------------------------------
      008235                        492 _print_byte_hex:
      008235 52 0C            [ 2]  493 	sub	sp, #12
                                    494 ;	sensors.c: 115: a = (buffer >> 4);
      008237 7B 0F            [ 1]  495 	ld	a, (0x0f, sp)
      008239 4E               [ 1]  496 	swap	a
      00823A A4 0F            [ 1]  497 	and	a, #0x0f
      00823C 5F               [ 1]  498 	clrw	x
      00823D 97               [ 1]  499 	ld	xl, a
                                    500 ;	sensors.c: 116: if (a > 9)
      00823E A3 00 09         [ 2]  501 	cpw	x, #0x0009
      008241 2D 07            [ 1]  502 	jrsle	00102$
                                    503 ;	sensors.c: 117: a = a + 'a' - 10;
      008243 1C 00 57         [ 2]  504 	addw	x, #0x0057
      008246 1F 03            [ 2]  505 	ldw	(0x03, sp), x
      008248 20 05            [ 2]  506 	jra	00103$
      00824A                        507 00102$:
                                    508 ;	sensors.c: 119: a += '0'; 
      00824A 1C 00 30         [ 2]  509 	addw	x, #0x0030
      00824D 1F 03            [ 2]  510 	ldw	(0x03, sp), x
      00824F                        511 00103$:
                                    512 ;	sensors.c: 120: b = buffer & 0x0f;
      00824F 7B 0F            [ 1]  513 	ld	a, (0x0f, sp)
      008251 A4 0F            [ 1]  514 	and	a, #0x0f
      008253 5F               [ 1]  515 	clrw	x
      008254 97               [ 1]  516 	ld	xl, a
                                    517 ;	sensors.c: 121: if (b > 9)
      008255 A3 00 09         [ 2]  518 	cpw	x, #0x0009
      008258 2D 07            [ 1]  519 	jrsle	00105$
                                    520 ;	sensors.c: 122: b = b + 'a' - 10;
      00825A 1C 00 57         [ 2]  521 	addw	x, #0x0057
      00825D 1F 01            [ 2]  522 	ldw	(0x01, sp), x
      00825F 20 05            [ 2]  523 	jra	00106$
      008261                        524 00105$:
                                    525 ;	sensors.c: 124: b += '0'; 
      008261 1C 00 30         [ 2]  526 	addw	x, #0x0030
      008264 1F 01            [ 2]  527 	ldw	(0x01, sp), x
      008266                        528 00106$:
                                    529 ;	sensors.c: 125: message[0] = a;
      008266 90 96            [ 1]  530 	ldw	y, sp
      008268 72 A9 00 05      [ 2]  531 	addw	y, #5
      00826C 7B 04            [ 1]  532 	ld	a, (0x04, sp)
      00826E 90 F7            [ 1]  533 	ld	(y), a
                                    534 ;	sensors.c: 126: message[1] = b;
      008270 93               [ 1]  535 	ldw	x, y
      008271 5C               [ 2]  536 	incw	x
      008272 7B 02            [ 1]  537 	ld	a, (0x02, sp)
      008274 F7               [ 1]  538 	ld	(x), a
                                    539 ;	sensors.c: 127: message[2] = 0;
      008275 93               [ 1]  540 	ldw	x, y
      008276 5C               [ 2]  541 	incw	x
      008277 5C               [ 2]  542 	incw	x
      008278 7F               [ 1]  543 	clr	(x)
                                    544 ;	sensors.c: 128: UARTPrintF (message);
      008279 90 89            [ 2]  545 	pushw	y
      00827B CD 81 80         [ 4]  546 	call	_UARTPrintF
      00827E 5B 02            [ 2]  547 	addw	sp, #2
      008280 5B 0C            [ 2]  548 	addw	sp, #12
      008282 81               [ 4]  549 	ret
                                    550 ;	sensors.c: 132: unsigned char i2c_read_register (UCHAR addr, UCHAR rg) {
                                    551 ;	-----------------------------------------
                                    552 ;	 function i2c_read_register
                                    553 ;	-----------------------------------------
      008283                        554 _i2c_read_register:
      008283 52 02            [ 2]  555 	sub	sp, #2
                                    556 ;	sensors.c: 135: i2c_set_start_ack ();
      008285 CD 82 27         [ 4]  557 	call	_i2c_set_start_ack
                                    558 ;	sensors.c: 136: i2c_send_address (addr, I2C_WRITE);
      008288 4B 00            [ 1]  559 	push	#0x00
      00828A 7B 06            [ 1]  560 	ld	a, (0x06, sp)
      00828C 88               [ 1]  561 	push	a
      00828D CD 81 E5         [ 4]  562 	call	_i2c_send_address
      008290 5B 02            [ 2]  563 	addw	sp, #2
                                    564 ;	sensors.c: 137: i2c_send_reg (rg);
      008292 7B 06            [ 1]  565 	ld	a, (0x06, sp)
      008294 88               [ 1]  566 	push	a
      008295 CD 81 5E         [ 4]  567 	call	_i2c_send_reg
      008298 84               [ 1]  568 	pop	a
                                    569 ;	sensors.c: 138: i2c_set_start_ack ();
      008299 CD 82 27         [ 4]  570 	call	_i2c_set_start_ack
                                    571 ;	sensors.c: 139: i2c_send_address (addr, I2C_READ);
      00829C 4B 01            [ 1]  572 	push	#0x01
      00829E 7B 06            [ 1]  573 	ld	a, (0x06, sp)
      0082A0 88               [ 1]  574 	push	a
      0082A1 CD 81 E5         [ 4]  575 	call	_i2c_send_address
      0082A4 5B 02            [ 2]  576 	addw	sp, #2
                                    577 ;	sensors.c: 140: reg = I2C_SR1;
      0082A6 AE 52 17         [ 2]  578 	ldw	x, #0x5217
      0082A9 F6               [ 1]  579 	ld	a, (x)
      0082AA 6B 01            [ 1]  580 	ld	(0x01, sp), a
                                    581 ;	sensors.c: 141: reg = I2C_SR3;
      0082AC AE 52 19         [ 2]  582 	ldw	x, #0x5219
      0082AF F6               [ 1]  583 	ld	a, (x)
      0082B0 6B 01            [ 1]  584 	ld	(0x01, sp), a
                                    585 ;	sensors.c: 142: i2c_set_nak ();
      0082B2 CD 81 4E         [ 4]  586 	call	_i2c_set_nak
                                    587 ;	sensors.c: 143: i2c_set_stop ();
      0082B5 CD 81 56         [ 4]  588 	call	_i2c_set_stop
                                    589 ;	sensors.c: 144: i2c_read (&x);
      0082B8 96               [ 1]  590 	ldw	x, sp
      0082B9 5C               [ 2]  591 	incw	x
      0082BA 5C               [ 2]  592 	incw	x
      0082BB 89               [ 2]  593 	pushw	x
      0082BC CD 81 3D         [ 4]  594 	call	_i2c_read
      0082BF 5B 02            [ 2]  595 	addw	sp, #2
                                    596 ;	sensors.c: 145: return (x);
      0082C1 7B 02            [ 1]  597 	ld	a, (0x02, sp)
      0082C3 5B 02            [ 2]  598 	addw	sp, #2
      0082C5 81               [ 4]  599 	ret
                                    600 ;	sensors.c: 148: void InitializeI2C (void) {
                                    601 ;	-----------------------------------------
                                    602 ;	 function InitializeI2C
                                    603 ;	-----------------------------------------
      0082C6                        604 _InitializeI2C:
                                    605 ;	sensors.c: 149: I2C_CR1 = 0;   //  Disable I2C before configuration starts. PE bit is bit 0
      0082C6 AE 52 10         [ 2]  606 	ldw	x, #0x5210
      0082C9 7F               [ 1]  607 	clr	(x)
                                    608 ;	sensors.c: 153: I2C_FREQR = 16;                     //  Set the internal clock frequency (MHz).
      0082CA AE 52 12         [ 2]  609 	ldw	x, #0x5212
      0082CD A6 10            [ 1]  610 	ld	a, #0x10
      0082CF F7               [ 1]  611 	ld	(x), a
                                    612 ;	sensors.c: 154: UNSET (I2C_CCRH, I2C_FS);           //  I2C running is standard mode.
      0082D0 72 17 52 1C      [ 1]  613 	bres	0x521c, #7
                                    614 ;	sensors.c: 156: I2C_CCRL = 0xa0;                    //  SCL clock speed is 50 kHz.
      0082D4 AE 52 1B         [ 2]  615 	ldw	x, #0x521b
      0082D7 A6 A0            [ 1]  616 	ld	a, #0xa0
      0082D9 F7               [ 1]  617 	ld	(x), a
                                    618 ;	sensors.c: 158: I2C_CCRH &= 0x00;	// Clears lower 4 bits "CCR"
      0082DA AE 52 1C         [ 2]  619 	ldw	x, #0x521c
      0082DD 7F               [ 1]  620 	clr	(x)
                                    621 ;	sensors.c: 162: UNSET (I2C_OARH, I2C_ADDMODE);      //  7 bit address mode.
      0082DE 72 17 52 14      [ 1]  622 	bres	0x5214, #7
                                    623 ;	sensors.c: 163: SET (I2C_OARH, I2C_ADDCONF);        //  Docs say this must always be 1.
      0082E2 AE 52 14         [ 2]  624 	ldw	x, #0x5214
      0082E5 F6               [ 1]  625 	ld	a, (x)
      0082E6 AA 40            [ 1]  626 	or	a, #0x40
      0082E8 F7               [ 1]  627 	ld	(x), a
                                    628 ;	sensors.c: 167: I2C_TRISER = 17;
      0082E9 AE 52 1D         [ 2]  629 	ldw	x, #0x521d
      0082EC A6 11            [ 1]  630 	ld	a, #0x11
      0082EE F7               [ 1]  631 	ld	(x), a
                                    632 ;	sensors.c: 175: I2C_CR1 = I2C_PE;	// Enables port
      0082EF AE 52 10         [ 2]  633 	ldw	x, #0x5210
      0082F2 A6 01            [ 1]  634 	ld	a, #0x01
      0082F4 F7               [ 1]  635 	ld	(x), a
      0082F5 81               [ 4]  636 	ret
                                    637 ;	sensors.c: 181: void InitializeUART() {
                                    638 ;	-----------------------------------------
                                    639 ;	 function InitializeUART
                                    640 ;	-----------------------------------------
      0082F6                        641 _InitializeUART:
                                    642 ;	sensors.c: 191: UART1_CR1 = 0;
      0082F6 AE 52 34         [ 2]  643 	ldw	x, #0x5234
      0082F9 7F               [ 1]  644 	clr	(x)
                                    645 ;	sensors.c: 192: UART1_CR2 = 0;
      0082FA AE 52 35         [ 2]  646 	ldw	x, #0x5235
      0082FD 7F               [ 1]  647 	clr	(x)
                                    648 ;	sensors.c: 193: UART1_CR4 = 0;
      0082FE AE 52 37         [ 2]  649 	ldw	x, #0x5237
      008301 7F               [ 1]  650 	clr	(x)
                                    651 ;	sensors.c: 194: UART1_CR3 = 0;
      008302 AE 52 36         [ 2]  652 	ldw	x, #0x5236
      008305 7F               [ 1]  653 	clr	(x)
                                    654 ;	sensors.c: 195: UART1_CR5 = 0;
      008306 AE 52 38         [ 2]  655 	ldw	x, #0x5238
      008309 7F               [ 1]  656 	clr	(x)
                                    657 ;	sensors.c: 196: UART1_GTR = 0;
      00830A AE 52 39         [ 2]  658 	ldw	x, #0x5239
      00830D 7F               [ 1]  659 	clr	(x)
                                    660 ;	sensors.c: 197: UART1_PSCR = 0;
      00830E AE 52 3A         [ 2]  661 	ldw	x, #0x523a
      008311 7F               [ 1]  662 	clr	(x)
                                    663 ;	sensors.c: 201: UNSET (UART1_CR1, CR1_M);        //  8 Data bits.
      008312 AE 52 34         [ 2]  664 	ldw	x, #0x5234
      008315 F6               [ 1]  665 	ld	a, (x)
      008316 A4 EF            [ 1]  666 	and	a, #0xef
      008318 F7               [ 1]  667 	ld	(x), a
                                    668 ;	sensors.c: 202: UNSET (UART1_CR1, CR1_PCEN);     //  Disable parity.
      008319 AE 52 34         [ 2]  669 	ldw	x, #0x5234
      00831C F6               [ 1]  670 	ld	a, (x)
      00831D A4 FB            [ 1]  671 	and	a, #0xfb
      00831F F7               [ 1]  672 	ld	(x), a
                                    673 ;	sensors.c: 203: UNSET (UART1_CR3, CR3_STOPH);    //  1 stop bit.
      008320 AE 52 36         [ 2]  674 	ldw	x, #0x5236
      008323 F6               [ 1]  675 	ld	a, (x)
      008324 A4 DF            [ 1]  676 	and	a, #0xdf
      008326 F7               [ 1]  677 	ld	(x), a
                                    678 ;	sensors.c: 204: UNSET (UART1_CR3, CR3_STOPL);    //  1 stop bit.
      008327 AE 52 36         [ 2]  679 	ldw	x, #0x5236
      00832A F6               [ 1]  680 	ld	a, (x)
      00832B A4 EF            [ 1]  681 	and	a, #0xef
      00832D F7               [ 1]  682 	ld	(x), a
                                    683 ;	sensors.c: 205: UART1_BRR2 = 0x0a;      //  Set the baud rate registers to 115200 baud
      00832E AE 52 33         [ 2]  684 	ldw	x, #0x5233
      008331 A6 0A            [ 1]  685 	ld	a, #0x0a
      008333 F7               [ 1]  686 	ld	(x), a
                                    687 ;	sensors.c: 206: UART1_BRR1 = 0x08;      //  based upon a 16 MHz system clock.
      008334 AE 52 32         [ 2]  688 	ldw	x, #0x5232
      008337 A6 08            [ 1]  689 	ld	a, #0x08
      008339 F7               [ 1]  690 	ld	(x), a
                                    691 ;	sensors.c: 210: UNSET (UART1_CR2, CR2_TEN);      //  Disable transmit.
      00833A AE 52 35         [ 2]  692 	ldw	x, #0x5235
      00833D F6               [ 1]  693 	ld	a, (x)
      00833E A4 F7            [ 1]  694 	and	a, #0xf7
      008340 F7               [ 1]  695 	ld	(x), a
                                    696 ;	sensors.c: 211: UNSET (UART1_CR2, CR2_REN);      //  Disable receive.
      008341 AE 52 35         [ 2]  697 	ldw	x, #0x5235
      008344 F6               [ 1]  698 	ld	a, (x)
      008345 A4 FB            [ 1]  699 	and	a, #0xfb
      008347 F7               [ 1]  700 	ld	(x), a
                                    701 ;	sensors.c: 215: SET (UART1_CR3, CR3_CPOL);
      008348 AE 52 36         [ 2]  702 	ldw	x, #0x5236
      00834B F6               [ 1]  703 	ld	a, (x)
      00834C AA 04            [ 1]  704 	or	a, #0x04
      00834E F7               [ 1]  705 	ld	(x), a
                                    706 ;	sensors.c: 216: SET (UART1_CR3, CR3_CPHA);
      00834F AE 52 36         [ 2]  707 	ldw	x, #0x5236
      008352 F6               [ 1]  708 	ld	a, (x)
      008353 AA 02            [ 1]  709 	or	a, #0x02
      008355 F7               [ 1]  710 	ld	(x), a
                                    711 ;	sensors.c: 217: SET (UART1_CR3, CR3_LBCL);
      008356 72 10 52 36      [ 1]  712 	bset	0x5236, #0
                                    713 ;	sensors.c: 221: SET (UART1_CR2, CR2_TEN);
      00835A AE 52 35         [ 2]  714 	ldw	x, #0x5235
      00835D F6               [ 1]  715 	ld	a, (x)
      00835E AA 08            [ 1]  716 	or	a, #0x08
      008360 F7               [ 1]  717 	ld	(x), a
                                    718 ;	sensors.c: 222: SET (UART1_CR2, CR2_REN);
      008361 AE 52 35         [ 2]  719 	ldw	x, #0x5235
      008364 F6               [ 1]  720 	ld	a, (x)
      008365 AA 04            [ 1]  721 	or	a, #0x04
      008367 F7               [ 1]  722 	ld	(x), a
                                    723 ;	sensors.c: 223: UART1_CR3 = CR3_CLKEN;
      008368 AE 52 36         [ 2]  724 	ldw	x, #0x5236
      00836B A6 08            [ 1]  725 	ld	a, #0x08
      00836D F7               [ 1]  726 	ld	(x), a
      00836E 81               [ 4]  727 	ret
                                    728 ;	sensors.c: 251: void tm1637Init(void)
                                    729 ;	-----------------------------------------
                                    730 ;	 function tm1637Init
                                    731 ;	-----------------------------------------
      00836F                        732 _tm1637Init:
                                    733 ;	sensors.c: 253: tm1637SetBrightness(8);
      00836F 4B 08            [ 1]  734 	push	#0x08
      008371 CD 84 14         [ 4]  735 	call	_tm1637SetBrightness
      008374 84               [ 1]  736 	pop	a
      008375 81               [ 4]  737 	ret
                                    738 ;	sensors.c: 258: void tm1637DisplayDecimal(long TT,unsigned int displaySeparator)
                                    739 ;	-----------------------------------------
                                    740 ;	 function tm1637DisplayDecimal
                                    741 ;	-----------------------------------------
      008376                        742 _tm1637DisplayDecimal:
      008376 52 13            [ 2]  743 	sub	sp, #19
                                    744 ;	sensors.c: 260: unsigned int v = TT & 0x0000FFFF;
      008378 7B 19            [ 1]  745 	ld	a, (0x19, sp)
      00837A 97               [ 1]  746 	ld	xl, a
      00837B 7B 18            [ 1]  747 	ld	a, (0x18, sp)
      00837D 95               [ 1]  748 	ld	xh, a
      00837E 0F 0A            [ 1]  749 	clr	(0x0a, sp)
      008380 4F               [ 1]  750 	clr	a
      008381 1F 05            [ 2]  751 	ldw	(0x05, sp), x
                                    752 ;	sensors.c: 266: for (ii = 0; ii < 4; ++ii) {
      008383 96               [ 1]  753 	ldw	x, sp
      008384 5C               [ 2]  754 	incw	x
      008385 1F 0E            [ 2]  755 	ldw	(0x0e, sp), x
      008387 AE 85 DD         [ 2]  756 	ldw	x, #_segmentMap+0
      00838A 1F 12            [ 2]  757 	ldw	(0x12, sp), x
      00838C 90 5F            [ 1]  758 	clrw	y
      00838E                        759 00106$:
                                    760 ;	sensors.c: 267: digitArr[ii] = segmentMap[v % 10];
      00838E 93               [ 1]  761 	ldw	x, y
      00838F 72 FB 0E         [ 2]  762 	addw	x, (0x0e, sp)
      008392 1F 10            [ 2]  763 	ldw	(0x10, sp), x
      008394 90 89            [ 2]  764 	pushw	y
      008396 1E 07            [ 2]  765 	ldw	x, (0x07, sp)
      008398 90 AE 00 0A      [ 2]  766 	ldw	y, #0x000a
      00839C 65               [ 2]  767 	divw	x, y
      00839D 93               [ 1]  768 	ldw	x, y
      00839E 90 85            [ 2]  769 	popw	y
      0083A0 72 FB 12         [ 2]  770 	addw	x, (0x12, sp)
      0083A3 F6               [ 1]  771 	ld	a, (x)
      0083A4 1E 10            [ 2]  772 	ldw	x, (0x10, sp)
      0083A6 F7               [ 1]  773 	ld	(x), a
                                    774 ;	sensors.c: 268: if (ii == 2 && displaySeparator) {
      0083A7 90 A3 00 02      [ 2]  775 	cpw	y, #0x0002
      0083AB 26 0C            [ 1]  776 	jrne	00102$
      0083AD 1E 1A            [ 2]  777 	ldw	x, (0x1a, sp)
      0083AF 27 08            [ 1]  778 	jreq	00102$
                                    779 ;	sensors.c: 269: digitArr[ii] |= 1 << 7;
      0083B1 1E 10            [ 2]  780 	ldw	x, (0x10, sp)
      0083B3 F6               [ 1]  781 	ld	a, (x)
      0083B4 AA 80            [ 1]  782 	or	a, #0x80
      0083B6 1E 10            [ 2]  783 	ldw	x, (0x10, sp)
      0083B8 F7               [ 1]  784 	ld	(x), a
      0083B9                        785 00102$:
                                    786 ;	sensors.c: 271: v /= 10;
      0083B9 90 89            [ 2]  787 	pushw	y
      0083BB 1E 07            [ 2]  788 	ldw	x, (0x07, sp)
      0083BD 90 AE 00 0A      [ 2]  789 	ldw	y, #0x000a
      0083C1 65               [ 2]  790 	divw	x, y
      0083C2 90 85            [ 2]  791 	popw	y
      0083C4 1F 05            [ 2]  792 	ldw	(0x05, sp), x
                                    793 ;	sensors.c: 266: for (ii = 0; ii < 4; ++ii) {
      0083C6 90 5C            [ 2]  794 	incw	y
      0083C8 90 A3 00 04      [ 2]  795 	cpw	y, #0x0004
      0083CC 25 C0            [ 1]  796 	jrc	00106$
                                    797 ;	sensors.c: 274: _tm1637Start();
      0083CE CD 84 26         [ 4]  798 	call	__tm1637Start
                                    799 ;	sensors.c: 275: _tm1637WriteByte(0x40);
      0083D1 4B 40            [ 1]  800 	push	#0x40
      0083D3 CD 84 7A         [ 4]  801 	call	__tm1637WriteByte
      0083D6 84               [ 1]  802 	pop	a
                                    803 ;	sensors.c: 276: _tm1637ReadResult();
      0083D7 CD 84 5F         [ 4]  804 	call	__tm1637ReadResult
                                    805 ;	sensors.c: 277: _tm1637Stop();
      0083DA CD 84 38         [ 4]  806 	call	__tm1637Stop
                                    807 ;	sensors.c: 279: _tm1637Start();
      0083DD CD 84 26         [ 4]  808 	call	__tm1637Start
                                    809 ;	sensors.c: 280: _tm1637WriteByte(0xc0);
      0083E0 4B C0            [ 1]  810 	push	#0xc0
      0083E2 CD 84 7A         [ 4]  811 	call	__tm1637WriteByte
      0083E5 84               [ 1]  812 	pop	a
                                    813 ;	sensors.c: 281: _tm1637ReadResult();
      0083E6 CD 84 5F         [ 4]  814 	call	__tm1637ReadResult
                                    815 ;	sensors.c: 283: for (ii = 0; ii < 4; ++ii) {
      0083E9 5F               [ 1]  816 	clrw	x
      0083EA 1F 07            [ 2]  817 	ldw	(0x07, sp), x
      0083EC                        818 00108$:
                                    819 ;	sensors.c: 284: _tm1637WriteByte(digitArr[3 - ii]);
      0083EC 7B 08            [ 1]  820 	ld	a, (0x08, sp)
      0083EE 6B 0D            [ 1]  821 	ld	(0x0d, sp), a
      0083F0 A6 03            [ 1]  822 	ld	a, #0x03
      0083F2 10 0D            [ 1]  823 	sub	a, (0x0d, sp)
      0083F4 5F               [ 1]  824 	clrw	x
      0083F5 97               [ 1]  825 	ld	xl, a
      0083F6 72 FB 0E         [ 2]  826 	addw	x, (0x0e, sp)
      0083F9 F6               [ 1]  827 	ld	a, (x)
      0083FA 88               [ 1]  828 	push	a
      0083FB CD 84 7A         [ 4]  829 	call	__tm1637WriteByte
      0083FE 84               [ 1]  830 	pop	a
                                    831 ;	sensors.c: 285: _tm1637ReadResult();
      0083FF CD 84 5F         [ 4]  832 	call	__tm1637ReadResult
                                    833 ;	sensors.c: 283: for (ii = 0; ii < 4; ++ii) {
      008402 1E 07            [ 2]  834 	ldw	x, (0x07, sp)
      008404 5C               [ 2]  835 	incw	x
      008405 1F 07            [ 2]  836 	ldw	(0x07, sp), x
      008407 1E 07            [ 2]  837 	ldw	x, (0x07, sp)
      008409 A3 00 04         [ 2]  838 	cpw	x, #0x0004
      00840C 25 DE            [ 1]  839 	jrc	00108$
                                    840 ;	sensors.c: 288: _tm1637Stop();
      00840E CD 84 38         [ 4]  841 	call	__tm1637Stop
      008411 5B 13            [ 2]  842 	addw	sp, #19
      008413 81               [ 4]  843 	ret
                                    844 ;	sensors.c: 293: void tm1637SetBrightness(char brightness)
                                    845 ;	-----------------------------------------
                                    846 ;	 function tm1637SetBrightness
                                    847 ;	-----------------------------------------
      008414                        848 _tm1637SetBrightness:
                                    849 ;	sensors.c: 300: _tm1637Start();
      008414 CD 84 26         [ 4]  850 	call	__tm1637Start
                                    851 ;	sensors.c: 301: _tm1637WriteByte(0x87 + brightness);
      008417 7B 03            [ 1]  852 	ld	a, (0x03, sp)
      008419 AB 87            [ 1]  853 	add	a, #0x87
      00841B 88               [ 1]  854 	push	a
      00841C CD 84 7A         [ 4]  855 	call	__tm1637WriteByte
      00841F 84               [ 1]  856 	pop	a
                                    857 ;	sensors.c: 302: _tm1637ReadResult();
      008420 CD 84 5F         [ 4]  858 	call	__tm1637ReadResult
                                    859 ;	sensors.c: 303: _tm1637Stop();
      008423 CC 84 38         [ 2]  860 	jp	__tm1637Stop
                                    861 ;	sensors.c: 306: void _tm1637Start(void)
                                    862 ;	-----------------------------------------
                                    863 ;	 function _tm1637Start
                                    864 ;	-----------------------------------------
      008426                        865 __tm1637Start:
                                    866 ;	sensors.c: 308: _tm1637ClkHigh();
      008426 CD 84 B8         [ 4]  867 	call	__tm1637ClkHigh
                                    868 ;	sensors.c: 309: _tm1637DioHigh();
      008429 CD 84 C8         [ 4]  869 	call	__tm1637DioHigh
                                    870 ;	sensors.c: 310: delay(5);
      00842C 4B 05            [ 1]  871 	push	#0x05
      00842E 4B 00            [ 1]  872 	push	#0x00
      008430 CD 80 F2         [ 4]  873 	call	_delay
      008433 5B 02            [ 2]  874 	addw	sp, #2
                                    875 ;	sensors.c: 311: _tm1637DioLow();
      008435 CC 84 D0         [ 2]  876 	jp	__tm1637DioLow
                                    877 ;	sensors.c: 314: void _tm1637Stop(void)
                                    878 ;	-----------------------------------------
                                    879 ;	 function _tm1637Stop
                                    880 ;	-----------------------------------------
      008438                        881 __tm1637Stop:
                                    882 ;	sensors.c: 316: _tm1637ClkLow();
      008438 CD 84 C0         [ 4]  883 	call	__tm1637ClkLow
                                    884 ;	sensors.c: 317: delay(5);
      00843B 4B 05            [ 1]  885 	push	#0x05
      00843D 4B 00            [ 1]  886 	push	#0x00
      00843F CD 80 F2         [ 4]  887 	call	_delay
      008442 5B 02            [ 2]  888 	addw	sp, #2
                                    889 ;	sensors.c: 318: _tm1637DioLow();
      008444 CD 84 D0         [ 4]  890 	call	__tm1637DioLow
                                    891 ;	sensors.c: 319: delay(5);
      008447 4B 05            [ 1]  892 	push	#0x05
      008449 4B 00            [ 1]  893 	push	#0x00
      00844B CD 80 F2         [ 4]  894 	call	_delay
      00844E 5B 02            [ 2]  895 	addw	sp, #2
                                    896 ;	sensors.c: 320: _tm1637ClkHigh();
      008450 CD 84 B8         [ 4]  897 	call	__tm1637ClkHigh
                                    898 ;	sensors.c: 321: delay(5);
      008453 4B 05            [ 1]  899 	push	#0x05
      008455 4B 00            [ 1]  900 	push	#0x00
      008457 CD 80 F2         [ 4]  901 	call	_delay
      00845A 5B 02            [ 2]  902 	addw	sp, #2
                                    903 ;	sensors.c: 322: _tm1637DioHigh();
      00845C CC 84 C8         [ 2]  904 	jp	__tm1637DioHigh
                                    905 ;	sensors.c: 325: void _tm1637ReadResult(void)
                                    906 ;	-----------------------------------------
                                    907 ;	 function _tm1637ReadResult
                                    908 ;	-----------------------------------------
      00845F                        909 __tm1637ReadResult:
                                    910 ;	sensors.c: 327: _tm1637ClkLow();
      00845F CD 84 C0         [ 4]  911 	call	__tm1637ClkLow
                                    912 ;	sensors.c: 328: delay(5);
      008462 4B 05            [ 1]  913 	push	#0x05
      008464 4B 00            [ 1]  914 	push	#0x00
      008466 CD 80 F2         [ 4]  915 	call	_delay
      008469 5B 02            [ 2]  916 	addw	sp, #2
                                    917 ;	sensors.c: 330: _tm1637ClkHigh();
      00846B CD 84 B8         [ 4]  918 	call	__tm1637ClkHigh
                                    919 ;	sensors.c: 331: delay(5);
      00846E 4B 05            [ 1]  920 	push	#0x05
      008470 4B 00            [ 1]  921 	push	#0x00
      008472 CD 80 F2         [ 4]  922 	call	_delay
      008475 5B 02            [ 2]  923 	addw	sp, #2
                                    924 ;	sensors.c: 332: _tm1637ClkLow();
      008477 CC 84 C0         [ 2]  925 	jp	__tm1637ClkLow
                                    926 ;	sensors.c: 335: void _tm1637WriteByte(unsigned char b)
                                    927 ;	-----------------------------------------
                                    928 ;	 function _tm1637WriteByte
                                    929 ;	-----------------------------------------
      00847A                        930 __tm1637WriteByte:
      00847A 52 02            [ 2]  931 	sub	sp, #2
                                    932 ;	sensors.c: 337: for (ii = 0; ii < 8; ++ii) {
      00847C 5F               [ 1]  933 	clrw	x
      00847D 1F 01            [ 2]  934 	ldw	(0x01, sp), x
      00847F                        935 00105$:
                                    936 ;	sensors.c: 338: _tm1637ClkLow();
      00847F CD 84 C0         [ 4]  937 	call	__tm1637ClkLow
                                    938 ;	sensors.c: 339: if (b & 0x01) {
      008482 7B 05            [ 1]  939 	ld	a, (0x05, sp)
      008484 44               [ 1]  940 	srl	a
      008485 24 05            [ 1]  941 	jrnc	00102$
                                    942 ;	sensors.c: 340: _tm1637DioHigh();
      008487 CD 84 C8         [ 4]  943 	call	__tm1637DioHigh
      00848A 20 03            [ 2]  944 	jra	00103$
      00848C                        945 00102$:
                                    946 ;	sensors.c: 343: _tm1637DioLow();
      00848C CD 84 D0         [ 4]  947 	call	__tm1637DioLow
      00848F                        948 00103$:
                                    949 ;	sensors.c: 345: delay(15);
      00848F 4B 0F            [ 1]  950 	push	#0x0f
      008491 4B 00            [ 1]  951 	push	#0x00
      008493 CD 80 F2         [ 4]  952 	call	_delay
      008496 5B 02            [ 2]  953 	addw	sp, #2
                                    954 ;	sensors.c: 346: b >>= 1;
      008498 7B 05            [ 1]  955 	ld	a, (0x05, sp)
      00849A 44               [ 1]  956 	srl	a
      00849B 6B 05            [ 1]  957 	ld	(0x05, sp), a
                                    958 ;	sensors.c: 347: _tm1637ClkHigh();
      00849D CD 84 B8         [ 4]  959 	call	__tm1637ClkHigh
                                    960 ;	sensors.c: 348: delay(15);
      0084A0 4B 0F            [ 1]  961 	push	#0x0f
      0084A2 4B 00            [ 1]  962 	push	#0x00
      0084A4 CD 80 F2         [ 4]  963 	call	_delay
      0084A7 5B 02            [ 2]  964 	addw	sp, #2
                                    965 ;	sensors.c: 337: for (ii = 0; ii < 8; ++ii) {
      0084A9 1E 01            [ 2]  966 	ldw	x, (0x01, sp)
      0084AB 5C               [ 2]  967 	incw	x
      0084AC 1F 01            [ 2]  968 	ldw	(0x01, sp), x
      0084AE 1E 01            [ 2]  969 	ldw	x, (0x01, sp)
      0084B0 A3 00 08         [ 2]  970 	cpw	x, #0x0008
      0084B3 2F CA            [ 1]  971 	jrslt	00105$
      0084B5 5B 02            [ 2]  972 	addw	sp, #2
      0084B7 81               [ 4]  973 	ret
                                    974 ;	sensors.c: 354: void _tm1637ClkHigh(void)
                                    975 ;	-----------------------------------------
                                    976 ;	 function _tm1637ClkHigh
                                    977 ;	-----------------------------------------
      0084B8                        978 __tm1637ClkHigh:
                                    979 ;	sensors.c: 359: PD_ODR |= 1 << 2;
      0084B8 AE 50 0F         [ 2]  980 	ldw	x, #0x500f
      0084BB F6               [ 1]  981 	ld	a, (x)
      0084BC AA 04            [ 1]  982 	or	a, #0x04
      0084BE F7               [ 1]  983 	ld	(x), a
      0084BF 81               [ 4]  984 	ret
                                    985 ;	sensors.c: 362: void _tm1637ClkLow(void)
                                    986 ;	-----------------------------------------
                                    987 ;	 function _tm1637ClkLow
                                    988 ;	-----------------------------------------
      0084C0                        989 __tm1637ClkLow:
                                    990 ;	sensors.c: 366: PD_ODR &= ~(1 << 2);
      0084C0 AE 50 0F         [ 2]  991 	ldw	x, #0x500f
      0084C3 F6               [ 1]  992 	ld	a, (x)
      0084C4 A4 FB            [ 1]  993 	and	a, #0xfb
      0084C6 F7               [ 1]  994 	ld	(x), a
      0084C7 81               [ 4]  995 	ret
                                    996 ;	sensors.c: 372: void _tm1637DioHigh(void)
                                    997 ;	-----------------------------------------
                                    998 ;	 function _tm1637DioHigh
                                    999 ;	-----------------------------------------
      0084C8                       1000 __tm1637DioHigh:
                                   1001 ;	sensors.c: 376: PD_ODR |= 1 << 3;
      0084C8 AE 50 0F         [ 2] 1002 	ldw	x, #0x500f
      0084CB F6               [ 1] 1003 	ld	a, (x)
      0084CC AA 08            [ 1] 1004 	or	a, #0x08
      0084CE F7               [ 1] 1005 	ld	(x), a
      0084CF 81               [ 4] 1006 	ret
                                   1007 ;	sensors.c: 380: void _tm1637DioLow(void)
                                   1008 ;	-----------------------------------------
                                   1009 ;	 function _tm1637DioLow
                                   1010 ;	-----------------------------------------
      0084D0                       1011 __tm1637DioLow:
                                   1012 ;	sensors.c: 382: PD_ODR &= ~(1 << 3);
      0084D0 AE 50 0F         [ 2] 1013 	ldw	x, #0x500f
      0084D3 F6               [ 1] 1014 	ld	a, (x)
      0084D4 A4 F7            [ 1] 1015 	and	a, #0xf7
      0084D6 F7               [ 1] 1016 	ld	(x), a
      0084D7 81               [ 4] 1017 	ret
                                   1018 ;	sensors.c: 391: unsigned int clock(void)
                                   1019 ;	-----------------------------------------
                                   1020 ;	 function clock
                                   1021 ;	-----------------------------------------
      0084D8                       1022 _clock:
      0084D8 52 03            [ 2] 1023 	sub	sp, #3
                                   1024 ;	sensors.c: 393: unsigned char h = TIM1_CNTRH; //origineel PCNTRH
      0084DA AE 52 5E         [ 2] 1025 	ldw	x, #0x525e
      0084DD F6               [ 1] 1026 	ld	a, (x)
                                   1027 ;	sensors.c: 394: unsigned char l = TIM1_CNTRL;
      0084DE AE 52 5F         [ 2] 1028 	ldw	x, #0x525f
      0084E1 88               [ 1] 1029 	push	a
      0084E2 F6               [ 1] 1030 	ld	a, (x)
      0084E3 6B 02            [ 1] 1031 	ld	(0x02, sp), a
      0084E5 84               [ 1] 1032 	pop	a
                                   1033 ;	sensors.c: 395: return((unsigned int)(h) << 8 | l);
      0084E6 5F               [ 1] 1034 	clrw	x
      0084E7 97               [ 1] 1035 	ld	xl, a
      0084E8 58               [ 2] 1036 	sllw	x
      0084E9 58               [ 2] 1037 	sllw	x
      0084EA 58               [ 2] 1038 	sllw	x
      0084EB 58               [ 2] 1039 	sllw	x
      0084EC 58               [ 2] 1040 	sllw	x
      0084ED 58               [ 2] 1041 	sllw	x
      0084EE 58               [ 2] 1042 	sllw	x
      0084EF 58               [ 2] 1043 	sllw	x
      0084F0 7B 01            [ 1] 1044 	ld	a, (0x01, sp)
      0084F2 6B 03            [ 1] 1045 	ld	(0x03, sp), a
      0084F4 0F 02            [ 1] 1046 	clr	(0x02, sp)
      0084F6 9F               [ 1] 1047 	ld	a, xl
      0084F7 1A 03            [ 1] 1048 	or	a, (0x03, sp)
      0084F9 97               [ 1] 1049 	ld	xl, a
      0084FA 9E               [ 1] 1050 	ld	a, xh
      0084FB 1A 02            [ 1] 1051 	or	a, (0x02, sp)
      0084FD 95               [ 1] 1052 	ld	xh, a
      0084FE 5B 03            [ 2] 1053 	addw	sp, #3
      008500 81               [ 4] 1054 	ret
                                   1055 ;	sensors.c: 402: int main () {
                                   1056 ;	-----------------------------------------
                                   1057 ;	 function main
                                   1058 ;	-----------------------------------------
      008501                       1059 _main:
      008501 52 0A            [ 2] 1060 	sub	sp, #10
                                   1061 ;	sensors.c: 404: int maxValue = 0;          // store max value here
      008503 5F               [ 1] 1062 	clrw	x
      008504 1F 01            [ 2] 1063 	ldw	(0x01, sp), x
                                   1064 ;	sensors.c: 407: unsigned int val=0;
      008506 5F               [ 1] 1065 	clrw	x
      008507 1F 05            [ 2] 1066 	ldw	(0x05, sp), x
                                   1067 ;	sensors.c: 410: InitializeSystemClock();
      008509 CD 80 A8         [ 4] 1068 	call	_InitializeSystemClock
                                   1069 ;	sensors.c: 412: PD_DDR = (1 << 3) | (1 << 2); // output mode
      00850C AE 50 11         [ 2] 1070 	ldw	x, #0x5011
      00850F A6 0C            [ 1] 1071 	ld	a, #0x0c
      008511 F7               [ 1] 1072 	ld	(x), a
                                   1073 ;	sensors.c: 413: PD_CR1 = (1 << 3) | (1 << 2); // push-pull
      008512 AE 50 12         [ 2] 1074 	ldw	x, #0x5012
      008515 A6 0C            [ 1] 1075 	ld	a, #0x0c
      008517 F7               [ 1] 1076 	ld	(x), a
                                   1077 ;	sensors.c: 414: PD_CR2 = (1 << 3) | (1 << 2); // up to 10MHz speed
      008518 AE 50 13         [ 2] 1078 	ldw	x, #0x5013
      00851B A6 0C            [ 1] 1079 	ld	a, #0x0c
      00851D F7               [ 1] 1080 	ld	(x), a
                                   1081 ;	sensors.c: 419: TIM1_PSCRH = 0x3e;
      00851E AE 52 60         [ 2] 1082 	ldw	x, #0x5260
      008521 A6 3E            [ 1] 1083 	ld	a, #0x3e
      008523 F7               [ 1] 1084 	ld	(x), a
                                   1085 ;	sensors.c: 420: TIM1_PSCRL = 0x80;
      008524 AE 52 61         [ 2] 1086 	ldw	x, #0x5261
      008527 A6 80            [ 1] 1087 	ld	a, #0x80
      008529 F7               [ 1] 1088 	ld	(x), a
                                   1089 ;	sensors.c: 430: ADC_CSR |= ((0x0F)&2); // select channel = 2 = PC4
      00852A AE 54 00         [ 2] 1090 	ldw	x, #0x5400
      00852D F6               [ 1] 1091 	ld	a, (x)
      00852E AA 02            [ 1] 1092 	or	a, #0x02
      008530 F7               [ 1] 1093 	ld	(x), a
                                   1094 ;	sensors.c: 431: ADC_CR2 |= (1<<3); // Right Aligned Data
      008531 AE 54 02         [ 2] 1095 	ldw	x, #0x5402
      008534 F6               [ 1] 1096 	ld	a, (x)
      008535 AA 08            [ 1] 1097 	or	a, #0x08
      008537 F7               [ 1] 1098 	ld	(x), a
                                   1099 ;	sensors.c: 432: ADC_CR1 |= (1<<0); // ADC ON
      008538 AE 54 01         [ 2] 1100 	ldw	x, #0x5401
      00853B F6               [ 1] 1101 	ld	a, (x)
      00853C AA 01            [ 1] 1102 	or	a, #0x01
      00853E F7               [ 1] 1103 	ld	(x), a
                                   1104 ;	sensors.c: 433: tm1637Init();
      00853F CD 83 6F         [ 4] 1105 	call	_tm1637Init
                                   1106 ;	sensors.c: 435: InitializeUART();
      008542 CD 82 F6         [ 4] 1107 	call	_InitializeUART
                                   1108 ;	sensors.c: 436: while (1) {
      008545                       1109 00111$:
                                   1110 ;	sensors.c: 438: ADC_CR1 |= (1<<0); // ADC Start Conversion
      008545 72 10 54 01      [ 1] 1111 	bset	0x5401, #0
                                   1112 ;	sensors.c: 439: while(((ADC_CSR)&(1<<7))== 0); // Wait till EOC
      008549                       1113 00101$:
      008549 AE 54 00         [ 2] 1114 	ldw	x, #0x5400
      00854C F6               [ 1] 1115 	ld	a, (x)
      00854D 48               [ 1] 1116 	sll	a
      00854E 24 F9            [ 1] 1117 	jrnc	00101$
                                   1118 ;	sensors.c: 440: val |= (unsigned int)ADC_DRL;
      008550 AE 54 05         [ 2] 1119 	ldw	x, #0x5405
      008553 F6               [ 1] 1120 	ld	a, (x)
      008554 5F               [ 1] 1121 	clrw	x
      008555 97               [ 1] 1122 	ld	xl, a
      008556 1A 06            [ 1] 1123 	or	a, (0x06, sp)
      008558 6B 0A            [ 1] 1124 	ld	(0x0a, sp), a
      00855A 9E               [ 1] 1125 	ld	a, xh
      00855B 1A 05            [ 1] 1126 	or	a, (0x05, sp)
      00855D 6B 03            [ 1] 1127 	ld	(0x03, sp), a
      00855F 7B 0A            [ 1] 1128 	ld	a, (0x0a, sp)
      008561 6B 04            [ 1] 1129 	ld	(0x04, sp), a
                                   1130 ;	sensors.c: 441: UARTPrintF("value = \n\r");
      008563 AE 85 EE         [ 2] 1131 	ldw	x, #___str_0+0
      008566 89               [ 2] 1132 	pushw	x
      008567 CD 81 80         [ 4] 1133 	call	_UARTPrintF
      00856A 5B 02            [ 2] 1134 	addw	sp, #2
                                   1135 ;	sensors.c: 442: print_UCHAR_hex(val);
      00856C 7B 04            [ 1] 1136 	ld	a, (0x04, sp)
      00856E 88               [ 1] 1137 	push	a
      00856F CD 81 97         [ 4] 1138 	call	_print_UCHAR_hex
      008572 84               [ 1] 1139 	pop	a
                                   1140 ;	sensors.c: 443: val |= (unsigned int)ADC_DRH<<8;
      008573 AE 54 04         [ 2] 1141 	ldw	x, #0x5404
      008576 F6               [ 1] 1142 	ld	a, (x)
      008577 5F               [ 1] 1143 	clrw	x
      008578 97               [ 1] 1144 	ld	xl, a
      008579 58               [ 2] 1145 	sllw	x
      00857A 58               [ 2] 1146 	sllw	x
      00857B 58               [ 2] 1147 	sllw	x
      00857C 58               [ 2] 1148 	sllw	x
      00857D 58               [ 2] 1149 	sllw	x
      00857E 58               [ 2] 1150 	sllw	x
      00857F 58               [ 2] 1151 	sllw	x
      008580 58               [ 2] 1152 	sllw	x
      008581 9F               [ 1] 1153 	ld	a, xl
      008582 1A 04            [ 1] 1154 	or	a, (0x04, sp)
      008584 6B 08            [ 1] 1155 	ld	(0x08, sp), a
      008586 9E               [ 1] 1156 	ld	a, xh
      008587 1A 03            [ 1] 1157 	or	a, (0x03, sp)
      008589 6B 05            [ 1] 1158 	ld	(0x05, sp), a
      00858B 7B 08            [ 1] 1159 	ld	a, (0x08, sp)
      00858D 6B 06            [ 1] 1160 	ld	(0x06, sp), a
                                   1161 ;	sensors.c: 444: ADC_CR1 &= ~(1<<0); // ADC Stop Conversion
      00858F AE 54 01         [ 2] 1162 	ldw	x, #0x5401
      008592 F6               [ 1] 1163 	ld	a, (x)
      008593 A4 FE            [ 1] 1164 	and	a, #0xfe
      008595 F7               [ 1] 1165 	ld	(x), a
                                   1166 ;	sensors.c: 445: readValue = val & 0x03ff;
      008596 7B 06            [ 1] 1167 	ld	a, (0x06, sp)
      008598 90 97            [ 1] 1168 	ld	yl, a
      00859A 7B 05            [ 1] 1169 	ld	a, (0x05, sp)
      00859C A4 03            [ 1] 1170 	and	a, #0x03
      00859E 90 95            [ 1] 1171 	ld	yh, a
                                   1172 ;	sensors.c: 446: if (readValue > maxValue) 
      0085A0 51               [ 1] 1173 	exgw	x, y
      0085A1 13 01            [ 2] 1174 	cpw	x, (0x01, sp)
      0085A3 51               [ 1] 1175 	exgw	x, y
      0085A4 2D 02            [ 1] 1176 	jrsle	00105$
                                   1177 ;	sensors.c: 449: maxValue = readValue;
      0085A6 17 01            [ 2] 1178 	ldw	(0x01, sp), y
      0085A8                       1179 00105$:
                                   1180 ;	sensors.c: 451: if (maxValue > minValue)
      0085A8 1E 01            [ 2] 1181 	ldw	x, (0x01, sp)
      0085AA A3 00 02         [ 2] 1182 	cpw	x, #0x0002
      0085AD 2D 06            [ 1] 1183 	jrsle	00107$
                                   1184 ;	sensors.c: 453: TIM1_CR1 = 0x01; // enable timer
      0085AF AE 52 50         [ 2] 1185 	ldw	x, #0x5250
      0085B2 A6 01            [ 1] 1186 	ld	a, #0x01
      0085B4 F7               [ 1] 1187 	ld	(x), a
      0085B5                       1188 00107$:
                                   1189 ;	sensors.c: 455: if (readValue < minValue)
      0085B5 90 A3 00 02      [ 2] 1190 	cpw	y, #0x0002
      0085B9 2E 0D            [ 1] 1191 	jrsge	00109$
                                   1192 ;	sensors.c: 457: TIM1_CR1 = 0x00; // disable timer
      0085BB AE 52 50         [ 2] 1193 	ldw	x, #0x5250
      0085BE 7F               [ 1] 1194 	clr	(x)
                                   1195 ;	sensors.c: 458: tijd=clock();
      0085BF CD 84 D8         [ 4] 1196 	call	_clock
                                   1197 ;	sensors.c: 459: print_UCHAR_hex(tijd);
      0085C2 9F               [ 1] 1198 	ld	a, xl
      0085C3 88               [ 1] 1199 	push	a
      0085C4 CD 81 97         [ 4] 1200 	call	_print_UCHAR_hex
      0085C7 84               [ 1] 1201 	pop	a
      0085C8                       1202 00109$:
                                   1203 ;	sensors.c: 465: tm1637DisplayDecimal(val, 1); // eg 37:12
      0085C8 16 05            [ 2] 1204 	ldw	y, (0x05, sp)
      0085CA 5F               [ 1] 1205 	clrw	x
      0085CB 4B 01            [ 1] 1206 	push	#0x01
      0085CD 4B 00            [ 1] 1207 	push	#0x00
      0085CF 90 89            [ 2] 1208 	pushw	y
      0085D1 89               [ 2] 1209 	pushw	x
      0085D2 CD 83 76         [ 4] 1210 	call	_tm1637DisplayDecimal
      0085D5 5B 06            [ 2] 1211 	addw	sp, #6
      0085D7 CC 85 45         [ 2] 1212 	jp	00111$
      0085DA 5B 0A            [ 2] 1213 	addw	sp, #10
      0085DC 81               [ 4] 1214 	ret
                                   1215 	.area CODE
      0085DD                       1216 _segmentMap:
      0085DD 3F                    1217 	.db #0x3F	;  63
      0085DE 06                    1218 	.db #0x06	;  6
      0085DF 5B                    1219 	.db #0x5B	;  91
      0085E0 4F                    1220 	.db #0x4F	;  79	'O'
      0085E1 66                    1221 	.db #0x66	;  102	'f'
      0085E2 6D                    1222 	.db #0x6D	;  109	'm'
      0085E3 7D                    1223 	.db #0x7D	;  125
      0085E4 07                    1224 	.db #0x07	;  7
      0085E5 7F                    1225 	.db #0x7F	;  127
      0085E6 6F                    1226 	.db #0x6F	;  111	'o'
      0085E7 77                    1227 	.db #0x77	;  119	'w'
      0085E8 7C                    1228 	.db #0x7C	;  124
      0085E9 39                    1229 	.db #0x39	;  57	'9'
      0085EA 5E                    1230 	.db #0x5E	;  94
      0085EB 79                    1231 	.db #0x79	;  121	'y'
      0085EC 71                    1232 	.db #0x71	;  113	'q'
      0085ED 00                    1233 	.db #0x00	;  0
      0085EE                       1234 ___str_0:
      0085EE 76 61 6C 75 65 20 3D  1235 	.ascii "value = "
             20
      0085F6 0A                    1236 	.db 0x0A
      0085F7 0D                    1237 	.db 0x0D
      0085F8 00                    1238 	.db 0x00
                                   1239 	.area INITIALIZER
                                   1240 	.area CABS (ABS)
