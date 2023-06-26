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
