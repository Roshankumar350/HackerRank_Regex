# Problem: 

https://www.hackerrank.com/challenges/hackerrank-tweets/problem

# Solution:

```
import Foundation

func findMatch(forPattern regexPattern: String, inText text: String) -> String? {
    let regex = try? NSRegularExpression(pattern: regexPattern, options: .caseInsensitive) 
    if let firstMatch = regex?.firstMatch(in: text, range: NSRange(text.startIndex... , in: text)) {
        return String(text[Range(firstMatch.range, in: text)!])
    }
    return nil
}

var times = Int(readLine()!)!
let regPattern = #"[#@]?(hackerrank)"#
var count = 0
(1...times).forEach { _ in
    let text = readLine()!
    if let _ = findMatch(forPattern: regPattern, inText: text) {
        count += 1
    }
}

print(count)

```
