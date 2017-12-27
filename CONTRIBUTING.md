# Contributing to SLSK

First of all, thank you very much for considering contributing to SLSK, your help makes all the difference :)

# Table of Contents

[A few words of comfort](#a-few-words-of-comfort)

[So how do I contribute?](#so-how-do-i-contribute)

* [Documentation](#documentation)

* [Improving code / UI](#improving-code--ui)

* [Improving the database](#improving-the-database)

* [Guidelines for adding entries](#guidelines-for-adding-entries)

* [Changelog and Versioning](#changelog-and-versioning)

[Closing words](#closing-words)

# A few words of comfort

*Make yourself at home.* Even though this might be considered a small hobby project, you are invited to take part of it if you so desire.

*Any help is welcome.* Whether it be a shoutout for a bug you just found or a mass addition of entries in the database, I appreciate your
time and effort, and again, thank you very much for your help.

And of course, the usual: *be friendly and polite*, but don't feel afraid to share your opinions if you need to, and, most importantly,
*don't be ashamed to ask for help*. Who knows, maybe your neighbor Github user has actually found that pesky save path you spent days
searching for ;)

# So how do I contribute?

First of all, make sure you have installed the [dependencies required](README.md#getting-started) for this project.

In short, there are some ways you can help contributing to this project, which will be explained below. Contributing is not limited to these only,
but they are essentially the main ones.

## Documentation

I'll be honest here: in the beginning, *I made SLSK with little to no planning. At all.* That also meant little to no documentation, aside from
commenting the code. I admit I'm to blame, at least partially. Whilist coding it, I thought "meh, it's such a small project, maybe it'll stay
simple like this, just add a thing here and there...". Heh, and then it became a monster. So this, along with the fact I was in the middle of
learning C++ and software engineering in college, while learning Qt at home and building SLSK, *all from scratch and at the same time*,
kinda left me without a solid ground and made me keep taking shots in the dark.

That said. This is literally the first program I've ever built and finished, so I'm paying the toll. I'll be glad to help with (and accept help to)
properly document this program if it is really needed even for a small project like  this one, according to the community's needs. All I need
is a little guidance because I'm a little clueless on *what* exactly to document. I'll be sure to give my best during my free time between college
and other things I have to take care of. To give you a head start, it's all commented in the code. If you have any doubts, don't be afraid to ask.

## Improving code / UI

Ah, now we're getting to the fun part. Both the code and the UI were made using the Qt Creator IDE. Using it is not obligatory, but highly
recommended so we can keep a standard.

* About the code:
  * Please try to keep the code *well commented*. It doesn't need to be a car manual, but let us know what your code does so documenting
gets easier (especially when you manage to reduce parts of the code)
  * Also, try to keep the code *well formatted*. It's OK if it gets kinda big, as long as it's functional and stable enough so it doesn't crash the
program, we can always reduce it later
  * Still regarding the point above, reduce code as you like but *don't reduce it too much* so it gets unreadable - I know we as programmers
are always itching to do things like [this](https://image.slidesharecdn.com/frontendoptimize-111122031131-phpapp02/95/heavy-web-optimization-frontend-11-728.jpg?cb=1357697476),
but remember that readability counts a lot, so reduce with moderation
* About the UI:
  * If you feel the UI needs a tweak here and there, let us know first so we can discuss about it (bring your mockups / screenshots as well!)
  * You may tweak the UI in whichever way you want, but please try to make it clean and minimalistic. Remember, *less is more*
  * Also, try to make it easy for the eyes - not wanting to start a flame war between light/dark themes here, but please consider those poor
folks who are trying to backup their stuff in their pitch black rooms at 1:00 AM (not me, but you get the drill) :(

If you don't feel like coding or tweaking the UI, it's all fine - you can add your ideas to the [TODO](TODO.md) list, which has a section for optional
suggestions.

## Improving the database

An SQLite database is generated during installation. This is the most important part of the whole project, without it we just have a pretty but
useless shell made in Qt. All the entries to this database are in a .csv file ([DB.csv](DB.csv)), so you can add entries easily and check for paths
quickly without having to download the whole project. It is highly recommended you open the spreadsheet file ([DB.ods](DB.ods)) and add or
edit entries there, then generating the CSV file there (you can do it in LibreOffice Calc for example, which is the one I recommend).

Each registered Linux Steam game in the file and consequently in the database (from now on referred as an "entry") has the following columns
(or "fields") in this exact order:

* **AppID (PRIMARY KEY)** - The game's AppID on Steam
* **SteamName** - The game's name (just make sure to remove any special symbols like copyright, tm, double quotes or what have you)
* **GameFolder** - The game folder's name
* **SavePath1** - The full path of the folder where the game stores its save files
* **SaveFolder1** - The name of the folder where the game stores its save files (last folder in the path - after the last "/")
* **ConfigPath1** - The full path of the folder where the game stores its configurations
* **ConfigFolder1** - The name of the folder where the game stores its configurations (last folder in the path - after the last "/")
* **SavePath2** - A second (optional) path for the save folder, if the game has more than one save location
* **SaveFolder2** - A second (optional) save folder
* **ConfigPath2** - A second (optional) path for the config folder, if the game has more than one config location
* **ConfigFolder2** - A second (optional) config folder
* **SavePath3** - A third (optional) path for the save folder
* **SaveFolder3** - A third (optional) save folder
* **ConfigPath3** - A third (optional) path for the config folder
* **ConfigFolder3** - A third (optional) config folder

Adding an entry to the file requires the three first columns as a bare minimum: AppID, SteamName and GameFolder. These three columns can *always* be found
in several ways:

* **AppID**: you can look at the game's URL (http://store.steampowered.com/app/`AppID-goes-here`), *or* search for the game at [SteamDB](https://steamdb.info),
it's under the "App ID" field
* **SteamName**: pretty obvious. It's also in the game's page at SteamDB under the "Name" field
* **GameFolder**: if you have the game installed, take a look at your Steam library folder (generally `~/.local/share/Steam/steamapps/common`, or wherever you
have your games installed). Alternatively, if you don't have the game, it can be found under SteamDB, in the Configuration menu at the side of the page (or if
you like URLs, `https://steamdb.info/app/AppID-goes-here/config`). Under "**Configuration**", the key called "**installdir**" shows the game's folder name

Here's a few guidelines which will help both the program on filtering and working in general, and whoever wants to take a quick look at the file to know where
there is missing information.

### Guidelines for adding entries

#### 1. **Entry structures**

When adding an entry to the CSV file, keep the following in mind:

* **One line, one entry**
* **Separate fields with a single pipeline --> |**
* **Every field needs to be filled**

Adding Half-Life directly to the .csv file, as an example:

70|Half-Life|Half-Life|$STEAMAPPS/Half-Life/valve|valve|$STEAMAPPS/Half-Life/valve|valve|[N/A]|[N/A]|[N/A]|[N/A]|[N/A]|[N/A]|[N/A]|[N/A]

If you're adding entries via spreadsheet, just make sure that:

* **The field delimiter is '|', there's no text delimiter**
* **Remove the first line which contains the column names after exporting the CSV file**
* **(OPTIONAL) Sort the spreadsheet by alphabetical order before exporting - [here's a good site for you if you wish](http://www.alphabetizer.org/)**

Additionally, if you want to batch add entries (or really just automate it so you don't need to enter each one individually), there's a batch script I wrote in
Python 3 [right here](db_batch) if you wanna use it.

All fields except for AppID, SteamName and GameFolder **must** make use of the following labels when applicable:

* **$STEAMUSER** - shortcut to `~/.local/share/Steam/userdata/7656*` *(including the wildcard)*
* **$STEAMAPPS** - shortcut to `~/.local/share/Steam/steamapps/common/<GameFolder>`
* **[N/A]** - game naturally doesn't have saves/configs
* **[CLOUD-ONLY]** - saves/configs only exist in the cloud or in the game's server, out of reach
* **[UNKNOWN]** - saves/configs are in an unknown location

**NOTE::** there's no need to end the path with a "/", like "$STEAMAPPS/Half-Life/valve/". The GUI tool may actually get confused with this.

So, giving a few examples on when to use each one of these labels:

* Some games like Saints Row The Third, Bioshock Infinite and PAYDAY 2 store their saves inside a folder with the user's STEAMID,
which is inside the Steam folder (like `~/.local/share/Steam/userdata/7656*/<AppID>`), so the SavePath/ConfigPath is written
like **$STEAMUSER/`<AppID>`**
* Half-Life 2 has its saves stored in `~/.local/share/Steam/steamapps/common/Half-Life 2/hl2/save`, so it's SavePath in the database
is written like **$STEAMAPPS/hl2/save**
* CS:GO has no save files at all due to its multiplayer-only nature, but has config files in `$STEAMAPPS/csgo/cfg`, so its ConfigPath
stays like that, but its SavePath is labeled **[N/A]** (this also applies to the second and third SavePath/ConfigPath fields, when there's
no second or third path for saves/configs)
* Killing Floor has its save games hosted exclusively in the Steam Cloud and thus unreachable from our computers, so its SavePath
is labeled **[CLOUD-ONLY]**, while its config files are in `~/.killingfloor`
* The idea is that all games store their saves and configs somewhere, no matter where. *But*, sometimes it's really hard to find those
paths, and that's where the **[UNKNOWN]** label comes in. This will be explained further below

#### 2. **Path structures**

Game saves and configs are usually structured in one of the following ways (not definitive, but these patterns were sure detected
when searching locally for paths):

* **Case 1** - saves/configs consist of *a single file* (e.g. `game/save.dat` - Crypt of the NecroDancer, Knights of Pen and Paper, etc)
* **Case 2** - saves/configs consist of *multiple files with the same extension* (e.g. `game/*.cfg` - System Shock 2)
* **Case 3** - saves/configs consist of *a single folder with lots of different files* (e.g. `game/save` - most common case for the majority
of games)
* **Case 4** - saves/configs consist of *multiple folders*, like one folder per save slot (e.g. `game/save_*` - again, System Shock 2)

That said, depending on how the SavePath/ConfigPath ends, the SaveFolder/ConfigFolder field(s) will change.
If the SavePath/ConfigPath ends in:

* *A single file or multiple files (Cases 1 and 2)* - put the **parent folder** of the path (in both cases, `game`)
* *A single folder or multiple folders (Cases 3 and 4)* - put the **last folder** of the path (`save` and `save_*`, respectively)

**NOTE:** if the config files happen to be *in the same folder as the save files*, or vice-versa, copy-paste the same path and folder for both.
Yes, this means duplicates may occur, but that's intentional. Also, *please* use `~` to indicate the user's home folder, people recognize it
easily and it's shorter than `$HOME`, plus the GUI tool needs it to do some work.

#### 3. **[UNKNOWN] paths**

**NOTE: this is exclusively for paths labeled as [UNKNOWN], it doesn't apply to games with paths labeled as [N/A] or [CLOUD-ONLY].**

If you want to add a game to the database but can't find its save/config paths, or you're not sure where the save/config files are located,
don't worry - we might find those paths sooner or later, but we need to know that you can't find them. That makes it easier to keep looking
for information about that game's paths (whether they actually exist or not). We keep a file called [MISSINGLIST.md](MISSINGLIST.md) for games that meet
this criteria, kind of like a "wanted list" or "bounty list" if you like catchy names. Here's how to proceed if you end up in this situation:

1. Add the game normally to the database using the **[UNKNOWN]** label in the respective missing fields
2. Include the game in [CHANGELOG.md](CHANGELOG.md) normally, but mark it as "(incomplete)", like this:
  * (incomplete) GameName
3. Write the game's name in MISSINGLIST.md, under the section "**LIST OF INCOMPLETE GAMES**", specifying which paths are unknown - only save path, only config
   path, or both - like this:
  * GameName (save and config)
4. Once the paths are found, or if it's proven that there are no paths - **[N/A]** - or that the missing information is **[CLOUD-ONLY]**:
  * update the database accordingly
  * add the game in the CHANGELOG but without the "(incomplete)" before it (more details below in Changelog and Versioning)
  * remove the game's name from MISSINGLIST.md

#### 4. Games that "aren't really games"

Steam is weird in a sense that it also counts DLCs, expansions and bundles as games, so the real game count is not accurate. We're looking to register only full,
standalone games. If you happen to find an entry in the Steam catalog like that, *don't* add it to the database. Add it only to [MISSINGLIST.md](MISSINGLIST.md)
instead, under the section "**LIST OF IGNORED ENTRIES**", stating why was it ignored. If you're not sure at all, or it all seems too confusing for you, add it under
the section **LIST OF NOT-ADDED GAMES**, stating why you couldn't add it normally.

Both sections "**LIST OF NOT-ADDED GAMES**" and "**LIST OF IGNORED ENTRIES**" do not need to be included in the CHANGELOG, so you don't need to state you've put
any game in either of those. Just put it and commit away.

*Examples of entries which would enter in this category*:

- DLCs (e.g. the numerous Saints Row ones)
- Bundles (e.g. game + soundtrack)
- Expansions (which depend on the base game - e.g. Binding of Isaac Afterbirth and Afterbirth+ - they depend on the base game, Rebirth)

**NOTE: "Expandalones" do NOT apply to this** - e.g. Saints Row Gat Out of Hell, it is its own thing in the sense it doesn't depend on Saints Row IV to run, so
it should be considered as a separate game.

## Changelog and Versioning

Even though the main focus of the project is the database, there's also the GUI tool which may need improvements as time passes.
When contributing, versioning applies only to the *core program* (be it code or UI). Database updates do not count for versioning, but
they still appear on the Changelog. SLSK uses the standard [Semantic Versioning](https://semver.org/) - MAJOR.MINOR.PATCH, no big
surprises here. In short, there may be Core updates and Database updates. The former applies to the core program, but *can* also include
database updates (as seen below), while the latter applies *exclusively* to database changes.

Pull requests related to updating docs and database entries will be commited directly to the *master* branch. Pull requests regading any change to the GUI tool
will be commited to a separate *dev* branch, which should be tested and proven stable enough to make sure it's stable enough before submitting a merge request,
as this will be considered a version increment.

### Example of changelog entry for database additions only:

#### YYYY-MM-DD - Database update
* X games added to the database:
  - this game
  - that other game
  - (incomplete) awesome game
  - ...
* X games fixed in the database:
  - superb delicious game (save path had an extra "save")
  - ...
* X games completed in the database:
  - that game i haven't played for ages
  - ...

### Example of changelog entry for core program versioning:

#### YYYY-MM-DD - Core update [vX.Y.Z]
* Added this neat feature
* Fixed those pesky bugs
* X games added to the database:
  - not-so-awesome game
  - ...
* X games completed in the database
  - awesome game
  - ...

# Closing words

This is it for now. It's a really simple project so there's not much specific detail, except for the database entries. If you have any doubts, don't be
afraid and ask away so I can improve this file ;)
