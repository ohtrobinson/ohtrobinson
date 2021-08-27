# rollBASIC Reference
This reference contains every built-in function, variable, statement, and keyword you can use.

rollBASIC syntax has been inspired off of various different programming languages. Its syntax however is mostly constrained around the compiler, and does contain some unusual things not found in C-like programming languages.

To use rollBASIC effectively, you must get used to the `is` and `as` keywords, to define variables. While the `is` keyword can be substituted with `=` when defining variables, its usage is not recommended and may be removed from future updates. In if statements, the `is` keyword cannot be substituted with `=`.

## Variables
Defining variables is done in one of three ways.
`x is "hello"` - The recommended way to create variables in this form factor.

`x = "hello"` - Not recommended. May be removed in later iterations of rollBASIC.

When using functions, or the `repeat` statement, the `as` keyword is used.

`getChannel("general") as channel`

`repeat for 5 times as i`

These values can be used just like regular variables, they are just defined differently. Note that `"hello" as x` will NOT work under any circumstances.

## Statements
### repeat
The `repeat` statement means a loop will be used. There are two types of loops, which you may be familliar with. `for`, and `while`. Note that these loops have some limitations. A `for` loop cannot repeat for more than 255 times. The total number of loops for a script cannot exeed 1000 currently. This is to reduce load on roll itself, to make sure the bot runs fast and well for everyone. These limits are subject to change (although are unlikely to decrease).

Currently, the only loop that has been implemented is the `for` loop.
For loops can be used as such:

```
repeat for 5 times as i
  send(i)
end
```

Note: You must include an "as" value. Howver, you do not need to include "times". `repeat for 5 as i` will work just fine.

### if
If statements have not yet been implemented. - This is on the todo list.

### end
All if statements & repeat statements must have an `end` statement at the end of it. Use the loop example above:

```
repeat for 5 times as i
  send(i)
end
```

## Comments & spaces
Like any programming language, you can include line spaces in your code, to make it more legible. This does not count towards your final line count.

Comments cannot currently be used on the same line as code. Comments are denoted using the `#` symbol.

## Operators
Currently, the only operator is the `+=` operator. This allows you to concatinate a string value to an already existing variable.

## Reserved variable names
The following variable names cannot be set by the user:
* msg
* args
* code
* compiled
* if
* as
* is
* false
* true
* none
* repeat

## Built in variables
The following variables are built in:
* `message` - Returns the message ID of the author's message.
* `message.channel` - Returns the channel ID of the author's message.
* `message.channel.name` - Returns the channel name of the author's message.
* `message.channel.mention` - Mentions the channel the author's message was sent in.
* `message.author` - Mentions the message author.
* `message.author.displayName` - Returns the message author's **display name** (NOT username)
* `message.arguments` - Returns an array of arguments for the message. These are seperated by spaces, and can be joined together using the `join` function.

## Literals
* `true` - Represents a boolean true.
* `false` - Represents a boolean false.
* `none` - Represents null or a NoneType.

## Functions & Objects Key
* Optional parameters are marked with a `?` after their name. This means the parameter is optional and does not need to be filled.
* Parameters with `...` after the parameter name accept infinite parameters, seperated with a comma.

## Functions
### send(message, channelID?)
Send a message to the (optional) given channel ID. If no channel ID is provided, the message will be sent to the current channel.

#### Example
`send("Hey there!") as mesg`

`send("Hello!", getChannel("my-channel-name")) as mesg`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| message | String | The message to send. |
| channelID? | String | The channel ID to send the message to. If none is provided, this value will default to the current channel ID. |

#### Returns
| Type | Description |
| ---- | ----------- |
| String | The sent message ID. |

### sendEmbed(title, description, color, fields)
Send an embed message to the channel.

#### Example
`sendEmbed("Title", "Description", "#FF0000", Array(EmbedField("Name", "Value"))) as mesg`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| title | String | The title of the embed. |
| description | String | The description of the embed. |
| color | String | The colour of the embed. You can use the `Color` function here if you would like. |
| fields | Array | The fields of the embed. Use `Array` function to create the fields array. |

#### Returns
| Type | Description |
| ---- | ----------- |
| String | The sent message ID. |

### getChannel(channelNameOrId)
Returns the channel ID of the given channel.

#### Example
`getChannel("general") as channel`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| channelNameOrId | String | The channel name, or ID. |

#### Returns
| Type | Description |
| ---- | ----------- |
| String | The channel ID. |

### channelExists(channelNameOrId)
Returns whether the given channel name or ID exists on the current guild.

#### Example
`channelExists("general") as exists`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| channelNameOrId | String | The channel name, or ID. |

#### Returns
| Type | Description |
| ---- | ----------- |
| Boolean | Whether the channel exists or not. |

### lower(text)
Converts the entire text string to lowercase.

#### Example
`lower("HELLO") as low`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| text | String | The text to make lowercase. |

#### Returns
| Type | Description |
| ---- | ----------- |
| String | The lowercase string. |

### upper(text)
Converts the entire text string to uppercase.

#### Example
`upper("hello") as up`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| text | String | The text to make uppercase. |

#### Returns
| Type | Description |
| ---- | ----------- |
| String | The uppercase string. |

### rand(low, high)
Generate a random number between two numbers. NOTE: This function currently uses strings. Literally, you need to encase the number in "" speech marks. **This will be fixed in due course.**

#### Example
`rand("1", "10") as num`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| low | String | The lowest number the random number should be (inclusive). |
| high | String | The highest number the random number should be (inclusive). |

#### Returns
| Type | Description |
| ---- | ----------- |
| String | The random number. |

### join(array, joinString)
Join each element in the array with the given join string.

#### Example
`join(Array("hello", "there"), " ") as str` - Will return `hello there`.

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| array | Array | The array of elements. |
| joinString | String | The string to join each element with. |

#### Returns
| Type | Description |
| ---- | ----------- |
| String | The joined string. |

### elementAt(array, index)
Return the array element at the given index. NOTE: Arrays are zero-indexed. NOTE: This function currently uses strings. Literally, you need to encase the number in "" speech marks. **This will be fixed in due course.**

#### Example
`elementAt(Array("hello", "there"), "1") as index` - Will return `there`.

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| array | Array | The array of elements. |
| index | String | The index of the element. |

#### Returns
| Type | Description |
| ---- | ----------- |
| String | The element at the given index. |

## Objects
Objects represent certain element types, that can be accessed with certain functions. Objects cannot be used like classes or structs, so the `.` or `->` operators cannot be used. Object attributes can only be accessed with the given function.

Object "constructors" work exactly like functions. That is because to the compiler, objects essentially _are_ functions. However, they do create a JavaScript object, which is why they are treated as objects and not functions. Object "constructors" are discerned by using PascalCase instead of camelCase which functions use.

Objects, however, are more akin to structs, as they are value types only and do not contain methods. For the purposes of rollBASIC however, they will be referred to as objects, despite not strictly being objects.

### Array(elements...)
Represents an array of elements.

#### Example
`Array("hello", "there", "item 3") as arr`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| elements | Any | Represents an array of items, seperated by a comma. There is no maximum length of items. |

### EmbedField(name, value, inline?)
Represents an embed field, consisting of a name (the white title), the value (the gray text), and whether it is inline (on the same line as up to 3 other fields). By default, this value is false.

#### Example
`EmbedField("Name", "Value") as field`

`EmbedField("Name", "Value", true) as field`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| name | String | The name of the field. |
| value | String | The value of the field. |
| inline? | Boolean | Whether the field is inline or not. By default, this is false. |

### Color(r, g, b)
Represents an RGB colour, which gets converted to a hex string. NOTE: This constructor currently uses strings. Literally, you need to encase the number in "" speech marks. **This will be fixed in due course.**

#### Example
`Color("255", "128", "34") as col`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| r | String | Represents the red component of this colour. |
| g | String | Represents the green component of this colour. |
| b | String | Represents the blue component of this colour. |
