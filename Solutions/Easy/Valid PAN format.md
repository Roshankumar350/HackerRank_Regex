# Problem: 

https://www.hackerrank.com/challenges/valid-pan-format/problem

# Solution:

```
import Foundation

// Enter your code here 
func findString(for pattern: String, inText text: String) -> String? {
    let regex = try? NSRegularExpression(pattern: pattern)
    if let firstMatch = regex?.firstMatch(in: text, range: NSRange(text.startIndex... , in: text)) {
        return String(text[Range(firstMatch.range, in: text)!])
    }
    return nil
}

let panPattern = #"^[A-Z]{5}\d{4}[A-Z]$"#

let times = Int(readLine()!)!

(1...times).forEach { _ in
    let text = readLine()!
    if let _ = findString(for: panPattern, inText: text) {
        print("YES")
    } else {
        print("NO")
    }
}

```
