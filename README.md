# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#define SIZE 3

int charToInt(char c) {
    return toupper(c) - 'A';
}

char intToChar(int n) {
    return (char)(n + 'A');
}

int main() {
    int key[SIZE][SIZE];
    char plaintext[100], ciphertext[100];
    int i, j, k, len;

    printf("Enter 3x3 key matrix (row-wise):\n");
    for (i = 0; i < SIZE; i++) {
        for (j = 0; j < SIZE; j++) {
            scanf("%d", &key[i][j]);
        }
    }

    printf("Enter plaintext (in CAPITAL letters, no spaces): ");
    scanf("%s", plaintext);

    len = strlen(plaintext);
    while (len % SIZE != 0) {
        plaintext[len++] = 'X';
        plaintext[len] = '\0';
    }

    int pos = 0;
    for (i = 0; i < len; i += SIZE) {
        for (j = 0; j < SIZE; j++) {
            int sum = 0;
            for (k = 0; k < SIZE; k++) {
                sum += key[j][k] * charToInt(plaintext[i + k]);
            }
            ciphertext[pos++] = intToChar(sum % 26);
        }
    }
    ciphertext[pos] = '\0';

    printf("\nPlaintext : %s", plaintext);
    printf("\nCiphertext: %s\n", ciphertext);

    return 0;
}

```
## OUTPUT
<img width="1784" height="701" alt="Screenshot 2025-09-19 122953" src="https://github.com/user-attachments/assets/d9fee08b-100f-4f99-a769-fd756c6e9578" />

## RESULT
Thus, the C program for Hill Cipher using a 3×3 key matrix was successfully executed, and the output was verified.
