---
layout: post
title: "Swift Substring Extension"
categories: [iOS, Extensions]
tags: [iOS, Swift, extensions, substring]
---

Getting a <span style="color:green;"><em>substring</em></span> in swift is not exactly simple which uses <span style="color:red;"><em>String.Index</em></span> instead of Int for indexing. This post gives an extension you can add to your next swift project. You simply give the method a starting index and the length of the substring you want all using Int!

```
extension String {
    
    enum SubstringErrors: Error {
        case length(String)
    }
    
    //will extract a string of length LEN from the starting index START and return that substring
    func substring(start: Int, len: Int) throws -> String {
        
        if start >= self.count || start < 0 {
            throw SubstringErrors.length("Make sure start is not greater than \(self.count-1) or less than 0")
        } else if len < 0 {
            throw SubstringErrors.length("Make sure len is not less than 0")
        }

        var end = len
        if len > self.count - start {
            end = self.count - start
        }

        return String(self[self.index(self.startIndex, offsetBy: start)..<self.index(self.startIndex, offsetBy: start + end)])
    }
}
```

## Example and Output

The first argument for the method is the starting index and the length of the desired substring is the second argument.

![image](/assets/imgs/2024-04-17/example1.png)