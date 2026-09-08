# EX-NO14-HASH-ALGORITHM

## AIM:
To implement HASH ALGORITHM

## ALGORITHM:

1. Hash Algorithm is used to convert input data (message) into a fixed-size string, typically a hash value, which uniquely represents the original data.

2. Initialization:
   - Choose a hash function \( H \) (e.g., SHA-256, MD5, etc.).
   - The message \( M \) to be hashed is input.

3. Message Preprocessing:
   - Break the message \( M \) into fixed-size blocks. If necessary, pad the message to make it compatible with the block size required by the hash function.
   - For example, in SHA-256, the message is padded to ensure that its length is a multiple of 512 bits.

4. Hash Calculation:
   - Process the message block by block, applying the hash function \( H \) iteratively to produce an intermediate hash value.
   - For SHA-256, each block is processed through a series of logical operations, bitwise manipulations, and modular additions.

5. Output:
   - After all blocks are processed, the final hash value (digest) is produced, which is a fixed-size output (e.g., 256-bit for SHA-256).
   - The resulting hash is unique to the input message, meaning even a small change in the message will result in a completely different hash.

6. Security: The strength of the hash algorithm lies in its collision resistance, ensuring that it is computationally infeasible to find two different messages that produce the same hash value.


## Program:

~~~
#include <stdio.h>
#include <string.h>

unsigned long hashFunction(char str[])
{
    unsigned long hash = 5381;
    int i;

    for (i = 0; str[i] != '\0'; i++)
    {
        hash = ((hash << 5) + hash) + str[i];
    }

    return hash;
}

void displayHash(unsigned long hash)
{
    printf("\nHash Value: ");

    printf("%08lx", hash);

    printf("\n");
}

int main()
{
    char message[500];
    unsigned long hashValue;

    printf("========================================\n");
    printf("          HASH ALGORITHM\n");
    printf("========================================\n");

    printf("\nEnter the message: ");
    fgets(message, sizeof(message), stdin);

    /* Remove newline character */
    message[strcspn(message, "\n")] = '\0';

    printf("\n----------------------------------------\n");
    printf("Original Message : %s\n", message);
    printf("Message Length   : %lu characters\n",
           strlen(message));
    printf("----------------------------------------\n");

    /* Generate hash value */
    hashValue = hashFunction(message);

    /* Display hash */
    displayHash(hashValue);

    printf("\n----------------------------------------\n");
    printf("Hash Generation : Successful\n");
    printf("----------------------------------------\n");

    printf("\n========================================\n");
    printf("             END OF PROGRAM\n");
    printf("========================================\n");

    return 0;
}
~~~
## Output:
![Uploading image.png…]()

## Result:
The program is executed successfully.
