---
layout: post
title: "Swift String Index Extension"
categories: [iOS, Extensions]
tags: [iOS, Swift, extensions, indexing]
---

Indexing a string in swift is not as intuitive as in other programming languages. Adding the extension below to your code makes it easier to index and view characters of a string. 

```

extension String {
    func at(_ index: Int) -> String {
        guard index >= 0, index < self.count else { return "" }
        
        let i = self.index(self.startIndex, offsetBy: index)
        return String(self[i])
    }
}
```

## Example and Output

The method only takes one argument which is the index. If the index is out of bounds, it will return an empty string.

![image](/assets/imgs/2026-01-15/example1.png)
![image](/assets/imgs/2026-01-15/output1.png)