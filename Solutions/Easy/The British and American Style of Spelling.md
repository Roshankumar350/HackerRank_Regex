# Problem: 

https://www.hackerrank.com/challenges/uk-and-us/problem

# Solution:

```
import Foundation

func findmatches(forRegex regexPattern: String, inText text: String) -> [String] {
    let regularExpression = try? NSRegularExpression(pattern: regexPattern)
    
    let textRange = NSRange(location: 0, length: text.utf16.count)
    var result: [String] = []
    if let matches = regularExpression?.matches(in: text, range: textRange) {
        
        for match in matches {
            let range = match.range
            let group = String(text[Range(range, in: text)!])
            result.append(group)
        }
    }
    
    return result
}

let numberOfLines = Int(readLine()!)!
var multiLine = """
"""
(1...numberOfLines).forEach { _ in
    if let text = readLine() {
        multiLine.append(text)
    }
}

var numberOfWords = Int(readLine()!)!
var words = [String]()
(1...numberOfWords).forEach { _ in
    if let word = readLine() {
        let patternWord = word.replacingOccurrences(of: "ze", with: "[sz]{1}e")
        words.append("\(patternWord)")
    }
}
words.forEach {word in
  let regexPattern = word
  let matches = findmatches(forRegex: regexPattern, inText: multiLine)
  print(matches.count)
  
}

```
