## Settings

### API_KEY
This key is given to you when setting up the bot. You can either store the key as plain text here or as a secret

=== "Plain Text"

    ```lua
    API_KEY = "EXAMPLEKEY_1234567";
    ```

=== "Roblox Secret"

    ```lua
    API_KEY = game:GetService("HttpService"):GetSecret("API_KEY");
    ```

### PROFILE_SERVICE
If you are currently using profile service, put its path here

=== "Default"

    Locksy will generate its own profile service instance

    ```lua
    PROFILE_SERVICE = nil;
    ```

=== "Path Provided"

    Use this if you already have a ProfileService handeler running

    ```lua
    PROFILE_SERVICE = game:GetService("ServerScriptService").ProfileHandeler;
    ```

    Your custom ProfileHandeler must contain the following method

    ```lua
    module.GetProfile = function(player :Player) :table
        return *THE PLAYERS PROFILE*
    end
    ```

### ENFORCE_BAN_LIST
When a player who is on our list of known predators and bad actors joins your game should it kick them

=== "Enabled"
    ```lua
    ENFORCE_BAN_LIST = true;
    ```

=== "Disabled"
    ```lua
    ENFORCE_BAN_LIST = false;
    ```

### ERP_API_KEY
If you get approved for an API_KEY from [Ruben Sim's erpsearcher](https://erpsearcher.com/dashboard) you can put it here and we will handle kicking them

=== "No Key"

    ```lua
    ERP_API_KEY = nil;
    ```

=== "API Key"

    ```lua
    ERP_API_KEY = "SEARCHER_example1234567example1234567";
    ```

### WEBHOOK
Place your webhook here for all moderation actions to be logged

=== "Enabled"
    ```lua
    WEBHOOK = "https://discord.com/api/webhooks/1234567890/example1234567_example1234567890";
    ```
=== "Disabled"
    ```lua
    WEBHOOK = "";
    ```

----------


## Types

### LocksyTier
```lua
type LocksyTier = "FREE" | "PAID"
```

### PossibleAddons
Describes what addons are available
```lua
type PossibleAddons = "MEDALS AND QUALIFICATIONS" | "CUSTOM UNIFORMS" | "FACTIONS"
```

### Info_Return
```lua
type Info_Return = {
    Status: boolean,                --Did it work?
    GroupName: string,              --Name of the group
    GroupID: number,                --ID of the group
    VerifiedMembers: number,        --How many members from your group in the system
    LocksyTier: LocksyTier,         --What tier are you running
    LocksyAddons: {PossibleAddons}, --List of all active addons
}
```

### XP_Return
```lua
type XP_Return = {
    Status: boolean,        --Successfull?
    XP_Val: number,         --Users new XP value (-1 if error)
    Last_Updated: number    --UNIX Timestamp (-1 if error)
}
```



------

## Functions

The main `LOCKSY` module script contains all the function you will ever need to call. They are all described below.

### GetInfo

Gets information about this groups running Locksy instance
```lua
Locksy.GetInfo() :Info_Return
```

### GetUserXP

Gets a users XP value
```lua
Locksy.GetUserXP(userid :number) :XP_Return
```

### SetUserXP

Sets a users XP value to the given value
```lua
Locksy.SetUserXP(userid :number, value :number) :XP_Return
```

### UpdateUserXP

Changes a users XP value by the ammount
```lua
Locksy.UpdateUserXP(userid :number, ammount :number) :XP_Return
```