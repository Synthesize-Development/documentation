# Roblox Module

## Settings

### `API_KEY`
This key is given to you when setting up the bot. You can either store the key as plain text here or as a secret

=== "Plain Text"

    ```lua
    API_KEY = "EXAMPLEKEY_1234567"
    ```

=== "Roblox Secret"

    ```lua
    API_KEY = game:GetService("HttpService"):GetSecret("API_KEY")
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

```
module.
```