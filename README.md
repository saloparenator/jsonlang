# jsonlang
json based programming language

synthax specification

Every tutorial start with hello world.
But I will show a function because there are more important to learn than print()
```json
{
  "name" : "hello",
  "code" : {
    "function" : [
      "msg = 'hello world'",
      "print(msg)",
      "msg"
    ]
  }
}
```
A function generaly take parameter but always return something.
return value is the result of the last statement in function
```json
{
  "name" : "hello",
  "code": {
    "function" : [
      "msg = 'hello ' ++ param.who",
      "print(msg)",
      "msg"
    ],
  }
}
```
In fact parameter always exist in the scope of a function.
But if the function is called like hello(), then the parameter variable will be empty.
btw function are polymorphic
```json
{
  "name" : "hello",
  "code": [
    {
      "predicate" : [
        "isEmpty(param)"
      ],
      "function" : [
        "msg = 'hello world'",
        "print(msg)",
        "msg"
      ]
    },
    {
      "predicate" : [
        "isString(param)"
      ],
      "function" : [
        "msg = 'hello ' ++ param.who",
        "print(msg)",
        "msg"
      ],
    }
  ]
}
```
code can contain a list of function declaration, it will execute the first one unless there is a predicate that fail, then it will execute next en return an unsuported parameter exception
But all we got is a function where 
hello("") will result in -> hello 
hello(["bob","mary"]) will result in -> hello [bob,mary]
```json
{
  "name" : "hello",
  "code": [
    {
      "predicate" : [
        "isEmpty()"
      ],
      "function" : [
        "msg = 'hello world'",
        "print(msg)",
        "msg"
      ]
    },
    {
      "predicate" : [
        "isString(param)"
      ],
      "function" : [
        "msg = 'hello ' ++ param.who",
        "print(msg)",
        "msg"
      ],
    },
    {
      "predicate" : [
        "isList(param)"
      ],
      "function" : [
        "hello(first(whom))",
        "hello(rest(whom))"
      ]
    }
  ]
}
```
Yes function are recursive.
And [Tail Call optimisation](https://en.wikipedia.org/wiki/Tail_call) is part of the specification.
But this is just another functional programming language.
We need documentation, logging and unitesting and everything that give industrial strenght.
```json
{
  "name" : "hello",
  "doc" : "will display an hello message",
  "code": [
    {
      "doc" : "without parameter, just display 'hello world'",
      "predicate" : [
        "isEmpty()"
      ],
      "function" : [
        "msg = 'hello world'",
        "print(msg)",
        "msg"
      ],
      "test" : []
    },
    {
      "doc" : "when provided a name, replace world with the name",
      "predicate" : [
        "isString(param)"
      ],
      "function" : [
        "msg = 'hello ' ++ param.who",
        "print(msg)",
        "msg"
      ],
      "test" : []
    },
    {
      "doc" : "when provided a list, do it in loop",
      "predicate" : [
        "isList(param)"
      ],
      "function" : [
        "hello(first(whom))",
        "hello(rest(whom))"
      ],
      "test" : []
    }
  ],
  "test" : [
    "'hello world' == hello()",
    "'hello jack' == hello('jack')",
    "'hello bob' == hello(['jack','alysson','bob'])",
    "'unsupported parameter on hello()' == hello({'key':'val'})"
  ]
}
```
And for logging, it is transparently added.
By specification : 
Every function call will be logged like : 
```json
{
  "id" : "logid",
  "date" : "yyyy/mm/dd",
  "time" : "HH:MM:SS.ttt",
  "function" : "functionname",
  "param" : {...},
  "scope" : {...},
  "return" : "return value or exception",
  "parent" : "logid"
}
```
And because this is a draft, I think it is not out of scope to handle more functionality like, metaprogramming, annotation, decorator, memoisation, lazy eval...
