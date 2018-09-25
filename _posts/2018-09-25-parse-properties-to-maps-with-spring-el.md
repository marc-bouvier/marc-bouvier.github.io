---
tags : Spring Java How-To Properties Configuration
---
Spring EL allows to map strings into complex objects. We can leverage that to store and read non trivial configuration from properties files.

You can use the SPEL json-like syntax to write a simple map or a map of list in property file.
```
    simple.map={'KEY1': 'value1', 'KEY2': 'value3', 'KEY3': 'value5'}
    
    map.of.list={\
      'KEY1': {'value1','value2'}, \
      'KEY2': {'value3','value4'}, \
      'KEY3': {'value5'} \
     }
```

I used `\` for multiline property to enhance readability

Then, in Java, you can access and parse it automatically with `@Value` like this.
```
    @Value("#{${simple.map}}")
    Map<String, String> simpleMap;
    
    @Value("#{${map.of.list}}")
    Map<String, List<String>> mapOfList;
```

Here with `${simple.map}`, `@Value` gets the following String from the property file:

```
    "{'KEY1': 'value1', 'KEY2': 'value3', 'KEY3': 'value5'}"
```

Then, it is evaluated as if it was inlined 

```
    @Value("&#35;{ { 'KEY1': 'value1', 'KEY2': 'value3', 'KEY3': 'value5'} }")
```

You can learn more in [the official documentation](https://docs.spring.io/spring/docs/4.3.10.RELEASE/spring-framework-reference/html/expressions.html#expressions-inline-lists)
