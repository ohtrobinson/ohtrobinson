# Key
`[Allows variables]` in a description means you can substitute values with `$variables`.

# Commands
### send TEXT
[Allows variables] Send a message as the bot.

#### Example
`send Testing.`

#### Parameters [OPTIONAL]
| Name | Usage | Description |
| - | - | - |
| --channel CHANNEL_ID | `--channel 619626439179763723` | Send a message to a specific channel. |
| --member MEMBER_ID | `--member 276384253166747649` | Send a message to a specific member. |

### sendembed EMBED_JSON
[Allows variables] Send an embed message as the bot.

#### Example
`sendembed {"title":"Hello!", "description":"Description!"}`

#### Parameters [OPTIONAL]
| Name | Usage | Description |
| - | - | - |
| --channel CHANNEL_ID | `--channel 619626439179763723` | Send a message to a specific channel. |
| --member MEMBER_ID | `--member 276384253166747649` | Send a message to a specific member. |
| --store VALUE | `--store text` | Store the message context so it can be retrieved later. |

### variable VAR_NAME VAR_VALUE
[Allows variables] Create a variable (string) of the given name & value.

#### Example
`variable text Hello there!`

### react MESSAGE_ID EMOJI CHANNEL_ID
[Allows variables] React to a specific message. A channel must be provided.

#### Example
`react 821177226036248587 ✅ 619626439179763723`

### if VALUE1 CONDITION VALUE2
[Allows variables] Evaluate something.

#### Example
```
variable x 4
variable y 5
if $x == $y
send Yes.
endif
```

#### Operators
| Operator | Description |
| - | - |
| = | Runs if the two values are equal. |
| == | Same as `=`. |
| != | Runs if the two values are **not** equal. |
| contains | Runs if the first value contains the text of the second value |
| hasrole | Runs if the guild member in `value1` has the role ID of `value2`.
| nothaverole | Runs if the guild member in `value1` **does not** have the role ID of `value2`. |

### delete MESSAGE_ID [Optional] CHANNEL_ID
[Allows variables] Delete a message with the given ID.

#### Example
`delete 821179037736239116`
OR
`delete 821179037736239116 619626439179763723`

### stop
Stop execution of the script.

#### Example
```
if 3 != 4
stop
endif
```

### store VALUE_NAME VALUE_DATA
[Allows variables] Store the given value data at the value name, able to be retrieved later.

#### Example
`store text Hello, this is some text.`

### load VALUE_NAME VARIABLE_OUT_NAME
[Allows variables] Load the given value name (which you would have stored using `store`) into the given variable out name.

#### Example
`load text storedText`

### giverole MEMBER_ID ROLE_ID
[Allows variables] Give the given member the role.

#### Example
`giverole 276384253166747649 566679649552171037`

### removerole MEMBER_ID ROLE_ID
[Allows variables] Remove the given role from the member.

#### Example
`removerole 276384253166747649 566679649552171037`

### sleep DELAY_IN_MILLISECONDS
Sleep for the given number of milliseconds.

#### Example
`sleep 1000`

# Built in variables

### $guildMemberCount
Returns the number of members in the guild.

### $getMessageArgs
Returns all the message arguments as a string.

### $getMessageArgsARGUMENT_STARTING_POINT
(Example: `$getMessageArgs1`) Return all the message arguments as a string, starting at the argument starting point.
(For example, you have arguments: `Hello there, this is a test.` By using `$getMessageArgs1` you will return `there, this is a test.`)

### $getMessageArgumentARGUMENT_NUMBER
(Example `$getMessageArgument1`) Get the current message argument at the specified position. Arguments are seperated by spaces.
(For example, you have arguments: `Hello there, this is a test.` By using `$getMessageArgument1` you will return `there,`)

### $null
A null parameter. Useful in if statements.

### $undefined
An undefined parameter. Useful in if statements.

### $getCommandMessage
Return the command message ID.

### $getCommandChannel
Return the command channel ID.

### $getCommandAuthor
Return the command author ID.

### $mentionCommandAuthor
Mentions the command author.

### $getCommandAuthorDisplayName
Returns the command author's display name

### $getCommandAuthorPicture
Returns the avatar URL of the command author. Can be used in embeds.

### $randMAX_NUMBER
(Example: `$rand100`) return a number between 0 and the max number.

# Example code
```
variable channel 814478934074327090
variable sendChannel 814478960351903764
if $getCommandChannel != $sendChannel
sendembed {"description":"Please submit your suggestion in <#$sendChannel>!", "color":"0xFF0000"}
stop
endif
delete $getCommandMessage
variable text $getMessageArgs
if $text == $undefined
sendembed --store noSuggestionMessage {"description":"You need to provide a suggestion! A blank suggestion cannot be submitted.", "color":"0xFF0000"}
sleep 5000
delete $noSuggestionMessage
stop
endif
variable id $rand99999
load text$id check
if $check != $undefined
sendembed --store oopsMessage {"description":"Sorry, something went a bit wrong. Please try again, if this error keeps occuring, please contact @Toasty", "color":"0xFF0000"}
sleep 5000
delete $oopsMessage
stop
endif
sendembed --store embed --channel $channel {"title":"New Music Suggestion", "description":" $getMessageArgs ", "author":{"name":" $getCommandAuthorDisplayName ", "icon_url":" $getCommandAuthorPicture "}, "color":"0xFFFF00", "footer":{"text":"ID: $id "}}
sendembed --store sentMessage {"description":"Your suggestion has been submitted!", "color":"0x00FF00"}
react $embed :white_check_mark: $channel
react $embed :x: $channel
react $embed :thinking: $channel
store text$id $getMessageArgs
store author$id $getCommandAuthor
store authorDisplayName$id $getCommandAuthorDisplayName
store authorPicture$id $getCommandAuthorPicture
store message$id $embed
sleep 5000
delete $sentMessage
```
