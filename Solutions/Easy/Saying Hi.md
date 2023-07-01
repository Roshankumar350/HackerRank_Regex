# Problem: 

https://www.hackerrank.com/challenges/saying-hi/problem

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

let pattern = #"^[Hh][Ii]\s[^Dd][\w\s]+"#

let times = Int(readLine()!)!

(1...times).forEach{ _ in
   let text = readLine()!
   if let match = findString(for: pattern, inText: text) {
       print(match)
   }
}

```
