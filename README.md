# Astrobot

A fully featured Astrology software for Discord! Astrobot can create a variety of astrological charts and supports a vast array of possibilities. Its features include:

* Planets, Stars, Asteroids, Arabic Parts, Comets, Artificial Satellites, and more
* Tropical, Sidereal and Draconic zodiacs
* Geocentric, Topocentric and Heliocentric
* 20+ House Systems and 40+ Ayanamsas
* Biwheels and composites
* Returns, Personas, Progressions and more
* Chart management and unlimited saved charts
* Custom themes and custom orb sets
* Extremely customizable

**Add Astrobot to your Discord server! -> [Invite Astrobot](https://discord.com/oauth2/authorize?client_id=344272098488877057&permissions=379968&scope=bot)**  
**If you need any help join our support server -> [Join Astro Dev](https://discord.gg/BpeedKh)**  

# ⚠️ Astrobot is currently transitioning to slash commands. Old prefix commands are not available anymore, and while definitive slash commands are not yet available, you can continue using legacy commands by using `/command` instead of the dot (`.`) prefix, for example `/command newchart` instead of `.newchart`.

## Index

* **[Prefix](#prefix)**
* **[Help](#help)**
* **[Charting Commands](#charting-commands)**
	* **[Newchart](#newchart)**
		* **[Single Charts](#single-charts)**
		* **[Biwheels](#biwheels)**
		* **[Now](#now)**
		* **[Saved Charts](#saved-charts)**
		* **[Chart Options](#chart-options)**
	* **[Openchart](#openchart)**
	* **[Savechart](#savechart)**
	* **[Editchart](#editchart)**
	* **[Deletechart](#deletechart)**
	* **[Findchart](#findchart)**
	* **[Mycharts](#mycharts)**
* **[Utility Commands](#utility-commands)**
	* **[Findobject](#findobject)**
	* **[Objectinfo](#objectinfo)**
	* **[About](#about)**
	* **[Settings](#settings)**
	* **[Prefix](#prefix)**
* **[Additional Information](#additional-information)**
	* **[Planets](#planets)**
	* **[Houses](#houses)**
	* **[Zodiacs](#zodiacs)**
	* **[Aspects](#aspects)**
* **[Donations and Premium Features](#premium)**
* **[About Astrobot](#about-astrobot)**

## Getting Started

Astrobot can be quite complex to use at first, but once you get the hang of it its quite easy!

Astrobot's uses slash commands `/` and it also works in DMs.

So lets get started with Astrobot's basic commands:

### Help

The help command opens an interactive menu that includes almost everything on this page in an acessible way. It divides the content in sections and pages that can be navigated by clicking on the buttons that show up at the bottom.

Examples:

* `/help` - shows the interactive help menu and displays available options
* `click on the "Charting Commands" button` - enters the "Charting Commands" section
* `click on the "Newchart" button` - enters the "Newchart" section
* `click on the "Back" button` - goes back to the "Charting Commands" section
* `click on the "Openchart" button` - enters the "Openchart" section
* `click on the "Back" button` - goes back to the "Charting Commands" section
* `click on the "Back" button again` - goes back to main menu

And so on... (easier to see it than to explain it here)

The interactive menu should always work regardless of how old it gets so you can safely open a permanent help menu in a read-only channel and send your users there so they dont need to use it again and again in other channels.

Multiple people can use the same help menu at the same time.

## Charting Commands

These commands are used to create and manage charts, and are the core feature of Astrobot.

### Newchart

This command lets you create a variety of astrological charts and supports an extensive amount of customization options including biwheels, solar returns, progressions, composites and more!

#### Single Charts

For starting, lets create a transit chart for a given date:

* `/commmand newchart 20/10/1995`

The above command will generate a chart for October 20th 1995 at noon UTC. By default it expects a **DD/MM/YYYY** date but you can change it to **MM/DD/YYYY** by using the dateformat option explained in the [Settings](#settings) section.

Now if you want to give it a specific time of the day:

* `/command newchart 20/10/1995, 15:30` or `/command newchart 20/10/1995, 3:30pm`

This will generate a chart for October 20th 1995 at 3:30pm UTC. Both 12h and 24h time formats are supported. In both cases no houses will be shown because the chart lacks a location, so lets give it one:

* `/command newchart 20/10/1995, madrid spain`
* `/command newchart 20/10/1995, 15:30, madrid spain`

Now we have a chart for noon and another for 3:30pm both in the madrid timezone, and since we defined a location this time, these charts will also display Houses!

Thats it for the basics of chart making and dont forget the commas between date, time and location (they are important). Now lets check some more advanced features below.

#### Biwheels

Now lets say we want to create a biwheel, all you have to do is add a ` + ` sign at the end of the command (with spaces around it), and then add a new set of data the same way as before:

* `/command newchart 20/10/1995, 15:30, rome italy + 15/5/1992, 6:45am, london uk`

Now we have a biwheel displaying both charts!

#### Now

Besides the above Date, Time and Location method, you can also use the keyword `now` to create a chart for the current date and time. For example:

* `/command newchart now`
* `/command newchart now, new york`
* `/command newchart 20/10/1995, 15:30, new york + now, new york`

This makes it easy to check the current transits, both in a single chart and in a biwheel with another chart. The `now` keyword can also be extended by adding or removing a number of days from it:

* `/command newchart now+1` - tomorrow
* `/command newchart now-1` - yesterday
* `/command newchart now+0.5` - 12 hours from now

Note that there should be no spaces around the plus/minus signs in this case.

#### Saved Charts

Astrobot's chart saving system lets you save charts under a name of your choice, as explained in the [Savechart](#savechart) section. Once you have a saved chart, you can easily pull it up by name, for example:

* `/command newchart jack`
* `/command newchart john doe`
* `/command newchart john doe + now`
* `/command newchart john doe + jack`

You can also load other people's charts, as long as they are public.

#### Chart Options

Additionally, there are multiple chart options that can be added to the command using the `--option=value` format. All of these options (with a few obvious exceptions) can be used together in any combination.

##### --add & --remove

These two options let you add and/or remove planets and objects from a chart. When used on biwheels, this option affects each chart independently. Additionally, the `--remove` option includes an `ALL` keyword to remove all planets. For example:

* `/command newchart now --add=A1,A2 --remove=A2060` - remove Chiron and add Ceres and Pallas
* `/command newchart jack --add=A1 + now --add=A1` - add Ceres to both charts
* `/command newchart now --remove=ALL --add=P0,P1` - remove everything exept Sun and Moon

Because of the amount of planets and objects that Astrobot supports, it uses an ID system to identify them. To find out which planets and objects are available and how to find them and their respective IDs, check out the [Planets](#planets) section.

##### --zodiac

This option lets you specify which zodiac or ayanamsa should be used (tropical by default). When used on biwheels, this option affects each chart independently. For example:

* `/command newchart now --zodiac=D1` - use the draconic (true node) zodiac
* `/command newchart jack --zodiac=S1 + now --zodiac=S1` - use the fagan/bradley sidereal zodiac in both charts

Check the available zodiacs and ayanamsas in the [Zodiacs](#zodiacs) section.

##### --houses

This option lets you specify which house system should be used (placidus by default). When used on biwheels, this option affects each chart independently. For example:

* `/command newchart now --houses=13` - use the koch house system
* `/command newchart jack --houses=24 + now --houses=24` - use the whole signs house system for both charts

Check the available house systems in the [Houses](#houses) section.

##### --timezone

This option lets you manually specify a timezone, which overrides any automatic timezone if applicable. A timezone can be specified by a TZData identifier or by a number of offset minutes. When used on biwheels, this option affects each chart independently. For example:

* `/command newchart 5/5/2015, 16:00 --timezone=America/New_York` - use the america/new_york timezone identifier
* `/command newchart 5/5/2015, 16:00 --timezone=+50 + 7/7/2016, 16:00 --timezone=-50` - use UTC+00:50 on the first chart and UTC-00:50 on the second chart

##### --return

This option lets you create a solar return chart by specifying a year and optionally a location. When used on biwheels, this option affects each chart independently. For example:

* `/command newchart john --return=2021` - john's solar return for 2021 in his birth place
* `/command newchart john --return=2021, london uk` - john's solar return for 2021 in london
* `/command newchart john --return=2021, london uk + jack --return=2021, madrid spain` - biwheel john's solar return for 2021 in london and jack's solar return for 2021 in madrid

##### --return2

This option lets you create a return chart for any planet, by specifying a planet ID, a search direction and a date-time-location separated by commas. Available search directions are `current`, `next` and `closest`. When used on biwheels, this option affects each chart independently. For example:

* `/command newchart john --return2=P1, next, now` - john's next lunar return starting from the current date and time
* `/command newchart jack --return2=P2, closest, 5/5/2025, lisbon portugal` - jack's mercury return closest to 5/5/2025 in lisbon portugal
* `/command newchart john --return2=P5, current, now + jack --return2=P5, current, now` - biwheel john's most recent jupiter return with jacks most recent jupiter return

##### --progression

This option lets you create a progressed chart using the secondary progression method. When used on biwheels, this option affects each chart independently. For example:

* `/command newchart john --progression=1/1/2025` - john's secondary progressed chart for 1/1/2025
* `/command newchart john + john --progression=now` - john's birth chart in a biwheel with his current secondary progressed chart

##### --persona

This option lets you create a "persona" chart for a specific planet. When used on biwheels, this option affects each chart independently. For example:

* `/command newchart john --persona=P5` - john's jupiter persona chart
* `/command newchart john --persona=P5 + john --persona=P6` - john's jupiter persona chart biwheeled with john's saturn persona chart

##### --design

This option lets you create a "design" chart as seen in the Human Design System. When used on biwheels, this option affects each chart independently. For example:

* `/command newchart john --design` - john's design chart
* `/command newchart john + john --design` - john's birth chart in a biwheel which his design chart

##### --coordinates

This option lets you set the chart's coordinate system between `Geocentric`, `Topocentric` and `Heliocentric`. When used on biwheels, this option affects each chart independently. For example:

* `/command newchart john --coordinates=heliocentric` - john's heliocentric chart
* `/command newchart john --coordinates=geocentric + john --coordinates=topocentric` - biwheel john's chart in geocentric and topocentric coordinates

##### --size

This option lets you change the resolution of the resulting chart image as well as the scale of the fonts and gyphs on the chart. For example:

* `/command newchart now --size=2000` - set the chart resolution to 2000x2000 pixels
* `/command newchart jack + now --size=1500,120` - set the chart resolution to 1500x1500 pixels and the font scaling to 120%

##### --theme

This option lets you change the chart's color theme. There are three built-in themes: `classic`, `elements` and `rainbow`. For example:

* `/command newchart now --theme=classic` - use the classic theme for this chart

Additionally, custom themes can be created as a premium feature, check the [Premium](#premium) section.

##### --orbs

This option lets you change the chart's orb values. There are three built-in orbs: `astrobot`, `astro.com` and `strict`. For example:

* `/command newchart now --orbs=strict`

Additionally, custom orbs can be created as a premium feature, check the [Premium](#premium) section

##### --aspects

This option lets you define which aspects should be enabled in the chart. For example:

* `/command newchart now --aspects=trine,sextile,square` - show only trines, sextiles and squares

A full list of supported aspects can be found in the [Aspects](#aspects) section.

##### --disable & --enable

These options let you disable or re-enable a planet's aspect points. Additionally, they include an `ALL` keyword for selecting all planets. For example:

* `/command newchart now --disable=P0,P1,P2` - disable aspects for sun, moon and mercury
* `/command newchart jack + now --enable=A1` - re-enable aspects to Ceres if disabled
* `/command newchart john --disable=ALL --enable=P0,P1` - disable aspects for all planets except Sun and Moon

##### --composite

This option lets you turn a biwheel into a composite chart using the midpoint composite method. For example:

* `/commandnewchart jack + john --composite` - create a midpoint composite between jack and john

##### --preset

This option lets you load a set of options from a preset. There are two built-in presets: `default` and `original`. When using biwheels, this option can be set separately for both charts. For example:

* `/command newchart jack --preset=default` - show this chart using the default settings
* `/command newchart jack --preset=original` - show this chart in its original state, using the same settings it was saved with
* `/command newchart jack --preset=myPreset` - show this chart using a custom preset
* `/command newchart jill --preset=myPreset + jack --preset=original` - show jill's chart with a custom preset in a biwheel with jack's chart in its original state

Check out the [Presets](#presets) section to learn how to create and manage your custom presets.

##### --chartinfo

This option lets you view more details about the chart or charts. When viewing other people's charts, any personal information will be redacted. For example

`/command newchart john --chartinfo` - view more information about john's chart

### Openchart

This command loads a saved chart in its original state, exactly as it was when it was saved. It is essentially a shortcut for `--preset=original`, it can only open saved charts and doesnt support additional options. For example:

* `/command openchart daniel` - show daniel's chart in its original state

### Savechart

This command lets you save the last chart you created under a name of your choice. All names are case sensitive and must not include commas, double dashes nor slashes. Mentions will be converted to Discord IDs For example:

* `/command savechart jack` - save the last chart you created under the name `jack`

#### Savechart Options

A chart can be saved as public or private (all charts are public by default). Private charts can also be shared with specific people using the options below:

##### --private & --share

Save this chart as a private chart. Private charts can only be opened by their owners and the people the chart was shared with. For example:

* `/command savechart jack --private` - save this chart as private
* `/command savechart jack --private --share=@john` - save this chart as private and share it with a specific person

##### --replace

If you already have a saved chart with a given name and you want to replace it with a new one, you can use this option to overwrite it:

* `/command savechart jack --replace` - replace a previously saved chart with a new one

### Editchart

This command lets you view information about one of your saved charts as well as change its name and privacy settings. For example:

* `/command editchart john` - view more information about john's chart

#### --rename

Change the name of your saved chart:

* `/command editchart john --rename=valentine` - change your chart's name to `valentine`

#### --private

Toggles your chart's privacy setting. Becomes private if its public or becomes public if its private.

* `/command editchart valentine --private` - toggle this chart's privacy setting

#### --share

If this chart is private, change who can use it:

* `/command editchart jack --share=@valentine` - share this chart with another person or unshare it if its already shared with this person
* `/command editchart jack --share=none` - unshare this chart with everyone

### Deletechart

This command lets you permanently delete a chart. You can only delete charts you own. For example:

* `/command deletechart jack` - permanently delete the chart `jack`

### Findchart

This command lets you find a saved chart by name, including charts made by other people. If you find too many results, try searching for a more specific name. For example:

* `/command findchart john` - show all charts containing `john` in their names

### Mycharts

This command lets you see all charts you have saved with your current discord account. For example:

* `/command mycharts` - show all the charts you own

## Utility Commands

The following utility commands provide assistance with many things for example finding object IDs by name, changing personal settings and more.

### Findobject

This command lets you search for objects by name and discover their IDs. If you cant find the object you're looking for, try a more specific search term as well as any alternative names it may have. For example:

* `/command findobject eris` - show all planets, stars and objects whose names contain `eris`

#### --type

Limit the search results to specific types. For example:

* `/command findobject eris --type=A` - show only asteroids whose name contains `eris`

More information about types can be found in the [Planets](#planets) section.

### Objectinfo

This command shows you information about a specific object ID, its names, type and a preview of how it appears in a chart. For example:

* `/command objectinfo P5` - show information about object P5 (jupiter)

More information about common object IDs can be found in the [Planets](#planets) section

### About

This command lets you obtain information about certain topics and components used by Astrobot such as glyphs, orbs, aspects and more.

* `/command about` - list components that offer additional information

#### About Glyphs

This option creates an image showing a preview and a description of every glyph and symbol that Astrobot uses including planets, asteroids and more:

* `/command about glyphs` - display all planetary symbols and glyphs that Astrobot uses

#### About Aspects

This option creates an image showing a preview and the distance degrees of every aspect supported by Astrobot:

* `/command about aspects` - display all aspects that Astrobot uses

#### About orbs

This option displays a list of available orb sets, as well as details about a specific orbs set:

* `/command about orbs` - display a list of available orb sets
* `/command about orbs astro.com` - describe the orb values of the `astro.com` orbs set

#### About Houses

This option displays a list of available house systems in Astrobot:

* `/command about houses` - display a list of available house systems

Alternatively you can check the list of house systems in the [Houses](#houses) section.

#### About Zodiacs

This option displays a list of available zodiacs and ayanamsas in Astrobot:

* `/command about zodiacs` - display a list of available zodiacs

Alternatively you can check the list of zodiacs and ayanamsas in the [Zodiacs](#zodiacs) section.

### About Planets

This option diplays a list of commonly used planets and their IDs:

* `/command about planets` - display a list of common planets

Alternatively you can check the list of planets in the [Planets](#planets) section.

### Settings

This command lets you configure your preferred default settings for all your charts. These settings are applied to all charts created using the `/command newchart` command, including saved charts, unless overriden by chart options or presets. Settings are divided into sections for easier management.

#### Settings Sections

The following sections are available to display your current settings. Each section also displays instructions for how to edit/configure it.

* `/command settings planets` - display your currently enabled planets as well as their aspect points
* `/command settings aspects` - display your currently enabled aspects as well as available aspects to chose from
* `/command settings houses` - display your preferred house system as well as available house systems to chose from
* `/command settings zodiac` - display your preferred zodiac as well as available zodiacs to chose from
* `/command settings themes` - display your current chart theme as well as available themes to chose from
* `/command settings orbs` - display your current orbs set as well as available sets to chose from
* `/command settings dateformat` - display your current preferred date format (DD/MM/YYYY or MM/DD/YYYY)
* `/command settings coordinates` - display your current preferred coordinate system
* `/command settings presets` - display your saved presets

#### Settings Options

The following options are available to change your personal settings.

##### --addplanets & --removeplanets

Add and remove planets from your settings. For example:

* `/command settings --addplanets=A1,A2,A3` - add Ceres, Pallas and Juno to your settings
* `/command settings --removeplanets=P7,P8,P9` - remove Uranus, Neptune and Pluto from your settings

##### --enableplanets & --disableplanets

Disable and re-enable aspects points for your selected planets. All planets have their aspect points enabled by default. For example:

* `/command settings --disableplanets=A1,A2,A3` - disable aspect points to Ceres, Pallas and Juno
* `/command settings --enableplanets=A1,A2,A3` - re-enable previously disabled aspect points

##### --enableaspects & --disableaspects

Enable and disable your preferred aspects. For example:

* `/command settings --enableaspects=conjunction,quincunx` - enable conjunctions and quincunxes
* `/command settings --disableaspects=sextile,opposition` - disable sextiles and oppositions

##### --houses

Set your preferred house system. For example:

* `/command settings --houses=24` - set Whole Signs as your default house system

##### --zodiac

Set your preferred zodiac. For example:

* `/command settings --zodiac=S2` - set Lahiri as your default zodiac

##### --theme

Set your preferred chart theme. For example:

* `/command settings --theme=rainbow` - set rainbow as your default theme

##### --orbs

Set your preferred orbs set

* `/command settings --orbs=strict` - set your default orbs to strict

##### --switchdateformat

Switch your preferred date format between **DD/MM/YYYY** and **MM/DD/YYYY**. For example:

* `/command settings --switchdateformat` - switch to another date format

##### --coordinates

Set your preferred coordinates system. For example:

* `/command settings --coordinates=HELIOCENTRIC` - set Heliocentric as your default coordinates system

##### --savepreset & --loadpreset & --deletepreset

Manage your saved presets. Additionally a built-in `default` preset is available to reset all settings back to default. For example:

* `/command settings --savepreset=custom1` - save all your current settings as a preset named custom1
* `/command settings --loadpreset=custom1` - replace all your current settings with those contained in the custom1 preset
* `/command settings --deletepreset=custom1` - delete the custom1 preset
* `/command settings --loadpreset=default` - reset all settings back to default

## Additional Information

More information about Astrobot, including how its planet ID system works, all available house systems, zodiacs, aspects and more.

### Planets

Astrobot uses an ID system due to the sheer amount of planets and objects it supports.

#### Object Types

Each planet and object has a unique ID starting with an object type represented by a letter:

| Object Type | Descripton |
|---|---|
| P | Planets and special objects |
| A | Asteroids |
| S | Stars |
| H | Hypothetical Planets |
| C | Comets |
| L | Arabic parts/lots |
| T | Artificial Satellites |

Asteroids and Artificial Satellites use the same numbering system they are commonly known to use (MPC Designation for Asteroids, SATCAT number for Satellites). Other object types do not follow any known numbering system and are instead organized either alphabetically, by importance, on a "first comes" basis or by any combination of those.

#### Common Objects

Some of the most common objects IDs are listed below. This list can also be found using the `/command about planets` command.

| ID | Object |
|---|---|
| P0 | Sun |
| P1 | Moon |
| P2 | Mercury |
| P3 | Venus |
| P4 | Mars |
| P5 | Jupiter |
| P6 | Saturn |
| P7 | Uranus |
| P8 | Neptune |
| P9 | Pluto |
| P10 | Mean Ascending (North) Node |
| P11 | True Ascending (North) Node |
| P23 | Mean Descending (South) Node |
| P24 | True Descending (South) Node |
| P14 | Earth |
| P12 | Mean Lilith |
| P13 | True Lilith |
| P21 | Natural Lilith |
| A1 | Ceres |
| A2 | Pallas |
| A3 | Juno |
| A4 | Vesta |
| A2060 | Chiron |
| C1 | Comet Halley |
| H1 | Cupido |
| H2 | Hades |
| H3 | Kronos |
| H4 | Apollon |
| H5 | Admetos |
| H6 | Vulkanus |
| H7 | Poseidon |
| L118 | Part of Fortune |
| L119 | Part of Spirit |
| S3071 | Aldebaran |
| S1351 | Regulus |
| S3099 | Sirius |
| S1224 | Vega |
| S2665 | Spica |

To find the ID of a specific object, check out the **[Findobject](#findobject)** command.

### Houses

Astrobot supports many different House Systems listed below. The list can also be found using the `/command about houses` command.

| ID | House System |
|---|---|
| 1 | Alcabitius |
| 2 | APC |
| 3 | Axial Rotation / Meridian / Zariel |
| 4 | Azimuthal / Horizontal |
| 5 | Campanus |
| 6 | Carter / Poli-Equatorial |
| 7 | Equal (1st House = Ascendant) |
| 8 | Equal (10th House = Midheaven) |
| 9 | Equal (1st House = 0° Aries) |
| 10 | Gauquelin Sectors |
| 11 | Sunshine / Makransky (Treindl) |
| 12 | Sunshine / Makransky (Makransky) |
| 13 | Koch |
| 14 | Krusinski / Pisa / Goelzer |
| 15 | Morinus |
| 16 | Placidus |
| 17 | Polich / Page / Topocentric |
| 18 | Porphyry |
| 19 | Pullen SD / Neo-Porphyry |
| 20 | Pullen SR |
| 21 | Regiomontanus |
| 22 | Sripati |
| 23 | Vehlow Equal |
| 24 | Whole Sign |
| none | none (disable houses) |

### Zodiacs

Astrobot suports many types of zodiacs, including Tropical, Sidereal and Draconic. Sidereal zodiacs also have many different calculation methods or "Ayanamsas" to chose from. The list below can also be found using the `/command about zodiacs` command.

| ID | Zodiac / Ayanamsa |
|---|---|
| T | Tropical |
| D1 | Draconic (True Node) |
| D2 | Draconic (Mean Node) |
| S1 | Fagan / Bradley |
| S2 | Lahiri |
| S3 | De Luce |
| S4 | Raman |
| S5 | Usha / Shashi |
| S6 | Krishnamurti |
| S7 | Djwhal Khul |
| S8 | Yukteshwar |
| S9 | J.N. Bhasin |
| S10 | Babylonian / Kugler 1 |
| S11 | Babylonian / Kugler 2 |
| S12 | Babylonian / Kugler 3 |
| S13 | Babylonian / Huber |
| S14 | Babylonian / Eta Piscium |
| S15 | Babylonian / Aldebaran at 15° Taurus |
| S16 | Hipparchos |
| S17 | Sassanian |
| S18 | Galactic Center at 0° Sagittarius |
| S19 | J2000 |
| S20 | J1900 |
| S21 | B1950 |
| S22 | Suryasiddhanta |
| S23 | Suryasiddhanta (mean Sun) |
| S24 | Aryabhata |
| S25 | Aryabhata (mean Sun) |
| S26 | SS Revati |
| S27 | SS Citra |
| S28 | True Citra |
| S29 | True Revati |
| S30 | True Pushya (PVR Narasimha Rao) |
| S31 | Galactic Center (Gil Brand) |
| S32 | Galactic Equator (IAU1958) |
| S33 | Galactic Equator |
| S34 | Galactic Equator mid-Mula |
| S35 | Skydram (Mardyks) |
| S36 | True Mula (Chandra Hari) |
| S37 | Dhruva / Galactic Center / Mula (Wilhelm) |
| S38 | Aryabhata 522 |
| S39 | Babylonian / Britton |
| S40 | Vedic / Sheoran |
| S41 | Cochrane / Galactic Center at 0° Capricorn |
| S42 | Galactic Equator (Fiorenza) |
| S43 | Vettius Valens |
| S44 | Sheratan at 2°15' Aries |
| S45 | Vasilis Kanatas |

### Aspects

Astrobot supports many different aspects to chose from. The list below can also be found using the `/command about aspects` command, which also include a preview of its glyphs and how they look in a chart.

| Aspect | Distance (degrees) |
|---|---|
| conjunction | 0 |
| opposition | 180 |
| trine | 120 |
| square | 90 |
| quintile | 72 |
| bi-quintile | 144 |
| sextile | 60 |
| septile | ~51.42 |
| bi-septile | ~102.85 |
| tri-septile | ~154.28 |
| semi-square | 45 |
| sesqui-square | 135 |
| novile | 40 |
| bi-novile | 80 |
| quadri-novile | 160 |
| decile | 36 |
| tri-decile | 108 |
| undecile | ~32.72 |
| bi-undecile | ~65.45 |
| tri-undecile | ~98.18 |
| quadri-undecile | ~130.90 |
| quinque-undecile | ~163.63 |
| semi-sextile | 30 |
| quincunx | 150 |
| tredecile | ~27.69 |
| bi-tredecile | ~55.38 |
| tri-tredecile | ~83.07 |
| quadri-tredecile | ~110.76 |
| quinque-tredecile | ~138.46 |
| sexa-tredecile | ~166.15 |
| semi-septile | ~25.71 |
| sesqui-septile | ~77.14 |
| sester-septile | ~128.57 |
| quindecile | 24 |
| bi-quindecile | 48 |
| quadri-quindecile | 96 |
| septua-quindecile | 168 |
| quarti-square | 22.5 |
| tri-quarti-square | 67.5 |
| quinque-quarti-square | 112.5 |
| septua-quarti-square | 157.5 |
| semi-novile | 20 |
| quinque-semi-novile | 100 |
| septua-semi-novile | 140 |
| vigintile | 18 |
| tri-vigintile | 54 |
| septua-vigintile | 126 |
| nona-vigintile | 126 |
| quarti-sextile | 15 |
| squile | 75 |
| squine | 105 |
| undeca-quarti-sextile | 165 |

## Premium

Astrobot is and will always be 100% free without limitations, but in order to help with development and maintenance costs, it offers a few "premium" features you can obtain by becoming a patron. Once you've pledged, send a DM to `Tim#2373` to receive instructions for receiving your premium features.

[Support Astrobot on Patreon](https://patreon.com/timotejroiko)

Thank you very much for all your love and support! <3

### Custom Orbs (€3+)

Astrobot includes 3 free orb sets to chose from. Becoming a €3+ patron lets you create your own custom orbs set with custom orb values for all aspects. Orb values can be defined on a per-aspect or a per-planet basis. Custom orbs are personal and can only be used by the person who owns them, but you can gift custom orbs to someone else.

### Custom Theme (€6+)

Astrobot includes 3 free chart themes for everyone to chose from. Becoming a €6+ patron allows you to design your own custom theme! Custom themes are extremely customizable and let you change the colors of almost everything in the chart. Here are a few examples of custom themes created by our lovely supporters:

![custom theme 1](https://github.com/timotejroiko/astrobot-docs/blob/master/theme1.png?raw=true) ![custom theme 2](https://github.com/timotejroiko/astrobot-docs/blob/master/theme2.png?raw=true) ![custom theme 3](https://github.com/timotejroiko/astrobot-docs/blob/master/theme3.png?raw=true)

Custom themes are personal and can only be used by the person who owns them, but you can gift custom themes to someone else.

### Custom Theme for Servers (€12+)

Spice up your discord server with a server-wide custom theme! Becoming a €12+ patron lets you define a custom theme for an entire server. Server-wide themes are applied to all charts created and opened in the server but individual users can still override it and/or turn it off if they prefer a different theme.

## About Astrobot

Astrobot is an Astrology Discord bot made with love by `Tim#2373`

Check out my other projects: [https://github.com/timotejroiko](https://github.com/timotejroiko)  
Join me on Discord: [https://discord.gg/BpeedKh](https://discord.gg/BpeedKh)  
Support me on Patreon: [https://patreon.com/timotejroiko](https://patreon.com/timotejroiko)  

[![top.gg widget](https://top.gg/api/widget/344272098488877057.svg)](https://top.gg/bot/344272098488877057)
