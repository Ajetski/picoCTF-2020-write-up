# Vault Door Training

## Question
AUTHOR: MARK E. HAASE
Description
Your mission is to enter Dr. Evil's laboratory and retrieve the blueprints for his Doomsday Project. The laboratory is protected by a series of locked vault doors. Each door is controlled by a computer and requires a password to open. Unfortunately, our undercover agents have not been able to obtain the secret passwords for the vault doors, but one of our junior agents obtained the source code for each vault's computer! You will need to read the source code for each level to figure out what the password is for that vault door. As a warmup, we have created a replica vault in our training facility. The source code for the training vault is here: [VaultDoorTraining.java](VaultDoorTraining.java)

## Hints
- The password is revealed in the program's source code.

## Solution
Based on the code in VaultDoorTrainig.java, we see that the function checkPassword will return true only when the the password parameter is equal to the string "w4rm1ng_Up_w1tH_jAv4_eec0716b713". If we input "picoCTF{w4rm1ng_Up_w1tH_jAv4_eec0716b713}" into standard input when prompted, then "w4rm1ng_Up_w1tH_jAv4_eec0716b713" will be passed to the checkPassword function.

Thus the flag for this challenge is `picoCTF{w4rm1ng_Up_w1tH_jAv4_eec0716b713}`.
