# Shorten Path

Given an **absolute path** for a file (Unix-style), simplify it. Or in other words, convert it to the **canonical path**.

In a UNIX-style file system, a period `.` refers to the current directory. Furthermore, a double period `..` moves the directory up a level.

Note that the returned canonical path must always begin with a slash `/`, and there must be only a single slash `/` between two directory names. The last directory name (if it exists) **must not** end with a trailing `/`. Also, the canonical path must be the **shortest** string representing the absolute path.

 

**Example 1:**

```
Input: "/home/"
Output: "/home"
Explanation: Note that there is no trailing slash after the last directory name.
```

**Example 2:**

```
Input: "/../"
Output: "/"
Explanation: Going one level up from the root directory is a no-op, as the root level is the highest level you can go.
```

**Example 3:**

```
Input: "/home//foo/"
Output: "/home/foo"
Explanation: In the canonical path, multiple consecutive slashes are replaced by a single one.
```

**Example 4:**

```
Input: "/a/./b/../../c/"
Output: "/c"
```

**Example 5:**

```
Input: "/a/../../b/../c//.//"
Output: "/c"
```

**Example 6:**

```
Input: "/a//b////c/d//././/.."
Output: "/a/b/c"
```



### Leetcode

https://leetcode.com/problems/simplify-path/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {string} path
 * @return {string}
 */
var simplifyPath = function(path) {
    const stack = [];
    const dirs = path.split('/');
    
    // push valid directories to stack
    for(const dir of dirs) {
        // pop it from stack if the directory value is ..
        // i.e go back to previous directory
        if(dir === "..") {
            stack.pop();
            continue;
        }
        
        // push to stack if value is not . or empty
        // empty values will be generated due to // slashes in the path
        if(dir != "." && dir != "") {
            stack.push(dir);
        }
    }
    
    // return the combined path
    return `/${stack.join("/")}`;
};
```



### Explanation

https://www.youtube.com/watch?v=EdvOGbOOUvA