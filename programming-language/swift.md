# Hello World
```swift
print("Hello, world!")
```

# 变量
```swift
var foo = 1
foo = 2
print(foo) // 2
```

# 常量
```swift
let foo = 1
foo = 2 // error
```

# 类型转换
```swift
let label = "The width is "
let width = 94
let widthLabel = label + String(width)
print(widthLabel)
```

# 字符串里的值
```swift
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let orangeSummary = "I have \(apples + oranges) pieces of fruit."
print(appleSummary) // 3
print(orangeSummary) // 8
```

# 多行字符串
```swift
var foo = """
First line.
Second line.
"""
print(foo)
```

# 数组
```swift
var intArray = [ 1, 2, 3 ]
intArray[0] = 0
intArray.append(4)
print(intArray)
var emptyArray = [String]()
print(emptyArray)
emptyArray = []
print(emptyArray)
```

# 字典
```swift
var fooDictionary = [
    "one": 1,
    "two": 2,
    "three": 3,
]
print(fooDictionary)
var emptyDictionary = [String: Float]()
print(emptyDictionary)
emptyDictionary = [:]
print(emptyDictionary)
```
