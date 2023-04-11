# Using ox_lib with Loki

Now that you have installed Loki and Grafana, you can using ox_lib to send logs to Loki.

## Install ox_lib

- Download the latest `ox_lib.zip` from [here](https://github.com/overextended/ox_lib/releases/latest)
- Open `ox_lib.zip` and copy the `ox_lib` folder to your server's `resources` folder
- Add `ensure ox_lib` in your server.cfg 

## Configure ox_lib logger

You will get all the convars that are needed for ox_lib at the end of the installation process. Add them to your server.cfg. They will look like the following:

```lua
set ox:logger "loki"
set loki:user "admin"
set loki:key "supersecurepassword"
set loki:key "https"
set loki:endpoint "loki.fivem-loki-demo.illenium.gg"
```

## Send logs

Add `ox_lib` to your resource via fxmanifest.lua:

```lua
shared_script '@ox_lib/init.lua'
```

Then you can send logs from the server-side using `lib.logger` like so:

```lua
lib.logger(source, event, message, ...)

-- Example
lib.logger(-1, 'CreateVehicle', "A vehicle was created")
```

Refer to the detailed documentation about the function [here](https://overextended.github.io/docs/ox_lib/Logger/Server)
