# CRYPTOGRAPHY
# HILL CIPHER
# EX. NO: 1(C) AIM:
 

# IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B= 1... Z = 25, is used, but this is not an essential feature of the cipher. 
To encrypt a message, each block of n letters is multiplied by an invertible n × n matrix, against modulus 26. 
To decrypt the message, each block is multiplied by the inverse of the matrix used for encryption. 
The matrix used for encryption is the cipher key, and 
it should be chosen randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. 

STEP-2: Split the plain text into groups of length three.

STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.


## PROGRAM 
```
#include <stdio.h>
#include <string.h>

int main() {
    unsigned int a[3][3] = {{6, 24, 1}, {13, 16, 10}, {20, 17, 15}};
    unsigned int b[3][3] = {{8, 5, 10}, {21, 8, 21}, {21, 12, 8}};
    int i, j, t = 0;
    unsigned int c[3], d[3];
    char msg[20];

    printf("Enter plain text (up to 3 characters): ");
    scanf("%s", msg);

    // Ensure the message length is 3 for proper encryption
    if (strlen(msg) != 3) {
        printf("Error: The message length must be exactly 3 characters.\n");
        return 1;
    }

    // Convert plain text to numerical values (A = 0, B = 1, ..., Z = 25)
    for (i = 0; i < 3; i++) {
        if (msg[i] < 'A' || msg[i] > 'Z') {
            printf("Error: Input must only contain uppercase letters (A-Z).\n");
            return 1;
        }
        c[i] = msg[i] - 'A';
        printf("%d ", c[i]);
    }

    // Encryption: Multiply the matrix 'a' by the plaintext vector
    for (i = 0; i < 3; i++) {
        t = 0;
        for (j = 0; j < 3; j++) {
            t = t + (a[i][j] * c[j]);
        }
        d[i] = t % 26;  // Take modulo 26 to wrap the values
    }

    printf("\nEncrypted Cipher Text: ");
    for (i = 0; i < 3; i++) {
        printf("%c ", d[i] + 'A');  // Convert numerical values back to characters
    }

    // Decryption: Multiply the matrix 'b' by the cipher text vector
    for (i = 0; i < 3; i++) {
        t = 0;
        for (j = 0; j < 3; j++) {
            t = t + (b[i][j] * d[j]);
        }
        c[i] = t % 26;  // Take modulo 26
    }

    printf("\nDecrypted Cipher Text: ");
    for (i = 0; i < 3; i++) {
        printf("%c ", c[i] + 'A');  // Convert numerical values back to characters
    }

    return 0;
}
 ``` 
## OUTPUT
![image](https://github.com/user-attachments/assets/393200cc-1437-4a9a-a7a9-ea4d881ee69f)


## RESULT

the implementation of hill cipher was executed successfully
