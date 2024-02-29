section .data
	msg:  db	'Hello World !', 0xa, 0xd
	tam:  equ $ - msg

section .text
	global _start
	
_start:
	mov	eax,4		  ; numero da syscall (sys_write)
	  mov	ebx,1		  ; local onde vamos escrever os bytes file descriptor (stdout)
	  mov	ecx,msg		; message to write
	  mov	edx,tam		; message length
	int 0x80      ; chama o kernel

	mov	eax, 1    ; syscall: sys_exit
	mov	ebx, 0    ; status: 0
	int 0x80      ; chama o kernel