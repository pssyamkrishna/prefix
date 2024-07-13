#include <stdio.h>
#include <string.h>

// Function to find the longest common prefix
char* longestCommonPrefix(char** strs, int strsSize) {
    if (strsSize == 0) {
        return "";
    }

    // Take the first string as the initial prefix
    char* prefix = strs[0];
    int prefixLength = strlen(prefix);

    // Iterate over the array of strings
    for (int i = 1; i < strsSize; i++) {
        int j = 0;
        // Compare the current string with the prefix character by character
        while (j < prefixLength && j < strlen(strs[i]) && prefix[j] == strs[i][j]) {
            j++;
        }
        // Update the prefix length to the common length
        prefixLength = j;
        if (prefixLength == 0) {
            return "";
        }
    }

    // Create a new string for the result
    char* result = (char*)malloc((prefixLength + 1) * sizeof(char));
    strncpy(result, prefix, prefixLength);
    result[prefixLength] = '\0';

    return result;
}

int main() {
    char* strs1[] = {"flower", "flow", "flight"};
    int size1 = sizeof(strs1) / sizeof(strs1[0]);
    printf("Longest Common Prefix: %s\n", longestCommonPrefix(strs1, size1));

    char* strs2[] = {"dog", "racecar", "car"};
    int size2 = sizeof(strs2) / sizeof(strs2[0]);
    printf("Longest Common Prefix: %s\n", longestCommonPrefix(strs2, size2));

    return 0;
}
