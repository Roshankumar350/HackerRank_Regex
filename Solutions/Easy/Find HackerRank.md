# Problem: 

https://www.hackerrank.com/challenges/find-hackerrank/problem

# Solution:

```
import Foundation


func findMatch(forPattern pattern: String, inText text: String) -> String? {
    let regex = try? NSRegularExpression(pattern: pattern)
    
    if let match = regex?.firstMatch(in: text, range: NSRange(text.startIndex..., in: text)) {
        return String(text[Range(match.range, in: text)!])
    }
    
    return nil
}

let sPattern = #"^hackerrank\s+.*"#
let mPattern = #"^hackerrank$"#
let ePattern = #".*hackerrank$"#

var times = Int(readLine()!)!

(1...times).forEach { _ in 
    let text = readLine()!
    if let _ = findMatch(forPattern: sPattern, inText: text) {
        print("1")
    } else if let _ = findMatch(forPattern: mPattern, inText: text) {
        print("0")
    } else if let _ = findMatch(forPattern: ePattern, inText: text) {
        print("2")
    } else {
        print("-1")
    }
    
     
}

```
