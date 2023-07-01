# Problem: 

https://www.hackerrank.com/challenges/ip-address-validation/problem

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

let ipv4 = #"(([0-9]|[1-9][0-9]|1[1-9][0-9]|2[0-4][0-9]|25[0-5])\.){3}([0-9]|[1-9][0-9]|1[1-9][0-9]|2[0-4][0-9]|25[0-5])$"#
let ipv6 = #"([a-f\d]{0,4}:){7}[a-f\d]{0,4}$"#

let input = Int(readLine()!)!
(1...input).forEach { _ in 
    let text = readLine()!
    if let _ = findString(for: ipv4, inText: text) {
        print("IPv4")
    } else if let _ = findString(for: ipv6, inText: text){
        print("IPv6")
    } else {
        print("Neither")
    }
}

```
