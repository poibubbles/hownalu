At work, some chargers/adapters in some outlets (typically extensions) charged the laptop sometimes. At home, the charger that came with the laptop worked consistently via one outlet+extension.

At work, 4.6V was reported by an equipped USB-C cable for *all* combinations of chargers (3 types), being plugged into sockets directly or not, using a couple different extensions, and using a portable battery charger. All of these combinations resulted in a "battery is plugged in but not charging" status indicator in the battery icon with the same 4.6V status. Hence it was determined that the laptop itself might be regulating voltage.

Sometimes the laptop charges at work. What would the voltage have been then? Dunno.

	ioreg -r -n AppleSmartBattery  # provides voltage (and much more)
	
	pmset -g batt        # battery icon info
	pmset -g accps       # same as above
	pmset -g rawbatt     # more details, including cycles
	pmset -g everything  # way more details
	
	# Apple > About > System Report > Power info
	system_profiler SPPowerDataType

Most of these commands came from: https://stackoverflow.com/q/53552864 and https://apple.stackexchange.com/a/415358
Helpful discussion on amps and volts (wrt to solar): https://discussions.apple.com/thread/7675064
Also, wattage may come from an Apple (-specific) power adapter - other brands may not provide this info : https://apple.stackexchange.com/a/16519

From `ioreg -r -n AppleSmartBattery` at home, plugged into the working charger+outlet+extension (edited):

	"AdapterDetails" =
    {"Watts"=30,"Current"=1500,"Voltage"=20000}
    "Voltage" = 12708
    "AppleRawAdapterDetails" =
    ({"Watts"=30,"Current"=1500,"Voltage"=20000})
    "LegacyBatteryInfo" =
    {"Amperage"=342,"Current"=3362,
    "Voltage"=12708,"Cycle Count"=299}
    "ChargerData" =
    {"ChargingCurrent"=1224,"ChargingVoltage"=12700,
    "VacVoltageLimit"=4240}
	"Voltage" = 12708

At work, charging happily, using the Anker multi-plug and a small Apple adapter (probably from the iPad or iPhone):

	"AdapterDetails" = {"Watts"=8,"Current"=1500,"Voltage"=5000}
    "Voltage" = 12350
    "AppleRawAdapterDetails" =
    ({"Watts"=8,"Current"=1500,"Voltage"=5000})
    "CurrentCapacity" = 3214
    "LegacyBatteryInfo" =
    {"Amperage"=18446744073709551519,
      "Capacity"=3534,"Current"=3214,"Voltage"=12350,
      "Cycle Count"=301}
      "CycleCount" = 301
      "ChargerData" =
      {"ChargingCurrent"=1536,"ChargingVoltage"=12720,
      "VacVoltageLimit"=4240}
The numbers above was just with the Anker multi-plug and small Apple adapter. Charging also worked when the USB-C port and charge extender was included. And charging continued when adding a USB-C drive to the laptop.