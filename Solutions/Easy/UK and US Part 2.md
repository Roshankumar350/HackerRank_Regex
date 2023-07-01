

# Problem :
https://www.hackerrank.com/challenges/uk-and-us-2/problem


# Solution: 
```
import Foundation

let n = Int(readLine()!)!

let lines = (0 ..< n).map { _ in readLine()! }.joined(separator: "\n")
let linesRange = NSRange(0 ..< lines.count)

let t = Int(readLine()!)!

let r = try! NSRegularExpression(pattern: "our", options: .caseInsensitive)

for _ in 0 ..< t {
    let w = readLine()!
    let regex0 = r.stringByReplacingMatches(in: w, options: [], range: NSRange(0 ..< w.count), withTemplate: "ou?r")
    let regex = "\\b\(regex0)\\b"
    let rt = try! NSRegularExpression(pattern: regex, options: [])
    let matches = rt.matches(in: lines, options: [], range: linesRange)
    print(matches.count)
}
```
