If u have any problem regarding script you can open a ticket from #〢urgent-help🎟 channel.
discord server link - https://discord.gg/3Vs5jpXTcm
discord tag - ᒎα爪ЄƧ#4411

I will respond as soon as possible.



# qb-sheriffjob
Sheriff Job for QB-Core Framework

THis is a modified version of 
- [qb-policejob](https://github.com/qbcore-framework/qb-policejob)

## Dependencies
- [qb-core](https://github.com/qbcore-framework/qb-core)
- [qb-management](https://github.com/qbcore-framework/qb-management) - For the boss menu
- [qb-garages](https://github.com/qbcore-framework/qb-garages) - For the vehicle spawner
- [qb-clothing](https://github.com/qbcore-framework/qb-clothing) - For the locker room
- [qb-phone](https://github.com/qbcore-framework/qb-phone) - For the MEOS app and notifications etc.
- [qb-log](https://github.com/qbcore-framework/qb-logs) - For logging certain events
- [qb-menu](https://github.com/qbcore-framework/qb-menu) - For the vehicle menus
- [qb-input](https://github.com/qbcore-framework/qb-input) - For accessing evidence stashes

## Features
- Classical requirements like on duty/off duty, clothing, vehicle, stash etc.
- Citizen ID based armory (Whitelisted)
- Fingerprint test
- Evidence locker (stash)
- Whitelisted vehicles
- Speed radars across the map
- Stormram
- Impounding player vehicle (permanent / for an amount of money)
- Integrated jail system
- Bullet casings
- GSR
- Blood drop
- Evidence bag & Money bag
- sheriff radar
- Handcuff as an item (Can used via command too. Check Commands section.)
- Emergency services can see each other on map

### Commands
- /spikestrip - Places spike strip on ground.
- /pobject [pion/barier/schotten/tent/light/delete] - Places or deletes an object on/from ground.
- /cuff - Cuffs/Uncuffs nearby player
- /escort - Escorts nearby plyer.
- /callsign [text] - Sets the player a callsign on database.
- /clearcasings - Clears nearby bullet casings.
- /jail [id] [time] - Sends a player to the jail.
- /unjail [id] - Takes the player out of jail.
- /clearblood - Clears nearby blood drops.
- /seizecash - Seizes nearby player's cash. (Puts in money bag)
- /sc - Puts soft cuff on nearby player.
- /cam [cam] - Shows the selected security cam display.
- /flagplate [plate] [reason] - Flags the vehicle.
- /unflagplate [plate] - Removes the flag of a vehicle.
- /plateinfo [plate] - Displays if a vehicle is marked or not.
- /depot [price] - Depots nearby vehicle. Player can take it after paying the cost.
- /impound - Impounds nearby vehicle permanently.
- /paytow [id] - Makes payment to the tow driver.
- /paylawyer [id] - Makes payment to the lawyer.
- /radar - Toggles the sheriff radar.
- /911 [message] - Sends a report to emergency services.
- /911r [id] - Used to respond the emergency alerts.
- /911a [message] - Sends an anonymous report to emergency services (gives no location).
- /anklet - Places anklet (tracking device) on nearby player.
- /removeanklet [citizenid] - Removes the anklet from player.
- /ebutton - Used to respond an emergency alert.
- /takedrivinglicense - Takes the driving license from nearby player.
- /takedna [id] - Takes a DNA sample from the player.

## Installation
### Manual
- Download the script and put it in the `[qb]` directory.
- Add the following code to your server.cfg/resouces.cfg
```
ensure qb-core
ensure qb-sheriffjob
```
## Add in qb-core\shared\items.lua

['sheriff_stormram'] 			 = {['name'] = 'sheriff_stormram', 			  	['label'] = 'Stormram', 				['weight'] = 18000, 	['type'] = 'item', 		['image'] = 'police_stormram.png', 		['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'A nice tool to break into doors'},

## Add in qb-core\shared\jobs.lua

{
	['sheriff'] = {
		label = 'Law Enforcement',
		defaultDuty = true,
		offDutyPay = false,
		grades = {
            ['0'] = {
                name = 'Recruit',
                payment = 50
            },
			['1'] = {
                name = 'Officer',
                payment = 75
            },
			['2'] = {
                name = 'Sergeant',
                payment = 100
            },
			['3'] = {
                name = 'Lieutenant',
                payment = 125
            },
			['4'] = {
                name = 'Chief',
				isboss = true,
                payment = 150
            },
        },
	},
}

## Add in qb-management\client\cl_congig.lua

Config.BossMenus = {
    ['sheriff'] = {
        vector3(461.45, -986.2, 30.73), ##enter your coords here 
    },
}

Config.BossMenuZones = {
    ['sheriff'] = {
        { coords = vector3(461.45, -986.2, 30.73), length = 0.35, width = 0.45, heading = 351.0, minZ = 30.58, maxZ = 30.68 } ,  ##enter your polyzone credentials here for bossmenu
    },
}

## Add in qb-management\qb-management.sql after line 12

('sheriff', 0, 'boss'),

## Add in qb-garages\config.lua

["sheriff"] = {
    label = "sheriff",
    takeVehicle = vector3(454.6, -1017.4, 28.4),
    spawnPoint = vector4(438.4, -1018.3, 27.7, 90.0),
    putVehicle = vector3(454.6, -1017.4, 28.4),
    showBlip = false,
    blipName = "sheriff",
    blipNumber = 357,
    type = 'job',                --public, job, gang, depot
    vehicle = 'car',              --car, air, sea
    job = "sheriff"
},

## Add in qb-clothing\config.lua

Config.ClothingRooms = {
    [1] = {requiredJob = 'sheriff', isGang = false, coords = vector3(454.43, -988.85, 30.69), width = 2, length = 2, cameraLocation = vector4(454.42, -990.52, 30.69, 358.48)},  ##enter your suitable coords here
}

## Add in qb-phone\config.lua

["meos"] = {
    app = "meos",
    color = "#004682",
    icon = "fas fa-ad",
    tooltipText = "MDT",
    job = "sheriff",
    blockedjobs = {},
    slot = 13,
    Alerts = 0,
},

