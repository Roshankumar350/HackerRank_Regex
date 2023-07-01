# Problem: 

https://www.hackerrank.com/challenges/split-number/problem

# Solution:

```
import Foundation

func matches(forPattern regPattern: String, inText text: String) -> [[String]] {
    let regex = try? NSRegularExpression(pattern: regPattern)
    var result: [[String]] = []
    let stringRange = NSRange(location: 0, length: text.utf16.count)
    if let matches = regex?.matches(in: text, range: stringRange) {
        for match in matches {
            var group = [String]()
            for rangeIndex in 1..<match.numberOfRanges {
                let nsRange = match.range(at: rangeIndex)
                guard !NSEqualRanges(nsRange, NSMakeRange(NSNotFound, 0)) else { continue }
                let string = String(text[Range(nsRange, in: text)!])
                group.append(string)
            }
            
            result.append(group)
        }
    }
    return result
}


let pattern = #"([\d]{1,3})[\s-]{1}([\d]{1,3})[\s-]{1}([\d]{4,10})"#

let times = Int(readLine()!)!

var multiLineText = """
"""
(1...times).forEach { _ in
    let eachLine = readLine()!
    multiLineText.append(eachLine)
    multiLineText.append("\n")
}

let results = matches(forPattern: pattern, inText: multiLineText)

for result in results {
    print("CountryCode=\(result[0]),LocalAreaCode=\(result[1]),Number=\(result[2])")
}

```
