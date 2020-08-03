# Astrobot

A fully featured Astrology software for Discord! Astrobot can create a variety of astrological charts and supports a vast array of possibilities. Its features include:

* Planets, Stars, Asteroids, Arabic Parts, Comets, Artificial Sattelites, and more
* Tropical and Sidereal zodiacs
* Geocentric, Topocentric and Heliocentric
* 20+ House Systems and 40+ Ayanamsas
* Extremely customizable
* Custom themes and custom orb sets (for patreons)

[![top.gg widget](https://top.gg/api/widget/344272098488877057.svg)](https://top.gg/bot/344272098488877057)

## Getting Started

To add Astrobot to your Discord server click here -> [Invite Astrobot](https://discord.com/oauth2/authorize?client_id=344272098488877057&permissions=379968&scope=bot)

If you need any help join our support server -> [Join Astro Dev](https://discord.gg/BpeedKh)

## Basic Commands

[Prefix](#prefix)
[Help](#help)

Astrobot can be quite complex to use at first, but once you get the hang of it its quite easy!

Astrobot's default prefix is `.` and it works both in servers as well as in DMs. You can also customize Astrobot's prefix in your server with the prefix command explained below.

So lets get started with Astrobot's basic commands:

### Prefix

Use this command to view and/or change Astrobot's prefix in your server. Only guild owners can change the guild prefix, and this command cannot be used in DMs.

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

The help command contains almost everything on this page in an acessible way. It divides the content in sections and pages that can be easily navigated by clicking on the emoji reactions that show up.

Examples:

* `.help` - shows the help menu and displays available options
* `click on the (1) emoji` - enters the first section and displays the options for that section
* `click on the (1) emoji again` - enters the first subsection of the first section and displays the options for it
* `click on the (<-) emoji` - goes back to the previous section
* `click on the (2) emoji` - enters the second section and displays the options for that section
* `click on the (<-) emoji` - goes back to the previous section
* `click on the (<-) emoji` - goes back to main menu

And so on (easier to see it on discord than to explain it here)

The help command always works regardless of how old it gets, you can safely open a permanent help menu in a read-only channel and send your users there instead of using it again and again.

Multiple people can use the same help menu at the same time, but if clicking on the buttons too fast some clicks will ignored to prevent overload, so avoid fighting with each other over which page to display :3

## Charting Commands

[Newchart](#newchart)
[Savechart](#savechart)
[Editchart](#editchart)
[Deletechart](#deletechart)
[Findchart](#findchart)
[Mycharts](#mycharts)

These commands are used to create a variety of charts and are the core feature of Astrobot

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

Now lets say we want to create a biwheel, all you have to do is add a ` + ` at the end of the command, and give it a new set of data the same way as above:

* `.newchart 10/20/1995, 15:30, madrid spain + 5/15/1992, 6:45am, london uk`

Now we have a biwheel displaying both charts!

#### Now

Besides the above Date, Time and Location method, you can also use the keyword `now` to create a chart for the current date and time. For example:

* `.newchart now`
* `.newchart now, madrid spain`
* `.newchart 10/20/1995, 15:30, madrid spain + now, madrid spain`

This makes it easy to check the current transits, both in a single chart of in a biwheel with another chart. The `now` keyword can also be modified by adding or removing a number of days from it:

* `.newchart now+1` - tomorrow
* `.newchart now-1` - yesterday
* `.newchart now+0.5` - 12 hours from now

Note that there should be no spaces around the plus sign in this case.

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

These two options let you add and/or remove planets and objects from a chart. When used on biwheels, this option affects each chart independently. For example:

* `.newchart now --add=A1,A2 --remove=A2060` - remove Chiron and add Ceres and Pallas
* `.newchart jack --add=A1 + now --add=A1` - add Ceres to both charts

To find out which planets and objects are available and how to get them check out the [Planets](#planets) section.

##### --zodiac

This option lets you specify which zodiac should be used. When used on biwheels, this option affects each chart independently. For example:

* `.newchart now --zodiac=D1` - use the draconic (true node) zodiac
* `.newchart jack --zodiac=S1 + now --zodiac=S1` - use the fagan/bradley sidereal zodiac in both charts

##### --houses

This option lets you specify which house system should be used. When used on biwheels, this option affects each chart independently. For example:

* `.newchart now --houses=13` - use the koch house system
* `.newchart jack --houses=24 + now --houses=24` - use the whole signs house system for both charts

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

* `.newchart john --return2=p1, next, now` - john's next lunar return starting from the current date and time
* `.newchart jack --return2=p2, closest, 5/5/2025 lisbon portugal` - jack's mercury return closest to 5/5/2025 in lisbon portugal
* `.newchart john --return2=p5, current, now + jack --return2=p5, current, now` - biwheel john's most recent jupiter return with jacks most recent jupiter return

##### --progression

This option lets you create a progressed chart using the secondary progressions method. When used on biwheels, this option affects each chart independently. For example:

* `.newchart john --progression=1/1/2025` - john's secondary progressed chart for 1/1/2025
* `.newchart john + john --progression=now` - john's birth chart biwheeled with his current secondary progressed chart

##### --persona

This option lets you create a "persona" chart for a specific planet. When used on biwheels, this option affects each chart independently. For example:

* `.newchart john --persona=p5` - john's jupiter persona chart
* `.newchart john --persona=p5 + john --persona=p6` - john's jupiter persona chart biwheeled with john's saturn persona chart

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

This option lets you change the chart's color theme. There are three built-in themes: `classic`, `elements` and `rainbow`. Additionally, custom themes can be created as a premium feature. For example:

* `.newchart now --theme=classic` - use the classic theme for this chart

##### --orbs

This option lets you change the chart's orb values. There are three built-in orbs: `astrobot`, `astro.com` and `strict`. Additionally, custom orbs can be created as a premium feature.

* `.newchart now --orbs=strict`

##### --aspects

This option lets you define which aspects should be enabled in the chart. A full list of supported aspects can be found in the [Aspects](#aspects) section. For example:

* `.newchart now --aspects=trine,sextile,square` - show only trines, sextiles and squares

##### --disable & --enable

This option lets you disable or re-enable a planet's aspect points. For example:

* `.newchart now --disable=p0,p1,p2` - disable aspects for the sun, moon and mercury
* `.newchart jack + now --enable=a1` - re-enable aspects to Ceres if disabled

##### --composite

This option lets you turn a biwheel into a composite chart using the midpoint composite method. For example:

* `.newchart jack + john --composite` - create a midpoint composite between jack and john

##### --preset

This option lets you load a set of options from a preset. There are two built-in presets: `default` and `original`. You can also create your own presets, check the [Presets](#presets) section. When using biwheels, this option can be set separately for both charts. For example:

* `.newchart jack --preset=default` - show this chart using the default settings
* `.newchart jack --preset=original` - show this chart using the same settings the chart was saved with
* `.newchart jack --preset=myPreset` - show this chart using a custom preset

##### --chartinfo

This option lets you view more details about the chart or charts. When viewing other people's charts, any personal information will be redacted. For example

`.newchart john --chartinfo` - view more information about john's chart

### Savechart

### Editchart

### Deletechart

### Findchart

### Mycharts