# Virtual Flight Online Transmitter

## What is "Virtual Flight Online Transmitter" ?

It is a small Windows application that transmits your position in Microsoft Flight Simulator to an online database where your last reported position is held for 1 minute. The website then produces a "whazzup" formatted file that can be used by LittleNavMap to plot aircraft positions live on a map.

## Why?

If you and your friends want to see each other on mapping software such as LittleNavMap to run your own air traffic control sessions for group flights, you will no doubt have discovered that Microsoft Flight Simulator only communicates AI aircraft to external mapping applications such as LittleNavMap - not users. The Virtual Flight Online Transmitter application addresses that.

## How It Works

The desktop application connects to a running copy of Microsoft Flight Simulator via the SimConnect interface, and reads your aircraft's latitude, longitude, altitude, and airspeed. It combines the data with your keyed callsign, aircraft type, and name, and sends it to a server on the internet via the "Server URL" entered into the application.

The server then provides a URL that outputs all aircraft that have been updated in the last 5 minutes in "whazzup" format - a data format commonly used with the likes of VATSIM and IVAO - and crucially LittleNavMap. The URL of the server can be used to configure LittleNavMap to show you and your friends aircraft on the map.

## Running the Program

* Launch Microsoft Flight Simulator.
* Run "VirtualFlight.Online Transmitter".
* Fill out the text boxes for your callsign, aircraft type, name, and group name
* Click Connect

After clicking connect, the application will broadcast your location within the simulator to the internet once a second.

## Running your own server

The /server subdirectory contains the resources required to make your own server. You'll need some MySQL and PHP webserver experience - a database.sql file is included to create the appropriate database to track aircraft positions (used by send.php and whazzup_ivao.php). The code should be self explanatory. Remember your users will also need to change their server URL to reflect the location of "send.php" for your server.

## Configuring LittleNavMap

If you would like to see everybody broadcasting their position with Virtual Flight Online Transmitter, follow these steps in LittleNavMap:

* Click on the Tools menu
* Click on Options
* Select the Online Flying section within the Options panel
* Choose the radio button for "Custom" within the Online Flying section
* Fill the URL http://your_server_name/whazzup_ivao into the URL field
* Set the update rate to something sensible (e.g. 5 seconds)
* Make sure IVAO is chosen in the format drop-down
* Click Apply, and OK

## Final note

I don't really have time to look after Transmitter any more. It was always a stop-gap until Microsoft released a multiplayer location API - but they never have. I will answer questions about Transmitter, but please don't expect me to support your installations or modifications to the code.
