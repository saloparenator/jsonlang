# jsonlang
json based programming language

synthax specification

```json
{
  "name" : "hello",
  "doc" : "construct an hello message and call print(hello message) then return the message",
  "code": [
    {
      "doc" : "with no parameter",
      "function" : [
        "msg = 'hello world'",
        "print(msg)",
        "msg"
      ]
    },
    {
      "doc" : "with one parameter and a predicate that make sure it is a non empty string",
      "param" : ["who"],
      "predicate" : [
        "isString(who)",
        "not empty(who)"
      ],
      "function" : [
        "msg = 'hello ' ++ who",
        "print(msg)",
        "msg"
      ],
    },
    {
      "doc" : "with the same parameter but if it is a list, repeat, note that last call is tail recursive",
      "param" : ["whom"],
      "predicate" : [
        "isList(whom)",
        "not empty(whom)"
      ],
      "function" : [
        "hello(first(whom))",
        "hello(rest(whom))"
      ]
    }
  ]
}
```
This function have three declarations. hello(), hello(who) and hello(whom)
