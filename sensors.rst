                                      1 ;--------------------------------------------------------
                                      2 ; File Created by SDCC : free open source ANSI-C Compiler
                                      3 ; Version 3.4.0 #8981 (Jul  5 2014) (Linux)
                                      4 ; This file was generated Sun Apr  9 21:45:50 2017
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
                                     22 	.globl _UARTPrintF
                                     23 	.globl _i2c_send_reg
                                     24 	.globl _i2c_set_stop
                                     25 	.globl _i2c_set_nak
                                     26 	.globl _i2c_read
                                     27 	.globl _delay
                                     28 	.globl _InitializeSystemClock
                                     29 	.globl _delayTenMicro
                                     30 	.globl _tm1637SetBrightness
                                     31 	.globl __tm1637Start
                                     32 	.globl __tm1637Stop
                                     33 	.globl __tm1637ReadResult
                                     34 	.globl __tm1637WriteByte
                                     35 	.globl __tm1637ClkHigh
                                     36 	.globl __tm1637ClkLow
                                     37 	.globl __tm1637DioHigh
                                     38 	.globl __tm1637DioLow
                                     39 ;--------------------------------------------------------
                                     40 ; ram data
                                     41 ;--------------------------------------------------------
                                     42 	.area DATA
                                     43 ;--------------------------------------------------------
                                     44 ; ram data
                                     45 ;--------------------------------------------------------
                                     46 	.area INITIALIZED
                                     47 ;--------------------------------------------------------
                                     48 ; Stack segment in internal ram 
                                     49 ;--------------------------------------------------------
                                     50 	.area	SSEG
      000000                         51 __start__stack:
      000000                         52 	.ds	1
                                     53 
                                     54 ;--------------------------------------------------------
                                     55 ; absolute external ram data
                                     56 ;--------------------------------------------------------
                                     57 	.area DABS (ABS)
                                     58 ;--------------------------------------------------------
                                     59 ; interrupt vector 
                                     60 ;--------------------------------------------------------
                                     61 	.area HOME
      008000                         62 __interrupt_vect:
      008000 82 00 80 83             63 	int s_GSINIT ;reset
      008004 82 00 00 00             64 	int 0x0000 ;trap
      008008 82 00 00 00             65 	int 0x0000 ;int0
      00800C 82 00 00 00             66 	int 0x0000 ;int1
      008010 82 00 00 00             67 	int 0x0000 ;int2
      008014 82 00 00 00             68 	int 0x0000 ;int3
      008018 82 00 00 00             69 	int 0x0000 ;int4
      00801C 82 00 00 00             70 	int 0x0000 ;int5
      008020 82 00 00 00             71 	int 0x0000 ;int6
      008024 82 00 00 00             72 	int 0x0000 ;int7
      008028 82 00 00 00             73 	int 0x0000 ;int8
      00802C 82 00 00 00             74 	int 0x0000 ;int9
      008030 82 00 00 00             75 	int 0x0000 ;int10
      008034 82 00 00 00             76 	int 0x0000 ;int11
      008038 82 00 00 00             77 	int 0x0000 ;int12
      00803C 82 00 00 00             78 	int 0x0000 ;int13
      008040 82 00 00 00             79 	int 0x0000 ;int14
      008044 82 00 00 00             80 	int 0x0000 ;int15
      008048 82 00 00 00             81 	int 0x0000 ;int16
      00804C 82 00 00 00             82 	int 0x0000 ;int17
      008050 82 00 00 00             83 	int 0x0000 ;int18
      008054 82 00 00 00             84 	int 0x0000 ;int19
      008058 82 00 00 00             85 	int 0x0000 ;int20
      00805C 82 00 00 00             86 	int 0x0000 ;int21
      008060 82 00 00 00             87 	int 0x0000 ;int22
      008064 82 00 00 00             88 	int 0x0000 ;int23
      008068 82 00 00 00             89 	int 0x0000 ;int24
      00806C 82 00 00 00             90 	int 0x0000 ;int25
      008070 82 00 00 00             91 	int 0x0000 ;int26
      008074 82 00 00 00             92 	int 0x0000 ;int27
      008078 82 00 00 00             93 	int 0x0000 ;int28
      00807C 82 00 00 00             94 	int 0x0000 ;int29
                                     95 ;--------------------------------------------------------
                                     96 ; global & static initialisations
                                     97 ;--------------------------------------------------------
                                     98 	.area HOME
                                     99 	.area GSINIT
                                    100 	.area GSFINAL
                                    101 	.area GSINIT
      008083                        102 __sdcc_gs_init_startup:
      008083                        103 __sdcc_init_data:
                                    104 ; stm8_genXINIT() start
      008083 AE 00 00         [ 2]  105 	ldw x, #l_DATA
      008086 27 07            [ 1]  106 	jreq	00002$
      008088                        107 00001$:
      008088 72 4F 00 00      [ 1]  108 	clr (s_DATA - 1, x)
      00808C 5A               [ 2]  109 	decw x
      00808D 26 F9            [ 1]  110 	jrne	00001$
      00808F                        111 00002$:
      00808F AE 00 00         [ 2]  112 	ldw	x, #l_INITIALIZER
      008092 27 09            [ 1]  113 	jreq	00004$
      008094                        114 00003$:
      008094 D6 85 8C         [ 1]  115 	ld	a, (s_INITIALIZER - 1, x)
      008097 D7 00 00         [ 1]  116 	ld	(s_INITIALIZED - 1, x), a
      00809A 5A               [ 2]  117 	decw	x
      00809B 26 F7            [ 1]  118 	jrne	00003$
      00809D                        119 00004$:
                                    120 ; stm8_genXINIT() end
                                    121 	.area GSFINAL
      00809D CC 80 80         [ 2]  122 	jp	__sdcc_program_startup
                                    123 ;--------------------------------------------------------
                                    124 ; Home
                                    125 ;--------------------------------------------------------
                                    126 	.area HOME
                                    127 	.area HOME
      008080                        128 __sdcc_program_startup:
      008080 CC 84 8A         [ 2]  129 	jp	_main
                                    130 ;	return from main will return to caller
                                    131 ;--------------------------------------------------------
                                    132 ; code
                                    133 ;--------------------------------------------------------
                                    134 	.area CODE
                                    135 ;	sensors.c: 15: void delayTenMicro (void) {
                                    136 ;	-----------------------------------------
                                    137 ;	 function delayTenMicro
                                    138 ;	-----------------------------------------
      0080A0                        139 _delayTenMicro:
                                    140 ;	sensors.c: 17: for (a = 0; a < 50; ++a)
      0080A0 A6 32            [ 1]  141 	ld	a, #0x32
      0080A2                        142 00104$:
                                    143 ;	sensors.c: 18: __asm__("nop");
      0080A2 9D               [ 1]  144 	nop
      0080A3 4A               [ 1]  145 	dec	a
                                    146 ;	sensors.c: 17: for (a = 0; a < 50; ++a)
      0080A4 4D               [ 1]  147 	tnz	a
      0080A5 26 FB            [ 1]  148 	jrne	00104$
      0080A7 81               [ 4]  149 	ret
                                    150 ;	sensors.c: 21: void InitializeSystemClock() {
                                    151 ;	-----------------------------------------
                                    152 ;	 function InitializeSystemClock
                                    153 ;	-----------------------------------------
      0080A8                        154 _InitializeSystemClock:
                                    155 ;	sensors.c: 22: CLK_ICKR = 0;                       //  Reset the Internal Clock Register.
      0080A8 AE 50 C0         [ 2]  156 	ldw	x, #0x50c0
      0080AB 7F               [ 1]  157 	clr	(x)
                                    158 ;	sensors.c: 23: CLK_ICKR = CLK_HSIEN;               //  Enable the HSI.
      0080AC AE 50 C0         [ 2]  159 	ldw	x, #0x50c0
      0080AF A6 01            [ 1]  160 	ld	a, #0x01
      0080B1 F7               [ 1]  161 	ld	(x), a
                                    162 ;	sensors.c: 24: CLK_ECKR = 0;                       //  Disable the external clock.
      0080B2 AE 50 C1         [ 2]  163 	ldw	x, #0x50c1
      0080B5 7F               [ 1]  164 	clr	(x)
                                    165 ;	sensors.c: 25: while ((CLK_ICKR & CLK_HSIRDY) == 0);       //  Wait for the HSI to be ready for use.
      0080B6                        166 00101$:
      0080B6 AE 50 C0         [ 2]  167 	ldw	x, #0x50c0
      0080B9 F6               [ 1]  168 	ld	a, (x)
      0080BA A5 02            [ 1]  169 	bcp	a, #0x02
      0080BC 27 F8            [ 1]  170 	jreq	00101$
                                    171 ;	sensors.c: 26: CLK_CKDIVR = 0;                     //  Ensure the clocks are running at full speed.
      0080BE AE 50 C6         [ 2]  172 	ldw	x, #0x50c6
      0080C1 7F               [ 1]  173 	clr	(x)
                                    174 ;	sensors.c: 27: CLK_PCKENR1 = 0xff;                 //  Enable all peripheral clocks.
      0080C2 AE 50 C7         [ 2]  175 	ldw	x, #0x50c7
      0080C5 A6 FF            [ 1]  176 	ld	a, #0xff
      0080C7 F7               [ 1]  177 	ld	(x), a
                                    178 ;	sensors.c: 28: CLK_PCKENR2 = 0xff;                 //  Ditto.
      0080C8 AE 50 CA         [ 2]  179 	ldw	x, #0x50ca
      0080CB A6 FF            [ 1]  180 	ld	a, #0xff
      0080CD F7               [ 1]  181 	ld	(x), a
                                    182 ;	sensors.c: 29: CLK_CCOR = 0;                       //  Turn off CCO.
      0080CE AE 50 C9         [ 2]  183 	ldw	x, #0x50c9
      0080D1 7F               [ 1]  184 	clr	(x)
                                    185 ;	sensors.c: 30: CLK_HSITRIMR = 0;                   //  Turn off any HSIU trimming.
      0080D2 AE 50 CC         [ 2]  186 	ldw	x, #0x50cc
      0080D5 7F               [ 1]  187 	clr	(x)
                                    188 ;	sensors.c: 31: CLK_SWIMCCR = 0;                    //  Set SWIM to run at clock / 2.
      0080D6 AE 50 CD         [ 2]  189 	ldw	x, #0x50cd
      0080D9 7F               [ 1]  190 	clr	(x)
                                    191 ;	sensors.c: 32: CLK_SWR = 0xe1;                     //  Use HSI as the clock source.
      0080DA AE 50 C4         [ 2]  192 	ldw	x, #0x50c4
      0080DD A6 E1            [ 1]  193 	ld	a, #0xe1
      0080DF F7               [ 1]  194 	ld	(x), a
                                    195 ;	sensors.c: 33: CLK_SWCR = 0;                       //  Reset the clock switch control register.
      0080E0 AE 50 C5         [ 2]  196 	ldw	x, #0x50c5
      0080E3 7F               [ 1]  197 	clr	(x)
                                    198 ;	sensors.c: 34: CLK_SWCR = CLK_SWEN;                //  Enable switching.
      0080E4 AE 50 C5         [ 2]  199 	ldw	x, #0x50c5
      0080E7 A6 02            [ 1]  200 	ld	a, #0x02
      0080E9 F7               [ 1]  201 	ld	(x), a
                                    202 ;	sensors.c: 35: while ((CLK_SWCR & CLK_SWBSY) != 0);        //  Pause while the clock switch is busy.
      0080EA                        203 00104$:
      0080EA AE 50 C5         [ 2]  204 	ldw	x, #0x50c5
      0080ED F6               [ 1]  205 	ld	a, (x)
      0080EE 44               [ 1]  206 	srl	a
      0080EF 25 F9            [ 1]  207 	jrc	00104$
      0080F1 81               [ 4]  208 	ret
                                    209 ;	sensors.c: 37: void delay (int time_ms) {
                                    210 ;	-----------------------------------------
                                    211 ;	 function delay
                                    212 ;	-----------------------------------------
      0080F2                        213 _delay:
      0080F2 52 0A            [ 2]  214 	sub	sp, #10
                                    215 ;	sensors.c: 39: for (x = 0; x < 1036*time_ms; ++x)
      0080F4 5F               [ 1]  216 	clrw	x
      0080F5 1F 03            [ 2]  217 	ldw	(0x03, sp), x
      0080F7 1F 01            [ 2]  218 	ldw	(0x01, sp), x
      0080F9 1E 0D            [ 2]  219 	ldw	x, (0x0d, sp)
      0080FB 89               [ 2]  220 	pushw	x
      0080FC 4B 0C            [ 1]  221 	push	#0x0c
      0080FE 4B 04            [ 1]  222 	push	#0x04
      008100 CD 85 37         [ 4]  223 	call	__mulint
      008103 5B 04            [ 2]  224 	addw	sp, #4
      008105 1F 09            [ 2]  225 	ldw	(0x09, sp), x
      008107                        226 00103$:
      008107 16 09            [ 2]  227 	ldw	y, (0x09, sp)
      008109 17 07            [ 2]  228 	ldw	(0x07, sp), y
      00810B 7B 07            [ 1]  229 	ld	a, (0x07, sp)
      00810D 49               [ 1]  230 	rlc	a
      00810E 4F               [ 1]  231 	clr	a
      00810F A2 00            [ 1]  232 	sbc	a, #0x00
      008111 6B 06            [ 1]  233 	ld	(0x06, sp), a
      008113 6B 05            [ 1]  234 	ld	(0x05, sp), a
      008115 1E 03            [ 2]  235 	ldw	x, (0x03, sp)
      008117 13 07            [ 2]  236 	cpw	x, (0x07, sp)
      008119 7B 02            [ 1]  237 	ld	a, (0x02, sp)
      00811B 12 06            [ 1]  238 	sbc	a, (0x06, sp)
      00811D 7B 01            [ 1]  239 	ld	a, (0x01, sp)
      00811F 12 05            [ 1]  240 	sbc	a, (0x05, sp)
      008121 2E 17            [ 1]  241 	jrsge	00105$
                                    242 ;	sensors.c: 40: __asm__("nop");
      008123 9D               [ 1]  243 	nop
                                    244 ;	sensors.c: 39: for (x = 0; x < 1036*time_ms; ++x)
      008124 16 03            [ 2]  245 	ldw	y, (0x03, sp)
      008126 72 A9 00 01      [ 2]  246 	addw	y, #0x0001
      00812A 7B 02            [ 1]  247 	ld	a, (0x02, sp)
      00812C A9 00            [ 1]  248 	adc	a, #0x00
      00812E 97               [ 1]  249 	ld	xl, a
      00812F 7B 01            [ 1]  250 	ld	a, (0x01, sp)
      008131 A9 00            [ 1]  251 	adc	a, #0x00
      008133 95               [ 1]  252 	ld	xh, a
      008134 17 03            [ 2]  253 	ldw	(0x03, sp), y
      008136 1F 01            [ 2]  254 	ldw	(0x01, sp), x
      008138 20 CD            [ 2]  255 	jra	00103$
      00813A                        256 00105$:
      00813A 5B 0A            [ 2]  257 	addw	sp, #10
      00813C 81               [ 4]  258 	ret
                                    259 ;	sensors.c: 42: void i2c_read (unsigned char *x) {
                                    260 ;	-----------------------------------------
                                    261 ;	 function i2c_read
                                    262 ;	-----------------------------------------
      00813D                        263 _i2c_read:
                                    264 ;	sensors.c: 43: while ((I2C_SR1 & I2C_RXNE) == 0);
      00813D                        265 00101$:
      00813D AE 52 17         [ 2]  266 	ldw	x, #0x5217
      008140 F6               [ 1]  267 	ld	a, (x)
      008141 A5 40            [ 1]  268 	bcp	a, #0x40
      008143 27 F8            [ 1]  269 	jreq	00101$
                                    270 ;	sensors.c: 44: *x = I2C_DR;
      008145 16 03            [ 2]  271 	ldw	y, (0x03, sp)
      008147 AE 52 16         [ 2]  272 	ldw	x, #0x5216
      00814A F6               [ 1]  273 	ld	a, (x)
      00814B 90 F7            [ 1]  274 	ld	(y), a
      00814D 81               [ 4]  275 	ret
                                    276 ;	sensors.c: 46: void i2c_set_nak (void) {
                                    277 ;	-----------------------------------------
                                    278 ;	 function i2c_set_nak
                                    279 ;	-----------------------------------------
      00814E                        280 _i2c_set_nak:
                                    281 ;	sensors.c: 47: I2C_CR2 &= ~I2C_ACK;
      00814E AE 52 11         [ 2]  282 	ldw	x, #0x5211
      008151 F6               [ 1]  283 	ld	a, (x)
      008152 A4 FB            [ 1]  284 	and	a, #0xfb
      008154 F7               [ 1]  285 	ld	(x), a
      008155 81               [ 4]  286 	ret
                                    287 ;	sensors.c: 49: void i2c_set_stop (void) {
                                    288 ;	-----------------------------------------
                                    289 ;	 function i2c_set_stop
                                    290 ;	-----------------------------------------
      008156                        291 _i2c_set_stop:
                                    292 ;	sensors.c: 50: I2C_CR2 |= I2C_STOP;
      008156 AE 52 11         [ 2]  293 	ldw	x, #0x5211
      008159 F6               [ 1]  294 	ld	a, (x)
      00815A AA 02            [ 1]  295 	or	a, #0x02
      00815C F7               [ 1]  296 	ld	(x), a
      00815D 81               [ 4]  297 	ret
                                    298 ;	sensors.c: 52: void i2c_send_reg (UCHAR addr) {
                                    299 ;	-----------------------------------------
                                    300 ;	 function i2c_send_reg
                                    301 ;	-----------------------------------------
      00815E                        302 _i2c_send_reg:
      00815E 52 02            [ 2]  303 	sub	sp, #2
                                    304 ;	sensors.c: 54: reg = I2C_SR1;
      008160 AE 52 17         [ 2]  305 	ldw	x, #0x5217
      008163 F6               [ 1]  306 	ld	a, (x)
      008164 5F               [ 1]  307 	clrw	x
      008165 97               [ 1]  308 	ld	xl, a
      008166 1F 01            [ 2]  309 	ldw	(0x01, sp), x
                                    310 ;	sensors.c: 55: reg = I2C_SR3;
      008168 AE 52 19         [ 2]  311 	ldw	x, #0x5219
      00816B F6               [ 1]  312 	ld	a, (x)
      00816C 5F               [ 1]  313 	clrw	x
      00816D 97               [ 1]  314 	ld	xl, a
      00816E 1F 01            [ 2]  315 	ldw	(0x01, sp), x
                                    316 ;	sensors.c: 56: I2C_DR = addr;
      008170 AE 52 16         [ 2]  317 	ldw	x, #0x5216
      008173 7B 05            [ 1]  318 	ld	a, (0x05, sp)
      008175 F7               [ 1]  319 	ld	(x), a
                                    320 ;	sensors.c: 57: while ((I2C_SR1 & I2C_TXE) == 0);
      008176                        321 00101$:
      008176 AE 52 17         [ 2]  322 	ldw	x, #0x5217
      008179 F6               [ 1]  323 	ld	a, (x)
      00817A 48               [ 1]  324 	sll	a
      00817B 24 F9            [ 1]  325 	jrnc	00101$
      00817D 5B 02            [ 2]  326 	addw	sp, #2
      00817F 81               [ 4]  327 	ret
                                    328 ;	sensors.c: 61: void UARTPrintF (char *message) {
                                    329 ;	-----------------------------------------
                                    330 ;	 function UARTPrintF
                                    331 ;	-----------------------------------------
      008180                        332 _UARTPrintF:
                                    333 ;	sensors.c: 62: char *ch = message;
      008180 16 03            [ 2]  334 	ldw	y, (0x03, sp)
                                    335 ;	sensors.c: 63: while (*ch) {
      008182                        336 00104$:
      008182 90 F6            [ 1]  337 	ld	a, (y)
      008184 4D               [ 1]  338 	tnz	a
      008185 27 0F            [ 1]  339 	jreq	00107$
                                    340 ;	sensors.c: 64: UART1_DR = (unsigned char) *ch;     //  Put the next character into the data transmission register.
      008187 AE 52 31         [ 2]  341 	ldw	x, #0x5231
      00818A F7               [ 1]  342 	ld	(x), a
                                    343 ;	sensors.c: 65: while ((UART1_SR & SR_TXE) == 0);   //  Wait for transmission to complete.
      00818B                        344 00101$:
      00818B AE 52 30         [ 2]  345 	ldw	x, #0x5230
      00818E F6               [ 1]  346 	ld	a, (x)
      00818F 48               [ 1]  347 	sll	a
      008190 24 F9            [ 1]  348 	jrnc	00101$
                                    349 ;	sensors.c: 66: ch++;                               //  Grab the next character.
      008192 90 5C            [ 2]  350 	incw	y
      008194 20 EC            [ 2]  351 	jra	00104$
      008196                        352 00107$:
      008196 81               [ 4]  353 	ret
                                    354 ;	sensors.c: 72: void i2c_send_address (UCHAR addr, UCHAR mode) {
                                    355 ;	-----------------------------------------
                                    356 ;	 function i2c_send_address
                                    357 ;	-----------------------------------------
      008197                        358 _i2c_send_address:
      008197 52 03            [ 2]  359 	sub	sp, #3
                                    360 ;	sensors.c: 74: reg = I2C_SR1;
      008199 AE 52 17         [ 2]  361 	ldw	x, #0x5217
      00819C F6               [ 1]  362 	ld	a, (x)
      00819D 5F               [ 1]  363 	clrw	x
      00819E 97               [ 1]  364 	ld	xl, a
      00819F 1F 01            [ 2]  365 	ldw	(0x01, sp), x
                                    366 ;	sensors.c: 75: I2C_DR = (addr << 1) | mode;
      0081A1 7B 06            [ 1]  367 	ld	a, (0x06, sp)
      0081A3 48               [ 1]  368 	sll	a
      0081A4 1A 07            [ 1]  369 	or	a, (0x07, sp)
      0081A6 AE 52 16         [ 2]  370 	ldw	x, #0x5216
      0081A9 F7               [ 1]  371 	ld	(x), a
                                    372 ;	sensors.c: 76: if (mode == I2C_READ) {
      0081AA 7B 07            [ 1]  373 	ld	a, (0x07, sp)
      0081AC A1 01            [ 1]  374 	cp	a, #0x01
      0081AE 26 06            [ 1]  375 	jrne	00127$
      0081B0 A6 01            [ 1]  376 	ld	a, #0x01
      0081B2 6B 03            [ 1]  377 	ld	(0x03, sp), a
      0081B4 20 02            [ 2]  378 	jra	00128$
      0081B6                        379 00127$:
      0081B6 0F 03            [ 1]  380 	clr	(0x03, sp)
      0081B8                        381 00128$:
      0081B8 0D 03            [ 1]  382 	tnz	(0x03, sp)
      0081BA 27 08            [ 1]  383 	jreq	00103$
                                    384 ;	sensors.c: 77: I2C_OARL = 0;
      0081BC AE 52 13         [ 2]  385 	ldw	x, #0x5213
      0081BF 7F               [ 1]  386 	clr	(x)
                                    387 ;	sensors.c: 78: I2C_OARH = 0;
      0081C0 AE 52 14         [ 2]  388 	ldw	x, #0x5214
      0081C3 7F               [ 1]  389 	clr	(x)
                                    390 ;	sensors.c: 81: while ((I2C_SR1 & I2C_ADDR) == 0);
      0081C4                        391 00103$:
                                    392 ;	sensors.c: 74: reg = I2C_SR1;
      0081C4 AE 52 17         [ 2]  393 	ldw	x, #0x5217
      0081C7 F6               [ 1]  394 	ld	a, (x)
                                    395 ;	sensors.c: 81: while ((I2C_SR1 & I2C_ADDR) == 0);
      0081C8 A5 02            [ 1]  396 	bcp	a, #0x02
      0081CA 27 F8            [ 1]  397 	jreq	00103$
                                    398 ;	sensors.c: 82: if (mode == I2C_READ)
      0081CC 0D 03            [ 1]  399 	tnz	(0x03, sp)
      0081CE 27 06            [ 1]  400 	jreq	00108$
                                    401 ;	sensors.c: 83: UNSET (I2C_SR1, I2C_ADDR);
      0081D0 A4 FD            [ 1]  402 	and	a, #0xfd
      0081D2 AE 52 17         [ 2]  403 	ldw	x, #0x5217
      0081D5 F7               [ 1]  404 	ld	(x), a
      0081D6                        405 00108$:
      0081D6 5B 03            [ 2]  406 	addw	sp, #3
      0081D8 81               [ 4]  407 	ret
                                    408 ;	sensors.c: 86: void i2c_set_start_ack (void) {
                                    409 ;	-----------------------------------------
                                    410 ;	 function i2c_set_start_ack
                                    411 ;	-----------------------------------------
      0081D9                        412 _i2c_set_start_ack:
                                    413 ;	sensors.c: 87: I2C_CR2 = I2C_ACK | I2C_START;
      0081D9 AE 52 11         [ 2]  414 	ldw	x, #0x5211
      0081DC A6 05            [ 1]  415 	ld	a, #0x05
      0081DE F7               [ 1]  416 	ld	(x), a
                                    417 ;	sensors.c: 88: while ((I2C_SR1 & I2C_SB) == 0);
      0081DF                        418 00101$:
      0081DF AE 52 17         [ 2]  419 	ldw	x, #0x5217
      0081E2 F6               [ 1]  420 	ld	a, (x)
      0081E3 44               [ 1]  421 	srl	a
      0081E4 24 F9            [ 1]  422 	jrnc	00101$
      0081E6 81               [ 4]  423 	ret
                                    424 ;	sensors.c: 95: void print_byte_hex (unsigned char buffer) {
                                    425 ;	-----------------------------------------
                                    426 ;	 function print_byte_hex
                                    427 ;	-----------------------------------------
      0081E7                        428 _print_byte_hex:
      0081E7 52 0C            [ 2]  429 	sub	sp, #12
                                    430 ;	sensors.c: 98: a = (buffer >> 4);
      0081E9 7B 0F            [ 1]  431 	ld	a, (0x0f, sp)
      0081EB 4E               [ 1]  432 	swap	a
      0081EC A4 0F            [ 1]  433 	and	a, #0x0f
      0081EE 5F               [ 1]  434 	clrw	x
      0081EF 97               [ 1]  435 	ld	xl, a
                                    436 ;	sensors.c: 99: if (a > 9)
      0081F0 A3 00 09         [ 2]  437 	cpw	x, #0x0009
      0081F3 2D 07            [ 1]  438 	jrsle	00102$
                                    439 ;	sensors.c: 100: a = a + 'a' - 10;
      0081F5 1C 00 57         [ 2]  440 	addw	x, #0x0057
      0081F8 1F 03            [ 2]  441 	ldw	(0x03, sp), x
      0081FA 20 05            [ 2]  442 	jra	00103$
      0081FC                        443 00102$:
                                    444 ;	sensors.c: 102: a += '0'; 
      0081FC 1C 00 30         [ 2]  445 	addw	x, #0x0030
      0081FF 1F 03            [ 2]  446 	ldw	(0x03, sp), x
      008201                        447 00103$:
                                    448 ;	sensors.c: 103: b = buffer & 0x0f;
      008201 7B 0F            [ 1]  449 	ld	a, (0x0f, sp)
      008203 A4 0F            [ 1]  450 	and	a, #0x0f
      008205 5F               [ 1]  451 	clrw	x
      008206 97               [ 1]  452 	ld	xl, a
                                    453 ;	sensors.c: 104: if (b > 9)
      008207 A3 00 09         [ 2]  454 	cpw	x, #0x0009
      00820A 2D 07            [ 1]  455 	jrsle	00105$
                                    456 ;	sensors.c: 105: b = b + 'a' - 10;
      00820C 1C 00 57         [ 2]  457 	addw	x, #0x0057
      00820F 1F 01            [ 2]  458 	ldw	(0x01, sp), x
      008211 20 05            [ 2]  459 	jra	00106$
      008213                        460 00105$:
                                    461 ;	sensors.c: 107: b += '0'; 
      008213 1C 00 30         [ 2]  462 	addw	x, #0x0030
      008216 1F 01            [ 2]  463 	ldw	(0x01, sp), x
      008218                        464 00106$:
                                    465 ;	sensors.c: 108: message[0] = a;
      008218 90 96            [ 1]  466 	ldw	y, sp
      00821A 72 A9 00 05      [ 2]  467 	addw	y, #5
      00821E 7B 04            [ 1]  468 	ld	a, (0x04, sp)
      008220 90 F7            [ 1]  469 	ld	(y), a
                                    470 ;	sensors.c: 109: message[1] = b;
      008222 93               [ 1]  471 	ldw	x, y
      008223 5C               [ 2]  472 	incw	x
      008224 7B 02            [ 1]  473 	ld	a, (0x02, sp)
      008226 F7               [ 1]  474 	ld	(x), a
                                    475 ;	sensors.c: 110: message[2] = 0;
      008227 93               [ 1]  476 	ldw	x, y
      008228 5C               [ 2]  477 	incw	x
      008229 5C               [ 2]  478 	incw	x
      00822A 7F               [ 1]  479 	clr	(x)
                                    480 ;	sensors.c: 111: UARTPrintF (message);
      00822B 90 89            [ 2]  481 	pushw	y
      00822D CD 81 80         [ 4]  482 	call	_UARTPrintF
      008230 5B 02            [ 2]  483 	addw	sp, #2
      008232 5B 0C            [ 2]  484 	addw	sp, #12
      008234 81               [ 4]  485 	ret
                                    486 ;	sensors.c: 115: unsigned char i2c_read_register (UCHAR addr, UCHAR rg) {
                                    487 ;	-----------------------------------------
                                    488 ;	 function i2c_read_register
                                    489 ;	-----------------------------------------
      008235                        490 _i2c_read_register:
      008235 52 02            [ 2]  491 	sub	sp, #2
                                    492 ;	sensors.c: 118: i2c_set_start_ack ();
      008237 CD 81 D9         [ 4]  493 	call	_i2c_set_start_ack
                                    494 ;	sensors.c: 119: i2c_send_address (addr, I2C_WRITE);
      00823A 4B 00            [ 1]  495 	push	#0x00
      00823C 7B 06            [ 1]  496 	ld	a, (0x06, sp)
      00823E 88               [ 1]  497 	push	a
      00823F CD 81 97         [ 4]  498 	call	_i2c_send_address
      008242 5B 02            [ 2]  499 	addw	sp, #2
                                    500 ;	sensors.c: 120: i2c_send_reg (rg);
      008244 7B 06            [ 1]  501 	ld	a, (0x06, sp)
      008246 88               [ 1]  502 	push	a
      008247 CD 81 5E         [ 4]  503 	call	_i2c_send_reg
      00824A 84               [ 1]  504 	pop	a
                                    505 ;	sensors.c: 121: i2c_set_start_ack ();
      00824B CD 81 D9         [ 4]  506 	call	_i2c_set_start_ack
                                    507 ;	sensors.c: 122: i2c_send_address (addr, I2C_READ);
      00824E 4B 01            [ 1]  508 	push	#0x01
      008250 7B 06            [ 1]  509 	ld	a, (0x06, sp)
      008252 88               [ 1]  510 	push	a
      008253 CD 81 97         [ 4]  511 	call	_i2c_send_address
      008256 5B 02            [ 2]  512 	addw	sp, #2
                                    513 ;	sensors.c: 123: reg = I2C_SR1;
      008258 AE 52 17         [ 2]  514 	ldw	x, #0x5217
      00825B F6               [ 1]  515 	ld	a, (x)
      00825C 6B 01            [ 1]  516 	ld	(0x01, sp), a
                                    517 ;	sensors.c: 124: reg = I2C_SR3;
      00825E AE 52 19         [ 2]  518 	ldw	x, #0x5219
      008261 F6               [ 1]  519 	ld	a, (x)
      008262 6B 01            [ 1]  520 	ld	(0x01, sp), a
                                    521 ;	sensors.c: 125: i2c_set_nak ();
      008264 CD 81 4E         [ 4]  522 	call	_i2c_set_nak
                                    523 ;	sensors.c: 126: i2c_set_stop ();
      008267 CD 81 56         [ 4]  524 	call	_i2c_set_stop
                                    525 ;	sensors.c: 127: i2c_read (&x);
      00826A 96               [ 1]  526 	ldw	x, sp
      00826B 5C               [ 2]  527 	incw	x
      00826C 5C               [ 2]  528 	incw	x
      00826D 89               [ 2]  529 	pushw	x
      00826E CD 81 3D         [ 4]  530 	call	_i2c_read
      008271 5B 02            [ 2]  531 	addw	sp, #2
                                    532 ;	sensors.c: 128: return (x);
      008273 7B 02            [ 1]  533 	ld	a, (0x02, sp)
      008275 5B 02            [ 2]  534 	addw	sp, #2
      008277 81               [ 4]  535 	ret
                                    536 ;	sensors.c: 131: void InitializeI2C (void) {
                                    537 ;	-----------------------------------------
                                    538 ;	 function InitializeI2C
                                    539 ;	-----------------------------------------
      008278                        540 _InitializeI2C:
                                    541 ;	sensors.c: 132: I2C_CR1 = 0;   //  Disable I2C before configuration starts. PE bit is bit 0
      008278 AE 52 10         [ 2]  542 	ldw	x, #0x5210
      00827B 7F               [ 1]  543 	clr	(x)
                                    544 ;	sensors.c: 136: I2C_FREQR = 16;                     //  Set the internal clock frequency (MHz).
      00827C AE 52 12         [ 2]  545 	ldw	x, #0x5212
      00827F A6 10            [ 1]  546 	ld	a, #0x10
      008281 F7               [ 1]  547 	ld	(x), a
                                    548 ;	sensors.c: 137: UNSET (I2C_CCRH, I2C_FS);           //  I2C running is standard mode.
      008282 72 17 52 1C      [ 1]  549 	bres	0x521c, #7
                                    550 ;	sensors.c: 139: I2C_CCRL = 0xa0;                    //  SCL clock speed is 50 kHz.
      008286 AE 52 1B         [ 2]  551 	ldw	x, #0x521b
      008289 A6 A0            [ 1]  552 	ld	a, #0xa0
      00828B F7               [ 1]  553 	ld	(x), a
                                    554 ;	sensors.c: 141: I2C_CCRH &= 0x00;	// Clears lower 4 bits "CCR"
      00828C AE 52 1C         [ 2]  555 	ldw	x, #0x521c
      00828F 7F               [ 1]  556 	clr	(x)
                                    557 ;	sensors.c: 145: UNSET (I2C_OARH, I2C_ADDMODE);      //  7 bit address mode.
      008290 72 17 52 14      [ 1]  558 	bres	0x5214, #7
                                    559 ;	sensors.c: 146: SET (I2C_OARH, I2C_ADDCONF);        //  Docs say this must always be 1.
      008294 AE 52 14         [ 2]  560 	ldw	x, #0x5214
      008297 F6               [ 1]  561 	ld	a, (x)
      008298 AA 40            [ 1]  562 	or	a, #0x40
      00829A F7               [ 1]  563 	ld	(x), a
                                    564 ;	sensors.c: 150: I2C_TRISER = 17;
      00829B AE 52 1D         [ 2]  565 	ldw	x, #0x521d
      00829E A6 11            [ 1]  566 	ld	a, #0x11
      0082A0 F7               [ 1]  567 	ld	(x), a
                                    568 ;	sensors.c: 158: I2C_CR1 = I2C_PE;	// Enables port
      0082A1 AE 52 10         [ 2]  569 	ldw	x, #0x5210
      0082A4 A6 01            [ 1]  570 	ld	a, #0x01
      0082A6 F7               [ 1]  571 	ld	(x), a
      0082A7 81               [ 4]  572 	ret
                                    573 ;	sensors.c: 164: void InitializeUART() {
                                    574 ;	-----------------------------------------
                                    575 ;	 function InitializeUART
                                    576 ;	-----------------------------------------
      0082A8                        577 _InitializeUART:
                                    578 ;	sensors.c: 174: UART1_CR1 = 0;
      0082A8 AE 52 34         [ 2]  579 	ldw	x, #0x5234
      0082AB 7F               [ 1]  580 	clr	(x)
                                    581 ;	sensors.c: 175: UART1_CR2 = 0;
      0082AC AE 52 35         [ 2]  582 	ldw	x, #0x5235
      0082AF 7F               [ 1]  583 	clr	(x)
                                    584 ;	sensors.c: 176: UART1_CR4 = 0;
      0082B0 AE 52 37         [ 2]  585 	ldw	x, #0x5237
      0082B3 7F               [ 1]  586 	clr	(x)
                                    587 ;	sensors.c: 177: UART1_CR3 = 0;
      0082B4 AE 52 36         [ 2]  588 	ldw	x, #0x5236
      0082B7 7F               [ 1]  589 	clr	(x)
                                    590 ;	sensors.c: 178: UART1_CR5 = 0;
      0082B8 AE 52 38         [ 2]  591 	ldw	x, #0x5238
      0082BB 7F               [ 1]  592 	clr	(x)
                                    593 ;	sensors.c: 179: UART1_GTR = 0;
      0082BC AE 52 39         [ 2]  594 	ldw	x, #0x5239
      0082BF 7F               [ 1]  595 	clr	(x)
                                    596 ;	sensors.c: 180: UART1_PSCR = 0;
      0082C0 AE 52 3A         [ 2]  597 	ldw	x, #0x523a
      0082C3 7F               [ 1]  598 	clr	(x)
                                    599 ;	sensors.c: 184: UNSET (UART1_CR1, CR1_M);        //  8 Data bits.
      0082C4 AE 52 34         [ 2]  600 	ldw	x, #0x5234
      0082C7 F6               [ 1]  601 	ld	a, (x)
      0082C8 A4 EF            [ 1]  602 	and	a, #0xef
      0082CA F7               [ 1]  603 	ld	(x), a
                                    604 ;	sensors.c: 185: UNSET (UART1_CR1, CR1_PCEN);     //  Disable parity.
      0082CB AE 52 34         [ 2]  605 	ldw	x, #0x5234
      0082CE F6               [ 1]  606 	ld	a, (x)
      0082CF A4 FB            [ 1]  607 	and	a, #0xfb
      0082D1 F7               [ 1]  608 	ld	(x), a
                                    609 ;	sensors.c: 186: UNSET (UART1_CR3, CR3_STOPH);    //  1 stop bit.
      0082D2 AE 52 36         [ 2]  610 	ldw	x, #0x5236
      0082D5 F6               [ 1]  611 	ld	a, (x)
      0082D6 A4 DF            [ 1]  612 	and	a, #0xdf
      0082D8 F7               [ 1]  613 	ld	(x), a
                                    614 ;	sensors.c: 187: UNSET (UART1_CR3, CR3_STOPL);    //  1 stop bit.
      0082D9 AE 52 36         [ 2]  615 	ldw	x, #0x5236
      0082DC F6               [ 1]  616 	ld	a, (x)
      0082DD A4 EF            [ 1]  617 	and	a, #0xef
      0082DF F7               [ 1]  618 	ld	(x), a
                                    619 ;	sensors.c: 188: UART1_BRR2 = 0x0a;      //  Set the baud rate registers to 115200 baud
      0082E0 AE 52 33         [ 2]  620 	ldw	x, #0x5233
      0082E3 A6 0A            [ 1]  621 	ld	a, #0x0a
      0082E5 F7               [ 1]  622 	ld	(x), a
                                    623 ;	sensors.c: 189: UART1_BRR1 = 0x08;      //  based upon a 16 MHz system clock.
      0082E6 AE 52 32         [ 2]  624 	ldw	x, #0x5232
      0082E9 A6 08            [ 1]  625 	ld	a, #0x08
      0082EB F7               [ 1]  626 	ld	(x), a
                                    627 ;	sensors.c: 193: UNSET (UART1_CR2, CR2_TEN);      //  Disable transmit.
      0082EC AE 52 35         [ 2]  628 	ldw	x, #0x5235
      0082EF F6               [ 1]  629 	ld	a, (x)
      0082F0 A4 F7            [ 1]  630 	and	a, #0xf7
      0082F2 F7               [ 1]  631 	ld	(x), a
                                    632 ;	sensors.c: 194: UNSET (UART1_CR2, CR2_REN);      //  Disable receive.
      0082F3 AE 52 35         [ 2]  633 	ldw	x, #0x5235
      0082F6 F6               [ 1]  634 	ld	a, (x)
      0082F7 A4 FB            [ 1]  635 	and	a, #0xfb
      0082F9 F7               [ 1]  636 	ld	(x), a
                                    637 ;	sensors.c: 198: SET (UART1_CR3, CR3_CPOL);
      0082FA AE 52 36         [ 2]  638 	ldw	x, #0x5236
      0082FD F6               [ 1]  639 	ld	a, (x)
      0082FE AA 04            [ 1]  640 	or	a, #0x04
      008300 F7               [ 1]  641 	ld	(x), a
                                    642 ;	sensors.c: 199: SET (UART1_CR3, CR3_CPHA);
      008301 AE 52 36         [ 2]  643 	ldw	x, #0x5236
      008304 F6               [ 1]  644 	ld	a, (x)
      008305 AA 02            [ 1]  645 	or	a, #0x02
      008307 F7               [ 1]  646 	ld	(x), a
                                    647 ;	sensors.c: 200: SET (UART1_CR3, CR3_LBCL);
      008308 72 10 52 36      [ 1]  648 	bset	0x5236, #0
                                    649 ;	sensors.c: 204: SET (UART1_CR2, CR2_TEN);
      00830C AE 52 35         [ 2]  650 	ldw	x, #0x5235
      00830F F6               [ 1]  651 	ld	a, (x)
      008310 AA 08            [ 1]  652 	or	a, #0x08
      008312 F7               [ 1]  653 	ld	(x), a
                                    654 ;	sensors.c: 205: SET (UART1_CR2, CR2_REN);
      008313 AE 52 35         [ 2]  655 	ldw	x, #0x5235
      008316 F6               [ 1]  656 	ld	a, (x)
      008317 AA 04            [ 1]  657 	or	a, #0x04
      008319 F7               [ 1]  658 	ld	(x), a
                                    659 ;	sensors.c: 206: UART1_CR3 = CR3_CLKEN;
      00831A AE 52 36         [ 2]  660 	ldw	x, #0x5236
      00831D A6 08            [ 1]  661 	ld	a, #0x08
      00831F F7               [ 1]  662 	ld	(x), a
      008320 81               [ 4]  663 	ret
                                    664 ;	sensors.c: 234: void tm1637Init(void)
                                    665 ;	-----------------------------------------
                                    666 ;	 function tm1637Init
                                    667 ;	-----------------------------------------
      008321                        668 _tm1637Init:
                                    669 ;	sensors.c: 236: tm1637SetBrightness(8);
      008321 4B 08            [ 1]  670 	push	#0x08
      008323 CD 83 C6         [ 4]  671 	call	_tm1637SetBrightness
      008326 84               [ 1]  672 	pop	a
      008327 81               [ 4]  673 	ret
                                    674 ;	sensors.c: 241: void tm1637DisplayDecimal(long TT,unsigned int displaySeparator)
                                    675 ;	-----------------------------------------
                                    676 ;	 function tm1637DisplayDecimal
                                    677 ;	-----------------------------------------
      008328                        678 _tm1637DisplayDecimal:
      008328 52 13            [ 2]  679 	sub	sp, #19
                                    680 ;	sensors.c: 243: unsigned int v = TT & 0x0000FFFF;
      00832A 7B 19            [ 1]  681 	ld	a, (0x19, sp)
      00832C 97               [ 1]  682 	ld	xl, a
      00832D 7B 18            [ 1]  683 	ld	a, (0x18, sp)
      00832F 95               [ 1]  684 	ld	xh, a
      008330 0F 0C            [ 1]  685 	clr	(0x0c, sp)
      008332 4F               [ 1]  686 	clr	a
      008333 1F 05            [ 2]  687 	ldw	(0x05, sp), x
                                    688 ;	sensors.c: 249: for (ii = 0; ii < 4; ++ii) {
      008335 96               [ 1]  689 	ldw	x, sp
      008336 5C               [ 2]  690 	incw	x
      008337 1F 09            [ 2]  691 	ldw	(0x09, sp), x
      008339 AE 85 26         [ 2]  692 	ldw	x, #_segmentMap+0
      00833C 1F 12            [ 2]  693 	ldw	(0x12, sp), x
      00833E 90 5F            [ 1]  694 	clrw	y
      008340                        695 00106$:
                                    696 ;	sensors.c: 250: digitArr[ii] = segmentMap[v % 10];
      008340 93               [ 1]  697 	ldw	x, y
      008341 72 FB 09         [ 2]  698 	addw	x, (0x09, sp)
      008344 1F 10            [ 2]  699 	ldw	(0x10, sp), x
      008346 90 89            [ 2]  700 	pushw	y
      008348 1E 07            [ 2]  701 	ldw	x, (0x07, sp)
      00834A 90 AE 00 0A      [ 2]  702 	ldw	y, #0x000a
      00834E 65               [ 2]  703 	divw	x, y
      00834F 93               [ 1]  704 	ldw	x, y
      008350 90 85            [ 2]  705 	popw	y
      008352 72 FB 12         [ 2]  706 	addw	x, (0x12, sp)
      008355 F6               [ 1]  707 	ld	a, (x)
      008356 1E 10            [ 2]  708 	ldw	x, (0x10, sp)
      008358 F7               [ 1]  709 	ld	(x), a
                                    710 ;	sensors.c: 251: if (ii == 2 && displaySeparator) {
      008359 90 A3 00 02      [ 2]  711 	cpw	y, #0x0002
      00835D 26 0C            [ 1]  712 	jrne	00102$
      00835F 1E 1A            [ 2]  713 	ldw	x, (0x1a, sp)
      008361 27 08            [ 1]  714 	jreq	00102$
                                    715 ;	sensors.c: 252: digitArr[ii] |= 1 << 7;
      008363 1E 10            [ 2]  716 	ldw	x, (0x10, sp)
      008365 F6               [ 1]  717 	ld	a, (x)
      008366 AA 80            [ 1]  718 	or	a, #0x80
      008368 1E 10            [ 2]  719 	ldw	x, (0x10, sp)
      00836A F7               [ 1]  720 	ld	(x), a
      00836B                        721 00102$:
                                    722 ;	sensors.c: 254: v /= 10;
      00836B 90 89            [ 2]  723 	pushw	y
      00836D 1E 07            [ 2]  724 	ldw	x, (0x07, sp)
      00836F 90 AE 00 0A      [ 2]  725 	ldw	y, #0x000a
      008373 65               [ 2]  726 	divw	x, y
      008374 90 85            [ 2]  727 	popw	y
      008376 1F 05            [ 2]  728 	ldw	(0x05, sp), x
                                    729 ;	sensors.c: 249: for (ii = 0; ii < 4; ++ii) {
      008378 90 5C            [ 2]  730 	incw	y
      00837A 90 A3 00 04      [ 2]  731 	cpw	y, #0x0004
      00837E 25 C0            [ 1]  732 	jrc	00106$
                                    733 ;	sensors.c: 257: _tm1637Start();
      008380 CD 83 D8         [ 4]  734 	call	__tm1637Start
                                    735 ;	sensors.c: 258: _tm1637WriteByte(0x40);
      008383 4B 40            [ 1]  736 	push	#0x40
      008385 CD 84 2C         [ 4]  737 	call	__tm1637WriteByte
      008388 84               [ 1]  738 	pop	a
                                    739 ;	sensors.c: 259: _tm1637ReadResult();
      008389 CD 84 11         [ 4]  740 	call	__tm1637ReadResult
                                    741 ;	sensors.c: 260: _tm1637Stop();
      00838C CD 83 EA         [ 4]  742 	call	__tm1637Stop
                                    743 ;	sensors.c: 262: _tm1637Start();
      00838F CD 83 D8         [ 4]  744 	call	__tm1637Start
                                    745 ;	sensors.c: 263: _tm1637WriteByte(0xc0);
      008392 4B C0            [ 1]  746 	push	#0xc0
      008394 CD 84 2C         [ 4]  747 	call	__tm1637WriteByte
      008397 84               [ 1]  748 	pop	a
                                    749 ;	sensors.c: 264: _tm1637ReadResult();
      008398 CD 84 11         [ 4]  750 	call	__tm1637ReadResult
                                    751 ;	sensors.c: 266: for (ii = 0; ii < 4; ++ii) {
      00839B 5F               [ 1]  752 	clrw	x
      00839C 1F 07            [ 2]  753 	ldw	(0x07, sp), x
      00839E                        754 00108$:
                                    755 ;	sensors.c: 267: _tm1637WriteByte(digitArr[3 - ii]);
      00839E 7B 08            [ 1]  756 	ld	a, (0x08, sp)
      0083A0 6B 0F            [ 1]  757 	ld	(0x0f, sp), a
      0083A2 A6 03            [ 1]  758 	ld	a, #0x03
      0083A4 10 0F            [ 1]  759 	sub	a, (0x0f, sp)
      0083A6 5F               [ 1]  760 	clrw	x
      0083A7 97               [ 1]  761 	ld	xl, a
      0083A8 72 FB 09         [ 2]  762 	addw	x, (0x09, sp)
      0083AB F6               [ 1]  763 	ld	a, (x)
      0083AC 88               [ 1]  764 	push	a
      0083AD CD 84 2C         [ 4]  765 	call	__tm1637WriteByte
      0083B0 84               [ 1]  766 	pop	a
                                    767 ;	sensors.c: 268: _tm1637ReadResult();
      0083B1 CD 84 11         [ 4]  768 	call	__tm1637ReadResult
                                    769 ;	sensors.c: 266: for (ii = 0; ii < 4; ++ii) {
      0083B4 1E 07            [ 2]  770 	ldw	x, (0x07, sp)
      0083B6 5C               [ 2]  771 	incw	x
      0083B7 1F 07            [ 2]  772 	ldw	(0x07, sp), x
      0083B9 1E 07            [ 2]  773 	ldw	x, (0x07, sp)
      0083BB A3 00 04         [ 2]  774 	cpw	x, #0x0004
      0083BE 25 DE            [ 1]  775 	jrc	00108$
                                    776 ;	sensors.c: 271: _tm1637Stop();
      0083C0 CD 83 EA         [ 4]  777 	call	__tm1637Stop
      0083C3 5B 13            [ 2]  778 	addw	sp, #19
      0083C5 81               [ 4]  779 	ret
                                    780 ;	sensors.c: 276: void tm1637SetBrightness(char brightness)
                                    781 ;	-----------------------------------------
                                    782 ;	 function tm1637SetBrightness
                                    783 ;	-----------------------------------------
      0083C6                        784 _tm1637SetBrightness:
                                    785 ;	sensors.c: 283: _tm1637Start();
      0083C6 CD 83 D8         [ 4]  786 	call	__tm1637Start
                                    787 ;	sensors.c: 284: _tm1637WriteByte(0x87 + brightness);
      0083C9 7B 03            [ 1]  788 	ld	a, (0x03, sp)
      0083CB AB 87            [ 1]  789 	add	a, #0x87
      0083CD 88               [ 1]  790 	push	a
      0083CE CD 84 2C         [ 4]  791 	call	__tm1637WriteByte
      0083D1 84               [ 1]  792 	pop	a
                                    793 ;	sensors.c: 285: _tm1637ReadResult();
      0083D2 CD 84 11         [ 4]  794 	call	__tm1637ReadResult
                                    795 ;	sensors.c: 286: _tm1637Stop();
      0083D5 CC 83 EA         [ 2]  796 	jp	__tm1637Stop
                                    797 ;	sensors.c: 289: void _tm1637Start(void)
                                    798 ;	-----------------------------------------
                                    799 ;	 function _tm1637Start
                                    800 ;	-----------------------------------------
      0083D8                        801 __tm1637Start:
                                    802 ;	sensors.c: 291: _tm1637ClkHigh();
      0083D8 CD 84 6A         [ 4]  803 	call	__tm1637ClkHigh
                                    804 ;	sensors.c: 292: _tm1637DioHigh();
      0083DB CD 84 7A         [ 4]  805 	call	__tm1637DioHigh
                                    806 ;	sensors.c: 293: delay(5);
      0083DE 4B 05            [ 1]  807 	push	#0x05
      0083E0 4B 00            [ 1]  808 	push	#0x00
      0083E2 CD 80 F2         [ 4]  809 	call	_delay
      0083E5 5B 02            [ 2]  810 	addw	sp, #2
                                    811 ;	sensors.c: 294: _tm1637DioLow();
      0083E7 CC 84 82         [ 2]  812 	jp	__tm1637DioLow
                                    813 ;	sensors.c: 297: void _tm1637Stop(void)
                                    814 ;	-----------------------------------------
                                    815 ;	 function _tm1637Stop
                                    816 ;	-----------------------------------------
      0083EA                        817 __tm1637Stop:
                                    818 ;	sensors.c: 299: _tm1637ClkLow();
      0083EA CD 84 72         [ 4]  819 	call	__tm1637ClkLow
                                    820 ;	sensors.c: 300: delay(5);
      0083ED 4B 05            [ 1]  821 	push	#0x05
      0083EF 4B 00            [ 1]  822 	push	#0x00
      0083F1 CD 80 F2         [ 4]  823 	call	_delay
      0083F4 5B 02            [ 2]  824 	addw	sp, #2
                                    825 ;	sensors.c: 301: _tm1637DioLow();
      0083F6 CD 84 82         [ 4]  826 	call	__tm1637DioLow
                                    827 ;	sensors.c: 302: delay(5);
      0083F9 4B 05            [ 1]  828 	push	#0x05
      0083FB 4B 00            [ 1]  829 	push	#0x00
      0083FD CD 80 F2         [ 4]  830 	call	_delay
      008400 5B 02            [ 2]  831 	addw	sp, #2
                                    832 ;	sensors.c: 303: _tm1637ClkHigh();
      008402 CD 84 6A         [ 4]  833 	call	__tm1637ClkHigh
                                    834 ;	sensors.c: 304: delay(5);
      008405 4B 05            [ 1]  835 	push	#0x05
      008407 4B 00            [ 1]  836 	push	#0x00
      008409 CD 80 F2         [ 4]  837 	call	_delay
      00840C 5B 02            [ 2]  838 	addw	sp, #2
                                    839 ;	sensors.c: 305: _tm1637DioHigh();
      00840E CC 84 7A         [ 2]  840 	jp	__tm1637DioHigh
                                    841 ;	sensors.c: 308: void _tm1637ReadResult(void)
                                    842 ;	-----------------------------------------
                                    843 ;	 function _tm1637ReadResult
                                    844 ;	-----------------------------------------
      008411                        845 __tm1637ReadResult:
                                    846 ;	sensors.c: 310: _tm1637ClkLow();
      008411 CD 84 72         [ 4]  847 	call	__tm1637ClkLow
                                    848 ;	sensors.c: 311: delay(5);
      008414 4B 05            [ 1]  849 	push	#0x05
      008416 4B 00            [ 1]  850 	push	#0x00
      008418 CD 80 F2         [ 4]  851 	call	_delay
      00841B 5B 02            [ 2]  852 	addw	sp, #2
                                    853 ;	sensors.c: 313: _tm1637ClkHigh();
      00841D CD 84 6A         [ 4]  854 	call	__tm1637ClkHigh
                                    855 ;	sensors.c: 314: delay(5);
      008420 4B 05            [ 1]  856 	push	#0x05
      008422 4B 00            [ 1]  857 	push	#0x00
      008424 CD 80 F2         [ 4]  858 	call	_delay
      008427 5B 02            [ 2]  859 	addw	sp, #2
                                    860 ;	sensors.c: 315: _tm1637ClkLow();
      008429 CC 84 72         [ 2]  861 	jp	__tm1637ClkLow
                                    862 ;	sensors.c: 318: void _tm1637WriteByte(unsigned char b)
                                    863 ;	-----------------------------------------
                                    864 ;	 function _tm1637WriteByte
                                    865 ;	-----------------------------------------
      00842C                        866 __tm1637WriteByte:
      00842C 52 02            [ 2]  867 	sub	sp, #2
                                    868 ;	sensors.c: 320: for (ii = 0; ii < 8; ++ii) {
      00842E 5F               [ 1]  869 	clrw	x
      00842F 1F 01            [ 2]  870 	ldw	(0x01, sp), x
      008431                        871 00105$:
                                    872 ;	sensors.c: 321: _tm1637ClkLow();
      008431 CD 84 72         [ 4]  873 	call	__tm1637ClkLow
                                    874 ;	sensors.c: 322: if (b & 0x01) {
      008434 7B 05            [ 1]  875 	ld	a, (0x05, sp)
      008436 44               [ 1]  876 	srl	a
      008437 24 05            [ 1]  877 	jrnc	00102$
                                    878 ;	sensors.c: 323: _tm1637DioHigh();
      008439 CD 84 7A         [ 4]  879 	call	__tm1637DioHigh
      00843C 20 03            [ 2]  880 	jra	00103$
      00843E                        881 00102$:
                                    882 ;	sensors.c: 326: _tm1637DioLow();
      00843E CD 84 82         [ 4]  883 	call	__tm1637DioLow
      008441                        884 00103$:
                                    885 ;	sensors.c: 328: delay(15);
      008441 4B 0F            [ 1]  886 	push	#0x0f
      008443 4B 00            [ 1]  887 	push	#0x00
      008445 CD 80 F2         [ 4]  888 	call	_delay
      008448 5B 02            [ 2]  889 	addw	sp, #2
                                    890 ;	sensors.c: 329: b >>= 1;
      00844A 7B 05            [ 1]  891 	ld	a, (0x05, sp)
      00844C 44               [ 1]  892 	srl	a
      00844D 6B 05            [ 1]  893 	ld	(0x05, sp), a
                                    894 ;	sensors.c: 330: _tm1637ClkHigh();
      00844F CD 84 6A         [ 4]  895 	call	__tm1637ClkHigh
                                    896 ;	sensors.c: 331: delay(15);
      008452 4B 0F            [ 1]  897 	push	#0x0f
      008454 4B 00            [ 1]  898 	push	#0x00
      008456 CD 80 F2         [ 4]  899 	call	_delay
      008459 5B 02            [ 2]  900 	addw	sp, #2
                                    901 ;	sensors.c: 320: for (ii = 0; ii < 8; ++ii) {
      00845B 1E 01            [ 2]  902 	ldw	x, (0x01, sp)
      00845D 5C               [ 2]  903 	incw	x
      00845E 1F 01            [ 2]  904 	ldw	(0x01, sp), x
      008460 1E 01            [ 2]  905 	ldw	x, (0x01, sp)
      008462 A3 00 08         [ 2]  906 	cpw	x, #0x0008
      008465 2F CA            [ 1]  907 	jrslt	00105$
      008467 5B 02            [ 2]  908 	addw	sp, #2
      008469 81               [ 4]  909 	ret
                                    910 ;	sensors.c: 337: void _tm1637ClkHigh(void)
                                    911 ;	-----------------------------------------
                                    912 ;	 function _tm1637ClkHigh
                                    913 ;	-----------------------------------------
      00846A                        914 __tm1637ClkHigh:
                                    915 ;	sensors.c: 342: PD_ODR |= 1 << 2;
      00846A AE 50 0F         [ 2]  916 	ldw	x, #0x500f
      00846D F6               [ 1]  917 	ld	a, (x)
      00846E AA 04            [ 1]  918 	or	a, #0x04
      008470 F7               [ 1]  919 	ld	(x), a
      008471 81               [ 4]  920 	ret
                                    921 ;	sensors.c: 345: void _tm1637ClkLow(void)
                                    922 ;	-----------------------------------------
                                    923 ;	 function _tm1637ClkLow
                                    924 ;	-----------------------------------------
      008472                        925 __tm1637ClkLow:
                                    926 ;	sensors.c: 349: PD_ODR &= ~(1 << 2);
      008472 AE 50 0F         [ 2]  927 	ldw	x, #0x500f
      008475 F6               [ 1]  928 	ld	a, (x)
      008476 A4 FB            [ 1]  929 	and	a, #0xfb
      008478 F7               [ 1]  930 	ld	(x), a
      008479 81               [ 4]  931 	ret
                                    932 ;	sensors.c: 355: void _tm1637DioHigh(void)
                                    933 ;	-----------------------------------------
                                    934 ;	 function _tm1637DioHigh
                                    935 ;	-----------------------------------------
      00847A                        936 __tm1637DioHigh:
                                    937 ;	sensors.c: 359: PD_ODR |= 1 << 3;
      00847A AE 50 0F         [ 2]  938 	ldw	x, #0x500f
      00847D F6               [ 1]  939 	ld	a, (x)
      00847E AA 08            [ 1]  940 	or	a, #0x08
      008480 F7               [ 1]  941 	ld	(x), a
      008481 81               [ 4]  942 	ret
                                    943 ;	sensors.c: 363: void _tm1637DioLow(void)
                                    944 ;	-----------------------------------------
                                    945 ;	 function _tm1637DioLow
                                    946 ;	-----------------------------------------
      008482                        947 __tm1637DioLow:
                                    948 ;	sensors.c: 365: PD_ODR &= ~(1 << 3);
      008482 AE 50 0F         [ 2]  949 	ldw	x, #0x500f
      008485 F6               [ 1]  950 	ld	a, (x)
      008486 A4 F7            [ 1]  951 	and	a, #0xf7
      008488 F7               [ 1]  952 	ld	(x), a
      008489 81               [ 4]  953 	ret
                                    954 ;	sensors.c: 379: int main () {
                                    955 ;	-----------------------------------------
                                    956 ;	 function main
                                    957 ;	-----------------------------------------
      00848A                        958 _main:
      00848A 52 06            [ 2]  959 	sub	sp, #6
                                    960 ;	sensors.c: 380: unsigned int val=0;
      00848C 5F               [ 1]  961 	clrw	x
      00848D 1F 05            [ 2]  962 	ldw	(0x05, sp), x
                                    963 ;	sensors.c: 382: InitializeSystemClock();
      00848F CD 80 A8         [ 4]  964 	call	_InitializeSystemClock
                                    965 ;	sensors.c: 385: PD_DDR = (1 << 3) | (1 << 2); // output mode
      008492 AE 50 11         [ 2]  966 	ldw	x, #0x5011
      008495 A6 0C            [ 1]  967 	ld	a, #0x0c
      008497 F7               [ 1]  968 	ld	(x), a
                                    969 ;	sensors.c: 386: PD_CR1 = (1 << 3) | (1 << 2); // push-pull
      008498 AE 50 12         [ 2]  970 	ldw	x, #0x5012
      00849B A6 0C            [ 1]  971 	ld	a, #0x0c
      00849D F7               [ 1]  972 	ld	(x), a
                                    973 ;	sensors.c: 387: PD_CR2 = (1 << 3) | (1 << 2); // up to 10MHz speed
      00849E AE 50 13         [ 2]  974 	ldw	x, #0x5013
      0084A1 A6 0C            [ 1]  975 	ld	a, #0x0c
      0084A3 F7               [ 1]  976 	ld	(x), a
                                    977 ;	sensors.c: 390: PA_DDR &= ~(1<<3); //port PA3 input
      0084A4 AE 50 02         [ 2]  978 	ldw	x, #0x5002
      0084A7 F6               [ 1]  979 	ld	a, (x)
      0084A8 A4 F7            [ 1]  980 	and	a, #0xf7
      0084AA F7               [ 1]  981 	ld	(x), a
                                    982 ;	sensors.c: 391: PA_CR1 |= 1<<3; //pull up enabled
      0084AB AE 50 03         [ 2]  983 	ldw	x, #0x5003
      0084AE F6               [ 1]  984 	ld	a, (x)
      0084AF AA 08            [ 1]  985 	or	a, #0x08
      0084B1 F7               [ 1]  986 	ld	(x), a
                                    987 ;	sensors.c: 394: ADC_CSR |= ((0x0F)&2); // select channel = 2 = PC4
      0084B2 AE 54 00         [ 2]  988 	ldw	x, #0x5400
      0084B5 F6               [ 1]  989 	ld	a, (x)
      0084B6 AA 02            [ 1]  990 	or	a, #0x02
      0084B8 F7               [ 1]  991 	ld	(x), a
                                    992 ;	sensors.c: 395: ADC_CR2 |= (1<<3); // Right Aligned Data
      0084B9 AE 54 02         [ 2]  993 	ldw	x, #0x5402
      0084BC F6               [ 1]  994 	ld	a, (x)
      0084BD AA 08            [ 1]  995 	or	a, #0x08
      0084BF F7               [ 1]  996 	ld	(x), a
                                    997 ;	sensors.c: 396: ADC_CR1 |= (1<<0); // ADC ON
      0084C0 AE 54 01         [ 2]  998 	ldw	x, #0x5401
      0084C3 F6               [ 1]  999 	ld	a, (x)
      0084C4 AA 01            [ 1] 1000 	or	a, #0x01
      0084C6 F7               [ 1] 1001 	ld	(x), a
                                   1002 ;	sensors.c: 397: tm1637Init();
      0084C7 CD 83 21         [ 4] 1003 	call	_tm1637Init
                                   1004 ;	sensors.c: 399: InitializeUART();
      0084CA CD 82 A8         [ 4] 1005 	call	_InitializeUART
                                   1006 ;	sensors.c: 400: while (1) {
      0084CD                       1007 00105$:
                                   1008 ;	sensors.c: 402: ADC_CR1 |= (1<<0); // ADC Start Conversion
      0084CD 72 10 54 01      [ 1] 1009 	bset	0x5401, #0
                                   1010 ;	sensors.c: 403: while(((ADC_CSR)&(1<<7))== 0); // Wait till EOC
      0084D1                       1011 00101$:
      0084D1 AE 54 00         [ 2] 1012 	ldw	x, #0x5400
      0084D4 F6               [ 1] 1013 	ld	a, (x)
      0084D5 48               [ 1] 1014 	sll	a
      0084D6 24 F9            [ 1] 1015 	jrnc	00101$
                                   1016 ;	sensors.c: 404: val |= (unsigned int)ADC_DRL;
      0084D8 AE 54 05         [ 2] 1017 	ldw	x, #0x5405
      0084DB F6               [ 1] 1018 	ld	a, (x)
      0084DC 5F               [ 1] 1019 	clrw	x
      0084DD 97               [ 1] 1020 	ld	xl, a
      0084DE 1A 06            [ 1] 1021 	or	a, (0x06, sp)
      0084E0 6B 04            [ 1] 1022 	ld	(0x04, sp), a
      0084E2 9E               [ 1] 1023 	ld	a, xh
      0084E3 1A 05            [ 1] 1024 	or	a, (0x05, sp)
      0084E5 6B 01            [ 1] 1025 	ld	(0x01, sp), a
      0084E7 7B 04            [ 1] 1026 	ld	a, (0x04, sp)
      0084E9 6B 02            [ 1] 1027 	ld	(0x02, sp), a
                                   1028 ;	sensors.c: 405: val |= (unsigned int)ADC_DRH<<8;
      0084EB AE 54 04         [ 2] 1029 	ldw	x, #0x5404
      0084EE F6               [ 1] 1030 	ld	a, (x)
      0084EF 5F               [ 1] 1031 	clrw	x
      0084F0 97               [ 1] 1032 	ld	xl, a
      0084F1 58               [ 2] 1033 	sllw	x
      0084F2 58               [ 2] 1034 	sllw	x
      0084F3 58               [ 2] 1035 	sllw	x
      0084F4 58               [ 2] 1036 	sllw	x
      0084F5 58               [ 2] 1037 	sllw	x
      0084F6 58               [ 2] 1038 	sllw	x
      0084F7 58               [ 2] 1039 	sllw	x
      0084F8 58               [ 2] 1040 	sllw	x
      0084F9 9F               [ 1] 1041 	ld	a, xl
      0084FA 1A 02            [ 1] 1042 	or	a, (0x02, sp)
      0084FC 90 97            [ 1] 1043 	ld	yl, a
      0084FE 9E               [ 1] 1044 	ld	a, xh
      0084FF 1A 01            [ 1] 1045 	or	a, (0x01, sp)
      008501 90 95            [ 1] 1046 	ld	yh, a
                                   1047 ;	sensors.c: 406: ADC_CR1 &= ~(1<<0); // ADC Stop Conversion
      008503 AE 54 01         [ 2] 1048 	ldw	x, #0x5401
      008506 F6               [ 1] 1049 	ld	a, (x)
      008507 A4 FE            [ 1] 1050 	and	a, #0xfe
      008509 F7               [ 1] 1051 	ld	(x), a
                                   1052 ;	sensors.c: 407: val &= 0x03ff;
      00850A 90 9E            [ 1] 1053 	ld	a, yh
      00850C A4 03            [ 1] 1054 	and	a, #0x03
      00850E 90 95            [ 1] 1055 	ld	yh, a
      008510 17 05            [ 2] 1056 	ldw	(0x05, sp), y
                                   1057 ;	sensors.c: 408: tm1637DisplayDecimal(val, 1); // eg 37:12
      008512 16 05            [ 2] 1058 	ldw	y, (0x05, sp)
      008514 5F               [ 1] 1059 	clrw	x
      008515 4B 01            [ 1] 1060 	push	#0x01
      008517 4B 00            [ 1] 1061 	push	#0x00
      008519 90 89            [ 2] 1062 	pushw	y
      00851B 89               [ 2] 1063 	pushw	x
      00851C CD 83 28         [ 4] 1064 	call	_tm1637DisplayDecimal
      00851F 5B 06            [ 2] 1065 	addw	sp, #6
      008521 20 AA            [ 2] 1066 	jra	00105$
      008523 5B 06            [ 2] 1067 	addw	sp, #6
      008525 81               [ 4] 1068 	ret
                                   1069 	.area CODE
      008526                       1070 _segmentMap:
      008526 3F                    1071 	.db #0x3F	;  63
      008527 06                    1072 	.db #0x06	;  6
      008528 5B                    1073 	.db #0x5B	;  91
      008529 4F                    1074 	.db #0x4F	;  79	'O'
      00852A 66                    1075 	.db #0x66	;  102	'f'
      00852B 6D                    1076 	.db #0x6D	;  109	'm'
      00852C 7D                    1077 	.db #0x7D	;  125
      00852D 07                    1078 	.db #0x07	;  7
      00852E 7F                    1079 	.db #0x7F	;  127
      00852F 6F                    1080 	.db #0x6F	;  111	'o'
      008530 77                    1081 	.db #0x77	;  119	'w'
      008531 7C                    1082 	.db #0x7C	;  124
      008532 39                    1083 	.db #0x39	;  57	'9'
      008533 5E                    1084 	.db #0x5E	;  94
      008534 79                    1085 	.db #0x79	;  121	'y'
      008535 71                    1086 	.db #0x71	;  113	'q'
      008536 00                    1087 	.db #0x00	;  0
                                   1088 	.area INITIALIZER
                                   1089 	.area CABS (ABS)
