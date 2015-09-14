qsort
```json
	{
		"name" : "qsort",
		"code" : [
			{
				"predicate" : [
					"isList(param)",
					"not(isEmpty(param))"
				],
				"function" : [
					"pivot = first(param)",
					"rest = rest(param)",
					"bigger = qsort(rest[this > pivot])",
					"smaller = qsort(rest[this <= pivot])",
					"smaller ++ [pivot] ++ bigger"
				]
			}
		]
	}
```

fizzbuzz
```json
	{
		"name" : "fizzbuzz",
		"code" : [
			{
				"predicate" : [
					"isNumber(param)",
					"param % 3 == 0",
					"param % 5 == 0"
				],
				"function" : [
					"fizzbuzz"
				]
			},
			{
				"predicate" : [
					"isNumber(param)",
					"param % 3 == 0"
				],
				"function" : [
					"fizz"
				]
			},
			{
				"predicate" : [
					"isNumber(param)",
					"param % 5 == 0"
				],
				"function" : [
					"buzz"
				]
			},
			{
				"predicate" : [
					"isNumber(param)"
				],
				"function" : [
					"param"
				]
			}
		]
	}
```
