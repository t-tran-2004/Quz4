# Variable Addition

## Equation
  result = x + y + z: x = 10, y = 25, z = 15

## Memory Usage
  This code allocates at least 4 bytes of memory.

## Execution Time
  real: 0m0.026s;
  user: 0m0.005s;
  sys:  0m0.003s

```assembly
section .data
	X EQU 10
	Y EQU 25
	Z EQU 15

section .text
	global _start

_start:
	push X
	push Y
	push Z
	call _sum
	mov eax, 1
	int 0x80

_sum:
	push ebp
	mov ebp, esp
	sub esp, 4

	mov eax, DWORD[ebp+16]
	mov ebx, DWORD[ebp+12]
	mov ecx, DWORD[ebp+8]
	add eax, ebx
	mov DWORD[ebp-4], eax
	add ecx, DWORD[ebp-4]
	mov [result], ecx

	leave
	ret

segment .bss
	result: RESB 1

```
