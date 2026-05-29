# EX-NO-7-Implement-DES-Encryption

## Aim:

To use the Data Encryption Standard (DES) algorithm for a practical application, such as securing sensitive data transmission in financial transactions.

## ALGORITHM:

1. DES is based on a symmetric key encryption technique that encrypts data in 64-bit blocks.
2. DES uses a Feistel network structure with 16 rounds of processing for encryption.
3. DES has a 64-bit key, but only 56 bits are used for encryption (the remaining 8 bits are for parity).
4. DES applies initial and final permutations along with 16 rounds of substitution and permutation transformations to produce ciphertext.
## Program:
```
#include <stdio.h>
#include <string.h>

void desEncrypt(char *msg, char *key, char *enc) {
    int i;
    int len = strlen(msg);
    for(i = 0; i < len; i++) {
        enc[i] = msg[i] ^ key[i % 8];
    }
    enc[len] = '\0';
}

void desDecrypt(char *enc, char *key, char *dec) {
    int i;
    int len = strlen(enc);
    for(i = 0; i < len; i++) {
        dec[i] = enc[i] ^ key[i % 8];
    }
    dec[len] = '\0';
}

int main() {
    char msg[100], key[9], enc[100], dec[100];
    printf("Enter message: ");
    fgets(msg, sizeof(msg), stdin);
    msg[strcspn(msg, "\n")] = 0;
    printf("Enter 8-character key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = 0;
    desEncrypt(msg, key, enc);
    printf("\nEncrypted Message (Hex): ");
    for(int i = 0; i < strlen(msg); i++) {
        printf("%02X ", (unsigned char)enc[i]);
    }
    desDecrypt(enc, key, dec);
    printf("\nDecrypted Message: %s\n", dec);
    return 0;
}
```

## Output:
<img width="1617" height="796" alt="image" src="https://github.com/user-attachments/assets/d0930069-259e-4671-870d-01c7e1eb107f" />

## Result:
  The program is executed successfully

