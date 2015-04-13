# GuessNumberTest


这是一个猜数字游戏。有一个是已经写好的model，计算公式。另一个是自己写的 while loop

### 写好的model在helpers.swift里：
import Foundation

func input() -> String {
  let keyboard = NSFileHandle.fileHandleWithStandardInput()
  let inputData = keyboard.availableData
  let rawString = NSString(data: inputData, encoding:NSUTF8StringEncoding)
  if let string = rawString {
    return string.stringByTrimmingCharactersInSet(NSCharacterSet.whitespaceAndNewlineCharacterSet())
  } else {
    return "Invalid input"
  }
}

func randomIntBetween(low:Int, high:Int) -> Int {
  let range = high - (low - 1)
  return (Int(arc4random()) % range) + (low - 1)
}

### 自己的while loop 在main.swift 里：
import Foundation

let answer = randomIntBetween(0, 100)

var turn = 1

while (true){
    
    turn = turn + 1
    println("Guess #\(turn):Enter the number between 1 and 100.")

let userInput = input()

let newInput = userInput.toInt()

if let guess = newInput{
    if ( guess > answer){
        println("higher!")
    }else if (guess < answer){
        println("lower!")
    }else {
        println("Correct! The right is \(answer)")
        break
    }
}else {
    println("Please enter the right number")
    continue
    }

}

println("You just have \(turn) tries！")
