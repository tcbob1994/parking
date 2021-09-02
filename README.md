# bob_parking
 ESX Parking System Version 13

You are able to park your vehicle anywhere you like it doesnt matter on wich position.
The vehicle stays there until you unpark it even if the server restarts.

## Features:
* Park anywhere
* even after restart
* Lockpick locked Vehicles
* Hotwire Vehicles
* Lock/Unlock Cars
* GPS Tracking System for Cars /searchVehicle PLATE and /searchEnd
* Self repairing database functions
* Information about wrong Configs in config.lua
* Self installing and updating database !NO DATABASE INSTALLATION REQUIRED!


## UPDATE
	+ Added slow vehicle save mode ( config updated )
	+ Added automatic database installation
	+ Added automatic update function
	* Fixed uninstalling and installing gps

## Installation

* add ensure parking to your server.cfg
* CHECK THE CONFIG!

```#*######################################################*```
#  * ONLY If you are using esx_advancedgarage !!!!!!! *
```#*######################################################*```

``` Comment out this part: esx_advancedgarage/server/main.lua

-- Make sure all Vehicles are Stored on restart
MySQL.ready(function()
	if Config.Main.ParkVehicles then
		--ParkVehicles()
		MySQL.Async.execute('UPDATE owned_vehicles SET `stored` = true WHERE `stored` = @stored', {
			['@stored'] = false
		}, function(rowsChanged)
			if rowsChanged > 0 then
				print(('esx_advancedgarage: %s vehicle(s) have been stored!'):format(rowsChanged))
			end
		end)
	else
		print('esx_advancedgarage: Parking Vehicles on restart is currently set to false.')
	end
end)
```

## Recommended Resources for the best results: // if you know what you are doing they are Optional
* progressBars


## Triggers
* TriggerServerEvent('parking:setup')
* TriggerServerEvent('parking:Update')
* TriggerClientEvent('parking:searchVehicle', source, plate)
* TriggerClientEvent('parking:searchEnd', source, plate)
* TriggerClientEvent('parking:sendMessage', source, message)


## Preview [Outdated]
https://www.youtube.com/watch?v=ClktMmmTYyQ
