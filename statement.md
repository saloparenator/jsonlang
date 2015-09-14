A statement represent one operation in a function.

variable assignation
```erlang
stringVar = 'value'
numVar = 5.0
boolVar = true
listVar = ['value',5,true]
dictVar = {
  keyA : 'value',
  keyB : 5,
  keyC : [],
  keyD : {}
}
refVar = otherVar
```

function call
```erlang
returnValueA = nonaryFunction()
returnValueB = unaryFunction(param)
returnvalueC = binaryFunction(paramA,paramB)
returnValueD = tenaryFunction(paramA, paramB, paramC)
```

operator
```erlang
addition = a + b
substraction = a - b
multiplication = a * b
division = a / b
modulo = a % b
exponent = a^b
chain = (a^2 + b^2)^0.5

boolean = a and (b or c) xor (d == 5)

concatenation = 'hello' ++ ' ' ++ 'world'

listAtFifth = list[5]
listWhereOdd = list[this % 2 == 0]

dictAttribute = dict.attribute
```
*note [this % 2 == 0] is a predicate*

native function
```erlang
first([],default=[])
rest([])
tail([],default=[])
size([])
sum([])
agg(value,list)

regexFind(regex,string,flag='')
regexSub(regex,substitute,string,flag='')

```

implementation function
```erland
print({0:1})
load(destination)
save(destination,value)
update(destination,value)
del(destination)
```
