# Problem: 

https://www.hackerrank.com/challenges/detect-html-tags/problem

# Solution:

```
import Foundation

// Enter your code here 

func match(forRegex regex: String, inString text: String) -> [String] {
    let regex = try? NSRegularExpression(pattern: regex)
    if let results = regex?.matches(in: text, range: NSRange(text.startIndex..., in: text)) {
        return results.map{ String(text[Range($0.range, in: text)!])}
    }
    print("error")
    return []
    
}

var times = Int(readLine()!)!

var tages = [String]()
(0..<times).forEach { _ in
    let input = readLine()!
    let regex = #"<\/?\w+"#
    
    let results = match(forRegex: regex, inString: input)
    results.forEach { string in
        if let result = match(forRegex: #"[a-z\d]+"#, inString: string).first {
            tages.append(result)
        } 
    }
}
let uniques = Array(Set(tages)).sorted()
print(uniques.joined(separator: ";"))



```
