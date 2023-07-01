# Problem: 

https://www.hackerrank.com/challenges/find-substring/problem

# Solution:

```
import Foundation

func findMatches(for pattern: String, inText text: String) -> Int {
    let regex = try? NSRegularExpression(pattern: pattern)
    
    if let matches = regex?.matches(in: text, range: NSRange(text.startIndex... , in: text)) {
        return matches.count
    }
    
    return 0
}

var times = Int(readLine()!)!
var multiLine = """
"""
(1...times).forEach { _ in
    if let line = readLine() {
        multiLine.append(line)
        multiLine.append("\n")
    }
}
// print(multiLine)

var wordsTimes = Int(readLine()!)!
var toFindWords = [String]()

(1...times).forEach {_ in
     if let word = readLine() {
         toFindWords.append(word)
      }
}

//print(toFindWords)

toFindWords.forEach{ word in  
   let pattern = #"\w"# + word + #"\w"#
   print(findMatches(for: pattern, inText: multiLine))
}


```
