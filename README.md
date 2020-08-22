[![top.gg widget](https://top.gg/api/widget/344272098488877057.svg)](https://top.gg/bot/344272098488877057)

# Astrobot

A fully featured Astrology software for Discord! Astrobot can create a variety of astrological charts and supports a vast array of possibilities. Its features include:

* Planets, Stars, Asteroids, Arabic Parts, Comets, Artificial Sattelites, and more
* Tropical and Sidereal zodiacs
* Geocentric, Topocentric and Heliocentric
* 20+ House Systems and 40+ Ayanamsas
* Biwheels and composites
* Extremely customizable
* Custom themes and custom orb sets (premium)

![preview](preview.png)

## Index

* **[Prefix](#prefix)**
* **[Help](#help)**
* **[Charting Commands](#charting-commands)**
	* **[Newchart](#newchart)**
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
* **[Donations and Premium Features](#donations-and-premium-features)**

## Getting Started

To add Astrobot to your Discord server click here -> [Invite Astrobot](https://discord.com/oauth2/authorize?client_id=344272098488877057&permissions=379968&scope=bot)

If you need any help join our support server -> [Join Astro Dev](https://discord.gg/BpeedKh)

Astrobot can be quite complex to use at first, but once you get the hang of it its quite easy!

Astrobot's default prefix is `.` and it works in servers as well as DMs. You can also customize Astrobot's prefix in your server with the prefix command explained below.

So lets get started with Astrobot's basic commands:

### Prefix

Use this command to view and/or change Astrobot's prefix in your server. Only server owners can change the prefix and it cannot be used in DMs.

Examples:

* `.prefix` - shows the current prefix
* `.prefix !!` - changes the prefix to `!!`
* `!!help` - use the new prefix

If you ever forget your prefix, you can also use `@astrobot` as a prefix:

* `@astrobot prefix` - shows the current prefix
* `@astrobot prefix !!` - changes the current prefix to `!!`
* `!!help` - use the new prefix

Kicking Astrobot from your server also resets its prefix.

### Help

The help command opens an interactive menu that includes almost everything on this page in an acessible way. It divides the content in sections and pages that can be easily navigated by clicking on the emoji reactions that show up.

Examples:

* `.help` - shows the interactive help menu and displays available options
* `click on the (1) emoji` - enters the first section and displays the options for that section
* `click on the (1) emoji again` - enters the first subsection of the first section and displays the options for it
* `click on the (<-) emoji` - goes back to the previous section
* `click on the (2) emoji` - enters the second section and displays the options for that section
* `click on the (<-) emoji` - goes back to the previous section
* `click on the (<-) emoji` - goes back to main menu

And so on (easier to see it on discord than to explain it here)

The interactive menu always works regardless of how old it gets so you can safely open a permanent help menu in a read-only channel and send your users there so they dont need to use it again and again.

Multiple people can use the same help menu at the same time, but if you click on the reactions too fast some clicks will be ignored to prevent overload, so avoid fighting with each other over which page to display.

## Charting Commands

These commands are used to create a variety of charts and are the core feature of Astrobot.

### Newchart

This command lets you create a variety of charts and supports an extensive amount of customization options including biwheels, solar returns, progressions, composites and more!

#### Single Charts

For starting, lets create a transit chart for a given date:

* `.newchart 10/20/1995`

The above command will generate a chart for October 20th 1995 at noon GMT. By default it expects a **MM/DD/YYYY** date but you can change it to **DD/MM/YYYY** by using the dateformat option explained in the [Settings](#settings) section.

Now if you want to give it a specific time of the day:

* `.newchart 10/20/1995, 15:30` or `.newchart 10/20/1995, 3:30pm`

This will generate a chart for October 20th 1995 at 3:30pm GMT. In both cases no houses will be shown because the chart lacks a location. So lets give it one:

* `.newchart 10/20/1995, madrid spain`
* `.newchart 10/20/1995, 15:30, madrid spain`

Now we have a chart for noon and another for 3:30pm both in the madrid timezone, and since we defined a location the charts will also display Houses!

PS: You can also edit your commands, and Astrobot will edit its response accordingly, no need to flood your chat with new charts, how cool is that? :3

#### Biwheels

Now lets say we want to create a biwheel, all you have to do is add a ` + ` at the end of the command (with spaces around it), and give it a new set of data the same way as above:

* `.newchart 10/20/1995, 15:30, madrid spain + 5/15/1992, 6:45am, london uk`

Now we have a biwheel displaying both charts!

#### Now

Besides the above Date, Time and Location method, you can also use the keyword `now` to create a chart for the current date and time. For example:

* `.newchart now`
* `.newchart now, madrid spain`
* `.newchart 10/20/1995, 15:30, madrid spain + now, madrid spain`

This makes it easy to check the current transits, both in a single chart and in a biwheel with another chart. The `now` keyword can also be modified by adding or removing a number of days from it:

* `.newchart now+1` - tomorrow
* `.newchart now-1` - yesterday
* `.newchart now+0.5` - 12 hours from now

Note that there should be no spaces around the plus/minus signs in this case.

#### Saved Charts

Astrobot's chart saving system lets you save charts under a name of your choice, as explained in the [Savechart](#savechart) section. Once you have a saved chart, you can easily pull it up by name, for example:

* `.newchart jack`
* `.newchart john doe`
* `.newchart john doe + now`
* `.newchart john doe + jack`

You can also load other people's charts, as long as they are public.

#### Chart Options

Additionally, there are multiple chart options that can be added to the Newchart command using the `--option=value` format. All of these options (with a few obvious exceptions) can be used together in any combination.

##### --add & --remove

These two options let you add and/or remove planets and objects from a chart. When used on biwheels, this option affects each chart independently. Additionally, the `--remove` option includes an `ALL` keyword to remove all planets. For example:

* `.newchart now --add=A1,A2 --remove=A2060` - remove Chiron and add Ceres and Pallas
* `.newchart jack --add=A1 + now --add=A1` - add Ceres to both charts
* `.newchart now --remove=ALL --add=P0,P1` - remove everything exept Sun and Moon

Because of the sheer amount of planets and objects that Astrobot supports, it makes use of an ID system to identify them. To find out which planets and objects are available and how to find them and their respective IDs, check out the [Planets](#planets) section.

##### --zodiac

This option lets you specify which zodiac should be used. When used on biwheels, this option affects each chart independently. For example:

* `.newchart now --zodiac=D1` - use the draconic (true node) zodiac
* `.newchart jack --zodiac=S1 + now --zodiac=S1` - use the fagan/bradley sidereal zodiac in both charts

Check the available zodiacs and ayanamsas in the [Zodiacs](#zodiacs) section.

##### --houses

This option lets you specify which house system should be used. When used on biwheels, this option affects each chart independently. For example:

* `.newchart now --houses=13` - use the koch house system
* `.newchart jack --houses=24 + now --houses=24` - use the whole signs house system for both charts

Check the available house systems in the [Houses](#houses) section.

##### --timezone

This option lets you specify a timezone, which overrides any automatic timezone if applicable. A timezone can be specified by a TZData identifier or by a number of offset minutes. When used on biwheels, this option affects each chart independently. For example:

* `.newchart 5/5/2015, 16:00 --timezone=America/New_York` - use the america/new_york timezone identifier
* `.newchart 5/5/2015, 16:00 --timezone=+50 + 7/7/2016, 16:00 --timezone=-50` - use UTC+00:50 on the first chart and UTC-00:50 on the second

##### --return

This option lets you create solar return charts by specifying a year and optionally a location. When used on biwheels, this option affects each chart independently. For example:

* `.newchart john --return=2021` - john's solar return for 2021 in his birth place
* `.newchart john --return=2021, london uk` - john's solar return for 2021 in london
* `.newchart john --return=2021, london uk + jack --return=2021, madrid spain` - biwheel john's solar return for 2021 in london and jack's solar return for 2021 in madrid

##### --return2

This option lets you create a return chart for any planet, not only the sun, by specifying a planet ID, a date and a search direction. Available search directions are `current`, `next` and `closest`. When used on biwheels, this option affects each chart independently. For example:

* `.newchart john --return2=P1, next, now` - john's next lunar return starting from the current date and time
* `.newchart jack --return2=P2, closest, 5/5/2025 lisbon portugal` - jack's mercury return closest to 5/5/2025 in lisbon portugal
* `.newchart john --return2=P5, current, now + jack --return2=P5, current, now` - biwheel john's most recent jupiter return with jacks most recent jupiter return

##### --progression

This option lets you create a progressed chart using the secondary progressions method. When used on biwheels, this option affects each chart independently. For example:

* `.newchart john --progression=1/1/2025` - john's secondary progressed chart for 1/1/2025
* `.newchart john + john --progression=now` - john's birth chart biwheeled with his current secondary progressed chart

##### --persona

This option lets you create a "persona" chart for a specific planet. When used on biwheels, this option affects each chart independently. For example:

* `.newchart john --persona=P5` - john's jupiter persona chart
* `.newchart john --persona=P5 + john --persona=P6` - john's jupiter persona chart biwheeled with john's saturn persona chart

##### --design

This option lets you create a "design" chart as seen in the Human Design System. When used on biwheels, this option affects each chart independently. For example:

* `.newchart john --design` - john's design chart
* `.newchart john + john --design` - john's birth chart in a biwheel which his design chart

##### --coordinates

This option lets you set the chart's coordinate system between `Geocentric`, `Topocentric` and `Heliocentric`. When used on biwheels, this option affects each chart independently. For example:

* `.newchart john --coordinates=heliocentric` - john's heliocentric chart
* `.newchart john --coordinates=geocentric + john --coordinates=topocentric` - biwheel john's chart in geocentric and topocentric coordinates

##### --size

This option lets you change the resolution of the resulting chart image as well as the scale of the fonts and gyphs on the chart. For example:

* `.newchart now --size=2000` - set the chart resolution to 2000x2000 pixels
* `.newchart jack + now --size=1500,120` - set the chart resolution to 1500x1500 pixels and the font scaling to 120%

##### --theme

This option lets you change the chart's color theme. There are three built-in themes: `classic`, `elements` and `rainbow`. For example:

* `.newchart now --theme=classic` - use the classic theme for this chart

Additionally, custom themes can be created as a premium feature, check the [Premium](#premium) section.

##### --orbs

This option lets you change the chart's orb values. There are three built-in orbs: `astrobot`, `astro.com` and `strict`. For example:

* `.newchart now --orbs=strict`

Additionally, custom orbs can be created as a premium feature, check the [Premium](#premium) section

##### --aspects

This option lets you define which aspects should be enabled in the chart. For example:

* `.newchart now --aspects=trine,sextile,square` - show only trines, sextiles and squares

A full list of supported aspects can be found in the [Aspects](#aspects) section.

##### --disable & --enable

These options let you disable or re-enable a planet's aspect points. Additionally, they include an `ALL` keyword for selecting all planets. For example:

* `.newchart now --disable=P0,P1,P2` - disable aspects for the sun, moon and mercury
* `.newchart jack + now --enable=A1` - re-enable aspects to Ceres if disabled
* `.newchart john --disable=ALL --enable=P0,P1` - disable aspects for all planets except Sun and Moon

##### --composite

This option lets you turn a biwheel into a composite chart using the midpoint composite method. For example:

* `.newchart jack + john --composite` - create a midpoint composite between jack and john

##### --preset

This option lets you load a set of options from a preset. There are two built-in presets: `default` and `original`. When using biwheels, this option can be set separately for both charts. For example:

* `.newchart jack --preset=default` - show this chart using the default settings
* `.newchart jack --preset=original` - show this chart using the same settings the chart was saved with
* `.newchart jack --preset=myPreset` - show this chart using a custom preset
* `.newchart jill --preset=myPreset + jack --preset=original` - show jill's chart with a custom preset in a biwheel with jack's chart in its original state

Check out the [Presets](#presets) section to learn how to create and manage your custom presets.

##### --chartinfo

This option lets you view more details about the chart or charts. When viewing other people's charts, any personal information will be redacted. For example

`.newchart john --chartinfo` - view more information about john's chart

### Openchart

This command loads a saved chart in its original state, exactly as it was when it was saved. It is essentially a shortcut for `--preset=original` but it can only open saved charts and doesnt support additional options. For example:

* `.openchart daniel` - show daniel's chart in its original state

### Savechart

This command lets you save the last chart you created under a name of your choice. All names are case sensitive and must not include commas, double dashes nor slashes and mentions will be converted to Discord IDs For example:

* `.savechart mychart` - save the last chart you created under the name `mychart`

#### Savechart Options

A chart can be saved as public or private, and also be shared with specific people, check out the following options:

##### --private & --share

Save this chart as a private chart. Private charts can only be opened by their owners and the people the chart was shared with. For example:

* `.savechart mychart --private` - save this chart as private
* `.savechart mychart --private --share=@myfriend` - save this chart as private and share it with a specific person

##### --replace

If you already have a saved chart with a given name and you want to replace it, you can use this option to overwrite it:

* `.savechart myexistingchart --replace` - replace your previous chart with a new one

### Editchart

This command lets you view information about one of your saved charts as well as change its name and privacy settings. For example:

* `.editchart chartname` - view information about your chart

##### --rename

Change the name of your saved chart:

* `.editchart mychart --rename=mychart2` - change your chart's name to `mychart2`

##### --private

Toggle your chart's privacy:

* `.editchart mychart --private` - toggle this chart's privacy setting

##### --share

If this chart is private, change who can use it:

* `.editchart mychart --share=@myfriend` - share or unshare this chart with a friend
* `.editchart mychart --share=none` - unshare this chart with everyone

### Deletechart

This command lets you permanently delete a chart. You can only delete charts you own. For example:

* `.deletechart mychart` - permanently delete `mychart`

### Findchart

This command lets you find a saved chart by name. If you find too many results, try searching for a more specific term. For example:

* `.findchart john` - show all charts containing `john` in their names

### Mycharts

This command lets you see all charts you have saved with your current discord account. For example:

* `.mycharts` - show all the charts you own

## Utility Commands

The following utility commands provide assistance with many things for example finding object IDs by name, changing personal settings and more.

### Findobject

This command lets you search for objects by name and discover their ID. If you cant find the object you're looking for, try a more specific search term as well as any alternative names it may have. For example:

* `.findobject eris` - show all planets, stars and objects whose names contain `eris`

##### --type

Limit the search results to specific types. For example:

* `.findobject eris --type=A` - show only asteroids whose name contains `eris`

More information about types can be found in the [Planets](#planets) section.

### Objectinfo

This command shows you information about a specific object ID, its names, type and a preview of how it appears in a chart. For example:

* `.objectinfo P5` - show information about object P5 (jupiter)

More information about common object IDs check the [Planets](#planets) section

### About

This command lets you obtain information about certain topics and components used by Astrobot such as glyphs, orbs, aspects and more.

* `.about` - list components that offer additional information

#### About Glyphs

This option creates an image showing a preview and a description of every glyph and symbol that Astrobot uses:

* `.about glyphs` - display all glyphs

#### About Aspects

This option creates an image showing a preview of every aspect supported by Astrobot:

* `.about aspects` - display all aspects

#### About orbs

This option displays a list of available orb sets, as well as orb details about a specific set:

* `.about orbs` - display a list of available orb sets
* `.about orbs astro.com` - describe the orb values of the `astro.com` orbs set

#### About Houses

This option displays a list of available house systems:

* `.about houses` - display a list of available house systems

Or check the list of house systems in the [Houses](#houses) section.

#### About Zodiacs

This option displays a list of available zodiacs and ayanamsas:

* `.about zodiacs` - display a list of available zodiacs

Or check the list of zodiacs and ayanamsas in the [Zodiacs](#zodiacs) section.

### About Planets

This option diplays a list of commonly used planets and their IDs:

* `.about planets` - display a list of common planets

Or check the list of planets in the [Planets](#planets) section.

### Settings

This command lets you configure your preferred default settings for all your charts. These settings are applied to all new charts as well as saved charts unless overriden by chart options or when using the `.openchart` command. Settings are also divided into sections for easier management.

#### Settings Sections

The following sections are available to display your current settings. Each section also includes instructions for how to edit it.

* `.settings planets` - display your currently enabled planets as well as their aspect points settings
* `.settings aspects` - display your currently enabled aspects
* `.settings houses` - display your current preferred house system as well as available house systems to chose from
* `.settings zodiac` - display your current preferred zodiac as well as available zodiacs to chose from
* `.settings themes` - display your current chart theme as well as available themes to chose from
* `.settings orbs` - display your current orbs set as well as available sets to chose from
* `.settings dateformat` - display your current preferred date format
* `.settings coordinates` - display your current preferred coordinate system
* `.settings presets` - display your saved presets

#### Settings Options

The following options are available to change your personal settings.

##### --addplanets & --removeplanets

Add and remove planets from your settings. For example:

* `.settings --addplanets=A1,A2,A3` - add Ceres, Pallas and Juno to your settings
* `.settings --removeplanets=P7,P8,P9` - remove Uranus, Neptune and Pluto from your settings

##### --enableplanets & --disableplanets

Disable and re-enable aspects points for your selected planets. All planets have their aspect points enabled by default. For example:

* `.settings --disableplanets=A1,A2,A3` - disable aspect points to Ceres, Pallas and Juno
* `.settings --enableplanets=A1,A2,A3` - re-enable previously disabled aspect points

##### --enableaspects & --disableaspects

Enable and disable your preferred aspects. For example:

* `.settings --enableaspects=conjunction,quincunx` - enable conjunctions and quincunxes
* `.settings --disableaspects=sextile,opposition` - disable sextiles and oppositions

##### --houses

Set your preferred house system. For example:

* `.settings --houses=24` - set Whole Signs as your default house system

##### --zodiac

Set your preferred zodiac. For example:

* `.settings --zodiac=S2` - set Lahiri as your default zodiac

##### --theme

Set your preferred chart theme. For example:

* `.settings --theme=rainbow` - set rainbow as your default theme

##### --orbs

Set your preferred orbs set

* `.settings --orbs=strict` - set your default orbs to strict

##### --switchdateformat

Switch your preferred date format between **DD/MM/YYYY** and **MM/DD/YYYY**. For example:

* `.settings --switchdateformat` - switch to another date format

##### --coordinates

Set your preferred coordinates system. For example:

* `.settings --coordinates=HELIOCENTRIC` - set Heliocentric as your default coordinates system

##### --savepreset & --loadpreset & --deletepreset

Manage your saved presets. Additionally a built-in `default` preset is available to reset all settings back to default. For example:

* `.settings --savepreset=custom1` - save all your current settings as a preset named custom1
* `.settings --loadpreset=custom1` - replace all your current settings with those contained in the custom1 preset
* `.settings --deletepreset=custom1` - delete the custom1 preset
* `.settings --loadpreset=default` - reset all settings back to default

### Prefix

See [Prefix](#prefix)


## Additional Information

Here you can see additional information about Astrobot including how its planet ID system works, all available house systems, zodiacs, aspects and more.

### Planets