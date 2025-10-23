# Settings

### `API_KEY`
This key is given to you when setting up the bot. You can either store the key as plain text here or as a secret

=== "Plain Text"

    ```lua
    API_KEY = "EXAMPLEKEY_1234567";
    ```

=== "Roblox Secret"

    ```lua
    API_KEY = game:GetService("HttpService"):GetSecret("API_KEY");
    ```

### `PROFILE_SERVICE`
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

    Your custom ProfileHandeler must contain the following methods

    ```lua
    module.GetProfile = function(player :Player) :table
        return *THE PLAYERS PROFILE DATA*
    end

    module.SetProfile = function(player :Player, val :table) :boolean
        *SET THE PLAYERS DATA TO THE VAL*
        return true
    end
    ```

### `ENFORCE_BAN_LIST`
When a player who is on our list of known predators and bad actors joins your game should it 

---------

# API

## Types

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

### GetUserXP

Gets a users XP value
```lua
Locksy.GetUserXP(userid :number) :XP_Return
```

### SetUserXP

Sets a users XP value
```lua
Locksy.SetUserXP(userid :number) :XP_Return
```

### UpdateUserXP

Sets a users XP value
```lua
Locksy.UpdateUserXP(userid :number, ammount :number) :XP_Return
```