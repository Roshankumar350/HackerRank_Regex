# Problem: 

https://www.hackerrank.com/challenges/hackerrank-language/problem

# Solution:

```
import Foundation

// Enter your code here 

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

let validLanguage = "C:CPP:JAVA:PYTHON:PERL:PHP:RUBY:CSHARP:HASKELL:CLOJURE:BASH:SCALA: ERLANG:CLISP:LUA:BRAINFUCK:JAVASCRIPT:GO:D:OCAML:R:PASCAL:SBCL:DART:GROOVY:OBJECTIVEC"


let regexPattern = #"(\d{4,5})\s([A-Z]{1,20})"#

let times = Int(readLine()!)!

var multilLine = """
"""
(1...times).forEach { _ in
    let text = readLine()!
    multilLine.append(text)
    multilLine.append("\n")
}

let results = matches(forPattern: regexPattern, inText: multilLine)
let languages = validLanguage.components(separatedBy: ":").map{$0.trimmingCharacters(in: .whitespaces)}
results.forEach{ result in 
    if let api_id = Int(result[0]), api_id >= 10000 && api_id < 100000 {
        let language = result[1]
        if languages.contains(language.trimmingCharacters(in: .whitespacesAndNewlines)) {
           print("VALID")
        } else {
            print("INVALID")
        }
    } else {
        print("INVALID")
    }
    
}


```
