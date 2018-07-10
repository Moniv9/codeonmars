---
description: Find the longest common substring between 2 given strings
---

# Longest Common Substring

**Recursive Approach**

```javascript
class LCS {

    get(str1, str2) {
        const str1Length = str1.length - 1;
        const str2Length = str2.length - 1;

        if (str1Length <= 0 || str2Length <= 0) {
            return 0;
        }

        if (str1[str1Length] === str2[str2Length]) {
            return 1 + this.get(str1.substring(0, str1Length), str2.substring(0, str2Length));
        }

        return Math.max(this.get(str1.substring(0, str1Length), str2),
            this.get(str1, str2.substring(0, str2Length)));
    }
}
```



Time complexity of this above approach is huge. So we will go with Dynamic programming to deduce solution for it.



