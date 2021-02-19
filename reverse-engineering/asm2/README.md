# asm2

## Question
AUTHOR: SANJAY C
Description
What does asm2(0x4,0x21) return? Submit the flag as b hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](test.S)

## Hints
- assembly [conditions](https://www.tutorialspoint.com/assembly_programming/assembly_conditions.htm)

## Solution

The assmebly code converted to C code is :
```c
#include <stdio.h>

int asm2(int a, int b) {
	while(a <= 0xfb46) {
		b += 0x1;
		a += 0x74;
	}
	return b;
}

int main() {
	printf("Result of asm2(0x4, 0x21): %x\n", asm2(0x4, 0x21));
	// prints 24c
}
```

Walking thorugh the assembly step by step:
| Assembly                               | Explanation                               |
|:--------------------------------------:|:-----------------------------------------:|
| `sub    esp,0x10`                      | Add 10 space on stack for local variables |
| `mov    eax,DWORD PTR [ebp+0xc]`       | Put x into eax temporarily                |
| `mov    DWORD PTR [ebp-0x4],eax`       | Put x into b local variable: b            |
| `mov    eax,DWORD PTR [ebp+0x8]`       | Put y into eax temporarily                |
| `mov    DWORD PTR [ebp-0x8],eax`       | Put y into b local variable: a            |
| `jmp    0x509 <asm2+28>`               | Go to the start of the loop               |
| `cmp    DWORD PTR [ebp-0x8],0xfb46`    | Compare a to 0xfb46                       |
| `jle    0x501 <asm2+20>`               | Enter loop if a <= 0xfb46                 |
| `add    DWORD PTR [ebp-0x4],0x1`       | Add 0x1 to b                              |
| `add    DWORD PTR [ebp-0x8],0x74`      | Add 0x74 to a                             |
| `cmp    DWORD PTR [ebp-0x8],0xfb46`    | Compare a to 0xfb46                       |
| `jle    0x501 <asm2+20>`               | Enter loop if a <= 0xfb46                 |
| ... continue looping until  a > 0xfb46 | keep adding 0x1 to b and 0x74 to a        |
| `mov    eax,DWORD PTR [ebp-0x4]`       | once a > 0xfb46, set eax to b             |
| `ret`                                  | return b                                  |

This assembly code will loop many times. It is not feasible to compute the result by hand. I have translated these instructions into the C code above. The result is 0x24c.
