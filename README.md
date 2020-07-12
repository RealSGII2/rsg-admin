# RSG Admin
A new administrator system for Roblox developed by RealSGII2.

## What is it?
It's an administrator system created out of pure boredom. It's based off of Nexus Admin and the deprecated Sync Admin (off-sale).

## How do I get the model?
You can get it via this link: https://www.roblox.com/library/5338792953/RSG-Admin-Loader
It is a loader so you don't have to worry about updating the model every time you get an update.

## How do I set it up?
The loader itself is the configuration. The properties are listed below:
| **Property**              | **Type**    | **Description**                                                                                                                                                                                     | **Example**              | **Default**                 |
|---------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|-----------------------------|
| Prefix                    | String      | The character(s) a user types before a command to execute it.                                                                                                                                       | !                        | ;                           |
| CommandBarKeybind         | KeyCodeEnum | The character on your keyboard you press to open the command line.                                                                                                                                  | `Enum.KeyCode.BackSlash` | `Enum.KeyCode.KeypadPeriod` |
| AllowCommandBar           | Boolean     | Should the command bar be shown if you press the correct key?                                                                                                                                       | `false`                  | `true`                      |
| NilCommandException       | Boolean     | Should an error show if a command doesn't exist?                                                                                                                                                    | `false`                  | `true`                      |
| ForbiddenCommandException | Number      | What should happen when a user attempts a command they don't have access to? `0`: Nothing; `1`: Tell the user the command doesn't exist; `2`: Tell the user they don't have access to that command. | `0`                      | `2`                         |
| Admins                    | Table       | A list of admins who can use the system.                                                                                                                                                            |                          |                             |
| Moderator                 | List        | A list of users with rank 1 (Moderator). This accepts UserIds or Usernames.                                                                                                                         | `"SGII2", 1234567`       | `"UsernameHere", 1234567`   |
| Admin                     | List        | A list of users with rank 2 (Admin). This accepts UserIds or Usernames.                                                                                                                             | `"madattak", 7654321`    | `"SomebodyElse", 7654321`   |
| Owner                     | List        | A list of users with rank 3 (Owner). This accepts UserIds or Usernames.                                                                                                                             | `57095879`               |                             |
| Creator                   | List        | A list of users with rank 4 (Creator). This accepts UserIds or Usernames. The owner of a game doesn't need to list them self here.                                                                  | `"a_username"`           |                             |

### What do these different ranks mean?
> More support for these will be added in the future.

These ranks determine which commands can be used by who.

## Can I add custom commands?
Of course you can! There is a simple API to add commands. However, you need to know Lua in order to use it.
1. Add a new script to `ServerScriptService`. You can name it whatever you want.
2. Wait for the admin to load. A global variable named `RGSALoaded` will become `true` once it's loaded. **Make sure this line is the first line in the file.**
```lua
repeat wait() until (_G.RGSALoaded ~= nil)
```
3. Get the API. Using this you can add commands, send messages and hints, and configure it. To add commands, get the admin's `CommandService`. Read more about the API and CommandService in the wiki.
```lua
local API = _G.GetRSGA()
local CS = API.CommandService
```
4. Add a command using the `CommandService:AddCommand()` method. Pass a `CommandConfigTable` to it. Read more about how to add commands in the wiki.
```lua
CS:AddCommand({
	Name = "examplecommand";
	Aliases = {"example"};
	Permission = 1;
	Description = "This is a command.";
	Args = {};
	Module = "Example";
	Execute = function (s, Ctx, ArgumentParser)
		
	end
})
```
5. Add your functions and settings to the command. Once the Admin loads, your command will be added.
