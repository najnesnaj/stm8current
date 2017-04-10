                                      1 ;--------------------------------------------------------
                                      2 ; File Created by SDCC : free open source ANSI-C Compiler
                                      3 ; Version 3.4.0 #8981 (Jul 11 2014) (Linux)
                                      4 ; This file was generated Mon Apr 10 14:57:47 2017
                                      5 ;--------------------------------------------------------
                                      6 	.module sensors
                                      7 	.optsdcc -mstm8
                                      8 	
                                      9 ;--------------------------------------------------------
                                     10 ; Public variables in this module
                                     11 ;--------------------------------------------------------
                                     12 	.globl _segmentMap
                                     13 	.globl _main
                                     14 	.globl _tm1637DisplayDecimal
                                     15 	.globl _tm1637Init
                                     16 	.globl _InitializeUART
                                     17 	.globl _InitializeI2C
                                     18 	.globl _i2c_read_register
                                     19 	.globl _print_byte_hex
                                     20 	.globl _i2c_set_start_ack
                                     21 	.globl _i2c_send_address
                                     22 	.globl _print_UCHAR_hex
                                     23 	.globl _UARTPrintF
                                     24 	.globl _i2c_send_reg
                                     25 	.globl _i2c_set_stop
                                     26 	.globl _i2c_set_nak
                                     27 	.globl _i2c_read
                                     28 	.globl _delay
                                     29 	.globl _InitializeSystemClock
                                     30 	.globl _delayTenMicro
                                     31 	.globl _tm1637SetBrightness
                                     32 	.globl __tm1637Start
                                     33 	.globl __tm1637Stop
                                     34 	.globl __tm1637ReadResult
                                     35 	.globl __tm1637WriteByte
                                     36 	.globl __tm1637ClkHigh
                                     37 	.globl __tm1637ClkLow
                                     38 	.globl __tm1637DioHigh
                                     39 	.globl __tm1637DioLow
                                     40 ;--------------------------------------------------------
                                     41 ; ram data
                                     42 ;--------------------------------------------------------
                                     43 	.area DATA
                                     44 ;--------------------------------------------------------
                                     45 ; ram data
                                     46 ;--------------------------------------------------------
                                     47 	.area INITIALIZED
                                     48 ;--------------------------------------------------------
                                     49 ; Stack segment in internal ram 
                                     50 ;--------------------------------------------------------
                                     51 	.area	SSEG
      000000                         52 __start__stack:
      000000                         53 	.ds	1
                                     54 
                                     55 ;--------------------------------------------------------
                                     56 ; absolute external ram data
                                     57 ;--------------------------------------------------------
                                     58 	.area DABS (ABS)
                                     59 ;--------------------------------------------------------
                                     60 ; interrupt vector 
                                     61 ;--------------------------------------------------------
                                     62 	.area HOME
      008000                         63 __interrupt_vect:
      008000 82 00 80 83             64 	int s_GSINIT ;reset
      008004 82 00 00 00             65 	int 0x0000 ;trap
      008008 82 00 00 00             66 	int 0x0000 ;int0
      00800C 82 00 00 00             67 	int 0x0000 ;int1
      008010 82 00 00 00             68 	int 0x0000 ;int2
      008014 82 00 00 00             69 	int 0x0000 ;int3
      008018 82 00 00 00             70 	int 0x0000 ;int4
      00801C 82 00 00 00             71 	int 0x0000 ;int5
      008020 82 00 00 00             72 	int 0x0000 ;int6
      008024 82 00 00 00             73 	int 0x0000 ;int7
      008028 82 00 00 00             74 	int 0x0000 ;int8
      00802C 82 00 00 00             75 	int 0x0000 ;int9
      008030 82 00 00 00             76 	int 0x0000 ;int10
      008034 82 00 00 00             77 	int 0x0000 ;int11
      008038 82 00 00 00             78 	int 0x0000 ;int12
      00803C 82 00 00 00             79 	int 0x0000 ;int13
      008040 82 00 00 00             80 	int 0x0000 ;int14
      008044 82 00 00 00             81 	int 0x0000 ;int15
      008048 82 00 00 00             82 	int 0x0000 ;int16
      00804C 82 00 00 00             83 	int 0x0000 ;int17
      008050 82 00 00 00             84 	int 0x0000 ;int18
      008054 82 00 00 00             85 	int 0x0000 ;int19
      008058 82 00 00 00             86 	int 0x0000 ;int20
      00805C 82 00 00 00             87 	int 0x0000 ;int21
      008060 82 00 00 00             88 	int 0x0000 ;int22
      008064 82 00 00 00             89 	int 0x0000 ;int23
      008068 82 00 00 00             90 	int 0x0000 ;int24
      00806C 82 00 00 00             91 	int 0x0000 ;int25
      008070 82 00 00 00             92 	int 0x0000 ;int26
      008074 82 00 00 00             93 	int 0x0000 ;int27
      008078 82 00 00 00             94 	int 0x0000 ;int28
      00807C 82 00 00 00             95 	int 0x0000 ;int29
                                     96 ;--------------------------------------------------------
                                     97 ; global & static initialisations
                                     98 ;--------------------------------------------------------
                                     99 	.area HOME
                                    100 	.area GSINIT
                                    101 	.area GSFINAL
                                    102 	.area GSINIT
      008083                        103 __sdcc_gs_init_startup:
      008083                        104 __sdcc_init_data:
                                    105 ; stm8_genXINIT() start
      008083 AE 00 00         [ 2]  106 	ldw x, #l_DATA
      008086 27 07            [ 1]  107 	jreq	00002$
      008088                        108 00001$:
      008088 72 4F 00 00      [ 1]  109 	clr (s_DATA - 1, x)
      00808C 5A               [ 2]  110 	decw x
      00808D 26 F9            [ 1]  111 	jrne	00001$
      00808F                        112 00002$:
      00808F AE 00 00         [ 2]  113 	ldw	x, #l_INITIALIZER
      008092 27 09            [ 1]  114 	jreq	00004$
      008094                        115 00003$:
      008094 D6 85 F5         [ 1]  116 	ld	a, (s_INITIALIZER - 1, x)
      008097 D7 00 00         [ 1]  117 	ld	(s_INITIALIZED - 1, x), a
      00809A 5A               [ 2]  118 	decw	x
      00809B 26 F7            [ 1]  119 	jrne	00003$
      00809D                        120 00004$:
                                    121 ; stm8_genXINIT() end
                                    122 	.area GSFINAL
      00809D CC 80 80         [ 2]  123 	jp	__sdcc_program_startup
                                    124 ;--------------------------------------------------------
                                    125 ; Home
                                    126 ;--------------------------------------------------------
                                    127 	.area HOME
                                    128 	.area HOME
      008080                        129 __sdcc_program_startup:
      008080 CC 84 D8         [ 2]  130 	jp	_main
                                    131 ;	return from main will return to caller
                                    132 ;--------------------------------------------------------
                                    133 ; code
                                    134 ;--------------------------------------------------------
                                    135 	.area CODE
                                    136 ;	sensors.c: 15: void delayTenMicro (void) {
                                    137 ;	-----------------------------------------
                                    138 ;	 function delayTenMicro
                                    139 ;	-----------------------------------------
      0080A0                        140 _delayTenMicro:
                                    141 ;	sensors.c: 17: for (a = 0; a < 50; ++a)
      0080A0 A6 32            [ 1]  142 	ld	a, #0x32
      0080A2                        143 00104$:
                                    144 ;	sensors.c: 18: __asm__("nop");
      0080A2 9D               [ 1]  145 	nop
      0080A3 4A               [ 1]  146 	dec	a
                                    147 ;	sensors.c: 17: for (a = 0; a < 50; ++a)
      0080A4 4D               [ 1]  148 	tnz	a
      0080A5 26 FB            [ 1]  149 	jrne	00104$
      0080A7 81               [ 4]  150 	ret
                                    151 ;	sensors.c: 21: void InitializeSystemClock() {
                                    152 ;	-----------------------------------------
                                    153 ;	 function InitializeSystemClock
                                    154 ;	-----------------------------------------
      0080A8                        155 _InitializeSystemClock:
                                    156 ;	sensors.c: 22: CLK_ICKR = 0;                       //  Reset the Internal Clock Register.
      0080A8 AE 50 C0         [ 2]  157 	ldw	x, #0x50c0
      0080AB 7F               [ 1]  158 	clr	(x)
                                    159 ;	sensors.c: 23: CLK_ICKR = CLK_HSIEN;               //  Enable the HSI.
      0080AC AE 50 C0         [ 2]  160 	ldw	x, #0x50c0
      0080AF A6 01            [ 1]  161 	ld	a, #0x01
      0080B1 F7               [ 1]  162 	ld	(x), a
                                    163 ;	sensors.c: 24: CLK_ECKR = 0;                       //  Disable the external clock.
      0080B2 AE 50 C1         [ 2]  164 	ldw	x, #0x50c1
      0080B5 7F               [ 1]  165 	clr	(x)
                                    166 ;	sensors.c: 25: while ((CLK_ICKR & CLK_HSIRDY) == 0);       //  Wait for the HSI to be ready for use.
      0080B6                        167 00101$:
      0080B6 AE 50 C0         [ 2]  168 	ldw	x, #0x50c0
      0080B9 F6               [ 1]  169 	ld	a, (x)
      0080BA A5 02            [ 1]  170 	bcp	a, #0x02
      0080BC 27 F8            [ 1]  171 	jreq	00101$
                                    172 ;	sensors.c: 26: CLK_CKDIVR = 0;                     //  Ensure the clocks are running at full speed.
      0080BE AE 50 C6         [ 2]  173 	ldw	x, #0x50c6
      0080C1 7F               [ 1]  174 	clr	(x)
                                    175 ;	sensors.c: 27: CLK_PCKENR1 = 0xff;                 //  Enable all peripheral clocks.
      0080C2 AE 50 C7         [ 2]  176 	ldw	x, #0x50c7
      0080C5 A6 FF            [ 1]  177 	ld	a, #0xff
      0080C7 F7               [ 1]  178 	ld	(x), a
                                    179 ;	sensors.c: 28: CLK_PCKENR2 = 0xff;                 //  Ditto.
      0080C8 AE 50 CA         [ 2]  180 	ldw	x, #0x50ca
      0080CB A6 FF            [ 1]  181 	ld	a, #0xff
      0080CD F7               [ 1]  182 	ld	(x), a
                                    183 ;	sensors.c: 29: CLK_CCOR = 0;                       //  Turn off CCO.
      0080CE AE 50 C9         [ 2]  184 	ldw	x, #0x50c9
      0080D1 7F               [ 1]  185 	clr	(x)
                                    186 ;	sensors.c: 30: CLK_HSITRIMR = 0;                   //  Turn off any HSIU trimming.
      0080D2 AE 50 CC         [ 2]  187 	ldw	x, #0x50cc
      0080D5 7F               [ 1]  188 	clr	(x)
                                    189 ;	sensors.c: 31: CLK_SWIMCCR = 0;                    //  Set SWIM to run at clock / 2.
      0080D6 AE 50 CD         [ 2]  190 	ldw	x, #0x50cd
      0080D9 7F               [ 1]  191 	clr	(x)
                                    192 ;	sensors.c: 32: CLK_SWR = 0xe1;                     //  Use HSI as the clock source.
      0080DA AE 50 C4         [ 2]  193 	ldw	x, #0x50c4
      0080DD A6 E1            [ 1]  194 	ld	a, #0xe1
      0080DF F7               [ 1]  195 	ld	(x), a
                                    196 ;	sensors.c: 33: CLK_SWCR = 0;                       //  Reset the clock switch control register.
      0080E0 AE 50 C5         [ 2]  197 	ldw	x, #0x50c5
      0080E3 7F               [ 1]  198 	clr	(x)
                                    199 ;	sensors.c: 34: CLK_SWCR = CLK_SWEN;                //  Enable switching.
      0080E4 AE 50 C5         [ 2]  200 	ldw	x, #0x50c5
      0080E7 A6 02            [ 1]  201 	ld	a, #0x02
      0080E9 F7               [ 1]  202 	ld	(x), a
                                    203 ;	sensors.c: 35: while ((CLK_SWCR & CLK_SWBSY) != 0);        //  Pause while the clock switch is busy.
      0080EA                        204 00104$:
      0080EA AE 50 C5         [ 2]  205 	ldw	x, #0x50c5
      0080ED F6               [ 1]  206 	ld	a, (x)
      0080EE 44               [ 1]  207 	srl	a
      0080EF 25 F9            [ 1]  208 	jrc	00104$
      0080F1 81               [ 4]  209 	ret
                                    210 ;	sensors.c: 37: void delay (int time_ms) {
                                    211 ;	-----------------------------------------
                                    212 ;	 function delay
                                    213 ;	-----------------------------------------
      0080F2                        214 _delay:
      0080F2 52 0A            [ 2]  215 	sub	sp, #10
                                    216 ;	sensors.c: 39: for (x = 0; x < 1036*time_ms; ++x)
      0080F4 5F               [ 1]  217 	clrw	x
      0080F5 1F 03            [ 2]  218 	ldw	(0x03, sp), x
      0080F7 1F 01            [ 2]  219 	ldw	(0x01, sp), x
      0080F9 1E 0D            [ 2]  220 	ldw	x, (0x0d, sp)
      0080FB 89               [ 2]  221 	pushw	x
      0080FC 4B 0C            [ 1]  222 	push	#0x0c
      0080FE 4B 04            [ 1]  223 	push	#0x04
      008100 CD 85 A0         [ 4]  224 	call	__mulint
      008103 5B 04            [ 2]  225 	addw	sp, #4
      008105 1F 09            [ 2]  226 	ldw	(0x09, sp), x
      008107                        227 00103$:
      008107 16 09            [ 2]  228 	ldw	y, (0x09, sp)
      008109 17 07            [ 2]  229 	ldw	(0x07, sp), y
      00810B 7B 07            [ 1]  230 	ld	a, (0x07, sp)
      00810D 49               [ 1]  231 	rlc	a
      00810E 4F               [ 1]  232 	clr	a
      00810F A2 00            [ 1]  233 	sbc	a, #0x00
      008111 6B 06            [ 1]  234 	ld	(0x06, sp), a
      008113 6B 05            [ 1]  235 	ld	(0x05, sp), a
      008115 1E 03            [ 2]  236 	ldw	x, (0x03, sp)
      008117 13 07            [ 2]  237 	cpw	x, (0x07, sp)
      008119 7B 02            [ 1]  238 	ld	a, (0x02, sp)
      00811B 12 06            [ 1]  239 	sbc	a, (0x06, sp)
      00811D 7B 01            [ 1]  240 	ld	a, (0x01, sp)
      00811F 12 05            [ 1]  241 	sbc	a, (0x05, sp)
      008121 2E 17            [ 1]  242 	jrsge	00105$
                                    243 ;	sensors.c: 40: __asm__("nop");
      008123 9D               [ 1]  244 	nop
                                    245 ;	sensors.c: 39: for (x = 0; x < 1036*time_ms; ++x)
      008124 16 03            [ 2]  246 	ldw	y, (0x03, sp)
      008126 72 A9 00 01      [ 2]  247 	addw	y, #0x0001
      00812A 7B 02            [ 1]  248 	ld	a, (0x02, sp)
      00812C A9 00            [ 1]  249 	adc	a, #0x00
      00812E 97               [ 1]  250 	ld	xl, a
      00812F 7B 01            [ 1]  251 	ld	a, (0x01, sp)
      008131 A9 00            [ 1]  252 	adc	a, #0x00
      008133 95               [ 1]  253 	ld	xh, a
      008134 17 03            [ 2]  254 	ldw	(0x03, sp), y
      008136 1F 01            [ 2]  255 	ldw	(0x01, sp), x
      008138 20 CD            [ 2]  256 	jra	00103$
      00813A                        257 00105$:
      00813A 5B 0A            [ 2]  258 	addw	sp, #10
      00813C 81               [ 4]  259 	ret
                                    260 ;	sensors.c: 42: void i2c_read (unsigned char *x) {
                                    261 ;	-----------------------------------------
                                    262 ;	 function i2c_read
                                    263 ;	-----------------------------------------
      00813D                        264 _i2c_read:
                                    265 ;	sensors.c: 43: while ((I2C_SR1 & I2C_RXNE) == 0);
      00813D                        266 00101$:
      00813D AE 52 17         [ 2]  267 	ldw	x, #0x5217
      008140 F6               [ 1]  268 	ld	a, (x)
      008141 A5 40            [ 1]  269 	bcp	a, #0x40
      008143 27 F8            [ 1]  270 	jreq	00101$
                                    271 ;	sensors.c: 44: *x = I2C_DR;
      008145 16 03            [ 2]  272 	ldw	y, (0x03, sp)
      008147 AE 52 16         [ 2]  273 	ldw	x, #0x5216
      00814A F6               [ 1]  274 	ld	a, (x)
      00814B 90 F7            [ 1]  275 	ld	(y), a
      00814D 81               [ 4]  276 	ret
                                    277 ;	sensors.c: 46: void i2c_set_nak (void) {
                                    278 ;	-----------------------------------------
                                    279 ;	 function i2c_set_nak
                                    280 ;	-----------------------------------------
      00814E                        281 _i2c_set_nak:
                                    282 ;	sensors.c: 47: I2C_CR2 &= ~I2C_ACK;
      00814E AE 52 11         [ 2]  283 	ldw	x, #0x5211
      008151 F6               [ 1]  284 	ld	a, (x)
      008152 A4 FB            [ 1]  285 	and	a, #0xfb
      008154 F7               [ 1]  286 	ld	(x), a
      008155 81               [ 4]  287 	ret
                                    288 ;	sensors.c: 49: void i2c_set_stop (void) {
                                    289 ;	-----------------------------------------
                                    290 ;	 function i2c_set_stop
                                    291 ;	-----------------------------------------
      008156                        292 _i2c_set_stop:
                                    293 ;	sensors.c: 50: I2C_CR2 |= I2C_STOP;
      008156 AE 52 11         [ 2]  294 	ldw	x, #0x5211
      008159 F6               [ 1]  295 	ld	a, (x)
      00815A AA 02            [ 1]  296 	or	a, #0x02
      00815C F7               [ 1]  297 	ld	(x), a
      00815D 81               [ 4]  298 	ret
                                    299 ;	sensors.c: 52: void i2c_send_reg (UCHAR addr) {
                                    300 ;	-----------------------------------------
                                    301 ;	 function i2c_send_reg
                                    302 ;	-----------------------------------------
      00815E                        303 _i2c_send_reg:
      00815E 52 02            [ 2]  304 	sub	sp, #2
                                    305 ;	sensors.c: 54: reg = I2C_SR1;
      008160 AE 52 17         [ 2]  306 	ldw	x, #0x5217
      008163 F6               [ 1]  307 	ld	a, (x)
      008164 5F               [ 1]  308 	clrw	x
      008165 97               [ 1]  309 	ld	xl, a
      008166 1F 01            [ 2]  310 	ldw	(0x01, sp), x
                                    311 ;	sensors.c: 55: reg = I2C_SR3;
      008168 AE 52 19         [ 2]  312 	ldw	x, #0x5219
      00816B F6               [ 1]  313 	ld	a, (x)
      00816C 5F               [ 1]  314 	clrw	x
      00816D 97               [ 1]  315 	ld	xl, a
      00816E 1F 01            [ 2]  316 	ldw	(0x01, sp), x
                                    317 ;	sensors.c: 56: I2C_DR = addr;
      008170 AE 52 16         [ 2]  318 	ldw	x, #0x5216
      008173 7B 05            [ 1]  319 	ld	a, (0x05, sp)
      008175 F7               [ 1]  320 	ld	(x), a
                                    321 ;	sensors.c: 57: while ((I2C_SR1 & I2C_TXE) == 0);
      008176                        322 00101$:
      008176 AE 52 17         [ 2]  323 	ldw	x, #0x5217
      008179 F6               [ 1]  324 	ld	a, (x)
      00817A 48               [ 1]  325 	sll	a
      00817B 24 F9            [ 1]  326 	jrnc	00101$
      00817D 5B 02            [ 2]  327 	addw	sp, #2
      00817F 81               [ 4]  328 	ret
                                    329 ;	sensors.c: 61: void UARTPrintF (char *message) {
                                    330 ;	-----------------------------------------
                                    331 ;	 function UARTPrintF
                                    332 ;	-----------------------------------------
      008180                        333 _UARTPrintF:
                                    334 ;	sensors.c: 62: char *ch = message;
      008180 16 03            [ 2]  335 	ldw	y, (0x03, sp)
                                    336 ;	sensors.c: 63: while (*ch) {
      008182                        337 00104$:
      008182 90 F6            [ 1]  338 	ld	a, (y)
      008184 4D               [ 1]  339 	tnz	a
      008185 27 0F            [ 1]  340 	jreq	00107$
                                    341 ;	sensors.c: 64: UART1_DR = (unsigned char) *ch;     //  Put the next character into the data transmission register.
      008187 AE 52 31         [ 2]  342 	ldw	x, #0x5231
      00818A F7               [ 1]  343 	ld	(x), a
                                    344 ;	sensors.c: 65: while ((UART1_SR & SR_TXE) == 0);   //  Wait for transmission to complete.
      00818B                        345 00101$:
      00818B AE 52 30         [ 2]  346 	ldw	x, #0x5230
      00818E F6               [ 1]  347 	ld	a, (x)
      00818F 48               [ 1]  348 	sll	a
      008190 24 F9            [ 1]  349 	jrnc	00101$
                                    350 ;	sensors.c: 66: ch++;                               //  Grab the next character.
      008192 90 5C            [ 2]  351 	incw	y
      008194 20 EC            [ 2]  352 	jra	00104$
      008196                        353 00107$:
      008196 81               [ 4]  354 	ret
                                    355 ;	sensors.c: 70: void print_UCHAR_hex (unsigned char buffer) {
                                    356 ;	-----------------------------------------
                                    357 ;	 function print_UCHAR_hex
                                    358 ;	-----------------------------------------
      008197                        359 _print_UCHAR_hex:
      008197 52 0C            [ 2]  360 	sub	sp, #12
                                    361 ;	sensors.c: 73: a = (buffer >> 4);
      008199 7B 0F            [ 1]  362 	ld	a, (0x0f, sp)
      00819B 4E               [ 1]  363 	swap	a
      00819C A4 0F            [ 1]  364 	and	a, #0x0f
      00819E 5F               [ 1]  365 	clrw	x
      00819F 97               [ 1]  366 	ld	xl, a
                                    367 ;	sensors.c: 74: if (a > 9)
      0081A0 A3 00 09         [ 2]  368 	cpw	x, #0x0009
      0081A3 2D 07            [ 1]  369 	jrsle	00102$
                                    370 ;	sensors.c: 75: a = a + 'a' - 10;
      0081A5 1C 00 57         [ 2]  371 	addw	x, #0x0057
      0081A8 1F 01            [ 2]  372 	ldw	(0x01, sp), x
      0081AA 20 05            [ 2]  373 	jra	00103$
      0081AC                        374 00102$:
                                    375 ;	sensors.c: 77: a += '0';
      0081AC 1C 00 30         [ 2]  376 	addw	x, #0x0030
      0081AF 1F 01            [ 2]  377 	ldw	(0x01, sp), x
      0081B1                        378 00103$:
                                    379 ;	sensors.c: 78: b = buffer & 0x0f;
      0081B1 7B 0F            [ 1]  380 	ld	a, (0x0f, sp)
      0081B3 A4 0F            [ 1]  381 	and	a, #0x0f
      0081B5 5F               [ 1]  382 	clrw	x
      0081B6 97               [ 1]  383 	ld	xl, a
                                    384 ;	sensors.c: 79: if (b > 9)
      0081B7 A3 00 09         [ 2]  385 	cpw	x, #0x0009
      0081BA 2D 07            [ 1]  386 	jrsle	00105$
                                    387 ;	sensors.c: 80: b = b + 'a' - 10;
      0081BC 1C 00 57         [ 2]  388 	addw	x, #0x0057
      0081BF 1F 0B            [ 2]  389 	ldw	(0x0b, sp), x
      0081C1 20 05            [ 2]  390 	jra	00106$
      0081C3                        391 00105$:
                                    392 ;	sensors.c: 82: b += '0';
      0081C3 1C 00 30         [ 2]  393 	addw	x, #0x0030
      0081C6 1F 0B            [ 2]  394 	ldw	(0x0b, sp), x
      0081C8                        395 00106$:
                                    396 ;	sensors.c: 83: message[0] = a;
      0081C8 90 96            [ 1]  397 	ldw	y, sp
      0081CA 72 A9 00 03      [ 2]  398 	addw	y, #3
      0081CE 7B 02            [ 1]  399 	ld	a, (0x02, sp)
      0081D0 90 F7            [ 1]  400 	ld	(y), a
                                    401 ;	sensors.c: 84: message[1] = b;
      0081D2 93               [ 1]  402 	ldw	x, y
      0081D3 5C               [ 2]  403 	incw	x
      0081D4 7B 0C            [ 1]  404 	ld	a, (0x0c, sp)
      0081D6 F7               [ 1]  405 	ld	(x), a
                                    406 ;	sensors.c: 85: message[2] = 0;
      0081D7 93               [ 1]  407 	ldw	x, y
      0081D8 5C               [ 2]  408 	incw	x
      0081D9 5C               [ 2]  409 	incw	x
      0081DA 7F               [ 1]  410 	clr	(x)
                                    411 ;	sensors.c: 86: UARTPrintF (message);
      0081DB 90 89            [ 2]  412 	pushw	y
      0081DD CD 81 80         [ 4]  413 	call	_UARTPrintF
      0081E0 5B 02            [ 2]  414 	addw	sp, #2
      0081E2 5B 0C            [ 2]  415 	addw	sp, #12
      0081E4 81               [ 4]  416 	ret
                                    417 ;	sensors.c: 89: void i2c_send_address (UCHAR addr, UCHAR mode) {
                                    418 ;	-----------------------------------------
                                    419 ;	 function i2c_send_address
                                    420 ;	-----------------------------------------
      0081E5                        421 _i2c_send_address:
      0081E5 52 03            [ 2]  422 	sub	sp, #3
                                    423 ;	sensors.c: 91: reg = I2C_SR1;
      0081E7 AE 52 17         [ 2]  424 	ldw	x, #0x5217
      0081EA F6               [ 1]  425 	ld	a, (x)
      0081EB 5F               [ 1]  426 	clrw	x
      0081EC 97               [ 1]  427 	ld	xl, a
      0081ED 1F 01            [ 2]  428 	ldw	(0x01, sp), x
                                    429 ;	sensors.c: 92: I2C_DR = (addr << 1) | mode;
      0081EF 7B 06            [ 1]  430 	ld	a, (0x06, sp)
      0081F1 48               [ 1]  431 	sll	a
      0081F2 1A 07            [ 1]  432 	or	a, (0x07, sp)
      0081F4 AE 52 16         [ 2]  433 	ldw	x, #0x5216
      0081F7 F7               [ 1]  434 	ld	(x), a
                                    435 ;	sensors.c: 93: if (mode == I2C_READ) {
      0081F8 7B 07            [ 1]  436 	ld	a, (0x07, sp)
      0081FA A1 01            [ 1]  437 	cp	a, #0x01
      0081FC 26 06            [ 1]  438 	jrne	00127$
      0081FE A6 01            [ 1]  439 	ld	a, #0x01
      008200 6B 03            [ 1]  440 	ld	(0x03, sp), a
      008202 20 02            [ 2]  441 	jra	00128$
      008204                        442 00127$:
      008204 0F 03            [ 1]  443 	clr	(0x03, sp)
      008206                        444 00128$:
      008206 0D 03            [ 1]  445 	tnz	(0x03, sp)
      008208 27 08            [ 1]  446 	jreq	00103$
                                    447 ;	sensors.c: 94: I2C_OARL = 0;
      00820A AE 52 13         [ 2]  448 	ldw	x, #0x5213
      00820D 7F               [ 1]  449 	clr	(x)
                                    450 ;	sensors.c: 95: I2C_OARH = 0;
      00820E AE 52 14         [ 2]  451 	ldw	x, #0x5214
      008211 7F               [ 1]  452 	clr	(x)
                                    453 ;	sensors.c: 98: while ((I2C_SR1 & I2C_ADDR) == 0);
      008212                        454 00103$:
                                    455 ;	sensors.c: 91: reg = I2C_SR1;
      008212 AE 52 17         [ 2]  456 	ldw	x, #0x5217
      008215 F6               [ 1]  457 	ld	a, (x)
                                    458 ;	sensors.c: 98: while ((I2C_SR1 & I2C_ADDR) == 0);
      008216 A5 02            [ 1]  459 	bcp	a, #0x02
      008218 27 F8            [ 1]  460 	jreq	00103$
                                    461 ;	sensors.c: 99: if (mode == I2C_READ)
      00821A 0D 03            [ 1]  462 	tnz	(0x03, sp)
      00821C 27 06            [ 1]  463 	jreq	00108$
                                    464 ;	sensors.c: 100: UNSET (I2C_SR1, I2C_ADDR);
      00821E A4 FD            [ 1]  465 	and	a, #0xfd
      008220 AE 52 17         [ 2]  466 	ldw	x, #0x5217
      008223 F7               [ 1]  467 	ld	(x), a
      008224                        468 00108$:
      008224 5B 03            [ 2]  469 	addw	sp, #3
      008226 81               [ 4]  470 	ret
                                    471 ;	sensors.c: 103: void i2c_set_start_ack (void) {
                                    472 ;	-----------------------------------------
                                    473 ;	 function i2c_set_start_ack
                                    474 ;	-----------------------------------------
      008227                        475 _i2c_set_start_ack:
                                    476 ;	sensors.c: 104: I2C_CR2 = I2C_ACK | I2C_START;
      008227 AE 52 11         [ 2]  477 	ldw	x, #0x5211
      00822A A6 05            [ 1]  478 	ld	a, #0x05
      00822C F7               [ 1]  479 	ld	(x), a
                                    480 ;	sensors.c: 105: while ((I2C_SR1 & I2C_SB) == 0);
      00822D                        481 00101$:
      00822D AE 52 17         [ 2]  482 	ldw	x, #0x5217
      008230 F6               [ 1]  483 	ld	a, (x)
      008231 44               [ 1]  484 	srl	a
      008232 24 F9            [ 1]  485 	jrnc	00101$
      008234 81               [ 4]  486 	ret
                                    487 ;	sensors.c: 112: void print_byte_hex (unsigned char buffer) {
                                    488 ;	-----------------------------------------
                                    489 ;	 function print_byte_hex
                                    490 ;	-----------------------------------------
      008235                        491 _print_byte_hex:
      008235 52 0C            [ 2]  492 	sub	sp, #12
                                    493 ;	sensors.c: 115: a = (buffer >> 4);
      008237 7B 0F            [ 1]  494 	ld	a, (0x0f, sp)
      008239 4E               [ 1]  495 	swap	a
      00823A A4 0F            [ 1]  496 	and	a, #0x0f
      00823C 5F               [ 1]  497 	clrw	x
      00823D 97               [ 1]  498 	ld	xl, a
                                    499 ;	sensors.c: 116: if (a > 9)
      00823E A3 00 09         [ 2]  500 	cpw	x, #0x0009
      008241 2D 07            [ 1]  501 	jrsle	00102$
                                    502 ;	sensors.c: 117: a = a + 'a' - 10;
      008243 1C 00 57         [ 2]  503 	addw	x, #0x0057
      008246 1F 03            [ 2]  504 	ldw	(0x03, sp), x
      008248 20 05            [ 2]  505 	jra	00103$
      00824A                        506 00102$:
                                    507 ;	sensors.c: 119: a += '0'; 
      00824A 1C 00 30         [ 2]  508 	addw	x, #0x0030
      00824D 1F 03            [ 2]  509 	ldw	(0x03, sp), x
      00824F                        510 00103$:
                                    511 ;	sensors.c: 120: b = buffer & 0x0f;
      00824F 7B 0F            [ 1]  512 	ld	a, (0x0f, sp)
      008251 A4 0F            [ 1]  513 	and	a, #0x0f
      008253 5F               [ 1]  514 	clrw	x
      008254 97               [ 1]  515 	ld	xl, a
                                    516 ;	sensors.c: 121: if (b > 9)
      008255 A3 00 09         [ 2]  517 	cpw	x, #0x0009
      008258 2D 07            [ 1]  518 	jrsle	00105$
                                    519 ;	sensors.c: 122: b = b + 'a' - 10;
      00825A 1C 00 57         [ 2]  520 	addw	x, #0x0057
      00825D 1F 01            [ 2]  521 	ldw	(0x01, sp), x
      00825F 20 05            [ 2]  522 	jra	00106$
      008261                        523 00105$:
                                    524 ;	sensors.c: 124: b += '0'; 
      008261 1C 00 30         [ 2]  525 	addw	x, #0x0030
      008264 1F 01            [ 2]  526 	ldw	(0x01, sp), x
      008266                        527 00106$:
                                    528 ;	sensors.c: 125: message[0] = a;
      008266 90 96            [ 1]  529 	ldw	y, sp
      008268 72 A9 00 05      [ 2]  530 	addw	y, #5
      00826C 7B 04            [ 1]  531 	ld	a, (0x04, sp)
      00826E 90 F7            [ 1]  532 	ld	(y), a
                                    533 ;	sensors.c: 126: message[1] = b;
      008270 93               [ 1]  534 	ldw	x, y
      008271 5C               [ 2]  535 	incw	x
      008272 7B 02            [ 1]  536 	ld	a, (0x02, sp)
      008274 F7               [ 1]  537 	ld	(x), a
                                    538 ;	sensors.c: 127: message[2] = 0;
      008275 93               [ 1]  539 	ldw	x, y
      008276 5C               [ 2]  540 	incw	x
      008277 5C               [ 2]  541 	incw	x
      008278 7F               [ 1]  542 	clr	(x)
                                    543 ;	sensors.c: 128: UARTPrintF (message);
      008279 90 89            [ 2]  544 	pushw	y
      00827B CD 81 80         [ 4]  545 	call	_UARTPrintF
      00827E 5B 02            [ 2]  546 	addw	sp, #2
      008280 5B 0C            [ 2]  547 	addw	sp, #12
      008282 81               [ 4]  548 	ret
                                    549 ;	sensors.c: 132: unsigned char i2c_read_register (UCHAR addr, UCHAR rg) {
                                    550 ;	-----------------------------------------
                                    551 ;	 function i2c_read_register
                                    552 ;	-----------------------------------------
      008283                        553 _i2c_read_register:
      008283 52 02            [ 2]  554 	sub	sp, #2
                                    555 ;	sensors.c: 135: i2c_set_start_ack ();
      008285 CD 82 27         [ 4]  556 	call	_i2c_set_start_ack
                                    557 ;	sensors.c: 136: i2c_send_address (addr, I2C_WRITE);
      008288 4B 00            [ 1]  558 	push	#0x00
      00828A 7B 06            [ 1]  559 	ld	a, (0x06, sp)
      00828C 88               [ 1]  560 	push	a
      00828D CD 81 E5         [ 4]  561 	call	_i2c_send_address
      008290 5B 02            [ 2]  562 	addw	sp, #2
                                    563 ;	sensors.c: 137: i2c_send_reg (rg);
      008292 7B 06            [ 1]  564 	ld	a, (0x06, sp)
      008294 88               [ 1]  565 	push	a
      008295 CD 81 5E         [ 4]  566 	call	_i2c_send_reg
      008298 84               [ 1]  567 	pop	a
                                    568 ;	sensors.c: 138: i2c_set_start_ack ();
      008299 CD 82 27         [ 4]  569 	call	_i2c_set_start_ack
                                    570 ;	sensors.c: 139: i2c_send_address (addr, I2C_READ);
      00829C 4B 01            [ 1]  571 	push	#0x01
      00829E 7B 06            [ 1]  572 	ld	a, (0x06, sp)
      0082A0 88               [ 1]  573 	push	a
      0082A1 CD 81 E5         [ 4]  574 	call	_i2c_send_address
      0082A4 5B 02            [ 2]  575 	addw	sp, #2
                                    576 ;	sensors.c: 140: reg = I2C_SR1;
      0082A6 AE 52 17         [ 2]  577 	ldw	x, #0x5217
      0082A9 F6               [ 1]  578 	ld	a, (x)
      0082AA 6B 01            [ 1]  579 	ld	(0x01, sp), a
                                    580 ;	sensors.c: 141: reg = I2C_SR3;
      0082AC AE 52 19         [ 2]  581 	ldw	x, #0x5219
      0082AF F6               [ 1]  582 	ld	a, (x)
      0082B0 6B 01            [ 1]  583 	ld	(0x01, sp), a
                                    584 ;	sensors.c: 142: i2c_set_nak ();
      0082B2 CD 81 4E         [ 4]  585 	call	_i2c_set_nak
                                    586 ;	sensors.c: 143: i2c_set_stop ();
      0082B5 CD 81 56         [ 4]  587 	call	_i2c_set_stop
                                    588 ;	sensors.c: 144: i2c_read (&x);
      0082B8 96               [ 1]  589 	ldw	x, sp
      0082B9 5C               [ 2]  590 	incw	x
      0082BA 5C               [ 2]  591 	incw	x
      0082BB 89               [ 2]  592 	pushw	x
      0082BC CD 81 3D         [ 4]  593 	call	_i2c_read
      0082BF 5B 02            [ 2]  594 	addw	sp, #2
                                    595 ;	sensors.c: 145: return (x);
      0082C1 7B 02            [ 1]  596 	ld	a, (0x02, sp)
      0082C3 5B 02            [ 2]  597 	addw	sp, #2
      0082C5 81               [ 4]  598 	ret
                                    599 ;	sensors.c: 148: void InitializeI2C (void) {
                                    600 ;	-----------------------------------------
                                    601 ;	 function InitializeI2C
                                    602 ;	-----------------------------------------
      0082C6                        603 _InitializeI2C:
                                    604 ;	sensors.c: 149: I2C_CR1 = 0;   //  Disable I2C before configuration starts. PE bit is bit 0
      0082C6 AE 52 10         [ 2]  605 	ldw	x, #0x5210
      0082C9 7F               [ 1]  606 	clr	(x)
                                    607 ;	sensors.c: 153: I2C_FREQR = 16;                     //  Set the internal clock frequency (MHz).
      0082CA AE 52 12         [ 2]  608 	ldw	x, #0x5212
      0082CD A6 10            [ 1]  609 	ld	a, #0x10
      0082CF F7               [ 1]  610 	ld	(x), a
                                    611 ;	sensors.c: 154: UNSET (I2C_CCRH, I2C_FS);           //  I2C running is standard mode.
      0082D0 72 17 52 1C      [ 1]  612 	bres	0x521c, #7
                                    613 ;	sensors.c: 156: I2C_CCRL = 0xa0;                    //  SCL clock speed is 50 kHz.
      0082D4 AE 52 1B         [ 2]  614 	ldw	x, #0x521b
      0082D7 A6 A0            [ 1]  615 	ld	a, #0xa0
      0082D9 F7               [ 1]  616 	ld	(x), a
                                    617 ;	sensors.c: 158: I2C_CCRH &= 0x00;	// Clears lower 4 bits "CCR"
      0082DA AE 52 1C         [ 2]  618 	ldw	x, #0x521c
      0082DD 7F               [ 1]  619 	clr	(x)
                                    620 ;	sensors.c: 162: UNSET (I2C_OARH, I2C_ADDMODE);      //  7 bit address mode.
      0082DE 72 17 52 14      [ 1]  621 	bres	0x5214, #7
                                    622 ;	sensors.c: 163: SET (I2C_OARH, I2C_ADDCONF);        //  Docs say this must always be 1.
      0082E2 AE 52 14         [ 2]  623 	ldw	x, #0x5214
      0082E5 F6               [ 1]  624 	ld	a, (x)
      0082E6 AA 40            [ 1]  625 	or	a, #0x40
      0082E8 F7               [ 1]  626 	ld	(x), a
                                    627 ;	sensors.c: 167: I2C_TRISER = 17;
      0082E9 AE 52 1D         [ 2]  628 	ldw	x, #0x521d
      0082EC A6 11            [ 1]  629 	ld	a, #0x11
      0082EE F7               [ 1]  630 	ld	(x), a
                                    631 ;	sensors.c: 175: I2C_CR1 = I2C_PE;	// Enables port
      0082EF AE 52 10         [ 2]  632 	ldw	x, #0x5210
      0082F2 A6 01            [ 1]  633 	ld	a, #0x01
      0082F4 F7               [ 1]  634 	ld	(x), a
      0082F5 81               [ 4]  635 	ret
                                    636 ;	sensors.c: 181: void InitializeUART() {
                                    637 ;	-----------------------------------------
                                    638 ;	 function InitializeUART
                                    639 ;	-----------------------------------------
      0082F6                        640 _InitializeUART:
                                    641 ;	sensors.c: 191: UART1_CR1 = 0;
      0082F6 AE 52 34         [ 2]  642 	ldw	x, #0x5234
      0082F9 7F               [ 1]  643 	clr	(x)
                                    644 ;	sensors.c: 192: UART1_CR2 = 0;
      0082FA AE 52 35         [ 2]  645 	ldw	x, #0x5235
      0082FD 7F               [ 1]  646 	clr	(x)
                                    647 ;	sensors.c: 193: UART1_CR4 = 0;
      0082FE AE 52 37         [ 2]  648 	ldw	x, #0x5237
      008301 7F               [ 1]  649 	clr	(x)
                                    650 ;	sensors.c: 194: UART1_CR3 = 0;
      008302 AE 52 36         [ 2]  651 	ldw	x, #0x5236
      008305 7F               [ 1]  652 	clr	(x)
                                    653 ;	sensors.c: 195: UART1_CR5 = 0;
      008306 AE 52 38         [ 2]  654 	ldw	x, #0x5238
      008309 7F               [ 1]  655 	clr	(x)
                                    656 ;	sensors.c: 196: UART1_GTR = 0;
      00830A AE 52 39         [ 2]  657 	ldw	x, #0x5239
      00830D 7F               [ 1]  658 	clr	(x)
                                    659 ;	sensors.c: 197: UART1_PSCR = 0;
      00830E AE 52 3A         [ 2]  660 	ldw	x, #0x523a
      008311 7F               [ 1]  661 	clr	(x)
                                    662 ;	sensors.c: 201: UNSET (UART1_CR1, CR1_M);        //  8 Data bits.
      008312 AE 52 34         [ 2]  663 	ldw	x, #0x5234
      008315 F6               [ 1]  664 	ld	a, (x)
      008316 A4 EF            [ 1]  665 	and	a, #0xef
      008318 F7               [ 1]  666 	ld	(x), a
                                    667 ;	sensors.c: 202: UNSET (UART1_CR1, CR1_PCEN);     //  Disable parity.
      008319 AE 52 34         [ 2]  668 	ldw	x, #0x5234
      00831C F6               [ 1]  669 	ld	a, (x)
      00831D A4 FB            [ 1]  670 	and	a, #0xfb
      00831F F7               [ 1]  671 	ld	(x), a
                                    672 ;	sensors.c: 203: UNSET (UART1_CR3, CR3_STOPH);    //  1 stop bit.
      008320 AE 52 36         [ 2]  673 	ldw	x, #0x5236
      008323 F6               [ 1]  674 	ld	a, (x)
      008324 A4 DF            [ 1]  675 	and	a, #0xdf
      008326 F7               [ 1]  676 	ld	(x), a
                                    677 ;	sensors.c: 204: UNSET (UART1_CR3, CR3_STOPL);    //  1 stop bit.
      008327 AE 52 36         [ 2]  678 	ldw	x, #0x5236
      00832A F6               [ 1]  679 	ld	a, (x)
      00832B A4 EF            [ 1]  680 	and	a, #0xef
      00832D F7               [ 1]  681 	ld	(x), a
                                    682 ;	sensors.c: 205: UART1_BRR2 = 0x0a;      //  Set the baud rate registers to 115200 baud
      00832E AE 52 33         [ 2]  683 	ldw	x, #0x5233
      008331 A6 0A            [ 1]  684 	ld	a, #0x0a
      008333 F7               [ 1]  685 	ld	(x), a
                                    686 ;	sensors.c: 206: UART1_BRR1 = 0x08;      //  based upon a 16 MHz system clock.
      008334 AE 52 32         [ 2]  687 	ldw	x, #0x5232
      008337 A6 08            [ 1]  688 	ld	a, #0x08
      008339 F7               [ 1]  689 	ld	(x), a
                                    690 ;	sensors.c: 210: UNSET (UART1_CR2, CR2_TEN);      //  Disable transmit.
      00833A AE 52 35         [ 2]  691 	ldw	x, #0x5235
      00833D F6               [ 1]  692 	ld	a, (x)
      00833E A4 F7            [ 1]  693 	and	a, #0xf7
      008340 F7               [ 1]  694 	ld	(x), a
                                    695 ;	sensors.c: 211: UNSET (UART1_CR2, CR2_REN);      //  Disable receive.
      008341 AE 52 35         [ 2]  696 	ldw	x, #0x5235
      008344 F6               [ 1]  697 	ld	a, (x)
      008345 A4 FB            [ 1]  698 	and	a, #0xfb
      008347 F7               [ 1]  699 	ld	(x), a
                                    700 ;	sensors.c: 215: SET (UART1_CR3, CR3_CPOL);
      008348 AE 52 36         [ 2]  701 	ldw	x, #0x5236
      00834B F6               [ 1]  702 	ld	a, (x)
      00834C AA 04            [ 1]  703 	or	a, #0x04
      00834E F7               [ 1]  704 	ld	(x), a
                                    705 ;	sensors.c: 216: SET (UART1_CR3, CR3_CPHA);
      00834F AE 52 36         [ 2]  706 	ldw	x, #0x5236
      008352 F6               [ 1]  707 	ld	a, (x)
      008353 AA 02            [ 1]  708 	or	a, #0x02
      008355 F7               [ 1]  709 	ld	(x), a
                                    710 ;	sensors.c: 217: SET (UART1_CR3, CR3_LBCL);
      008356 72 10 52 36      [ 1]  711 	bset	0x5236, #0
                                    712 ;	sensors.c: 221: SET (UART1_CR2, CR2_TEN);
      00835A AE 52 35         [ 2]  713 	ldw	x, #0x5235
      00835D F6               [ 1]  714 	ld	a, (x)
      00835E AA 08            [ 1]  715 	or	a, #0x08
      008360 F7               [ 1]  716 	ld	(x), a
                                    717 ;	sensors.c: 222: SET (UART1_CR2, CR2_REN);
      008361 AE 52 35         [ 2]  718 	ldw	x, #0x5235
      008364 F6               [ 1]  719 	ld	a, (x)
      008365 AA 04            [ 1]  720 	or	a, #0x04
      008367 F7               [ 1]  721 	ld	(x), a
                                    722 ;	sensors.c: 223: UART1_CR3 = CR3_CLKEN;
      008368 AE 52 36         [ 2]  723 	ldw	x, #0x5236
      00836B A6 08            [ 1]  724 	ld	a, #0x08
      00836D F7               [ 1]  725 	ld	(x), a
      00836E 81               [ 4]  726 	ret
                                    727 ;	sensors.c: 251: void tm1637Init(void)
                                    728 ;	-----------------------------------------
                                    729 ;	 function tm1637Init
                                    730 ;	-----------------------------------------
      00836F                        731 _tm1637Init:
                                    732 ;	sensors.c: 253: tm1637SetBrightness(8);
      00836F 4B 08            [ 1]  733 	push	#0x08
      008371 CD 84 14         [ 4]  734 	call	_tm1637SetBrightness
      008374 84               [ 1]  735 	pop	a
      008375 81               [ 4]  736 	ret
                                    737 ;	sensors.c: 258: void tm1637DisplayDecimal(long TT,unsigned int displaySeparator)
                                    738 ;	-----------------------------------------
                                    739 ;	 function tm1637DisplayDecimal
                                    740 ;	-----------------------------------------
      008376                        741 _tm1637DisplayDecimal:
      008376 52 13            [ 2]  742 	sub	sp, #19
                                    743 ;	sensors.c: 260: unsigned int v = TT & 0x0000FFFF;
      008378 7B 19            [ 1]  744 	ld	a, (0x19, sp)
      00837A 97               [ 1]  745 	ld	xl, a
      00837B 7B 18            [ 1]  746 	ld	a, (0x18, sp)
      00837D 95               [ 1]  747 	ld	xh, a
      00837E 0F 0A            [ 1]  748 	clr	(0x0a, sp)
      008380 4F               [ 1]  749 	clr	a
      008381 1F 05            [ 2]  750 	ldw	(0x05, sp), x
                                    751 ;	sensors.c: 266: for (ii = 0; ii < 4; ++ii) {
      008383 96               [ 1]  752 	ldw	x, sp
      008384 5C               [ 2]  753 	incw	x
      008385 1F 0E            [ 2]  754 	ldw	(0x0e, sp), x
      008387 AE 85 84         [ 2]  755 	ldw	x, #_segmentMap+0
      00838A 1F 12            [ 2]  756 	ldw	(0x12, sp), x
      00838C 90 5F            [ 1]  757 	clrw	y
      00838E                        758 00106$:
                                    759 ;	sensors.c: 267: digitArr[ii] = segmentMap[v % 10];
      00838E 93               [ 1]  760 	ldw	x, y
      00838F 72 FB 0E         [ 2]  761 	addw	x, (0x0e, sp)
      008392 1F 10            [ 2]  762 	ldw	(0x10, sp), x
      008394 90 89            [ 2]  763 	pushw	y
      008396 1E 07            [ 2]  764 	ldw	x, (0x07, sp)
      008398 90 AE 00 0A      [ 2]  765 	ldw	y, #0x000a
      00839C 65               [ 2]  766 	divw	x, y
      00839D 93               [ 1]  767 	ldw	x, y
      00839E 90 85            [ 2]  768 	popw	y
      0083A0 72 FB 12         [ 2]  769 	addw	x, (0x12, sp)
      0083A3 F6               [ 1]  770 	ld	a, (x)
      0083A4 1E 10            [ 2]  771 	ldw	x, (0x10, sp)
      0083A6 F7               [ 1]  772 	ld	(x), a
                                    773 ;	sensors.c: 268: if (ii == 2 && displaySeparator) {
      0083A7 90 A3 00 02      [ 2]  774 	cpw	y, #0x0002
      0083AB 26 0C            [ 1]  775 	jrne	00102$
      0083AD 1E 1A            [ 2]  776 	ldw	x, (0x1a, sp)
      0083AF 27 08            [ 1]  777 	jreq	00102$
                                    778 ;	sensors.c: 269: digitArr[ii] |= 1 << 7;
      0083B1 1E 10            [ 2]  779 	ldw	x, (0x10, sp)
      0083B3 F6               [ 1]  780 	ld	a, (x)
      0083B4 AA 80            [ 1]  781 	or	a, #0x80
      0083B6 1E 10            [ 2]  782 	ldw	x, (0x10, sp)
      0083B8 F7               [ 1]  783 	ld	(x), a
      0083B9                        784 00102$:
                                    785 ;	sensors.c: 271: v /= 10;
      0083B9 90 89            [ 2]  786 	pushw	y
      0083BB 1E 07            [ 2]  787 	ldw	x, (0x07, sp)
      0083BD 90 AE 00 0A      [ 2]  788 	ldw	y, #0x000a
      0083C1 65               [ 2]  789 	divw	x, y
      0083C2 90 85            [ 2]  790 	popw	y
      0083C4 1F 05            [ 2]  791 	ldw	(0x05, sp), x
                                    792 ;	sensors.c: 266: for (ii = 0; ii < 4; ++ii) {
      0083C6 90 5C            [ 2]  793 	incw	y
      0083C8 90 A3 00 04      [ 2]  794 	cpw	y, #0x0004
      0083CC 25 C0            [ 1]  795 	jrc	00106$
                                    796 ;	sensors.c: 274: _tm1637Start();
      0083CE CD 84 26         [ 4]  797 	call	__tm1637Start
                                    798 ;	sensors.c: 275: _tm1637WriteByte(0x40);
      0083D1 4B 40            [ 1]  799 	push	#0x40
      0083D3 CD 84 7A         [ 4]  800 	call	__tm1637WriteByte
      0083D6 84               [ 1]  801 	pop	a
                                    802 ;	sensors.c: 276: _tm1637ReadResult();
      0083D7 CD 84 5F         [ 4]  803 	call	__tm1637ReadResult
                                    804 ;	sensors.c: 277: _tm1637Stop();
      0083DA CD 84 38         [ 4]  805 	call	__tm1637Stop
                                    806 ;	sensors.c: 279: _tm1637Start();
      0083DD CD 84 26         [ 4]  807 	call	__tm1637Start
                                    808 ;	sensors.c: 280: _tm1637WriteByte(0xc0);
      0083E0 4B C0            [ 1]  809 	push	#0xc0
      0083E2 CD 84 7A         [ 4]  810 	call	__tm1637WriteByte
      0083E5 84               [ 1]  811 	pop	a
                                    812 ;	sensors.c: 281: _tm1637ReadResult();
      0083E6 CD 84 5F         [ 4]  813 	call	__tm1637ReadResult
                                    814 ;	sensors.c: 283: for (ii = 0; ii < 4; ++ii) {
      0083E9 5F               [ 1]  815 	clrw	x
      0083EA 1F 07            [ 2]  816 	ldw	(0x07, sp), x
      0083EC                        817 00108$:
                                    818 ;	sensors.c: 284: _tm1637WriteByte(digitArr[3 - ii]);
      0083EC 7B 08            [ 1]  819 	ld	a, (0x08, sp)
      0083EE 6B 0D            [ 1]  820 	ld	(0x0d, sp), a
      0083F0 A6 03            [ 1]  821 	ld	a, #0x03
      0083F2 10 0D            [ 1]  822 	sub	a, (0x0d, sp)
      0083F4 5F               [ 1]  823 	clrw	x
      0083F5 97               [ 1]  824 	ld	xl, a
      0083F6 72 FB 0E         [ 2]  825 	addw	x, (0x0e, sp)
      0083F9 F6               [ 1]  826 	ld	a, (x)
      0083FA 88               [ 1]  827 	push	a
      0083FB CD 84 7A         [ 4]  828 	call	__tm1637WriteByte
      0083FE 84               [ 1]  829 	pop	a
                                    830 ;	sensors.c: 285: _tm1637ReadResult();
      0083FF CD 84 5F         [ 4]  831 	call	__tm1637ReadResult
                                    832 ;	sensors.c: 283: for (ii = 0; ii < 4; ++ii) {
      008402 1E 07            [ 2]  833 	ldw	x, (0x07, sp)
      008404 5C               [ 2]  834 	incw	x
      008405 1F 07            [ 2]  835 	ldw	(0x07, sp), x
      008407 1E 07            [ 2]  836 	ldw	x, (0x07, sp)
      008409 A3 00 04         [ 2]  837 	cpw	x, #0x0004
      00840C 25 DE            [ 1]  838 	jrc	00108$
                                    839 ;	sensors.c: 288: _tm1637Stop();
      00840E CD 84 38         [ 4]  840 	call	__tm1637Stop
      008411 5B 13            [ 2]  841 	addw	sp, #19
      008413 81               [ 4]  842 	ret
                                    843 ;	sensors.c: 293: void tm1637SetBrightness(char brightness)
                                    844 ;	-----------------------------------------
                                    845 ;	 function tm1637SetBrightness
                                    846 ;	-----------------------------------------
      008414                        847 _tm1637SetBrightness:
                                    848 ;	sensors.c: 300: _tm1637Start();
      008414 CD 84 26         [ 4]  849 	call	__tm1637Start
                                    850 ;	sensors.c: 301: _tm1637WriteByte(0x87 + brightness);
      008417 7B 03            [ 1]  851 	ld	a, (0x03, sp)
      008419 AB 87            [ 1]  852 	add	a, #0x87
      00841B 88               [ 1]  853 	push	a
      00841C CD 84 7A         [ 4]  854 	call	__tm1637WriteByte
      00841F 84               [ 1]  855 	pop	a
                                    856 ;	sensors.c: 302: _tm1637ReadResult();
      008420 CD 84 5F         [ 4]  857 	call	__tm1637ReadResult
                                    858 ;	sensors.c: 303: _tm1637Stop();
      008423 CC 84 38         [ 2]  859 	jp	__tm1637Stop
                                    860 ;	sensors.c: 306: void _tm1637Start(void)
                                    861 ;	-----------------------------------------
                                    862 ;	 function _tm1637Start
                                    863 ;	-----------------------------------------
      008426                        864 __tm1637Start:
                                    865 ;	sensors.c: 308: _tm1637ClkHigh();
      008426 CD 84 B8         [ 4]  866 	call	__tm1637ClkHigh
                                    867 ;	sensors.c: 309: _tm1637DioHigh();
      008429 CD 84 C8         [ 4]  868 	call	__tm1637DioHigh
                                    869 ;	sensors.c: 310: delay(5);
      00842C 4B 05            [ 1]  870 	push	#0x05
      00842E 4B 00            [ 1]  871 	push	#0x00
      008430 CD 80 F2         [ 4]  872 	call	_delay
      008433 5B 02            [ 2]  873 	addw	sp, #2
                                    874 ;	sensors.c: 311: _tm1637DioLow();
      008435 CC 84 D0         [ 2]  875 	jp	__tm1637DioLow
                                    876 ;	sensors.c: 314: void _tm1637Stop(void)
                                    877 ;	-----------------------------------------
                                    878 ;	 function _tm1637Stop
                                    879 ;	-----------------------------------------
      008438                        880 __tm1637Stop:
                                    881 ;	sensors.c: 316: _tm1637ClkLow();
      008438 CD 84 C0         [ 4]  882 	call	__tm1637ClkLow
                                    883 ;	sensors.c: 317: delay(5);
      00843B 4B 05            [ 1]  884 	push	#0x05
      00843D 4B 00            [ 1]  885 	push	#0x00
      00843F CD 80 F2         [ 4]  886 	call	_delay
      008442 5B 02            [ 2]  887 	addw	sp, #2
                                    888 ;	sensors.c: 318: _tm1637DioLow();
      008444 CD 84 D0         [ 4]  889 	call	__tm1637DioLow
                                    890 ;	sensors.c: 319: delay(5);
      008447 4B 05            [ 1]  891 	push	#0x05
      008449 4B 00            [ 1]  892 	push	#0x00
      00844B CD 80 F2         [ 4]  893 	call	_delay
      00844E 5B 02            [ 2]  894 	addw	sp, #2
                                    895 ;	sensors.c: 320: _tm1637ClkHigh();
      008450 CD 84 B8         [ 4]  896 	call	__tm1637ClkHigh
                                    897 ;	sensors.c: 321: delay(5);
      008453 4B 05            [ 1]  898 	push	#0x05
      008455 4B 00            [ 1]  899 	push	#0x00
      008457 CD 80 F2         [ 4]  900 	call	_delay
      00845A 5B 02            [ 2]  901 	addw	sp, #2
                                    902 ;	sensors.c: 322: _tm1637DioHigh();
      00845C CC 84 C8         [ 2]  903 	jp	__tm1637DioHigh
                                    904 ;	sensors.c: 325: void _tm1637ReadResult(void)
                                    905 ;	-----------------------------------------
                                    906 ;	 function _tm1637ReadResult
                                    907 ;	-----------------------------------------
      00845F                        908 __tm1637ReadResult:
                                    909 ;	sensors.c: 327: _tm1637ClkLow();
      00845F CD 84 C0         [ 4]  910 	call	__tm1637ClkLow
                                    911 ;	sensors.c: 328: delay(5);
      008462 4B 05            [ 1]  912 	push	#0x05
      008464 4B 00            [ 1]  913 	push	#0x00
      008466 CD 80 F2         [ 4]  914 	call	_delay
      008469 5B 02            [ 2]  915 	addw	sp, #2
                                    916 ;	sensors.c: 330: _tm1637ClkHigh();
      00846B CD 84 B8         [ 4]  917 	call	__tm1637ClkHigh
                                    918 ;	sensors.c: 331: delay(5);
      00846E 4B 05            [ 1]  919 	push	#0x05
      008470 4B 00            [ 1]  920 	push	#0x00
      008472 CD 80 F2         [ 4]  921 	call	_delay
      008475 5B 02            [ 2]  922 	addw	sp, #2
                                    923 ;	sensors.c: 332: _tm1637ClkLow();
      008477 CC 84 C0         [ 2]  924 	jp	__tm1637ClkLow
                                    925 ;	sensors.c: 335: void _tm1637WriteByte(unsigned char b)
                                    926 ;	-----------------------------------------
                                    927 ;	 function _tm1637WriteByte
                                    928 ;	-----------------------------------------
      00847A                        929 __tm1637WriteByte:
      00847A 52 02            [ 2]  930 	sub	sp, #2
                                    931 ;	sensors.c: 337: for (ii = 0; ii < 8; ++ii) {
      00847C 5F               [ 1]  932 	clrw	x
      00847D 1F 01            [ 2]  933 	ldw	(0x01, sp), x
      00847F                        934 00105$:
                                    935 ;	sensors.c: 338: _tm1637ClkLow();
      00847F CD 84 C0         [ 4]  936 	call	__tm1637ClkLow
                                    937 ;	sensors.c: 339: if (b & 0x01) {
      008482 7B 05            [ 1]  938 	ld	a, (0x05, sp)
      008484 44               [ 1]  939 	srl	a
      008485 24 05            [ 1]  940 	jrnc	00102$
                                    941 ;	sensors.c: 340: _tm1637DioHigh();
      008487 CD 84 C8         [ 4]  942 	call	__tm1637DioHigh
      00848A 20 03            [ 2]  943 	jra	00103$
      00848C                        944 00102$:
                                    945 ;	sensors.c: 343: _tm1637DioLow();
      00848C CD 84 D0         [ 4]  946 	call	__tm1637DioLow
      00848F                        947 00103$:
                                    948 ;	sensors.c: 345: delay(15);
      00848F 4B 0F            [ 1]  949 	push	#0x0f
      008491 4B 00            [ 1]  950 	push	#0x00
      008493 CD 80 F2         [ 4]  951 	call	_delay
      008496 5B 02            [ 2]  952 	addw	sp, #2
                                    953 ;	sensors.c: 346: b >>= 1;
      008498 7B 05            [ 1]  954 	ld	a, (0x05, sp)
      00849A 44               [ 1]  955 	srl	a
      00849B 6B 05            [ 1]  956 	ld	(0x05, sp), a
                                    957 ;	sensors.c: 347: _tm1637ClkHigh();
      00849D CD 84 B8         [ 4]  958 	call	__tm1637ClkHigh
                                    959 ;	sensors.c: 348: delay(15);
      0084A0 4B 0F            [ 1]  960 	push	#0x0f
      0084A2 4B 00            [ 1]  961 	push	#0x00
      0084A4 CD 80 F2         [ 4]  962 	call	_delay
      0084A7 5B 02            [ 2]  963 	addw	sp, #2
                                    964 ;	sensors.c: 337: for (ii = 0; ii < 8; ++ii) {
      0084A9 1E 01            [ 2]  965 	ldw	x, (0x01, sp)
      0084AB 5C               [ 2]  966 	incw	x
      0084AC 1F 01            [ 2]  967 	ldw	(0x01, sp), x
      0084AE 1E 01            [ 2]  968 	ldw	x, (0x01, sp)
      0084B0 A3 00 08         [ 2]  969 	cpw	x, #0x0008
      0084B3 2F CA            [ 1]  970 	jrslt	00105$
      0084B5 5B 02            [ 2]  971 	addw	sp, #2
      0084B7 81               [ 4]  972 	ret
                                    973 ;	sensors.c: 354: void _tm1637ClkHigh(void)
                                    974 ;	-----------------------------------------
                                    975 ;	 function _tm1637ClkHigh
                                    976 ;	-----------------------------------------
      0084B8                        977 __tm1637ClkHigh:
                                    978 ;	sensors.c: 359: PD_ODR |= 1 << 2;
      0084B8 AE 50 0F         [ 2]  979 	ldw	x, #0x500f
      0084BB F6               [ 1]  980 	ld	a, (x)
      0084BC AA 04            [ 1]  981 	or	a, #0x04
      0084BE F7               [ 1]  982 	ld	(x), a
      0084BF 81               [ 4]  983 	ret
                                    984 ;	sensors.c: 362: void _tm1637ClkLow(void)
                                    985 ;	-----------------------------------------
                                    986 ;	 function _tm1637ClkLow
                                    987 ;	-----------------------------------------
      0084C0                        988 __tm1637ClkLow:
                                    989 ;	sensors.c: 366: PD_ODR &= ~(1 << 2);
      0084C0 AE 50 0F         [ 2]  990 	ldw	x, #0x500f
      0084C3 F6               [ 1]  991 	ld	a, (x)
      0084C4 A4 FB            [ 1]  992 	and	a, #0xfb
      0084C6 F7               [ 1]  993 	ld	(x), a
      0084C7 81               [ 4]  994 	ret
                                    995 ;	sensors.c: 372: void _tm1637DioHigh(void)
                                    996 ;	-----------------------------------------
                                    997 ;	 function _tm1637DioHigh
                                    998 ;	-----------------------------------------
      0084C8                        999 __tm1637DioHigh:
                                   1000 ;	sensors.c: 376: PD_ODR |= 1 << 3;
      0084C8 AE 50 0F         [ 2] 1001 	ldw	x, #0x500f
      0084CB F6               [ 1] 1002 	ld	a, (x)
      0084CC AA 08            [ 1] 1003 	or	a, #0x08
      0084CE F7               [ 1] 1004 	ld	(x), a
      0084CF 81               [ 4] 1005 	ret
                                   1006 ;	sensors.c: 380: void _tm1637DioLow(void)
                                   1007 ;	-----------------------------------------
                                   1008 ;	 function _tm1637DioLow
                                   1009 ;	-----------------------------------------
      0084D0                       1010 __tm1637DioLow:
                                   1011 ;	sensors.c: 382: PD_ODR &= ~(1 << 3);
      0084D0 AE 50 0F         [ 2] 1012 	ldw	x, #0x500f
      0084D3 F6               [ 1] 1013 	ld	a, (x)
      0084D4 A4 F7            [ 1] 1014 	and	a, #0xf7
      0084D6 F7               [ 1] 1015 	ld	(x), a
      0084D7 81               [ 4] 1016 	ret
                                   1017 ;	sensors.c: 396: int main () {
                                   1018 ;	-----------------------------------------
                                   1019 ;	 function main
                                   1020 ;	-----------------------------------------
      0084D8                       1021 _main:
      0084D8 52 06            [ 2] 1022 	sub	sp, #6
                                   1023 ;	sensors.c: 397: unsigned int val=0;
      0084DA 5F               [ 1] 1024 	clrw	x
      0084DB 1F 05            [ 2] 1025 	ldw	(0x05, sp), x
                                   1026 ;	sensors.c: 399: InitializeSystemClock();
      0084DD CD 80 A8         [ 4] 1027 	call	_InitializeSystemClock
                                   1028 ;	sensors.c: 402: PD_DDR = (1 << 3) | (1 << 2); // output mode
      0084E0 AE 50 11         [ 2] 1029 	ldw	x, #0x5011
      0084E3 A6 0C            [ 1] 1030 	ld	a, #0x0c
      0084E5 F7               [ 1] 1031 	ld	(x), a
                                   1032 ;	sensors.c: 403: PD_CR1 = (1 << 3) | (1 << 2); // push-pull
      0084E6 AE 50 12         [ 2] 1033 	ldw	x, #0x5012
      0084E9 A6 0C            [ 1] 1034 	ld	a, #0x0c
      0084EB F7               [ 1] 1035 	ld	(x), a
                                   1036 ;	sensors.c: 404: PD_CR2 = (1 << 3) | (1 << 2); // up to 10MHz speed
      0084EC AE 50 13         [ 2] 1037 	ldw	x, #0x5013
      0084EF A6 0C            [ 1] 1038 	ld	a, #0x0c
      0084F1 F7               [ 1] 1039 	ld	(x), a
                                   1040 ;	sensors.c: 407: PA_DDR &= ~(1<<3); //port PA3 input
      0084F2 AE 50 02         [ 2] 1041 	ldw	x, #0x5002
      0084F5 F6               [ 1] 1042 	ld	a, (x)
      0084F6 A4 F7            [ 1] 1043 	and	a, #0xf7
      0084F8 F7               [ 1] 1044 	ld	(x), a
                                   1045 ;	sensors.c: 408: PA_CR1 |= 1<<3; //pull up enabled
      0084F9 AE 50 03         [ 2] 1046 	ldw	x, #0x5003
      0084FC F6               [ 1] 1047 	ld	a, (x)
      0084FD AA 08            [ 1] 1048 	or	a, #0x08
      0084FF F7               [ 1] 1049 	ld	(x), a
                                   1050 ;	sensors.c: 411: ADC_CSR |= ((0x0F)&2); // select channel = 2 = PC4
      008500 AE 54 00         [ 2] 1051 	ldw	x, #0x5400
      008503 F6               [ 1] 1052 	ld	a, (x)
      008504 AA 02            [ 1] 1053 	or	a, #0x02
      008506 F7               [ 1] 1054 	ld	(x), a
                                   1055 ;	sensors.c: 412: ADC_CR2 |= (1<<3); // Right Aligned Data
      008507 AE 54 02         [ 2] 1056 	ldw	x, #0x5402
      00850A F6               [ 1] 1057 	ld	a, (x)
      00850B AA 08            [ 1] 1058 	or	a, #0x08
      00850D F7               [ 1] 1059 	ld	(x), a
                                   1060 ;	sensors.c: 413: ADC_CR1 |= (1<<0); // ADC ON
      00850E AE 54 01         [ 2] 1061 	ldw	x, #0x5401
      008511 F6               [ 1] 1062 	ld	a, (x)
      008512 AA 01            [ 1] 1063 	or	a, #0x01
      008514 F7               [ 1] 1064 	ld	(x), a
                                   1065 ;	sensors.c: 414: tm1637Init();
      008515 CD 83 6F         [ 4] 1066 	call	_tm1637Init
                                   1067 ;	sensors.c: 416: InitializeUART();
      008518 CD 82 F6         [ 4] 1068 	call	_InitializeUART
                                   1069 ;	sensors.c: 417: while (1) {
      00851B                       1070 00105$:
                                   1071 ;	sensors.c: 419: ADC_CR1 |= (1<<0); // ADC Start Conversion
      00851B 72 10 54 01      [ 1] 1072 	bset	0x5401, #0
                                   1073 ;	sensors.c: 420: while(((ADC_CSR)&(1<<7))== 0); // Wait till EOC
      00851F                       1074 00101$:
      00851F AE 54 00         [ 2] 1075 	ldw	x, #0x5400
      008522 F6               [ 1] 1076 	ld	a, (x)
      008523 48               [ 1] 1077 	sll	a
      008524 24 F9            [ 1] 1078 	jrnc	00101$
                                   1079 ;	sensors.c: 421: val |= (unsigned int)ADC_DRL;
      008526 AE 54 05         [ 2] 1080 	ldw	x, #0x5405
      008529 F6               [ 1] 1081 	ld	a, (x)
      00852A 5F               [ 1] 1082 	clrw	x
      00852B 97               [ 1] 1083 	ld	xl, a
      00852C 1A 06            [ 1] 1084 	or	a, (0x06, sp)
      00852E 6B 04            [ 1] 1085 	ld	(0x04, sp), a
      008530 9E               [ 1] 1086 	ld	a, xh
      008531 1A 05            [ 1] 1087 	or	a, (0x05, sp)
      008533 6B 01            [ 1] 1088 	ld	(0x01, sp), a
      008535 7B 04            [ 1] 1089 	ld	a, (0x04, sp)
      008537 6B 02            [ 1] 1090 	ld	(0x02, sp), a
                                   1091 ;	sensors.c: 422: UARTPrintF("value = \n\r");
      008539 AE 85 95         [ 2] 1092 	ldw	x, #___str_0+0
      00853C 89               [ 2] 1093 	pushw	x
      00853D CD 81 80         [ 4] 1094 	call	_UARTPrintF
      008540 5B 02            [ 2] 1095 	addw	sp, #2
                                   1096 ;	sensors.c: 423: print_UCHAR_hex(val);
      008542 7B 02            [ 1] 1097 	ld	a, (0x02, sp)
      008544 88               [ 1] 1098 	push	a
      008545 CD 81 97         [ 4] 1099 	call	_print_UCHAR_hex
      008548 84               [ 1] 1100 	pop	a
                                   1101 ;	sensors.c: 424: val |= (unsigned int)ADC_DRH<<8;
      008549 AE 54 04         [ 2] 1102 	ldw	x, #0x5404
      00854C F6               [ 1] 1103 	ld	a, (x)
      00854D 5F               [ 1] 1104 	clrw	x
      00854E 97               [ 1] 1105 	ld	xl, a
      00854F 58               [ 2] 1106 	sllw	x
      008550 58               [ 2] 1107 	sllw	x
      008551 58               [ 2] 1108 	sllw	x
      008552 58               [ 2] 1109 	sllw	x
      008553 58               [ 2] 1110 	sllw	x
      008554 58               [ 2] 1111 	sllw	x
      008555 58               [ 2] 1112 	sllw	x
      008556 58               [ 2] 1113 	sllw	x
      008557 9F               [ 1] 1114 	ld	a, xl
      008558 1A 02            [ 1] 1115 	or	a, (0x02, sp)
      00855A 90 97            [ 1] 1116 	ld	yl, a
      00855C 9E               [ 1] 1117 	ld	a, xh
      00855D 1A 01            [ 1] 1118 	or	a, (0x01, sp)
      00855F 90 95            [ 1] 1119 	ld	yh, a
                                   1120 ;	sensors.c: 425: ADC_CR1 &= ~(1<<0); // ADC Stop Conversion
      008561 AE 54 01         [ 2] 1121 	ldw	x, #0x5401
      008564 F6               [ 1] 1122 	ld	a, (x)
      008565 A4 FE            [ 1] 1123 	and	a, #0xfe
      008567 F7               [ 1] 1124 	ld	(x), a
                                   1125 ;	sensors.c: 426: val &= 0x03ff;
      008568 90 9E            [ 1] 1126 	ld	a, yh
      00856A A4 03            [ 1] 1127 	and	a, #0x03
      00856C 90 95            [ 1] 1128 	ld	yh, a
      00856E 17 05            [ 2] 1129 	ldw	(0x05, sp), y
                                   1130 ;	sensors.c: 427: tm1637DisplayDecimal(val, 1); // eg 37:12
      008570 16 05            [ 2] 1131 	ldw	y, (0x05, sp)
      008572 5F               [ 1] 1132 	clrw	x
      008573 4B 01            [ 1] 1133 	push	#0x01
      008575 4B 00            [ 1] 1134 	push	#0x00
      008577 90 89            [ 2] 1135 	pushw	y
      008579 89               [ 2] 1136 	pushw	x
      00857A CD 83 76         [ 4] 1137 	call	_tm1637DisplayDecimal
      00857D 5B 06            [ 2] 1138 	addw	sp, #6
      00857F 20 9A            [ 2] 1139 	jra	00105$
      008581 5B 06            [ 2] 1140 	addw	sp, #6
      008583 81               [ 4] 1141 	ret
                                   1142 	.area CODE
      008584                       1143 _segmentMap:
      008584 3F                    1144 	.db #0x3F	;  63
      008585 06                    1145 	.db #0x06	;  6
      008586 5B                    1146 	.db #0x5B	;  91
      008587 4F                    1147 	.db #0x4F	;  79	'O'
      008588 66                    1148 	.db #0x66	;  102	'f'
      008589 6D                    1149 	.db #0x6D	;  109	'm'
      00858A 7D                    1150 	.db #0x7D	;  125
      00858B 07                    1151 	.db #0x07	;  7
      00858C 7F                    1152 	.db #0x7F	;  127
      00858D 6F                    1153 	.db #0x6F	;  111	'o'
      00858E 77                    1154 	.db #0x77	;  119	'w'
      00858F 7C                    1155 	.db #0x7C	;  124
      008590 39                    1156 	.db #0x39	;  57	'9'
      008591 5E                    1157 	.db #0x5E	;  94
      008592 79                    1158 	.db #0x79	;  121	'y'
      008593 71                    1159 	.db #0x71	;  113	'q'
      008594 00                    1160 	.db #0x00	;  0
      008595                       1161 ___str_0:
      008595 76 61 6C 75 65 20 3D  1162 	.ascii "value = "
             20
      00859D 0A                    1163 	.db 0x0A
      00859E 0D                    1164 	.db 0x0D
      00859F 00                    1165 	.db 0x00
                                   1166 	.area INITIALIZER
                                   1167 	.area CABS (ABS)
