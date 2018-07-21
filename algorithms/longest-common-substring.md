---
description: Find the longest common substring between 2 given strings
---

# Longest Common Substring

**Iterative Approach**

```javascript
class LCS {

    get(str1, str2) {
        const str1Length = str1.length - 1;
        const str2Length = str2.length - 1;
        let result = 0;

        if (str1Length <= 0 || str2Length <= 0) {
            return 0;
        }

        for (let i = 0; i < str1Length; i++) {
            let localMax = 0;
            let tempIndex = i;

            for (let j = 0; j < str2Length; j++) {
                if (str1[tempIndex] === str[j]) {
                    localMax++;
                    tempIndex++;
                }
            }

            result = Math.max(result, localMax);
        }

        return result;
    }
}
```



Time complexity of this above approach is huge. So we will go with Dynamic programming to deduce a solution for it.

```javascript
class LCS {

    constructor() {
        this.table = [];
    }

    _createMatrix(str1Length, str2Length) {
        for (let i = 0; i <= str1Length; i++) {
            this.table[i] = [];

            for (let j = 0; j <= str2Length; j++) {
                this.table[i][j] = 0;
            }
        }
    }

    get(str1, str2) {
        const str1Length = str1.length;
        const str2Length = str2.length;
        let result = 0;

        this._createMatrix(str1Length, str2Length);

        for (let i = 1; i <= str1Length; i++) {
            for (let j = 1; j <= str2Length; j++) {

                if (str1[i - 1] === str2[j - 1]) {
                    this.table[i][j] = this.table[i - 1][j - 1] + 1;
                    result = Math.max(result, this.table[i][j]);
                } else {
                    this.table[i][j] = 0;
                }
            }
        }

        return result;
    }
}
```







