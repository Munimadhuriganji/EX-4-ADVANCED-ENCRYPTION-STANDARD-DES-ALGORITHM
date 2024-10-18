# Ex-7 - Implement DES Encryption and Decryption

## Aim:

  To use Advanced Encryption Standard (AES) Algorithm for a practical application like URL Encryption.

## ALGORITHM: 

  1. AES is based on a design principle known as a substitution–permutation.
    
  2. AES does not use a Feistel network like DES, it uses variant of Rijndael.
   
  3. It has a fixed block size of 128 bits, and a key size of 128, 192, or 256 bits.
   
  4. AES operates on a 4 × 4 column-major order array of bytes, termed the state

## PROGRAM: 
# ENCRYPTION
```
#include <stdio.h>
#include <string.h>

void simpleAESEncrypt(const char *plaintext, const char *key, char *ciphertext) {
    int i;
    int textLength = strlen(plaintext);
    int keyLength = strlen(key);

    for (i = 0; i < textLength; i++) {
        ciphertext[i] = plaintext[i] ^ key[i % keyLength]; 
    }
    ciphertext[i] = '\0'; 
}

void printASCII(const char *ciphertext) {
    printf("Encrypted Message (ASCII values): ");
    for (int i = 0; i < strlen(ciphertext); i++) {
        printf("%d ", (unsigned char)ciphertext[i]); 
    }
    printf("\n");
}

int main() {
    char plaintext[100], key[100], ciphertext[100];

    printf("Enter the plaintext: ");
    fgets(plaintext, sizeof(plaintext), stdin);
    plaintext[strcspn(plaintext, "\n")] = 0; // Remove trailing newline

    printf("Enter the key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = 0; // Remove trailing newline

    simpleAESEncrypt(plaintext, key, ciphertext);
    printASCII(ciphertext);  

    return 0;
}
```
## OUTPUT:

![Screenshot 2024-10-18 142752](https://github.com/user-attachments/assets/a6954bda-c477-4e0b-b5d7-c7305113cc16)
# DECRYPTION
```
#include <stdio.h>
#include <string.h>

void simpleAESDecrypt(const char *ciphertext, const char *key, char *decryptedText) {
    int i;
    int textLength = strlen(ciphertext);
    int keyLength = strlen(key);

    for (i = 0; i < textLength; i++) {
        decryptedText[i] = ciphertext[i] ^ key[i % keyLength]; 
    }
    decryptedText[i] = '\0'; 
}

int main() {
    char ciphertext[100], key[100], decryptedText[100];

    printf("Enter the ciphertext (ASCII values separated by spaces): ");
    fgets(ciphertext, sizeof(ciphertext), stdin);
    
    // Convert the input ASCII values back to the ciphertext
    char processedCiphertext[100];
    int index = 0;
    int value;

    char *token = strtok(ciphertext, " ");
    while (token != NULL) {
        value = atoi(token);
        processedCiphertext[index++] = (char)value; // Convert ASCII to character
        token = strtok(NULL, " ");
    }
    processedCiphertext[index] = '\0'; // Null-terminate the string

    printf("Enter the key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = 0; // Remove trailing newline

    simpleAESDecrypt(processedCiphertext, key, decryptedText);
    printf("Decrypted Message: %s\n", decryptedText);

    return 0;
}

```
# OUTPUT
![WhatsApp Image 2024-10-18 at 14 40 02_8cdfbd05](https://github.com/user-attachments/assets/72e23210-3940-422f-a516-be1b182d485b)


## RESULT: 

Hence,to use Advanced Encryption Standard (AES) Algorithm for a practical application is done successfully.
