# coa_lab
##  obj 1

addition of two 16bits numbers using immediate addressing mode.
```
mov ds,ax
mov ax,3241h
mov bx,1221h
add ax,bx
hlt
```
subtraction of two 16bits numbers using direct addressing mode.
```
mov ds,ax
mov ax,[3000h]
mov bx,[3002h]
sub ax,bx
mov [3004h],ax
hlt
```
addition of two 16bits numbers using indirect addressing mode.
```
mov ds,ax   
mov si,0500h
mov di,0502h
mov ax,[si] 
add ax,[di] 
inc si
mov[si],ax
hlt
```

subtraction of two 16bits numbers using index addressing mode.
```

mov ds,ax
mov si,3000h
mov ax,[si+0000h]
mov bx,[si+0002h]
sub ax,bx
mov [si+0004h],ax
hlt
```

addition of two 16bits numbers using base index addressing mode.
```
mov ax,0000h
mov ds,ax
mov si,[5000h]
mov bx,[5002h]
mov ax,[bx+si+0000h]
mov cx,[bx+si+0002h]
add ax,cx
mov [si+0004h],ax
hlt
```
multiplication of two 16bits numbers without using MUL instruction.
```
mov ds,ax
mov ax,[3000h]
mov bx,[3002h]
add ax,bx
add ax,bx
add ax,bx
add ax,bx
mov [3004h],ax
hlt
```
division of two 16bits numbers without using DIV instruction.
```
mov si,4000h
mov ax,[si]
mov bx,[si+02h]
l1: cmp ax,bx
jl l2
sub ax,bx
inc dx
jmp l1
l2: mov [si+04],ax
mov [si+06],dx
hlt
```

## obj2
 2's complement
```
mov al,[3500h]
not al
add al,01h
mov [3501h],al
hlt
```
 grays code
 ```
mov bl,[4100h]
mov al,bl
shr al,01h
xor al,bl
mov [4101h],al
hlt
```
nibble ,26 62
```
mov al,[2500h]
mov cl,04h
ror al,04h
mov [2501h],al
hlt
```

data, AB CD 00 00 00 EF
```
mov bx,3c00h
mov ax,[bx]
inc bx
mov ah,[bx]
mov dl,al
mov dh,ah
and dl,dh
xor al,ah
or dl,al
mov bx,3c05h
mov [bx],dl
hlt
```
## obj 3

 find the sum and average of n 16-bit number
```
mov ax,0000h
mov dx,0000h
mov cx,0006h
mov bx,cx
mov si,5000h
l1: add ax,[si]
jnc l2
inc dx
l2: inc si
inc si
dec cx
jnz l1
mov [5010h],ax
mov [5012h],dx
div bx
mov [5014h],ax
hlt
```
count 1's in an 8bit 
```
mov ax,0000h
mov ds,ax
mov al,2000h
mov cl,08h
mov dl,0000h
l1: shr al,01h
jnc l2
inc dl
l2: dec cl
jnz l1
inc ax
mov [ax],cl
hlt
```

move block 16bit data from one location to other
```
mov si,5700h
mov di,5720h
mov cl,0ah
l1:mov ax,[si]
mov [di],ax
inc si
inc si
inc di
inc di
dec cl
jnz l1
hlt
```
## obj 4

smallest and largest
```
mov ax,3000h
mov ds,ax
mov si,1000h
mov cl,[si]
inc si
mov bl,[si]
mov bh,[si]
back: mov al,[si]
cmp al,bl
jnz l1
mov b1,[si]
l1: mov ah ,[si]
cmp ah,[si]
jc l2
mov bh,[si]
l2: inc si
dec cl
jnz back
mov [si],bl
inc si
mov [si],bh
hlt
```
 large 
 ```
MOV AX,2F00H 
MOV DS, AX
MOV SI,4E00H
MOV AX, 00H
 MOV CX, 05H
BACK: CMP AX, [SI]
JNC FWD
MOV AX, [SI]
JNC FWD
MOV AX,[SI]
FWD: INC SI
INC SI
DEC CX
JNZ BACK
MOV[4E0AH], AX
HLT
```
dec 
```
MOV CH,05H
 L1:MOV CL,05H
MOV SI, 3000H
L2: MOV AL, [SI]
MOV AH, [SI+1]
CMP AL, AH
JNC L3
JZ L3
MOV [SI], AH
 MOV [SI+1],AL
 L3: INC SI
DEC CL
JNZ L2
DEC CH
JNZ L1
HLT
```

## obj 5


## obj 6

largest in array
```
.global_start
_start:
ldr r0,=count
ldr r1, [r0]
mov r4, #0x00
ldr r2,=array
back: ldr r3, [r2],#4
cmp r4,r3
bgt fwd
mov r4,r3
fwd: subs r1,r1,#01
bne back
str r4, [r2]
exit: b exit
.data
count: word 0x05
array: .word 0x15,0x35,0x45,0x10,0x4f
```

smallest in array
```
.global_start
_start:
ldr r0,=count
ldr rl, [r0]
mov r4, #0xff
ldr r2,=array
back: ldr r3, [r2],#4
cmp r4,r3
blt fwd
mov r4,r3
fwd: subs r1,r1,#01
bne back
str r4, [r2]
exit: b exit
.data
count: word 0x05
array: word 0x15,0x35,0x45,0x10,0x4f
```

separate even odd
```
.global_start
_start:
ldr r0, =count
ldr r1, =odd_list
mov r2, =even_list
ldr r3, =count
ldr r3,[r3]
loop:ldr r4,[r0],#4
and r5,r4,#1
cmp r5,#1
beq odd
str r4,[r2],#4
bal flow
odd:str r4,[r1],#4
forw:subs r3,r3,#1
bne loop
mov r7,#1
swi 0
.data
count: .words 5
array: .word 0*11 0*12 0*13 0*14 0*15
```
