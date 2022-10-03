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

Just simply drag and drop into your [qb] folder