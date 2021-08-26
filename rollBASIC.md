# rollBASIC Reference
This reference contains every built-in function, variable, and keyword you can use.

## Key
* Optional parameters are marked with a `?` after their name. This means the parameter is optional and does not need to be filled.

## Functions
### send(message, channelID?)
Send a message to the (optional) given channel ID. If no channel ID is provided, the message will be sent to the current channel.

#### Example
`send("Hey there!")`

`send("Hello!", getChannel("my-channel-name"))`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| message | String | The message to send. |
| channelID? | String | The channel ID to send the message to. |

#### Returns
| Type | Description |
| String | The sent message ID. |

### sendEmbed(title, description, color, fields)
Send an embed message to the channel.

#### Example
`sendEmbed("Title", "Description", "#FF0000", Array(EmbedField("Name", "Value")))`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| title | String | The title of the embed. |
| description | String | The description of the embed. |
| color | String | The colour of the embed. You can use the `Color` function here if you would like. |
| fields | Array | The fields of the embed. Use `Array` function to create the fields array. |

#### Returns
| Type | Description |
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
