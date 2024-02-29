section .data
message: db 'Ola Mundo!', 0xa, 0xd
lMessage: equ $ - message

section .text
%define exit int 0x80; executa syscall
%macro print 4
  mov eax, %1
  mov ebx, %2
  mov ecx, %3
  mov edx, %4
  exit
%endmacro

%macro end_program 1
  mov eax, %1
  xor ebx, ebx
  exit
%endmacro

global _start
_start:
  print 4, 1, message, lMessage
  end_program 1
