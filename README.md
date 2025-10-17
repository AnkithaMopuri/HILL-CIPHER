# HILL CIPHER
# Name: Mopuri Ankitha
# Register Number:212223040117
HILL CIPHER
EX. NO: 3 
IMPLEMENTATION OF HILL CIPHER
# AIM:
To write a C program to implement the hill cipher substitution techniques.

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

int mod26(int x) {
    return (x % 26 + 26) % 26;
}


void encrypt(int key[SIZE][SIZE], int pt[SIZE], int ct[SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        ct[i] = 0;
        for (int j = 0; j < SIZE; j++) {
            ct[i] += key[i][j] * pt[j];
        }
        ct[i] = mod26(ct[i]);
    }
}

int main() {
    char plaintext[100];
    int key[SIZE][SIZE], ptVec[SIZE], ctVec[SIZE];
    char ciphertext[100];
    int len, k = 0;

    printf("HILL CIPHER IMPLEMENTATION\n");
    printf("Enter the plaintext: ");
    scanf("%s", plaintext);

    for (int i = 0; i < strlen(plaintext); i++) {
        plaintext[i] = toupper(plaintext[i]);
    }

  
    printf("Enter the 3x3 key matrix :\n");
    for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
            scanf("%d", &key[i][j]);
        }
    }

    len = strlen(plaintext);


    while (len % SIZE != 0) {
        plaintext[len++] = 'X';
    }
    plaintext[len] = '\0';


    for (int i = 0; i < len; i += SIZE) {
        for (int j = 0; j < SIZE; j++) {
            ptVec[j] = plaintext[i + j] - 'A';
        }

        encrypt(key, ptVec, ctVec);

        for (int j = 0; j < SIZE; j++) {
            ciphertext[k++] = ctVec[j] + 'A';
        }
    }

    ciphertext[k] = '\0';

    printf("\nEncrypted Ciphertext: %s\n", ciphertext);

    return 0;
}

```

## OUTPUT
<img width="815" height="408" alt="image" src="https://github.com/user-attachments/assets/53e67c35-e7e0-4312-a264-d137ecefed2c" />


## RESULT
Thus writing a C program to implement the hill cipher substitution techniques was successfully Done.
