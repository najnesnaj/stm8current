                                      1 ;--------------------------------------------------------
                                      2 ; File Created by SDCC : free open source ANSI-C Compiler
                                      3 ; Version 3.4.0 #8981 (Jul 11 2014) (Linux)
                                      4 ; This file was generated Wed Apr 19 15:37:51 2017
                                      5 ;--------------------------------------------------------
                                      6 	.module sensors
                                      7 	.optsdcc -mstm8
                                      8 	
                                      9 ;--------------------------------------------------------
                                     10 ; Public variables in this module
                                     11 ;--------------------------------------------------------
                                     12 	.globl _segmentMap
                                     13 	.globl _main
                                     14 	.globl _timer_isr
                                     15 	.globl _clock
                                     16 	.globl _tm1637DisplayDecimal
                                     17 	.globl _tm1637Init
                                     18 	.globl _InitializeUART
                                     19 	.globl _InitializeI2C
                                     20 	.globl _i2c_read_register
                                     21 	.globl _print_byte_hex
                                     22 	.globl _i2c_set_start_ack
                                     23 	.globl _i2c_send_address
                                     24 	.globl _print_UCHAR_hex
                                     25 	.globl _UARTPrintF
                                     26 	.globl _i2c_send_reg
                                     27 	.globl _i2c_set_stop
                                     28 	.globl _i2c_set_nak
                                     29 	.globl _i2c_read
                                     30 	.globl _delay
                                     31 	.globl _InitializeSystemClock
                                     32 	.globl _delayTenMicro
                                     33 	.globl _seconden
                                     34 	.globl _internteller
                                     35 	.globl _tm1637SetBrightness
                                     36 	.globl __tm1637Start
                                     37 	.globl __tm1637Stop
                                     38 	.globl __tm1637ReadResult
                                     39 	.globl __tm1637WriteByte
                                     40 	.globl __tm1637ClkHigh
                                     41 	.globl __tm1637ClkLow
                                     42 	.globl __tm1637DioHigh
                                     43 	.globl __tm1637DioLow
                                     44 ;--------------------------------------------------------
                                     45 ; ram data
                                     46 ;--------------------------------------------------------
                                     47 	.area DATA
      000001                         48 _internteller::
      000001                         49 	.ds 2
      000003                         50 _seconden::
      000003                         51 	.ds 2
                                     52 ;--------------------------------------------------------
                                     53 ; ram data
                                     54 ;--------------------------------------------------------
                                     55 	.area INITIALIZED
                                     56 ;--------------------------------------------------------
                                     57 ; Stack segment in internal ram 
                                     58 ;--------------------------------------------------------
                                     59 	.area	SSEG
      000000                         60 __start__stack:
      000000                         61 	.ds	1
                                     62 
                                     63 ;--------------------------------------------------------
                                     64 ; absolute external ram data
                                     65 ;--------------------------------------------------------
                                     66 	.area DABS (ABS)
                                     67 ;--------------------------------------------------------
                                     68 ; interrupt vector 
                                     69 ;--------------------------------------------------------
                                     70 	.area HOME
      008000                         71 __interrupt_vect:
      008000 82 00 80 83             72 	int s_GSINIT ;reset
      008004 82 00 00 00             73 	int 0x0000 ;trap
      008008 82 00 00 00             74 	int 0x0000 ;int0
      00800C 82 00 00 00             75 	int 0x0000 ;int1
      008010 82 00 00 00             76 	int 0x0000 ;int2
      008014 82 00 00 00             77 	int 0x0000 ;int3
      008018 82 00 00 00             78 	int 0x0000 ;int4
      00801C 82 00 00 00             79 	int 0x0000 ;int5
      008020 82 00 00 00             80 	int 0x0000 ;int6
      008024 82 00 00 00             81 	int 0x0000 ;int7
      008028 82 00 00 00             82 	int 0x0000 ;int8
      00802C 82 00 00 00             83 	int 0x0000 ;int9
      008030 82 00 00 00             84 	int 0x0000 ;int10
      008034 82 00 00 00             85 	int 0x0000 ;int11
      008038 82 00 00 00             86 	int 0x0000 ;int12
      00803C 82 00 00 00             87 	int 0x0000 ;int13
      008040 82 00 00 00             88 	int 0x0000 ;int14
      008044 82 00 00 00             89 	int 0x0000 ;int15
      008048 82 00 00 00             90 	int 0x0000 ;int16
      00804C 82 00 00 00             91 	int 0x0000 ;int17
      008050 82 00 00 00             92 	int 0x0000 ;int18
      008054 82 00 00 00             93 	int 0x0000 ;int19
      008058 82 00 00 00             94 	int 0x0000 ;int20
      00805C 82 00 00 00             95 	int 0x0000 ;int21
      008060 82 00 00 00             96 	int 0x0000 ;int22
      008064 82 00 85 01             97 	int _timer_isr ;int23
      008068 82 00 00 00             98 	int 0x0000 ;int24
      00806C 82 00 00 00             99 	int 0x0000 ;int25
      008070 82 00 00 00            100 	int 0x0000 ;int26
      008074 82 00 00 00            101 	int 0x0000 ;int27
      008078 82 00 00 00            102 	int 0x0000 ;int28
      00807C 82 00 00 00            103 	int 0x0000 ;int29
                                    104 ;--------------------------------------------------------
                                    105 ; global & static initialisations
                                    106 ;--------------------------------------------------------
                                    107 	.area HOME
                                    108 	.area GSINIT
                                    109 	.area GSFINAL
                                    110 	.area GSINIT
      008083                        111 __sdcc_gs_init_startup:
      008083                        112 __sdcc_init_data:
                                    113 ; stm8_genXINIT() start
      008083 AE 00 04         [ 2]  114 	ldw x, #l_DATA
      008086 27 07            [ 1]  115 	jreq	00002$
      008088                        116 00001$:
      008088 72 4F 00 00      [ 1]  117 	clr (s_DATA - 1, x)
      00808C 5A               [ 2]  118 	decw x
      00808D 26 F9            [ 1]  119 	jrne	00001$
      00808F                        120 00002$:
      00808F AE 00 00         [ 2]  121 	ldw	x, #l_INITIALIZER
      008092 27 09            [ 1]  122 	jreq	00004$
      008094                        123 00003$:
      008094 D6 86 62         [ 1]  124 	ld	a, (s_INITIALIZER - 1, x)
      008097 D7 00 04         [ 1]  125 	ld	(s_INITIALIZED - 1, x), a
      00809A 5A               [ 2]  126 	decw	x
      00809B 26 F7            [ 1]  127 	jrne	00003$
      00809D                        128 00004$:
                                    129 ; stm8_genXINIT() end
                                    130 	.area GSFINAL
      00809D CC 80 80         [ 2]  131 	jp	__sdcc_program_startup
                                    132 ;--------------------------------------------------------
                                    133 ; Home
                                    134 ;--------------------------------------------------------
                                    135 	.area HOME
                                    136 	.area HOME
      008080                        137 __sdcc_program_startup:
      008080 CC 85 24         [ 2]  138 	jp	_main
                                    139 ;	return from main will return to caller
                                    140 ;--------------------------------------------------------
                                    141 ; code
                                    142 ;--------------------------------------------------------
                                    143 	.area CODE
                                    144 ;	sensors.c: 15: void delayTenMicro (void) {
                                    145 ;	-----------------------------------------
                                    146 ;	 function delayTenMicro
                                    147 ;	-----------------------------------------
      0080A0                        148 _delayTenMicro:
                                    149 ;	sensors.c: 17: for (a = 0; a < 50; ++a)
      0080A0 A6 32            [ 1]  150 	ld	a, #0x32
      0080A2                        151 00104$:
                                    152 ;	sensors.c: 18: __asm__("nop");
      0080A2 9D               [ 1]  153 	nop
      0080A3 4A               [ 1]  154 	dec	a
                                    155 ;	sensors.c: 17: for (a = 0; a < 50; ++a)
      0080A4 4D               [ 1]  156 	tnz	a
      0080A5 26 FB            [ 1]  157 	jrne	00104$
      0080A7 81               [ 4]  158 	ret
                                    159 ;	sensors.c: 21: void InitializeSystemClock() {
                                    160 ;	-----------------------------------------
                                    161 ;	 function InitializeSystemClock
                                    162 ;	-----------------------------------------
      0080A8                        163 _InitializeSystemClock:
                                    164 ;	sensors.c: 22: CLK_ICKR = 0;                       //  Reset the Internal Clock Register.
      0080A8 AE 50 C0         [ 2]  165 	ldw	x, #0x50c0
      0080AB 7F               [ 1]  166 	clr	(x)
                                    167 ;	sensors.c: 23: CLK_ICKR = CLK_HSIEN;               //  Enable the HSI.
      0080AC AE 50 C0         [ 2]  168 	ldw	x, #0x50c0
      0080AF A6 01            [ 1]  169 	ld	a, #0x01
      0080B1 F7               [ 1]  170 	ld	(x), a
                                    171 ;	sensors.c: 24: CLK_ECKR = 0;                       //  Disable the external clock.
      0080B2 AE 50 C1         [ 2]  172 	ldw	x, #0x50c1
      0080B5 7F               [ 1]  173 	clr	(x)
                                    174 ;	sensors.c: 25: while ((CLK_ICKR & CLK_HSIRDY) == 0);       //  Wait for the HSI to be ready for use.
      0080B6                        175 00101$:
      0080B6 AE 50 C0         [ 2]  176 	ldw	x, #0x50c0
      0080B9 F6               [ 1]  177 	ld	a, (x)
      0080BA A5 02            [ 1]  178 	bcp	a, #0x02
      0080BC 27 F8            [ 1]  179 	jreq	00101$
                                    180 ;	sensors.c: 26: CLK_CKDIVR = 0;                     //  Ensure the clocks are running at full speed.
      0080BE AE 50 C6         [ 2]  181 	ldw	x, #0x50c6
      0080C1 7F               [ 1]  182 	clr	(x)
                                    183 ;	sensors.c: 27: CLK_PCKENR1 = 0xff;                 //  Enable all peripheral clocks.
      0080C2 AE 50 C7         [ 2]  184 	ldw	x, #0x50c7
      0080C5 A6 FF            [ 1]  185 	ld	a, #0xff
      0080C7 F7               [ 1]  186 	ld	(x), a
                                    187 ;	sensors.c: 28: CLK_PCKENR2 = 0xff;                 //  Ditto.
      0080C8 AE 50 CA         [ 2]  188 	ldw	x, #0x50ca
      0080CB A6 FF            [ 1]  189 	ld	a, #0xff
      0080CD F7               [ 1]  190 	ld	(x), a
                                    191 ;	sensors.c: 29: CLK_CCOR = 0;                       //  Turn off CCO.
      0080CE AE 50 C9         [ 2]  192 	ldw	x, #0x50c9
      0080D1 7F               [ 1]  193 	clr	(x)
                                    194 ;	sensors.c: 30: CLK_HSITRIMR = 0;                   //  Turn off any HSIU trimming.
      0080D2 AE 50 CC         [ 2]  195 	ldw	x, #0x50cc
      0080D5 7F               [ 1]  196 	clr	(x)
                                    197 ;	sensors.c: 31: CLK_SWIMCCR = 0;                    //  Set SWIM to run at clock / 2.
      0080D6 AE 50 CD         [ 2]  198 	ldw	x, #0x50cd
      0080D9 7F               [ 1]  199 	clr	(x)
                                    200 ;	sensors.c: 32: CLK_SWR = 0xe1;                     //  Use HSI as the clock source.
      0080DA AE 50 C4         [ 2]  201 	ldw	x, #0x50c4
      0080DD A6 E1            [ 1]  202 	ld	a, #0xe1
      0080DF F7               [ 1]  203 	ld	(x), a
                                    204 ;	sensors.c: 33: CLK_SWCR = 0;                       //  Reset the clock switch control register.
      0080E0 AE 50 C5         [ 2]  205 	ldw	x, #0x50c5
      0080E3 7F               [ 1]  206 	clr	(x)
                                    207 ;	sensors.c: 34: CLK_SWCR = CLK_SWEN;                //  Enable switching.
      0080E4 AE 50 C5         [ 2]  208 	ldw	x, #0x50c5
      0080E7 A6 02            [ 1]  209 	ld	a, #0x02
      0080E9 F7               [ 1]  210 	ld	(x), a
                                    211 ;	sensors.c: 35: while ((CLK_SWCR & CLK_SWBSY) != 0);        //  Pause while the clock switch is busy.
      0080EA                        212 00104$:
      0080EA AE 50 C5         [ 2]  213 	ldw	x, #0x50c5
      0080ED F6               [ 1]  214 	ld	a, (x)
      0080EE 44               [ 1]  215 	srl	a
      0080EF 25 F9            [ 1]  216 	jrc	00104$
      0080F1 81               [ 4]  217 	ret
                                    218 ;	sensors.c: 37: void delay (int time_ms) {
                                    219 ;	-----------------------------------------
                                    220 ;	 function delay
                                    221 ;	-----------------------------------------
      0080F2                        222 _delay:
      0080F2 52 0A            [ 2]  223 	sub	sp, #10
                                    224 ;	sensors.c: 39: for (x = 0; x < 1036*time_ms; ++x)
      0080F4 5F               [ 1]  225 	clrw	x
      0080F5 1F 03            [ 2]  226 	ldw	(0x03, sp), x
      0080F7 1F 01            [ 2]  227 	ldw	(0x01, sp), x
      0080F9 1E 0D            [ 2]  228 	ldw	x, (0x0d, sp)
      0080FB 89               [ 2]  229 	pushw	x
      0080FC 4B 0C            [ 1]  230 	push	#0x0c
      0080FE 4B 04            [ 1]  231 	push	#0x04
      008100 CD 86 0D         [ 4]  232 	call	__mulint
      008103 5B 04            [ 2]  233 	addw	sp, #4
      008105 1F 09            [ 2]  234 	ldw	(0x09, sp), x
      008107                        235 00103$:
      008107 16 09            [ 2]  236 	ldw	y, (0x09, sp)
      008109 17 07            [ 2]  237 	ldw	(0x07, sp), y
      00810B 7B 07            [ 1]  238 	ld	a, (0x07, sp)
      00810D 49               [ 1]  239 	rlc	a
      00810E 4F               [ 1]  240 	clr	a
      00810F A2 00            [ 1]  241 	sbc	a, #0x00
      008111 6B 06            [ 1]  242 	ld	(0x06, sp), a
      008113 6B 05            [ 1]  243 	ld	(0x05, sp), a
      008115 1E 03            [ 2]  244 	ldw	x, (0x03, sp)
      008117 13 07            [ 2]  245 	cpw	x, (0x07, sp)
      008119 7B 02            [ 1]  246 	ld	a, (0x02, sp)
      00811B 12 06            [ 1]  247 	sbc	a, (0x06, sp)
      00811D 7B 01            [ 1]  248 	ld	a, (0x01, sp)
      00811F 12 05            [ 1]  249 	sbc	a, (0x05, sp)
      008121 2E 17            [ 1]  250 	jrsge	00105$
                                    251 ;	sensors.c: 40: __asm__("nop");
      008123 9D               [ 1]  252 	nop
                                    253 ;	sensors.c: 39: for (x = 0; x < 1036*time_ms; ++x)
      008124 16 03            [ 2]  254 	ldw	y, (0x03, sp)
      008126 72 A9 00 01      [ 2]  255 	addw	y, #0x0001
      00812A 7B 02            [ 1]  256 	ld	a, (0x02, sp)
      00812C A9 00            [ 1]  257 	adc	a, #0x00
      00812E 97               [ 1]  258 	ld	xl, a
      00812F 7B 01            [ 1]  259 	ld	a, (0x01, sp)
      008131 A9 00            [ 1]  260 	adc	a, #0x00
      008133 95               [ 1]  261 	ld	xh, a
      008134 17 03            [ 2]  262 	ldw	(0x03, sp), y
      008136 1F 01            [ 2]  263 	ldw	(0x01, sp), x
      008138 20 CD            [ 2]  264 	jra	00103$
      00813A                        265 00105$:
      00813A 5B 0A            [ 2]  266 	addw	sp, #10
      00813C 81               [ 4]  267 	ret
                                    268 ;	sensors.c: 42: void i2c_read (unsigned char *x) {
                                    269 ;	-----------------------------------------
                                    270 ;	 function i2c_read
                                    271 ;	-----------------------------------------
      00813D                        272 _i2c_read:
                                    273 ;	sensors.c: 43: while ((I2C_SR1 & I2C_RXNE) == 0);
      00813D                        274 00101$:
      00813D AE 52 17         [ 2]  275 	ldw	x, #0x5217
      008140 F6               [ 1]  276 	ld	a, (x)
      008141 A5 40            [ 1]  277 	bcp	a, #0x40
      008143 27 F8            [ 1]  278 	jreq	00101$
                                    279 ;	sensors.c: 44: *x = I2C_DR;
      008145 16 03            [ 2]  280 	ldw	y, (0x03, sp)
      008147 AE 52 16         [ 2]  281 	ldw	x, #0x5216
      00814A F6               [ 1]  282 	ld	a, (x)
      00814B 90 F7            [ 1]  283 	ld	(y), a
      00814D 81               [ 4]  284 	ret
                                    285 ;	sensors.c: 46: void i2c_set_nak (void) {
                                    286 ;	-----------------------------------------
                                    287 ;	 function i2c_set_nak
                                    288 ;	-----------------------------------------
      00814E                        289 _i2c_set_nak:
                                    290 ;	sensors.c: 47: I2C_CR2 &= ~I2C_ACK;
      00814E AE 52 11         [ 2]  291 	ldw	x, #0x5211
      008151 F6               [ 1]  292 	ld	a, (x)
      008152 A4 FB            [ 1]  293 	and	a, #0xfb
      008154 F7               [ 1]  294 	ld	(x), a
      008155 81               [ 4]  295 	ret
                                    296 ;	sensors.c: 49: void i2c_set_stop (void) {
                                    297 ;	-----------------------------------------
                                    298 ;	 function i2c_set_stop
                                    299 ;	-----------------------------------------
      008156                        300 _i2c_set_stop:
                                    301 ;	sensors.c: 50: I2C_CR2 |= I2C_STOP;
      008156 AE 52 11         [ 2]  302 	ldw	x, #0x5211
      008159 F6               [ 1]  303 	ld	a, (x)
      00815A AA 02            [ 1]  304 	or	a, #0x02
      00815C F7               [ 1]  305 	ld	(x), a
      00815D 81               [ 4]  306 	ret
                                    307 ;	sensors.c: 52: void i2c_send_reg (UCHAR addr) {
                                    308 ;	-----------------------------------------
                                    309 ;	 function i2c_send_reg
                                    310 ;	-----------------------------------------
      00815E                        311 _i2c_send_reg:
      00815E 52 02            [ 2]  312 	sub	sp, #2
                                    313 ;	sensors.c: 54: reg = I2C_SR1;
      008160 AE 52 17         [ 2]  314 	ldw	x, #0x5217
      008163 F6               [ 1]  315 	ld	a, (x)
      008164 5F               [ 1]  316 	clrw	x
      008165 97               [ 1]  317 	ld	xl, a
      008166 1F 01            [ 2]  318 	ldw	(0x01, sp), x
                                    319 ;	sensors.c: 55: reg = I2C_SR3;
      008168 AE 52 19         [ 2]  320 	ldw	x, #0x5219
      00816B F6               [ 1]  321 	ld	a, (x)
      00816C 5F               [ 1]  322 	clrw	x
      00816D 97               [ 1]  323 	ld	xl, a
      00816E 1F 01            [ 2]  324 	ldw	(0x01, sp), x
                                    325 ;	sensors.c: 56: I2C_DR = addr;
      008170 AE 52 16         [ 2]  326 	ldw	x, #0x5216
      008173 7B 05            [ 1]  327 	ld	a, (0x05, sp)
      008175 F7               [ 1]  328 	ld	(x), a
                                    329 ;	sensors.c: 57: while ((I2C_SR1 & I2C_TXE) == 0);
      008176                        330 00101$:
      008176 AE 52 17         [ 2]  331 	ldw	x, #0x5217
      008179 F6               [ 1]  332 	ld	a, (x)
      00817A 48               [ 1]  333 	sll	a
      00817B 24 F9            [ 1]  334 	jrnc	00101$
      00817D 5B 02            [ 2]  335 	addw	sp, #2
      00817F 81               [ 4]  336 	ret
                                    337 ;	sensors.c: 61: void UARTPrintF (char *message) {
                                    338 ;	-----------------------------------------
                                    339 ;	 function UARTPrintF
                                    340 ;	-----------------------------------------
      008180                        341 _UARTPrintF:
                                    342 ;	sensors.c: 62: char *ch = message;
      008180 16 03            [ 2]  343 	ldw	y, (0x03, sp)
                                    344 ;	sensors.c: 63: while (*ch) {
      008182                        345 00104$:
      008182 90 F6            [ 1]  346 	ld	a, (y)
      008184 4D               [ 1]  347 	tnz	a
      008185 27 0F            [ 1]  348 	jreq	00107$
                                    349 ;	sensors.c: 64: UART1_DR = (unsigned char) *ch;     //  Put the next character into the data transmission register.
      008187 AE 52 31         [ 2]  350 	ldw	x, #0x5231
      00818A F7               [ 1]  351 	ld	(x), a
                                    352 ;	sensors.c: 65: while ((UART1_SR & SR_TXE) == 0);   //  Wait for transmission to complete.
      00818B                        353 00101$:
      00818B AE 52 30         [ 2]  354 	ldw	x, #0x5230
      00818E F6               [ 1]  355 	ld	a, (x)
      00818F 48               [ 1]  356 	sll	a
      008190 24 F9            [ 1]  357 	jrnc	00101$
                                    358 ;	sensors.c: 66: ch++;                               //  Grab the next character.
      008192 90 5C            [ 2]  359 	incw	y
      008194 20 EC            [ 2]  360 	jra	00104$
      008196                        361 00107$:
      008196 81               [ 4]  362 	ret
                                    363 ;	sensors.c: 70: void print_UCHAR_hex (unsigned char buffer) {
                                    364 ;	-----------------------------------------
                                    365 ;	 function print_UCHAR_hex
                                    366 ;	-----------------------------------------
      008197                        367 _print_UCHAR_hex:
      008197 52 0C            [ 2]  368 	sub	sp, #12
                                    369 ;	sensors.c: 73: a = (buffer >> 4);
      008199 7B 0F            [ 1]  370 	ld	a, (0x0f, sp)
      00819B 4E               [ 1]  371 	swap	a
      00819C A4 0F            [ 1]  372 	and	a, #0x0f
      00819E 5F               [ 1]  373 	clrw	x
      00819F 97               [ 1]  374 	ld	xl, a
                                    375 ;	sensors.c: 74: if (a > 9)
      0081A0 A3 00 09         [ 2]  376 	cpw	x, #0x0009
      0081A3 2D 07            [ 1]  377 	jrsle	00102$
                                    378 ;	sensors.c: 75: a = a + 'a' - 10;
      0081A5 1C 00 57         [ 2]  379 	addw	x, #0x0057
      0081A8 1F 01            [ 2]  380 	ldw	(0x01, sp), x
      0081AA 20 05            [ 2]  381 	jra	00103$
      0081AC                        382 00102$:
                                    383 ;	sensors.c: 77: a += '0';
      0081AC 1C 00 30         [ 2]  384 	addw	x, #0x0030
      0081AF 1F 01            [ 2]  385 	ldw	(0x01, sp), x
      0081B1                        386 00103$:
                                    387 ;	sensors.c: 78: b = buffer & 0x0f;
      0081B1 7B 0F            [ 1]  388 	ld	a, (0x0f, sp)
      0081B3 A4 0F            [ 1]  389 	and	a, #0x0f
      0081B5 5F               [ 1]  390 	clrw	x
      0081B6 97               [ 1]  391 	ld	xl, a
                                    392 ;	sensors.c: 79: if (b > 9)
      0081B7 A3 00 09         [ 2]  393 	cpw	x, #0x0009
      0081BA 2D 07            [ 1]  394 	jrsle	00105$
                                    395 ;	sensors.c: 80: b = b + 'a' - 10;
      0081BC 1C 00 57         [ 2]  396 	addw	x, #0x0057
      0081BF 1F 0B            [ 2]  397 	ldw	(0x0b, sp), x
      0081C1 20 05            [ 2]  398 	jra	00106$
      0081C3                        399 00105$:
                                    400 ;	sensors.c: 82: b += '0';
      0081C3 1C 00 30         [ 2]  401 	addw	x, #0x0030
      0081C6 1F 0B            [ 2]  402 	ldw	(0x0b, sp), x
      0081C8                        403 00106$:
                                    404 ;	sensors.c: 83: message[0] = a;
      0081C8 90 96            [ 1]  405 	ldw	y, sp
      0081CA 72 A9 00 03      [ 2]  406 	addw	y, #3
      0081CE 7B 02            [ 1]  407 	ld	a, (0x02, sp)
      0081D0 90 F7            [ 1]  408 	ld	(y), a
                                    409 ;	sensors.c: 84: message[1] = b;
      0081D2 93               [ 1]  410 	ldw	x, y
      0081D3 5C               [ 2]  411 	incw	x
      0081D4 7B 0C            [ 1]  412 	ld	a, (0x0c, sp)
      0081D6 F7               [ 1]  413 	ld	(x), a
                                    414 ;	sensors.c: 85: message[2] = 0;
      0081D7 93               [ 1]  415 	ldw	x, y
      0081D8 5C               [ 2]  416 	incw	x
      0081D9 5C               [ 2]  417 	incw	x
      0081DA 7F               [ 1]  418 	clr	(x)
                                    419 ;	sensors.c: 86: UARTPrintF (message);
      0081DB 90 89            [ 2]  420 	pushw	y
      0081DD CD 81 80         [ 4]  421 	call	_UARTPrintF
      0081E0 5B 02            [ 2]  422 	addw	sp, #2
      0081E2 5B 0C            [ 2]  423 	addw	sp, #12
      0081E4 81               [ 4]  424 	ret
                                    425 ;	sensors.c: 89: void i2c_send_address (UCHAR addr, UCHAR mode) {
                                    426 ;	-----------------------------------------
                                    427 ;	 function i2c_send_address
                                    428 ;	-----------------------------------------
      0081E5                        429 _i2c_send_address:
      0081E5 52 03            [ 2]  430 	sub	sp, #3
                                    431 ;	sensors.c: 91: reg = I2C_SR1;
      0081E7 AE 52 17         [ 2]  432 	ldw	x, #0x5217
      0081EA F6               [ 1]  433 	ld	a, (x)
      0081EB 5F               [ 1]  434 	clrw	x
      0081EC 97               [ 1]  435 	ld	xl, a
      0081ED 1F 01            [ 2]  436 	ldw	(0x01, sp), x
                                    437 ;	sensors.c: 92: I2C_DR = (addr << 1) | mode;
      0081EF 7B 06            [ 1]  438 	ld	a, (0x06, sp)
      0081F1 48               [ 1]  439 	sll	a
      0081F2 1A 07            [ 1]  440 	or	a, (0x07, sp)
      0081F4 AE 52 16         [ 2]  441 	ldw	x, #0x5216
      0081F7 F7               [ 1]  442 	ld	(x), a
                                    443 ;	sensors.c: 93: if (mode == I2C_READ) {
      0081F8 7B 07            [ 1]  444 	ld	a, (0x07, sp)
      0081FA A1 01            [ 1]  445 	cp	a, #0x01
      0081FC 26 06            [ 1]  446 	jrne	00127$
      0081FE A6 01            [ 1]  447 	ld	a, #0x01
      008200 6B 03            [ 1]  448 	ld	(0x03, sp), a
      008202 20 02            [ 2]  449 	jra	00128$
      008204                        450 00127$:
      008204 0F 03            [ 1]  451 	clr	(0x03, sp)
      008206                        452 00128$:
      008206 0D 03            [ 1]  453 	tnz	(0x03, sp)
      008208 27 08            [ 1]  454 	jreq	00103$
                                    455 ;	sensors.c: 94: I2C_OARL = 0;
      00820A AE 52 13         [ 2]  456 	ldw	x, #0x5213
      00820D 7F               [ 1]  457 	clr	(x)
                                    458 ;	sensors.c: 95: I2C_OARH = 0;
      00820E AE 52 14         [ 2]  459 	ldw	x, #0x5214
      008211 7F               [ 1]  460 	clr	(x)
                                    461 ;	sensors.c: 98: while ((I2C_SR1 & I2C_ADDR) == 0);
      008212                        462 00103$:
                                    463 ;	sensors.c: 91: reg = I2C_SR1;
      008212 AE 52 17         [ 2]  464 	ldw	x, #0x5217
      008215 F6               [ 1]  465 	ld	a, (x)
                                    466 ;	sensors.c: 98: while ((I2C_SR1 & I2C_ADDR) == 0);
      008216 A5 02            [ 1]  467 	bcp	a, #0x02
      008218 27 F8            [ 1]  468 	jreq	00103$
                                    469 ;	sensors.c: 99: if (mode == I2C_READ)
      00821A 0D 03            [ 1]  470 	tnz	(0x03, sp)
      00821C 27 06            [ 1]  471 	jreq	00108$
                                    472 ;	sensors.c: 100: UNSET (I2C_SR1, I2C_ADDR);
      00821E A4 FD            [ 1]  473 	and	a, #0xfd
      008220 AE 52 17         [ 2]  474 	ldw	x, #0x5217
      008223 F7               [ 1]  475 	ld	(x), a
      008224                        476 00108$:
      008224 5B 03            [ 2]  477 	addw	sp, #3
      008226 81               [ 4]  478 	ret
                                    479 ;	sensors.c: 103: void i2c_set_start_ack (void) {
                                    480 ;	-----------------------------------------
                                    481 ;	 function i2c_set_start_ack
                                    482 ;	-----------------------------------------
      008227                        483 _i2c_set_start_ack:
                                    484 ;	sensors.c: 104: I2C_CR2 = I2C_ACK | I2C_START;
      008227 AE 52 11         [ 2]  485 	ldw	x, #0x5211
      00822A A6 05            [ 1]  486 	ld	a, #0x05
      00822C F7               [ 1]  487 	ld	(x), a
                                    488 ;	sensors.c: 105: while ((I2C_SR1 & I2C_SB) == 0);
      00822D                        489 00101$:
      00822D AE 52 17         [ 2]  490 	ldw	x, #0x5217
      008230 F6               [ 1]  491 	ld	a, (x)
      008231 44               [ 1]  492 	srl	a
      008232 24 F9            [ 1]  493 	jrnc	00101$
      008234 81               [ 4]  494 	ret
                                    495 ;	sensors.c: 112: void print_byte_hex (unsigned char buffer) {
                                    496 ;	-----------------------------------------
                                    497 ;	 function print_byte_hex
                                    498 ;	-----------------------------------------
      008235                        499 _print_byte_hex:
      008235 52 0C            [ 2]  500 	sub	sp, #12
                                    501 ;	sensors.c: 115: a = (buffer >> 4);
      008237 7B 0F            [ 1]  502 	ld	a, (0x0f, sp)
      008239 4E               [ 1]  503 	swap	a
      00823A A4 0F            [ 1]  504 	and	a, #0x0f
      00823C 5F               [ 1]  505 	clrw	x
      00823D 97               [ 1]  506 	ld	xl, a
                                    507 ;	sensors.c: 116: if (a > 9)
      00823E A3 00 09         [ 2]  508 	cpw	x, #0x0009
      008241 2D 07            [ 1]  509 	jrsle	00102$
                                    510 ;	sensors.c: 117: a = a + 'a' - 10;
      008243 1C 00 57         [ 2]  511 	addw	x, #0x0057
      008246 1F 03            [ 2]  512 	ldw	(0x03, sp), x
      008248 20 05            [ 2]  513 	jra	00103$
      00824A                        514 00102$:
                                    515 ;	sensors.c: 119: a += '0'; 
      00824A 1C 00 30         [ 2]  516 	addw	x, #0x0030
      00824D 1F 03            [ 2]  517 	ldw	(0x03, sp), x
      00824F                        518 00103$:
                                    519 ;	sensors.c: 120: b = buffer & 0x0f;
      00824F 7B 0F            [ 1]  520 	ld	a, (0x0f, sp)
      008251 A4 0F            [ 1]  521 	and	a, #0x0f
      008253 5F               [ 1]  522 	clrw	x
      008254 97               [ 1]  523 	ld	xl, a
                                    524 ;	sensors.c: 121: if (b > 9)
      008255 A3 00 09         [ 2]  525 	cpw	x, #0x0009
      008258 2D 07            [ 1]  526 	jrsle	00105$
                                    527 ;	sensors.c: 122: b = b + 'a' - 10;
      00825A 1C 00 57         [ 2]  528 	addw	x, #0x0057
      00825D 1F 01            [ 2]  529 	ldw	(0x01, sp), x
      00825F 20 05            [ 2]  530 	jra	00106$
      008261                        531 00105$:
                                    532 ;	sensors.c: 124: b += '0'; 
      008261 1C 00 30         [ 2]  533 	addw	x, #0x0030
      008264 1F 01            [ 2]  534 	ldw	(0x01, sp), x
      008266                        535 00106$:
                                    536 ;	sensors.c: 125: message[0] = a;
      008266 90 96            [ 1]  537 	ldw	y, sp
      008268 72 A9 00 05      [ 2]  538 	addw	y, #5
      00826C 7B 04            [ 1]  539 	ld	a, (0x04, sp)
      00826E 90 F7            [ 1]  540 	ld	(y), a
                                    541 ;	sensors.c: 126: message[1] = b;
      008270 93               [ 1]  542 	ldw	x, y
      008271 5C               [ 2]  543 	incw	x
      008272 7B 02            [ 1]  544 	ld	a, (0x02, sp)
      008274 F7               [ 1]  545 	ld	(x), a
                                    546 ;	sensors.c: 127: message[2] = 0;
      008275 93               [ 1]  547 	ldw	x, y
      008276 5C               [ 2]  548 	incw	x
      008277 5C               [ 2]  549 	incw	x
      008278 7F               [ 1]  550 	clr	(x)
                                    551 ;	sensors.c: 128: UARTPrintF (message);
      008279 90 89            [ 2]  552 	pushw	y
      00827B CD 81 80         [ 4]  553 	call	_UARTPrintF
      00827E 5B 02            [ 2]  554 	addw	sp, #2
      008280 5B 0C            [ 2]  555 	addw	sp, #12
      008282 81               [ 4]  556 	ret
                                    557 ;	sensors.c: 132: unsigned char i2c_read_register (UCHAR addr, UCHAR rg) {
                                    558 ;	-----------------------------------------
                                    559 ;	 function i2c_read_register
                                    560 ;	-----------------------------------------
      008283                        561 _i2c_read_register:
      008283 52 02            [ 2]  562 	sub	sp, #2
                                    563 ;	sensors.c: 135: i2c_set_start_ack ();
      008285 CD 82 27         [ 4]  564 	call	_i2c_set_start_ack
                                    565 ;	sensors.c: 136: i2c_send_address (addr, I2C_WRITE);
      008288 4B 00            [ 1]  566 	push	#0x00
      00828A 7B 06            [ 1]  567 	ld	a, (0x06, sp)
      00828C 88               [ 1]  568 	push	a
      00828D CD 81 E5         [ 4]  569 	call	_i2c_send_address
      008290 5B 02            [ 2]  570 	addw	sp, #2
                                    571 ;	sensors.c: 137: i2c_send_reg (rg);
      008292 7B 06            [ 1]  572 	ld	a, (0x06, sp)
      008294 88               [ 1]  573 	push	a
      008295 CD 81 5E         [ 4]  574 	call	_i2c_send_reg
      008298 84               [ 1]  575 	pop	a
                                    576 ;	sensors.c: 138: i2c_set_start_ack ();
      008299 CD 82 27         [ 4]  577 	call	_i2c_set_start_ack
                                    578 ;	sensors.c: 139: i2c_send_address (addr, I2C_READ);
      00829C 4B 01            [ 1]  579 	push	#0x01
      00829E 7B 06            [ 1]  580 	ld	a, (0x06, sp)
      0082A0 88               [ 1]  581 	push	a
      0082A1 CD 81 E5         [ 4]  582 	call	_i2c_send_address
      0082A4 5B 02            [ 2]  583 	addw	sp, #2
                                    584 ;	sensors.c: 140: reg = I2C_SR1;
      0082A6 AE 52 17         [ 2]  585 	ldw	x, #0x5217
      0082A9 F6               [ 1]  586 	ld	a, (x)
      0082AA 6B 01            [ 1]  587 	ld	(0x01, sp), a
                                    588 ;	sensors.c: 141: reg = I2C_SR3;
      0082AC AE 52 19         [ 2]  589 	ldw	x, #0x5219
      0082AF F6               [ 1]  590 	ld	a, (x)
      0082B0 6B 01            [ 1]  591 	ld	(0x01, sp), a
                                    592 ;	sensors.c: 142: i2c_set_nak ();
      0082B2 CD 81 4E         [ 4]  593 	call	_i2c_set_nak
                                    594 ;	sensors.c: 143: i2c_set_stop ();
      0082B5 CD 81 56         [ 4]  595 	call	_i2c_set_stop
                                    596 ;	sensors.c: 144: i2c_read (&x);
      0082B8 96               [ 1]  597 	ldw	x, sp
      0082B9 5C               [ 2]  598 	incw	x
      0082BA 5C               [ 2]  599 	incw	x
      0082BB 89               [ 2]  600 	pushw	x
      0082BC CD 81 3D         [ 4]  601 	call	_i2c_read
      0082BF 5B 02            [ 2]  602 	addw	sp, #2
                                    603 ;	sensors.c: 145: return (x);
      0082C1 7B 02            [ 1]  604 	ld	a, (0x02, sp)
      0082C3 5B 02            [ 2]  605 	addw	sp, #2
      0082C5 81               [ 4]  606 	ret
                                    607 ;	sensors.c: 148: void InitializeI2C (void) {
                                    608 ;	-----------------------------------------
                                    609 ;	 function InitializeI2C
                                    610 ;	-----------------------------------------
      0082C6                        611 _InitializeI2C:
                                    612 ;	sensors.c: 149: I2C_CR1 = 0;   //  Disable I2C before configuration starts. PE bit is bit 0
      0082C6 AE 52 10         [ 2]  613 	ldw	x, #0x5210
      0082C9 7F               [ 1]  614 	clr	(x)
                                    615 ;	sensors.c: 153: I2C_FREQR = 16;                     //  Set the internal clock frequency (MHz).
      0082CA AE 52 12         [ 2]  616 	ldw	x, #0x5212
      0082CD A6 10            [ 1]  617 	ld	a, #0x10
      0082CF F7               [ 1]  618 	ld	(x), a
                                    619 ;	sensors.c: 154: UNSET (I2C_CCRH, I2C_FS);           //  I2C running is standard mode.
      0082D0 72 17 52 1C      [ 1]  620 	bres	0x521c, #7
                                    621 ;	sensors.c: 156: I2C_CCRL = 0xa0;                    //  SCL clock speed is 50 kHz.
      0082D4 AE 52 1B         [ 2]  622 	ldw	x, #0x521b
      0082D7 A6 A0            [ 1]  623 	ld	a, #0xa0
      0082D9 F7               [ 1]  624 	ld	(x), a
                                    625 ;	sensors.c: 158: I2C_CCRH &= 0x00;	// Clears lower 4 bits "CCR"
      0082DA AE 52 1C         [ 2]  626 	ldw	x, #0x521c
      0082DD 7F               [ 1]  627 	clr	(x)
                                    628 ;	sensors.c: 162: UNSET (I2C_OARH, I2C_ADDMODE);      //  7 bit address mode.
      0082DE 72 17 52 14      [ 1]  629 	bres	0x5214, #7
                                    630 ;	sensors.c: 163: SET (I2C_OARH, I2C_ADDCONF);        //  Docs say this must always be 1.
      0082E2 AE 52 14         [ 2]  631 	ldw	x, #0x5214
      0082E5 F6               [ 1]  632 	ld	a, (x)
      0082E6 AA 40            [ 1]  633 	or	a, #0x40
      0082E8 F7               [ 1]  634 	ld	(x), a
                                    635 ;	sensors.c: 167: I2C_TRISER = 17;
      0082E9 AE 52 1D         [ 2]  636 	ldw	x, #0x521d
      0082EC A6 11            [ 1]  637 	ld	a, #0x11
      0082EE F7               [ 1]  638 	ld	(x), a
                                    639 ;	sensors.c: 175: I2C_CR1 = I2C_PE;	// Enables port
      0082EF AE 52 10         [ 2]  640 	ldw	x, #0x5210
      0082F2 A6 01            [ 1]  641 	ld	a, #0x01
      0082F4 F7               [ 1]  642 	ld	(x), a
      0082F5 81               [ 4]  643 	ret
                                    644 ;	sensors.c: 181: void InitializeUART() {
                                    645 ;	-----------------------------------------
                                    646 ;	 function InitializeUART
                                    647 ;	-----------------------------------------
      0082F6                        648 _InitializeUART:
                                    649 ;	sensors.c: 191: UART1_CR1 = 0;
      0082F6 AE 52 34         [ 2]  650 	ldw	x, #0x5234
      0082F9 7F               [ 1]  651 	clr	(x)
                                    652 ;	sensors.c: 192: UART1_CR2 = 0;
      0082FA AE 52 35         [ 2]  653 	ldw	x, #0x5235
      0082FD 7F               [ 1]  654 	clr	(x)
                                    655 ;	sensors.c: 193: UART1_CR4 = 0;
      0082FE AE 52 37         [ 2]  656 	ldw	x, #0x5237
      008301 7F               [ 1]  657 	clr	(x)
                                    658 ;	sensors.c: 194: UART1_CR3 = 0;
      008302 AE 52 36         [ 2]  659 	ldw	x, #0x5236
      008305 7F               [ 1]  660 	clr	(x)
                                    661 ;	sensors.c: 195: UART1_CR5 = 0;
      008306 AE 52 38         [ 2]  662 	ldw	x, #0x5238
      008309 7F               [ 1]  663 	clr	(x)
                                    664 ;	sensors.c: 196: UART1_GTR = 0;
      00830A AE 52 39         [ 2]  665 	ldw	x, #0x5239
      00830D 7F               [ 1]  666 	clr	(x)
                                    667 ;	sensors.c: 197: UART1_PSCR = 0;
      00830E AE 52 3A         [ 2]  668 	ldw	x, #0x523a
      008311 7F               [ 1]  669 	clr	(x)
                                    670 ;	sensors.c: 201: UNSET (UART1_CR1, CR1_M);        //  8 Data bits.
      008312 AE 52 34         [ 2]  671 	ldw	x, #0x5234
      008315 F6               [ 1]  672 	ld	a, (x)
      008316 A4 EF            [ 1]  673 	and	a, #0xef
      008318 F7               [ 1]  674 	ld	(x), a
                                    675 ;	sensors.c: 202: UNSET (UART1_CR1, CR1_PCEN);     //  Disable parity.
      008319 AE 52 34         [ 2]  676 	ldw	x, #0x5234
      00831C F6               [ 1]  677 	ld	a, (x)
      00831D A4 FB            [ 1]  678 	and	a, #0xfb
      00831F F7               [ 1]  679 	ld	(x), a
                                    680 ;	sensors.c: 203: UNSET (UART1_CR3, CR3_STOPH);    //  1 stop bit.
      008320 AE 52 36         [ 2]  681 	ldw	x, #0x5236
      008323 F6               [ 1]  682 	ld	a, (x)
      008324 A4 DF            [ 1]  683 	and	a, #0xdf
      008326 F7               [ 1]  684 	ld	(x), a
                                    685 ;	sensors.c: 204: UNSET (UART1_CR3, CR3_STOPL);    //  1 stop bit.
      008327 AE 52 36         [ 2]  686 	ldw	x, #0x5236
      00832A F6               [ 1]  687 	ld	a, (x)
      00832B A4 EF            [ 1]  688 	and	a, #0xef
      00832D F7               [ 1]  689 	ld	(x), a
                                    690 ;	sensors.c: 205: UART1_BRR2 = 0x0a;      //  Set the baud rate registers to 115200 baud
      00832E AE 52 33         [ 2]  691 	ldw	x, #0x5233
      008331 A6 0A            [ 1]  692 	ld	a, #0x0a
      008333 F7               [ 1]  693 	ld	(x), a
                                    694 ;	sensors.c: 206: UART1_BRR1 = 0x08;      //  based upon a 16 MHz system clock.
      008334 AE 52 32         [ 2]  695 	ldw	x, #0x5232
      008337 A6 08            [ 1]  696 	ld	a, #0x08
      008339 F7               [ 1]  697 	ld	(x), a
                                    698 ;	sensors.c: 210: UNSET (UART1_CR2, CR2_TEN);      //  Disable transmit.
      00833A AE 52 35         [ 2]  699 	ldw	x, #0x5235
      00833D F6               [ 1]  700 	ld	a, (x)
      00833E A4 F7            [ 1]  701 	and	a, #0xf7
      008340 F7               [ 1]  702 	ld	(x), a
                                    703 ;	sensors.c: 211: UNSET (UART1_CR2, CR2_REN);      //  Disable receive.
      008341 AE 52 35         [ 2]  704 	ldw	x, #0x5235
      008344 F6               [ 1]  705 	ld	a, (x)
      008345 A4 FB            [ 1]  706 	and	a, #0xfb
      008347 F7               [ 1]  707 	ld	(x), a
                                    708 ;	sensors.c: 215: SET (UART1_CR3, CR3_CPOL);
      008348 AE 52 36         [ 2]  709 	ldw	x, #0x5236
      00834B F6               [ 1]  710 	ld	a, (x)
      00834C AA 04            [ 1]  711 	or	a, #0x04
      00834E F7               [ 1]  712 	ld	(x), a
                                    713 ;	sensors.c: 216: SET (UART1_CR3, CR3_CPHA);
      00834F AE 52 36         [ 2]  714 	ldw	x, #0x5236
      008352 F6               [ 1]  715 	ld	a, (x)
      008353 AA 02            [ 1]  716 	or	a, #0x02
      008355 F7               [ 1]  717 	ld	(x), a
                                    718 ;	sensors.c: 217: SET (UART1_CR3, CR3_LBCL);
      008356 72 10 52 36      [ 1]  719 	bset	0x5236, #0
                                    720 ;	sensors.c: 221: SET (UART1_CR2, CR2_TEN);
      00835A AE 52 35         [ 2]  721 	ldw	x, #0x5235
      00835D F6               [ 1]  722 	ld	a, (x)
      00835E AA 08            [ 1]  723 	or	a, #0x08
      008360 F7               [ 1]  724 	ld	(x), a
                                    725 ;	sensors.c: 222: SET (UART1_CR2, CR2_REN);
      008361 AE 52 35         [ 2]  726 	ldw	x, #0x5235
      008364 F6               [ 1]  727 	ld	a, (x)
      008365 AA 04            [ 1]  728 	or	a, #0x04
      008367 F7               [ 1]  729 	ld	(x), a
                                    730 ;	sensors.c: 223: UART1_CR3 = CR3_CLKEN;
      008368 AE 52 36         [ 2]  731 	ldw	x, #0x5236
      00836B A6 08            [ 1]  732 	ld	a, #0x08
      00836D F7               [ 1]  733 	ld	(x), a
      00836E 81               [ 4]  734 	ret
                                    735 ;	sensors.c: 251: void tm1637Init(void)
                                    736 ;	-----------------------------------------
                                    737 ;	 function tm1637Init
                                    738 ;	-----------------------------------------
      00836F                        739 _tm1637Init:
                                    740 ;	sensors.c: 253: tm1637SetBrightness(8);
      00836F 4B 08            [ 1]  741 	push	#0x08
      008371 CD 84 14         [ 4]  742 	call	_tm1637SetBrightness
      008374 84               [ 1]  743 	pop	a
      008375 81               [ 4]  744 	ret
                                    745 ;	sensors.c: 258: void tm1637DisplayDecimal(long TT,unsigned int displaySeparator)
                                    746 ;	-----------------------------------------
                                    747 ;	 function tm1637DisplayDecimal
                                    748 ;	-----------------------------------------
      008376                        749 _tm1637DisplayDecimal:
      008376 52 13            [ 2]  750 	sub	sp, #19
                                    751 ;	sensors.c: 260: unsigned int v = TT & 0x0000FFFF;
      008378 7B 19            [ 1]  752 	ld	a, (0x19, sp)
      00837A 97               [ 1]  753 	ld	xl, a
      00837B 7B 18            [ 1]  754 	ld	a, (0x18, sp)
      00837D 95               [ 1]  755 	ld	xh, a
      00837E 0F 0D            [ 1]  756 	clr	(0x0d, sp)
      008380 4F               [ 1]  757 	clr	a
      008381 1F 05            [ 2]  758 	ldw	(0x05, sp), x
                                    759 ;	sensors.c: 266: for (ii = 0; ii < 4; ++ii) {
      008383 96               [ 1]  760 	ldw	x, sp
      008384 5C               [ 2]  761 	incw	x
      008385 1F 12            [ 2]  762 	ldw	(0x12, sp), x
      008387 AE 85 FC         [ 2]  763 	ldw	x, #_segmentMap+0
      00838A 1F 09            [ 2]  764 	ldw	(0x09, sp), x
      00838C 90 5F            [ 1]  765 	clrw	y
      00838E                        766 00106$:
                                    767 ;	sensors.c: 267: digitArr[ii] = segmentMap[v % 10];
      00838E 93               [ 1]  768 	ldw	x, y
      00838F 72 FB 12         [ 2]  769 	addw	x, (0x12, sp)
      008392 1F 10            [ 2]  770 	ldw	(0x10, sp), x
      008394 90 89            [ 2]  771 	pushw	y
      008396 1E 07            [ 2]  772 	ldw	x, (0x07, sp)
      008398 90 AE 00 0A      [ 2]  773 	ldw	y, #0x000a
      00839C 65               [ 2]  774 	divw	x, y
      00839D 93               [ 1]  775 	ldw	x, y
      00839E 90 85            [ 2]  776 	popw	y
      0083A0 72 FB 09         [ 2]  777 	addw	x, (0x09, sp)
      0083A3 F6               [ 1]  778 	ld	a, (x)
      0083A4 1E 10            [ 2]  779 	ldw	x, (0x10, sp)
      0083A6 F7               [ 1]  780 	ld	(x), a
                                    781 ;	sensors.c: 268: if (ii == 2 && displaySeparator) {
      0083A7 90 A3 00 02      [ 2]  782 	cpw	y, #0x0002
      0083AB 26 0C            [ 1]  783 	jrne	00102$
      0083AD 1E 1A            [ 2]  784 	ldw	x, (0x1a, sp)
      0083AF 27 08            [ 1]  785 	jreq	00102$
                                    786 ;	sensors.c: 269: digitArr[ii] |= 1 << 7;
      0083B1 1E 10            [ 2]  787 	ldw	x, (0x10, sp)
      0083B3 F6               [ 1]  788 	ld	a, (x)
      0083B4 AA 80            [ 1]  789 	or	a, #0x80
      0083B6 1E 10            [ 2]  790 	ldw	x, (0x10, sp)
      0083B8 F7               [ 1]  791 	ld	(x), a
      0083B9                        792 00102$:
                                    793 ;	sensors.c: 271: v /= 10;
      0083B9 90 89            [ 2]  794 	pushw	y
      0083BB 1E 07            [ 2]  795 	ldw	x, (0x07, sp)
      0083BD 90 AE 00 0A      [ 2]  796 	ldw	y, #0x000a
      0083C1 65               [ 2]  797 	divw	x, y
      0083C2 90 85            [ 2]  798 	popw	y
      0083C4 1F 05            [ 2]  799 	ldw	(0x05, sp), x
                                    800 ;	sensors.c: 266: for (ii = 0; ii < 4; ++ii) {
      0083C6 90 5C            [ 2]  801 	incw	y
      0083C8 90 A3 00 04      [ 2]  802 	cpw	y, #0x0004
      0083CC 25 C0            [ 1]  803 	jrc	00106$
                                    804 ;	sensors.c: 274: _tm1637Start();
      0083CE CD 84 26         [ 4]  805 	call	__tm1637Start
                                    806 ;	sensors.c: 275: _tm1637WriteByte(0x40);
      0083D1 4B 40            [ 1]  807 	push	#0x40
      0083D3 CD 84 7A         [ 4]  808 	call	__tm1637WriteByte
      0083D6 84               [ 1]  809 	pop	a
                                    810 ;	sensors.c: 276: _tm1637ReadResult();
      0083D7 CD 84 5F         [ 4]  811 	call	__tm1637ReadResult
                                    812 ;	sensors.c: 277: _tm1637Stop();
      0083DA CD 84 38         [ 4]  813 	call	__tm1637Stop
                                    814 ;	sensors.c: 279: _tm1637Start();
      0083DD CD 84 26         [ 4]  815 	call	__tm1637Start
                                    816 ;	sensors.c: 280: _tm1637WriteByte(0xc0);
      0083E0 4B C0            [ 1]  817 	push	#0xc0
      0083E2 CD 84 7A         [ 4]  818 	call	__tm1637WriteByte
      0083E5 84               [ 1]  819 	pop	a
                                    820 ;	sensors.c: 281: _tm1637ReadResult();
      0083E6 CD 84 5F         [ 4]  821 	call	__tm1637ReadResult
                                    822 ;	sensors.c: 283: for (ii = 0; ii < 4; ++ii) {
      0083E9 5F               [ 1]  823 	clrw	x
      0083EA 1F 07            [ 2]  824 	ldw	(0x07, sp), x
      0083EC                        825 00108$:
                                    826 ;	sensors.c: 284: _tm1637WriteByte(digitArr[3 - ii]);
      0083EC 7B 08            [ 1]  827 	ld	a, (0x08, sp)
      0083EE 6B 0B            [ 1]  828 	ld	(0x0b, sp), a
      0083F0 A6 03            [ 1]  829 	ld	a, #0x03
      0083F2 10 0B            [ 1]  830 	sub	a, (0x0b, sp)
      0083F4 5F               [ 1]  831 	clrw	x
      0083F5 97               [ 1]  832 	ld	xl, a
      0083F6 72 FB 12         [ 2]  833 	addw	x, (0x12, sp)
      0083F9 F6               [ 1]  834 	ld	a, (x)
      0083FA 88               [ 1]  835 	push	a
      0083FB CD 84 7A         [ 4]  836 	call	__tm1637WriteByte
      0083FE 84               [ 1]  837 	pop	a
                                    838 ;	sensors.c: 285: _tm1637ReadResult();
      0083FF CD 84 5F         [ 4]  839 	call	__tm1637ReadResult
                                    840 ;	sensors.c: 283: for (ii = 0; ii < 4; ++ii) {
      008402 1E 07            [ 2]  841 	ldw	x, (0x07, sp)
      008404 5C               [ 2]  842 	incw	x
      008405 1F 07            [ 2]  843 	ldw	(0x07, sp), x
      008407 1E 07            [ 2]  844 	ldw	x, (0x07, sp)
      008409 A3 00 04         [ 2]  845 	cpw	x, #0x0004
      00840C 25 DE            [ 1]  846 	jrc	00108$
                                    847 ;	sensors.c: 288: _tm1637Stop();
      00840E CD 84 38         [ 4]  848 	call	__tm1637Stop
      008411 5B 13            [ 2]  849 	addw	sp, #19
      008413 81               [ 4]  850 	ret
                                    851 ;	sensors.c: 293: void tm1637SetBrightness(char brightness)
                                    852 ;	-----------------------------------------
                                    853 ;	 function tm1637SetBrightness
                                    854 ;	-----------------------------------------
      008414                        855 _tm1637SetBrightness:
                                    856 ;	sensors.c: 300: _tm1637Start();
      008414 CD 84 26         [ 4]  857 	call	__tm1637Start
                                    858 ;	sensors.c: 301: _tm1637WriteByte(0x87 + brightness);
      008417 7B 03            [ 1]  859 	ld	a, (0x03, sp)
      008419 AB 87            [ 1]  860 	add	a, #0x87
      00841B 88               [ 1]  861 	push	a
      00841C CD 84 7A         [ 4]  862 	call	__tm1637WriteByte
      00841F 84               [ 1]  863 	pop	a
                                    864 ;	sensors.c: 302: _tm1637ReadResult();
      008420 CD 84 5F         [ 4]  865 	call	__tm1637ReadResult
                                    866 ;	sensors.c: 303: _tm1637Stop();
      008423 CC 84 38         [ 2]  867 	jp	__tm1637Stop
                                    868 ;	sensors.c: 306: void _tm1637Start(void)
                                    869 ;	-----------------------------------------
                                    870 ;	 function _tm1637Start
                                    871 ;	-----------------------------------------
      008426                        872 __tm1637Start:
                                    873 ;	sensors.c: 308: _tm1637ClkHigh();
      008426 CD 84 B8         [ 4]  874 	call	__tm1637ClkHigh
                                    875 ;	sensors.c: 309: _tm1637DioHigh();
      008429 CD 84 C8         [ 4]  876 	call	__tm1637DioHigh
                                    877 ;	sensors.c: 310: delay(5);
      00842C 4B 05            [ 1]  878 	push	#0x05
      00842E 4B 00            [ 1]  879 	push	#0x00
      008430 CD 80 F2         [ 4]  880 	call	_delay
      008433 5B 02            [ 2]  881 	addw	sp, #2
                                    882 ;	sensors.c: 311: _tm1637DioLow();
      008435 CC 84 D0         [ 2]  883 	jp	__tm1637DioLow
                                    884 ;	sensors.c: 314: void _tm1637Stop(void)
                                    885 ;	-----------------------------------------
                                    886 ;	 function _tm1637Stop
                                    887 ;	-----------------------------------------
      008438                        888 __tm1637Stop:
                                    889 ;	sensors.c: 316: _tm1637ClkLow();
      008438 CD 84 C0         [ 4]  890 	call	__tm1637ClkLow
                                    891 ;	sensors.c: 317: delay(5);
      00843B 4B 05            [ 1]  892 	push	#0x05
      00843D 4B 00            [ 1]  893 	push	#0x00
      00843F CD 80 F2         [ 4]  894 	call	_delay
      008442 5B 02            [ 2]  895 	addw	sp, #2
                                    896 ;	sensors.c: 318: _tm1637DioLow();
      008444 CD 84 D0         [ 4]  897 	call	__tm1637DioLow
                                    898 ;	sensors.c: 319: delay(5);
      008447 4B 05            [ 1]  899 	push	#0x05
      008449 4B 00            [ 1]  900 	push	#0x00
      00844B CD 80 F2         [ 4]  901 	call	_delay
      00844E 5B 02            [ 2]  902 	addw	sp, #2
                                    903 ;	sensors.c: 320: _tm1637ClkHigh();
      008450 CD 84 B8         [ 4]  904 	call	__tm1637ClkHigh
                                    905 ;	sensors.c: 321: delay(5);
      008453 4B 05            [ 1]  906 	push	#0x05
      008455 4B 00            [ 1]  907 	push	#0x00
      008457 CD 80 F2         [ 4]  908 	call	_delay
      00845A 5B 02            [ 2]  909 	addw	sp, #2
                                    910 ;	sensors.c: 322: _tm1637DioHigh();
      00845C CC 84 C8         [ 2]  911 	jp	__tm1637DioHigh
                                    912 ;	sensors.c: 325: void _tm1637ReadResult(void)
                                    913 ;	-----------------------------------------
                                    914 ;	 function _tm1637ReadResult
                                    915 ;	-----------------------------------------
      00845F                        916 __tm1637ReadResult:
                                    917 ;	sensors.c: 327: _tm1637ClkLow();
      00845F CD 84 C0         [ 4]  918 	call	__tm1637ClkLow
                                    919 ;	sensors.c: 328: delay(5);
      008462 4B 05            [ 1]  920 	push	#0x05
      008464 4B 00            [ 1]  921 	push	#0x00
      008466 CD 80 F2         [ 4]  922 	call	_delay
      008469 5B 02            [ 2]  923 	addw	sp, #2
                                    924 ;	sensors.c: 330: _tm1637ClkHigh();
      00846B CD 84 B8         [ 4]  925 	call	__tm1637ClkHigh
                                    926 ;	sensors.c: 331: delay(5);
      00846E 4B 05            [ 1]  927 	push	#0x05
      008470 4B 00            [ 1]  928 	push	#0x00
      008472 CD 80 F2         [ 4]  929 	call	_delay
      008475 5B 02            [ 2]  930 	addw	sp, #2
                                    931 ;	sensors.c: 332: _tm1637ClkLow();
      008477 CC 84 C0         [ 2]  932 	jp	__tm1637ClkLow
                                    933 ;	sensors.c: 335: void _tm1637WriteByte(unsigned char b)
                                    934 ;	-----------------------------------------
                                    935 ;	 function _tm1637WriteByte
                                    936 ;	-----------------------------------------
      00847A                        937 __tm1637WriteByte:
      00847A 52 02            [ 2]  938 	sub	sp, #2
                                    939 ;	sensors.c: 337: for (ii = 0; ii < 8; ++ii) {
      00847C 5F               [ 1]  940 	clrw	x
      00847D 1F 01            [ 2]  941 	ldw	(0x01, sp), x
      00847F                        942 00105$:
                                    943 ;	sensors.c: 338: _tm1637ClkLow();
      00847F CD 84 C0         [ 4]  944 	call	__tm1637ClkLow
                                    945 ;	sensors.c: 339: if (b & 0x01) {
      008482 7B 05            [ 1]  946 	ld	a, (0x05, sp)
      008484 44               [ 1]  947 	srl	a
      008485 24 05            [ 1]  948 	jrnc	00102$
                                    949 ;	sensors.c: 340: _tm1637DioHigh();
      008487 CD 84 C8         [ 4]  950 	call	__tm1637DioHigh
      00848A 20 03            [ 2]  951 	jra	00103$
      00848C                        952 00102$:
                                    953 ;	sensors.c: 343: _tm1637DioLow();
      00848C CD 84 D0         [ 4]  954 	call	__tm1637DioLow
      00848F                        955 00103$:
                                    956 ;	sensors.c: 345: delay(15);
      00848F 4B 0F            [ 1]  957 	push	#0x0f
      008491 4B 00            [ 1]  958 	push	#0x00
      008493 CD 80 F2         [ 4]  959 	call	_delay
      008496 5B 02            [ 2]  960 	addw	sp, #2
                                    961 ;	sensors.c: 346: b >>= 1;
      008498 7B 05            [ 1]  962 	ld	a, (0x05, sp)
      00849A 44               [ 1]  963 	srl	a
      00849B 6B 05            [ 1]  964 	ld	(0x05, sp), a
                                    965 ;	sensors.c: 347: _tm1637ClkHigh();
      00849D CD 84 B8         [ 4]  966 	call	__tm1637ClkHigh
                                    967 ;	sensors.c: 348: delay(15);
      0084A0 4B 0F            [ 1]  968 	push	#0x0f
      0084A2 4B 00            [ 1]  969 	push	#0x00
      0084A4 CD 80 F2         [ 4]  970 	call	_delay
      0084A7 5B 02            [ 2]  971 	addw	sp, #2
                                    972 ;	sensors.c: 337: for (ii = 0; ii < 8; ++ii) {
      0084A9 1E 01            [ 2]  973 	ldw	x, (0x01, sp)
      0084AB 5C               [ 2]  974 	incw	x
      0084AC 1F 01            [ 2]  975 	ldw	(0x01, sp), x
      0084AE 1E 01            [ 2]  976 	ldw	x, (0x01, sp)
      0084B0 A3 00 08         [ 2]  977 	cpw	x, #0x0008
      0084B3 2F CA            [ 1]  978 	jrslt	00105$
      0084B5 5B 02            [ 2]  979 	addw	sp, #2
      0084B7 81               [ 4]  980 	ret
                                    981 ;	sensors.c: 354: void _tm1637ClkHigh(void)
                                    982 ;	-----------------------------------------
                                    983 ;	 function _tm1637ClkHigh
                                    984 ;	-----------------------------------------
      0084B8                        985 __tm1637ClkHigh:
                                    986 ;	sensors.c: 359: PD_ODR |= 1 << 2;
      0084B8 AE 50 0F         [ 2]  987 	ldw	x, #0x500f
      0084BB F6               [ 1]  988 	ld	a, (x)
      0084BC AA 04            [ 1]  989 	or	a, #0x04
      0084BE F7               [ 1]  990 	ld	(x), a
      0084BF 81               [ 4]  991 	ret
                                    992 ;	sensors.c: 362: void _tm1637ClkLow(void)
                                    993 ;	-----------------------------------------
                                    994 ;	 function _tm1637ClkLow
                                    995 ;	-----------------------------------------
      0084C0                        996 __tm1637ClkLow:
                                    997 ;	sensors.c: 366: PD_ODR &= ~(1 << 2);
      0084C0 AE 50 0F         [ 2]  998 	ldw	x, #0x500f
      0084C3 F6               [ 1]  999 	ld	a, (x)
      0084C4 A4 FB            [ 1] 1000 	and	a, #0xfb
      0084C6 F7               [ 1] 1001 	ld	(x), a
      0084C7 81               [ 4] 1002 	ret
                                   1003 ;	sensors.c: 372: void _tm1637DioHigh(void)
                                   1004 ;	-----------------------------------------
                                   1005 ;	 function _tm1637DioHigh
                                   1006 ;	-----------------------------------------
      0084C8                       1007 __tm1637DioHigh:
                                   1008 ;	sensors.c: 376: PD_ODR |= 1 << 3;
      0084C8 AE 50 0F         [ 2] 1009 	ldw	x, #0x500f
      0084CB F6               [ 1] 1010 	ld	a, (x)
      0084CC AA 08            [ 1] 1011 	or	a, #0x08
      0084CE F7               [ 1] 1012 	ld	(x), a
      0084CF 81               [ 4] 1013 	ret
                                   1014 ;	sensors.c: 380: void _tm1637DioLow(void)
                                   1015 ;	-----------------------------------------
                                   1016 ;	 function _tm1637DioLow
                                   1017 ;	-----------------------------------------
      0084D0                       1018 __tm1637DioLow:
                                   1019 ;	sensors.c: 382: PD_ODR &= ~(1 << 3);
      0084D0 AE 50 0F         [ 2] 1020 	ldw	x, #0x500f
      0084D3 F6               [ 1] 1021 	ld	a, (x)
      0084D4 A4 F7            [ 1] 1022 	and	a, #0xf7
      0084D6 F7               [ 1] 1023 	ld	(x), a
      0084D7 81               [ 4] 1024 	ret
                                   1025 ;	sensors.c: 391: unsigned int clock(void)
                                   1026 ;	-----------------------------------------
                                   1027 ;	 function clock
                                   1028 ;	-----------------------------------------
      0084D8                       1029 _clock:
      0084D8 52 03            [ 2] 1030 	sub	sp, #3
                                   1031 ;	sensors.c: 393: unsigned char h = TIM1_CNTRH; //origineel PCNTRH
      0084DA AE 52 5E         [ 2] 1032 	ldw	x, #0x525e
      0084DD F6               [ 1] 1033 	ld	a, (x)
                                   1034 ;	sensors.c: 394: unsigned char l = TIM1_CNTRL;
      0084DE AE 52 5F         [ 2] 1035 	ldw	x, #0x525f
      0084E1 88               [ 1] 1036 	push	a
      0084E2 F6               [ 1] 1037 	ld	a, (x)
      0084E3 6B 02            [ 1] 1038 	ld	(0x02, sp), a
      0084E5 84               [ 1] 1039 	pop	a
                                   1040 ;	sensors.c: 395: return((unsigned int)(h) << 8 | l);
      0084E6 5F               [ 1] 1041 	clrw	x
      0084E7 97               [ 1] 1042 	ld	xl, a
      0084E8 58               [ 2] 1043 	sllw	x
      0084E9 58               [ 2] 1044 	sllw	x
      0084EA 58               [ 2] 1045 	sllw	x
      0084EB 58               [ 2] 1046 	sllw	x
      0084EC 58               [ 2] 1047 	sllw	x
      0084ED 58               [ 2] 1048 	sllw	x
      0084EE 58               [ 2] 1049 	sllw	x
      0084EF 58               [ 2] 1050 	sllw	x
      0084F0 7B 01            [ 1] 1051 	ld	a, (0x01, sp)
      0084F2 6B 03            [ 1] 1052 	ld	(0x03, sp), a
      0084F4 0F 02            [ 1] 1053 	clr	(0x02, sp)
      0084F6 9F               [ 1] 1054 	ld	a, xl
      0084F7 1A 03            [ 1] 1055 	or	a, (0x03, sp)
      0084F9 97               [ 1] 1056 	ld	xl, a
      0084FA 9E               [ 1] 1057 	ld	a, xh
      0084FB 1A 02            [ 1] 1058 	or	a, (0x02, sp)
      0084FD 95               [ 1] 1059 	ld	xh, a
      0084FE 5B 03            [ 2] 1060 	addw	sp, #3
      008500 81               [ 4] 1061 	ret
                                   1062 ;	sensors.c: 429: void timer_isr(void) __interrupt(TIM4_ISR) {
                                   1063 ;	-----------------------------------------
                                   1064 ;	 function timer_isr
                                   1065 ;	-----------------------------------------
      008501                       1066 _timer_isr:
                                   1067 ;	sensors.c: 430: if (++internteller > 260) {
      008501 CE 00 01         [ 2] 1068 	ldw	x, _internteller+0
      008504 5C               [ 2] 1069 	incw	x
      008505 CF 00 01         [ 2] 1070 	ldw	_internteller+0, x
      008508 A3 01 04         [ 2] 1071 	cpw	x, #0x0104
      00850B 23 0F            [ 2] 1072 	jrule	00102$
                                   1073 ;	sensors.c: 431: internteller=0;
      00850D 72 5F 00 02      [ 1] 1074 	clr	_internteller+1
      008511 72 5F 00 01      [ 1] 1075 	clr	_internteller+0
                                   1076 ;	sensors.c: 432: ++seconden;
      008515 CE 00 03         [ 2] 1077 	ldw	x, _seconden+0
      008518 5C               [ 2] 1078 	incw	x
      008519 CF 00 03         [ 2] 1079 	ldw	_seconden+0, x
      00851C                       1080 00102$:
                                   1081 ;	sensors.c: 434: TIM4_SR &= ~(TIMx_UIF); //update interrupt
      00851C AE 53 44         [ 2] 1082 	ldw	x, #0x5344
      00851F F6               [ 1] 1083 	ld	a, (x)
      008520 A4 FE            [ 1] 1084 	and	a, #0xfe
      008522 F7               [ 1] 1085 	ld	(x), a
      008523 80               [11] 1086 	iret
                                   1087 ;	sensors.c: 441: int main () {
                                   1088 ;	-----------------------------------------
                                   1089 ;	 function main
                                   1090 ;	-----------------------------------------
      008524                       1091 _main:
      008524 52 06            [ 2] 1092 	sub	sp, #6
                                   1093 ;	sensors.c: 446: unsigned int val=0;
      008526 5F               [ 1] 1094 	clrw	x
      008527 1F 05            [ 2] 1095 	ldw	(0x05, sp), x
                                   1096 ;	sensors.c: 448: InitializeSystemClock();
      008529 CD 80 A8         [ 4] 1097 	call	_InitializeSystemClock
                                   1098 ;	sensors.c: 450: PD_DDR = (1 << 3) | (1 << 2); // output mode
      00852C AE 50 11         [ 2] 1099 	ldw	x, #0x5011
      00852F A6 0C            [ 1] 1100 	ld	a, #0x0c
      008531 F7               [ 1] 1101 	ld	(x), a
                                   1102 ;	sensors.c: 451: PD_CR1 = (1 << 3) | (1 << 2); // push-pull
      008532 AE 50 12         [ 2] 1103 	ldw	x, #0x5012
      008535 A6 0C            [ 1] 1104 	ld	a, #0x0c
      008537 F7               [ 1] 1105 	ld	(x), a
                                   1106 ;	sensors.c: 452: PD_CR2 = (1 << 3) | (1 << 2); // up to 10MHz speed
      008538 AE 50 13         [ 2] 1107 	ldw	x, #0x5013
      00853B A6 0C            [ 1] 1108 	ld	a, #0x0c
      00853D F7               [ 1] 1109 	ld	(x), a
                                   1110 ;	sensors.c: 456: TIM1_PSCRH = 0x3e;
      00853E AE 52 60         [ 2] 1111 	ldw	x, #0x5260
      008541 A6 3E            [ 1] 1112 	ld	a, #0x3e
      008543 F7               [ 1] 1113 	ld	(x), a
                                   1114 ;	sensors.c: 457: TIM1_PSCRL = 0x80;
      008544 AE 52 61         [ 2] 1115 	ldw	x, #0x5261
      008547 A6 80            [ 1] 1116 	ld	a, #0x80
      008549 F7               [ 1] 1117 	ld	(x), a
                                   1118 ;	sensors.c: 459: tm1637Init();
      00854A CD 83 6F         [ 4] 1119 	call	_tm1637Init
                                   1120 ;	sensors.c: 461: InitializeUART();
      00854D CD 82 F6         [ 4] 1121 	call	_InitializeUART
                                   1122 ;	sensors.c: 464: __asm__("rim");
      008550 9A               [ 1] 1123 	rim
                                   1124 ;	sensors.c: 467: TIM4_PSCR = 0b00000111;
      008551 AE 53 47         [ 2] 1125 	ldw	x, #0x5347
      008554 A6 07            [ 1] 1126 	ld	a, #0x07
      008556 F7               [ 1] 1127 	ld	(x), a
                                   1128 ;	sensors.c: 469: TIM4_ARR = 239;
      008557 AE 53 48         [ 2] 1129 	ldw	x, #0x5348
      00855A A6 EF            [ 1] 1130 	ld	a, #0xef
      00855C F7               [ 1] 1131 	ld	(x), a
                                   1132 ;	sensors.c: 471: TIM4_IER |= TIMx_UIE;// Enable Update Interrupt
      00855D 72 10 53 43      [ 1] 1133 	bset	0x5343, #0
                                   1134 ;	sensors.c: 473: TIM4_CR1 |= TIMx_CEN; // Enable TIM4
      008561 72 10 53 40      [ 1] 1135 	bset	0x5340, #0
                                   1136 ;	sensors.c: 478: while (1) {
      008565                       1137 00109$:
                                   1138 ;	sensors.c: 483: ADC_CR1 |= ADC_ADON; // ADC ON
      008565 72 10 54 01      [ 1] 1139 	bset	0x5401, #0
                                   1140 ;	sensors.c: 484: ADC_CSR |= ((0x0F)&2); // select channel = 2 = PC4
      008569 AE 54 00         [ 2] 1141 	ldw	x, #0x5400
      00856C F6               [ 1] 1142 	ld	a, (x)
      00856D AA 02            [ 1] 1143 	or	a, #0x02
      00856F F7               [ 1] 1144 	ld	(x), a
                                   1145 ;	sensors.c: 485: ADC_CR2 |= ADC_ALIGN; // Right Aligned Data
      008570 AE 54 02         [ 2] 1146 	ldw	x, #0x5402
      008573 F6               [ 1] 1147 	ld	a, (x)
      008574 AA 08            [ 1] 1148 	or	a, #0x08
      008576 F7               [ 1] 1149 	ld	(x), a
                                   1150 ;	sensors.c: 486: ADC_CR1 |= ADC_ADON; // start conversion 
      008577 72 10 54 01      [ 1] 1151 	bset	0x5401, #0
                                   1152 ;	sensors.c: 487: while(((ADC_CSR)&(1<<7))== 0); // Wait till EOC
      00857B                       1153 00101$:
      00857B AE 54 00         [ 2] 1154 	ldw	x, #0x5400
      00857E F6               [ 1] 1155 	ld	a, (x)
      00857F 48               [ 1] 1156 	sll	a
      008580 24 F9            [ 1] 1157 	jrnc	00101$
                                   1158 ;	sensors.c: 489: val |= (unsigned int)ADC_DRL;
      008582 AE 54 05         [ 2] 1159 	ldw	x, #0x5405
      008585 F6               [ 1] 1160 	ld	a, (x)
      008586 5F               [ 1] 1161 	clrw	x
      008587 97               [ 1] 1162 	ld	xl, a
      008588 1A 06            [ 1] 1163 	or	a, (0x06, sp)
      00858A 6B 04            [ 1] 1164 	ld	(0x04, sp), a
      00858C 9E               [ 1] 1165 	ld	a, xh
      00858D 1A 05            [ 1] 1166 	or	a, (0x05, sp)
      00858F 6B 01            [ 1] 1167 	ld	(0x01, sp), a
      008591 7B 04            [ 1] 1168 	ld	a, (0x04, sp)
      008593 6B 02            [ 1] 1169 	ld	(0x02, sp), a
                                   1170 ;	sensors.c: 491: val |= (unsigned int)ADC_DRH<<8;
      008595 AE 54 04         [ 2] 1171 	ldw	x, #0x5404
      008598 F6               [ 1] 1172 	ld	a, (x)
      008599 5F               [ 1] 1173 	clrw	x
      00859A 97               [ 1] 1174 	ld	xl, a
      00859B 58               [ 2] 1175 	sllw	x
      00859C 58               [ 2] 1176 	sllw	x
      00859D 58               [ 2] 1177 	sllw	x
      00859E 58               [ 2] 1178 	sllw	x
      00859F 58               [ 2] 1179 	sllw	x
      0085A0 58               [ 2] 1180 	sllw	x
      0085A1 58               [ 2] 1181 	sllw	x
      0085A2 58               [ 2] 1182 	sllw	x
      0085A3 9F               [ 1] 1183 	ld	a, xl
      0085A4 1A 02            [ 1] 1184 	or	a, (0x02, sp)
      0085A6 90 97            [ 1] 1185 	ld	yl, a
      0085A8 9E               [ 1] 1186 	ld	a, xh
      0085A9 1A 01            [ 1] 1187 	or	a, (0x01, sp)
      0085AB 90 95            [ 1] 1188 	ld	yh, a
                                   1189 ;	sensors.c: 492: ADC_CR1 &= ~(1<<0); // ADC Stop Conversion
      0085AD AE 54 01         [ 2] 1190 	ldw	x, #0x5401
      0085B0 F6               [ 1] 1191 	ld	a, (x)
      0085B1 A4 FE            [ 1] 1192 	and	a, #0xfe
      0085B3 F7               [ 1] 1193 	ld	(x), a
                                   1194 ;	sensors.c: 493: readValue = val & 0x03ff;
      0085B4 90 9E            [ 1] 1195 	ld	a, yh
      0085B6 A4 03            [ 1] 1196 	and	a, #0x03
      0085B8 90 95            [ 1] 1197 	ld	yh, a
                                   1198 ;	sensors.c: 494: if (readValue > minValue)
      0085BA 90 A3 00 0A      [ 2] 1199 	cpw	y, #0x000a
      0085BE 2D 06            [ 1] 1200 	jrsle	00105$
                                   1201 ;	sensors.c: 496: TIM1_CR1 = 0x01; // enable timer
      0085C0 AE 52 50         [ 2] 1202 	ldw	x, #0x5250
      0085C3 A6 01            [ 1] 1203 	ld	a, #0x01
      0085C5 F7               [ 1] 1204 	ld	(x), a
      0085C6                       1205 00105$:
                                   1206 ;	sensors.c: 498: if (readValue < minValue)
      0085C6 90 A3 00 0A      [ 2] 1207 	cpw	y, #0x000a
      0085CA 2E 0D            [ 1] 1208 	jrsge	00107$
                                   1209 ;	sensors.c: 500: TIM1_CR1 = 0x00; // disable timer
      0085CC AE 52 50         [ 2] 1210 	ldw	x, #0x5250
      0085CF 7F               [ 1] 1211 	clr	(x)
                                   1212 ;	sensors.c: 501: tijd=clock();
      0085D0 CD 84 D8         [ 4] 1213 	call	_clock
                                   1214 ;	sensors.c: 502: print_UCHAR_hex(tijd);
      0085D3 9F               [ 1] 1215 	ld	a, xl
      0085D4 88               [ 1] 1216 	push	a
      0085D5 CD 81 97         [ 4] 1217 	call	_print_UCHAR_hex
      0085D8 84               [ 1] 1218 	pop	a
      0085D9                       1219 00107$:
                                   1220 ;	sensors.c: 506: tm1637DisplayDecimal(seconden, 0); // tijd in seconden 
      0085D9 90 CE 00 03      [ 2] 1221 	ldw	y, _seconden+0
      0085DD 5F               [ 1] 1222 	clrw	x
      0085DE 4B 00            [ 1] 1223 	push	#0x00
      0085E0 4B 00            [ 1] 1224 	push	#0x00
      0085E2 90 89            [ 2] 1225 	pushw	y
      0085E4 89               [ 2] 1226 	pushw	x
      0085E5 CD 83 76         [ 4] 1227 	call	_tm1637DisplayDecimal
      0085E8 5B 06            [ 2] 1228 	addw	sp, #6
                                   1229 ;	sensors.c: 507: val=0;
      0085EA 5F               [ 1] 1230 	clrw	x
      0085EB 1F 05            [ 2] 1231 	ldw	(0x05, sp), x
                                   1232 ;	sensors.c: 508: delay(1);
      0085ED 4B 01            [ 1] 1233 	push	#0x01
      0085EF 4B 00            [ 1] 1234 	push	#0x00
      0085F1 CD 80 F2         [ 4] 1235 	call	_delay
      0085F4 5B 02            [ 2] 1236 	addw	sp, #2
      0085F6 CC 85 65         [ 2] 1237 	jp	00109$
      0085F9 5B 06            [ 2] 1238 	addw	sp, #6
      0085FB 81               [ 4] 1239 	ret
                                   1240 	.area CODE
      0085FC                       1241 _segmentMap:
      0085FC 3F                    1242 	.db #0x3F	;  63
      0085FD 06                    1243 	.db #0x06	;  6
      0085FE 5B                    1244 	.db #0x5B	;  91
      0085FF 4F                    1245 	.db #0x4F	;  79	'O'
      008600 66                    1246 	.db #0x66	;  102	'f'
      008601 6D                    1247 	.db #0x6D	;  109	'm'
      008602 7D                    1248 	.db #0x7D	;  125
      008603 07                    1249 	.db #0x07	;  7
      008604 7F                    1250 	.db #0x7F	;  127
      008605 6F                    1251 	.db #0x6F	;  111	'o'
      008606 77                    1252 	.db #0x77	;  119	'w'
      008607 7C                    1253 	.db #0x7C	;  124
      008608 39                    1254 	.db #0x39	;  57	'9'
      008609 5E                    1255 	.db #0x5E	;  94
      00860A 79                    1256 	.db #0x79	;  121	'y'
      00860B 71                    1257 	.db #0x71	;  113	'q'
      00860C 00                    1258 	.db #0x00	;  0
                                   1259 	.area INITIALIZER
                                   1260 	.area CABS (ABS)
