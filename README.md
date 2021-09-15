# exString
A small lua module that aims to extend the standard lua string library.
It provides a selection of functions that can be appended to the string table if desired.

I'd like to note off the top, If you have a decent grasp of the standard library, This module is probably useless to you.

Here's the functions it comes with:
### exString.import()
If you call this function, All the exString functions will be appended to the string table, Meaning you can call them like the standard library functions.
```
local exString = require("exString")
exString.import()

local str = "Hello world!"
str:print()
-- or
string.print(str)
```
All code examples after this point assume you've used exString.import()

### exString:startsWith(str, start) / exString:endsWith(str, end)
These functions return true if 'str' starts with or ends with the 2nd argument
```
local str = "Hello world!"
print(str:startsWith("Hell"))
> true

print(str:endsWith("foo"))
> false
```

### exString.append(str, delimiter, ...)
This function appends all arguments after the 2nd one to 'str' and returns it,
Optionally seperates the arguments with a delimiter if one is provided.
```
local str = "Hello"
local str2 = str:append(" ", "World!"):print()
> "Hello World!"
```

### exString.split(str, delimiter)
This functions splits a string by a delimiter. And returns the results as a table. 'delimiter' defaults to ",". The delimiter is removed from the results.
```
local str = "This,is,string"
for i,v in ipairs(str:split()) do
   print(v)
end
> This
> is
> string
```

### exString.strip(str)
This functions will remove any trailing and leading punctuation and whitespace characetrs from a string.
```
local str = "  .,.Hello.world!.,.  "
str:strip():print()
> "Hello.world"
```

### exString.join(delimiter, ...)
As i'm writing this i realized this function is almost exactly the same as exString.append. I'll probably remove this.

### exString.replace(str, target, repl)
This is probably the least useful function here, It's just an alias for string.gsub. Although the name might make your code a little clearer for someone not familiar with gsub.
```
local str = "Hello world!"
str:replace("world", "moon"):print()
> "Hello moon!"
```

### exString.print(str)
This is just an alias to print(), But implemented like this it can be called directly on a string.
```
local str = "Hello world!"
str:print()
> "Hello world!"
```
