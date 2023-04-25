# hashtable_add_pair

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_SIZE 100

// Define a struct for each key-value pair in the associative array
struct pair {
    char *key;
    char *value;
};

// Define the associative array as an array of pairs
struct pair hash_table[MAX_SIZE];

// Hash function to map keys to indices in the array
int hash(char *key) {
    int sum = 0;
    for (int i = 0; i < strlen(key); i++) {
        sum += key[i];
    }
    return sum % MAX_SIZE;
}

// Function to add a new key-value pair to the associative array
void add_pair(char *key, char *value) {
    int index = hash(key);
    hash_table[index].key = strdup(key);
    hash_table[index].value = strdup(value);
}

// Function to retrieve the value associated with a given key
char *get_value(char *key) {
    int index = hash(key);
    return hash_table[index].value;
}

int main() {
    // add some key-value pairs to the associative array
    add_pair("apple", "fruit");
    add_pair("banana", "7");
    add_pair("orange", "3");
    add_pair("tomato", "fruit");
    add_pair("Hosakote", "Sharath Kumar Bachegowda");

    // retrieve the values associated with some keys
    printf("apple: %s\n", get_value("apple"));
    printf("banana: %s\n", get_value("banana"));
    printf("pear: %s\n", get_value("pear"));
    printf("tomato: %s\n", get_value("tomato"));
    printf("Hosakote: %s\n", get_value("Hosakote"));
    return 0;
}

```
