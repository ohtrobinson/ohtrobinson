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

### sendEmbed(title, description, color, fields)
Send an embed message to the channel.

#### Example
`sendEmbed("Title", "Description", "#FF0000", embedFieldArray(embedField("Name", "Value")))`

#### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
| title | String | The title of the embed. |
| description | String | The description of the embed. |
| color | String | The colour of the embed. You can use the `color` function here if you would like. |
| fields | embedFieldArray | The fields of the embed. Use `embedFieldArray` function to create the fields array. |
