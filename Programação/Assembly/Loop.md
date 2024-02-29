```asm6502
section .data
numerais: db "0123456789"
pulalinha: db 0xa, 0xd

section .text
  global  _start

_start:
  xor esi, esi
  call loop
  
loop:
  mov eax, 4
  mov ebx, 1
  lea ecx, [numerais + esi]
  mov edx, 1
  int 0x80
   
  mov eax,4
  mov ebx, 1
  mov ecx, pulalinha
  mov edx, 2
  int 0x80
   
  inc esi
  cmp esi, 0xA
  jle loop
  
  mov eax, 1
  mov ebx, 0
  int 0x80
```

```assembly
	cmp [ebp+var_8], 1
	jz loc_401027
	cmp [ebp+var_8], 2
	jz loc_40103D
	cmp [ebp+var_8], 3
	jz loc_401053
	jmp loc_401058
loc_401027
	Code for case 1
	jmp loc_401058
loc_40103D
	Code for case 2
	jmp loc_401058
loc_401053
	Code for case 3
loc_401058
	Program end

```
