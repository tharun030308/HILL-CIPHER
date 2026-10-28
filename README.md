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

STEP-1: Read the plain text and key from the user. 

STEP-2: Split the plain text into groups of length three. 

STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main()
{
    char text[100], encrypted[100], decrypted[100];
    int key[2][2] = {{3, 3}, {2, 5}};
    int inv[2][2] = {{15, 17}, {20, 9}};
    int i, a, b, x, y, len = 0;

    printf("Enter the plaintext: ");
    fgets(text, sizeof(text), stdin);

    for (i = 0; text[i] != '\0'; i++)
    {
        if (isalpha((unsigned char)text[i]))
        {
            text[len++] = toupper((unsigned char)text[i]);
        }
    }
    text[len] = '\0';

    if (len == 0)
    {
        printf("Invalid plaintext\n");
        return 0;
    }

    if (len % 2 != 0)
    {
        text[len++] = 'X';
        text[len] = '\0';
    }

    for (i = 0; i < len; i += 2)
    {
        a = text[i] - 'A';
        b = text[i + 1] - 'A';

        x = (key[0][0] * a + key[0][1] * b) % 26;
        y = (key[1][0] * a + key[1][1] * b) % 26;

        encrypted[i] = x + 'A';
        encrypted[i + 1] = y + 'A';
    }
    encrypted[len] = '\0';

    printf("Encrypted text: %s\n", encrypted);

    for (i = 0; i < len; i += 2)
    {
        a = encrypted[i] - 'A';
        b = encrypted[i + 1] - 'A';

        x = (inv[0][0] * a + inv[0][1] * b) % 26;
        y = (inv[1][0] * a + inv[1][1] * b) % 26;

        decrypted[i] = x + 'A';
        decrypted[i + 1] = y + 'A';
    }
    decrypted[len] = '\0';

    printf("Decrypted text: ");
    for (i = 0; i < len && i < strlen(text); i++)
    {
        if (i < len)
            printf("%c", decrypted[i]);
    }
    printf("\n");

    return 0;
}
```
## OUTPUT
<img width="325" height="70" alt="image" src="https://github.com/user-attachments/assets/4186bacb-e892-4c1f-9885-a904f7dd76e5" />



## RESULT
Thus the program to perform Hill Cipher has been executed successfully
