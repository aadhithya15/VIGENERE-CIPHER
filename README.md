# VIGENERE-CIPHER
## EX. NO: 4
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
// FuncƟon to generate repeaƟng key
void generateKey(char message[], char key[], char newKey[]) {
 int msgLen = strlen(message);
 int keyLen = strlen(key);
 int i, j = 0;
 for(i = 0; i < msgLen; i++) {
 if(isalpha(message[i])) {
 newKey[i] = key[j % keyLen];
 j++;
 } else {
 newKey[i] = message[i]; // Keep non-leƩers as they are
 }
 }
 newKey[i] = '\0';
}
// EncrypƟon funcƟon
void encrypt(char message[], char key[], char cipher[]) {
 int i;
 for(i = 0; i < strlen(message); i++) {
 if(isupper(message[i]))
 cipher[i] = ((message[i] - 'A') + (toupper(key[i]) - 'A')) % 26 + 'A';
 else if(islower(message[i]))
 cipher[i] = ((message[i] - 'a') + (tolower(key[i]) - 'a')) % 26 + 'a';
 else
 cipher[i] = message[i]; // Non-leƩer characters
 }
 cipher[i] = '\0';
}
// DecrypƟon funcƟon
void decrypt(char cipher[], char key[], char message[]) {
 int i;
 for(i = 0; i < strlen(cipher); i++) {
 if(isupper(cipher[i]))
 message[i] = ((cipher[i] - 'A') - (toupper(key[i]) - 'A') + 26) % 26 + 'A';
 else if(islower(cipher[i]))
 message[i] = ((cipher[i] - 'a') - (tolower(key[i]) - 'a') + 26) % 26 + 'a';
 else
 message[i] = cipher[i]; // Non-leƩer characters
 }
 message[i] = '\0';
}
int main() {
 char message[1000], key[1000], newKey[1000], cipher[1000], decrypted[1000];
 prinƞ("Enter the message: ");
 fgets(message, sizeof(message), stdin);
 message[strcspn(message, "\n")] = '\0'; // Remove newline
 prinƞ("Enter the key: ");
 scanf("%s", key);
 generateKey(message, key, newKey);
 encrypt(message, newKey, cipher);
 prinƞ("Encrypted Text: %s\n", cipher);
 decrypt(cipher, newKey, decrypted);
 prinƞ("Decrypted Text: %s\n", decrypted);
return 0;
}
```
## OUTPUT
<img width="543" height="407" alt="image" src="https://github.com/user-attachments/assets/012c42d3-60b3-46ac-a347-39fdabd83c32" />

## RESULT
Vigenere Cipher substitution technique has been implemented using C program.
