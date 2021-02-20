# Vault Door 1

## Question
AUTHOR: MARK E. HAASE
Description
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: (VaultDoor1.java)[VaultDoor1.java]

## Hints
- Look up the charAt() method online.

## Solution
From the following java code, we can see that we must make the checkPassword funciton return `true` if we want access to the vault.
```java
if (vaultDoor.checkPassword(input)) {
	System.out.println("Access granted.");
} else {
	System.out.println("Access denied!");
}
```

Instead of comparing input with a hardcoded string, the author of this java code decided to include a large number of conditions checking each index of the string. While it is entirely possible to go through the conditions and find the desired value at each index in the string from index 0 to index 31, I automated this process using the script below (written in JavaScript).

```js
const lines =`password.charAt(0)  == 'd' &&
password.charAt(29) == '3' &&
password.charAt(4)  == 'r' &&
password.charAt(2)  == '5' &&
password.charAt(23) == 'r' &&
password.charAt(3)  == 'c' &&
password.charAt(17) == '4' &&
password.charAt(1)  == '3' &&
password.charAt(7)  == 'b' &&
password.charAt(10) == '_' &&
password.charAt(5)  == '4' &&
password.charAt(9)  == '3' &&
password.charAt(11) == 't' &&
password.charAt(15) == 'c' &&
password.charAt(8)  == 'l' &&
password.charAt(12) == 'H' &&
password.charAt(20) == 'c' &&
password.charAt(14) == '_' &&
password.charAt(6)  == 'm' &&
password.charAt(24) == '5' &&
password.charAt(18) == 'r' &&
password.charAt(13) == '3' &&
password.charAt(19) == '4' &&
password.charAt(21) == 'T' &&
password.charAt(16) == 'H' &&
password.charAt(27) == 'f' &&
password.charAt(30) == 'b' &&
password.charAt(25) == '_' &&
password.charAt(22) == '3' &&
password.charAt(28) == '6' &&
password.charAt(26) == 'f' &&
password.charAt(31) == '0';`.split('\n');

let output = [];
lines.forEach(line => {
	idx = parseInt(line.substring('password.charAt('.length, line.indexOf(')') + 1));
	output[idx] = line[line.indexOf("'") + 1];
});

console.log(output.join(''));
// prints 'd35cr4mbl3_tH3_cH4r4cT3r5_ff63b0'
```

From the ouptut of the script, we can see that the flag should be `picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_ff63b0}`.
