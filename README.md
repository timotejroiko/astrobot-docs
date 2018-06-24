# Astrobot

A fully featured Astrology software for Discord!

This repo is currently being used as a user guide and for feedback and bug tracking purposes only.

## Getting Started

To add Astrobot to your Discord server, click [here](https://discordapp.com/oauth2/authorize?=&client_id=344272098488877057&permissions=116800&scope=bot)

Astrobot requires the following permissions:

`SEND MESSAGES`
`ADD REACTIONS`
`ATTACH FILES`
`EMBED LINKS`
`READ MESSAGE HISTORY`

### 

## How to use

### Help

This user guide can be accessed inside Discord by using the help command. To navigate the guide simply click on the emoji buttons that will appear or specify a page number to open it directly. If you dont see anything, you need to enable Link Previews in your Discord settings.

```
.help (open this user guide)
.help 4 (directly opens page 4)
```

### Creating Charts
```
.newchart MM/DD/YYYY, HH:MM, city country
```

Both 24h and 12h time formats are supported and the full year must be used. Location and Timezones are calculated using Google's Geocoding and Timezone APIs.

Examples:
```
.newchart 03/25/1988, 15:43, munich germany
.newchart 11/18/2041, 3:43pm, lisbon portugal
.newchart 06/02/450, 23:20:30, los angeles california (with seconds)
.newchart 11/18/-35, 8:30:10am, lisbon portugal (BC dates)
```

If your birth time is unknown, standard practice is to use 12:00, but you should not attempt to read houses as they are highly dependant on time of birth.


### Current Transit Chart

To get the current transits, use the keyword "now". Default location is London UK. Optionally you can specify a custom location by using a comma.

Examples:
```
.newchart now (default location)
.newchart now, barcelona spain (with custom location)
```

### Saving Charts
```
.savechart name
```

You can give it any name you want, but names with spaces are not supported and names are case sensitive. You can also protect your chart so only you can open it by adding `--private` to the end of the command.
Charts are saved globally, meaning you can access them in any Discord server that has Astrobot in it, as well as in DMs with Astrobot.

Examples:
```
.savechart robert
.savechart LizGreene --private (protected chart)
.savechart insert_weird-name4781@@@here>good!luck
```

### Opening Charts
```
.openchart name
```
Opens a snapshot of the saved chart exactly the way it was. It is not affected by settings nor extended options.

```
.newchart name
```
Rebuilds the chart from saved information. It uses your current settings and also supports extended options. Extended options from saved charts are removed in favor of new ones or returned to default, meaning if you saved a chart using an extended option, you need to use the extended option again when opening with `.newchart` or it will be rebuilt with default options.

### Listing and Finding Charts
```
.listcharts (lists ALL charts. Be careful with this)
.mycharts - (lists your charts)
.find name - (lists all charts that partially match a name)
```

Charts are color coded and organized in brackets depending if they are protected or not. (colors are not supported in mobile phones)

### Editing, Replacing and Deleting Charts
```
.editchart name newname (change chart name)
.editchart name --private (toggle chart protection)
.savechart name --replace (replace saved chart)
.deletechart name (delete chart)
```

### Creating a Biwheel
```
.biwheel chart1 + chart2
```

Biwheels work the same way as the `.newchart` command. You can use full birth information, the 'now' keyword, or saved charts. Biwheels also support extended options and can also be saved, but can only be opened by `.openchart`.

Examples:
```
.biwheel kennedy + rickfox
.biwheel 03/07/1999, 15:50, london uk + 03/07/1998, 15:50, london uk
.biwheel WhatsHappeningToMe + now (current transits)
.biwheel John + 10/10/2010, 10:10, rome italy (specific transits)
```

### Creating a Mid-point Composite
```
.composite chart1 + chart2
```

Composite Charts work the same way as Biwheels and have the same opening and saving rules.

Examples:
```
.composite darling + love
.composite 10/10/1995, 10:10, london + 5/18/1994, 15:00, london
```

### Settings
```
.settings (opens the settings menu in your DMs)
```

Settings can be used to customize your charts, toggle planets, toggle aspects, etc... Once opened, the menu will show you which settings are enabled or disabled by color coding and brackets. (color coding doesnt work on mobile phones). Then you can use the settings commands in your DMs to toggle options on or off. Changing settings only works in DMs. Multiple commands can be used at once.

Examples (in DMs):
```
.settings --planets=vesta (toggles vesta)
.settings --aspects=quintile (toggles quintile)
.settings --points=north node (toggles north node aspects)
.settings --houses=whole sign (sets default house system to whole sign)
.settings --planets=zeus,hades,chronos,south node (multiple toggles)
.settings --planets=jupiter --aspects=trine (multiple toggles)
.settings --reset (restore default settings)
.settings --theme (change color theme. themes are currently a premium feature)
```

## Extended Options

Extended options can be used at the end of a command for extra functionality. Multiple options can be used at once. For biwheels, `--format` and `--size` should only be used at the end of the entire command.

### Formatting
```
--format
```
Changes image format. Supported formats are JPG (white background) and PNG (transparent background). Default is PNG.

```
--size
```
Changes image size in pixels. Supported sizes are from 10 to 8000. Default is 800. Large sizes can take longer to generate.

Examples:
```
.newchart 10/10/1980, 10:10, london uk --format=JPG
.biwheel uvuvwevwevwe + now --size=2000
.newchart zelda --format=JPG --size=3333
```

### Asteroids
```
--asteroids
```

Asteroids can be added to the chart by their official number and multiple asteroids can be used at once. A full list of asteroids and their numbers can be found [here](http://www.astro.com/swisseph/astlist.htm)

Examples:
```
.newchart timmy --asteroids=399 (persephone)
.biwheel batman --asteroids=1108 + robin --asteroids=1108 (demeter)
.newchart joker --asteroids=5731,103,433 (zeus,hera,eros)
```

### Zodiac Modes
```
--mode
```

Changes zodiacs between Tropical, Sidereal and Draconic. Default is Tropical. Sidereal and Draconic zodiacs have an additional option to specify the calculation used, ayanamsa for sidereal and node for draconic.

Examples:
```
.newchart now --mode=draconic (true node)
.newchart now --mode=draconic,mean (mean node)
.newchart now --mode=sidereal (fagan/bradley)
.newchart now --mode=sidereal,1 (lahiri)
.newchart now --mode=sidereal,5 (Krishnamurti)
.biwheel me --mode=sidereal + now --mode=sidereal (same zodiac)
.biwheel me + me --mode=sidereal (compare zodiacs)
.help sidereal (list all sidereal ayanamsas)
```

### Houses
```
--houses
```

Changes the house system used. House systems can be selected by name or by key code and can also be set in the settings menu. Default is Placidus.

Examples:
```
.newchart now --houses=W (wholesign)
.biwheel jesus --houses=koch + buddha --houses=koch (koch)
.newchart onyetenyevwe --houses=T (topocentric)
.help houses (list all house systems)
```

### Solar Return
```
--return
```

Creates a Solar Return chart. A reference year and a reference location are required. If no location is specified, the chart's original location is used.

Examples:
```
.newchart jack --return=2018 (birth location)
.newchart jessica --return=2020, paris france
.biwheel ana + ana --return=2015, moscow russia
```

### Secondary Progressions
```
--progression
```

Creates a Progressed Chart using the Secondary Progression method (1 year = 1 day) with angles progressed by solar arc. Currently can only be used with saved charts. To specify a progressed date, use only MM/DD/YYYY, no need for time or location. Secondary Progressions should primarily be used together with natal charts in a biwheel.

Examples:
```
.newchart krishna --progression=now (current progression)
.newchart TheRock --progression=03/15/2025 (specific date)
.biwheel Ana + Ana --progression=now (biwheel)
```

### More Examples

Most extended options can be chained together (except solar return with secondary progressions) and most options can be used in biwheels independently for inner and outer wheel (except format and size which should only be used at the end)

```
.newchart now --size=2000 --houses=topocentric --asteroids=555,777
.biwheel ugwemubwem --houses=W --mode=sidereal --asteroids=433 + ossas --houses=W --mode=sidereal --asteroids=433 --format=JPG --size=4000
.newchart iAmTheLaw --asteroids=1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50
```

### Extras

Some extra commands and features that are also available

```
.help lastupdate (view latest changes)
.help changelog (view full changelog)
.stats (view fun statistics)
```

Astrobot will also ask you random questions if you mention it in your message but will open the help menu if you only mention it

```
@Astrobot hello (random question)
ask me anything @Astrobot (random question)
@Astrobot (help menu)
```

### Support Server

Our sponsor server, which is also our support server, can be found [here](https://discord.gg/jtaCURK)

## Credits

Astrobot was made by Timotej Valentin Rojko (Tim#2373) using Discord.js, Google's geocoding and timezone API's and astro.com's Swiss Ephemeris.

This project is currently closed source as its code is in the process of being implemented in our future astrology website: [astrologico.org](https://astrologico.org)

## Donate

All donations are going towards our website's construction, which will feature an interactive online version of Astrobot!

```
Paypal: paypal.me/timotejroiko
BTC: 3AwSvBXV6cXy5tTadopZetTGB4StNXbYYj
LTC: MEe1ymrHgSWusPyPp6nxYNNGTs5X7Mo82v
ETH: 0x8bAe3a23d11592a656d983c4a3eDC4DC1C15E1EA
```

Users who donate above 5$ get to request a custom color theme!
(if you donated send a dm to Tim#2373)

Thank you for your preference. Astrobot loves you!
