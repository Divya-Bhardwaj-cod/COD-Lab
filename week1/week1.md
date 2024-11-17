week1
a.
.data
a: .word 0x12345678
.text
la x10,a
lw x11,0(x10)
addi x12,x0,0
andi x13,x11,0xff
slli x13,x13,24
add x12,x12,x13
srli x11,x11,8
andi x13,x11,0xff
slli x13,x13,16
add x12,x12,x13
srli x11,x11,8
andi x13,x11,0xff
slli x13,x13,8
add x12,x12,x13
srli x11,x11,8
add x12,x12,x11
sw,x12,4(x10)

b.
.data
a:.word 0xFF,0xA0000002,0xFFFFFFFF,0xB0000001
.text
la x10,a
lw x9,0(x10)#msb1
lw x8,4(x10)#lab1
lw x7,8(x10)#msb2
lw x6,12(x10)#lsb2
add x5,x8,x6  #lsb addition
sltu x11,x5,x8  #carry lsb
add x2,x9,x7   #msb addition
sltu x12,x2,x7  #carry msb
add x3,x2,x11
#storing in data memory
sw x5,16(x10)
sw x3,20(x10)
sw x12,24(x10)
