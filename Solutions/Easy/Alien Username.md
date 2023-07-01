# Problem: 

https://www.hackerrank.com/challenges/alien-username/problem

# Solution:

```
import Foundation

func findString(for pattern: String, inText text: String) -> String? {
    let regex = try? NSRegularExpression(pattern: pattern)
    if let firstMatch = regex?.firstMatch(in: text, range: NSRange(text.startIndex... , in: text)) {
        return String(text[Range(firstMatch.range, in: text)!])
    }
    return nil
}

let pattern = #"^[\._]\d+[a-zA-Z]{0,}_?$"#

let input = Int(readLine()!)!
(1...input).forEach { num in 
    let text = readLine()!
    if let _ = findString(for: pattern, inText: text) {
        print("VALID")
    } else {
        print("INVALID")
    }
}

```
