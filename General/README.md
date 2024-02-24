# Infinite Leaftide General Meta

This meta provides both simple UIs and task automation specific to infinite leaftide content. It requires [utilitybelt](https://utilitybelt.gitlab.io/) and vtank expression patching: `/ub opt set VTank.PatchExpressionEngine true`.

do **NOT** edit in MIMB, you will break the meta, the strings for functions, as well as the xml for the UIs is too long. It will get cut off, the meta will break.

UIs:

- Main
  - Attributes
    - View unbuffed values with +1 & +10 buttons
    - `?` by each `+n` to get xp for next `n`
  - Bank
    - View bank balance
    - /b d (refreshed balance info)
    - /b d n (refreshed balance info)

Tasks:

- Reveal lvl 5 Aetheria
- Chunk Aetheria
- Powder Aetheria
- Make Enl/weakly coins
- Carve legendary keys
- Lum Gamble
  - Talk to the NPC, will trigger and gamble as many times as `gambleLum` is set
- Low/mid/high stakes gamble with keep/garbage settings, any casino
  - Hand a token to appropriate NPC, will trigger and gamble til all gambling tokens are gone from your pack

Gambling is semi-automated, all the crafting skills will immediately trigger when conditions are met.

## Meta Settings

General Settings:

```js
STATE: {Default}
    IF: Expr {getvar[generalSettings]==0}
        DO: DoAll
                DoExpr {setvar[generalSettings, 1]}     //Sets var `generalSettings` to True, signifying settings have been set.
                DoExpr {setvar[powderRed, True]}        //Convert Red Chunks to Red Powder
                DoExpr {setvar[powderBlue, False]}      //Convert Blue Chunks to Blue Powder
                DoExpr {setvar[coinRed, True]}          //Combine tokens and power for Enl coin
                DoExpr {setvar[coinBlue, False]}        //Combine tokens and power for weakly coin
                DoExpr {setvar[gambleLum, 5000]}        //Number of times to gamble Lum per run, 5k = 250m lum
                SetState {Default}
```

Under Garbage is the primary list of gambling items to trash. Tokens, xp gems, olthoi/lugian xp items, trade notes, casino recall gems, poison (5 writs per), and promisary notes are automatically kept and not included in the list below. Everything is else can be set to whatever you want. Its currently set to keep 100 massive mana stones, and 25 black market dispel gems.

```js
STATE: {Garbage}
    IF: All
            ItemCountLE 0 {Ash Gromnie Wings}
            ItemCountLE 0 {Dansha-Ki's Gem of Portal Recall}
            ItemCountLE 0 {Gem of Purity}
            ItemCountLE 0 {Gonjoku's Mana Infusion}
            ItemCountLE 0 {Mana Forge Key}
            ItemCountLE 0 {Pack Drudge}
            ItemCountLE 0 {Refreshing Water}
            ItemCountLE 0 {Tasty Pudding}
            ItemCountLE 0 {Treated Healing Kit}
            ItemCountLE 0 {Cave Penguin Cake}
            ItemCountLE 0 {Gem of Balance}
            ItemCountLE 0 {Golden Gromnie}
            ItemCountLE 0 {Hearty Lugian Loaf}
            ItemCountLE 0 {Mosswart Armband}
            ItemCountLE 0 {Potion of Black Fire}
            ItemCountLE 0 {Scroll of Raven Fury}
            ItemCountLE 0 {Thick Lugian Stew}
            ItemCountLE 0 {Antiquated Compass}
            ItemCountLE 0 {Licorice Rat}
            ItemCountLE 0 {Olthoi Larvae Steak}
            ItemCountLE 0 {Priceless Ore}
            ItemCountLE 0 {Stout Lugian Ale}
            ItemCountLE 0 {Black Page of Salt and Ash}
            ItemCountLE 0 {Health Tonic}
            ItemCountLE 0 {Mana Tonic}
            ItemCountLE 0 {Stamina Tonic}
            ItemCountLE 0 {Adjanite Mana Stone}
            ItemCountLE 0 {Azure Gromnie Wings}
            ItemCountLE 0 {Lesser Stamina Kit}
            ItemCountLE 0 {Renegade Herbal Kit}
            ItemCountLE 0 {Gem of Stillness}
            ItemCountLE 0 {Hard Boiled Olthoi Egg}
            ItemCountLE 0 {Pack Golem}
            ItemCountLE 0 {Potion of Destiny's Wind}
            ItemCountLE 0 {Vesayen Style Fried Olthoi Egg}
            ItemCountLE 0 {Fried Olthoi Egg}
            ItemCountLE 0 {Lesser Mana Kit}
            ItemCountLE 0 {Olthoi Egg}
            ItemCountLE 0 {Pickled Olthoi Egg}
            ItemCountLE 0 {Platinum Spirits}
            ItemCountLE 0 {Potion of Endless Vigor}
            ItemCountLE 0 {Candy Corn}
            ItemCountLE 0 {Health Philtre}
            ItemCountLE 0 {Mana Philtre}
            ItemCountLE 0 {Stamina Philtre}
            ItemCountLE 25 {Black Market Gem of Dispelling}
            ItemCountLE 100 {Massive Mana Charge}
            ItemCountLE 0 {Greater Mana Kit}
            ItemCountLE 0 {Ivory Gromnie Wings}
            ItemCountLE 0 {Chocolate Gromnie}
            ItemCountLE 0 {Enhanced Health Elixir}
            ItemCountLE 0 {Enhanced Mana Elixir}
            ItemCountLE 0 {Burning Coal}
            ItemCountLE 0 {Greater Stamina Kit}
            ItemCountLE 0 {Black Luster Pearl}
            ItemCountLE 0 {Pack Scarecrow}
            ItemCountLE 0 {The Orphanage}
            ItemCountLE 0 {Cow}
            ItemCountLE 0 {Crystal}
            ItemCountLE 0 {Eater}
            ItemCountLE 0 {Gearknight}
            ItemCountLE 0 {Lugian}
            ItemCountLE 0 {Moarsman}
            ItemCountLE 0 {Rat}
            ItemCountLE 0 {Remoran}
            ItemCountLE 0 {Rift}
            ItemCountLE 0 {Shadow}
            ItemCountLE 0 {Shreth}
            ItemCountLE 0 {Skeleton}
            ItemCountLE 0 {Tusker}
            ItemCountLE 0 {Zefir}
            ItemCountLE 0 {Banderling}
            ItemCountLE 0 {Drudge}
            ItemCountLE 0 {Idol}
            ItemCountLE 0 {Moar}
            ItemCountLE 0 {Mukkir}
            ItemCountLE 0 {Olthoi}
            ItemCountLE 0 {Phyntos Wasp}
            ItemCountLE 0 {Ruschk}
            ItemCountLE 0 {Scarecrow}
            ItemCountLE 0 {Shark}
            ItemCountLE 0 {Slithis}
            ItemCountLE 0 {Statue}
            ItemCountLE 0 {Tumerok}
            ItemCountLE 0 {Wisp}
            ItemCountLE 0 {Armoredillo}
            ItemCountLE 0 {Carenzi}
            ItemCountLE 0 {Ghost}
            ItemCountLE 0 {Gromnie}
            ItemCountLE 0 {Hollow Minion}
            ItemCountLE 0 {Knath'taed}
            ItemCountLE 0 {Marionette}
            ItemCountLE 0 {Mite}
            ItemCountLE 0 {Monouga}
            ItemCountLE 0 {Mosswart}
            ItemCountLE 0 {Sclavus}
            ItemCountLE 0 {Simulacrum}
            ItemCountLE 0 {Siraluun}
            ItemCountLE 0 {Undead}
            ItemCountLE 0 {Ursuin}
            ItemCountLE 0 {Virindi}
            ItemCountLE 0 {Auroch}
            ItemCountLE 0 {Burun}
            ItemCountLE 0 {Chicken}
            ItemCountLE 0 {Chittick}
            ItemCountLE 0 {Doll}
            ItemCountLE 0 {Elemental}
            ItemCountLE 0 {Fiun}
            ItemCountLE 0 {Golem}
            ItemCountLE 0 {Grievver}
            ItemCountLE 0 {Isparian}
            ItemCountLE 0 {Margul}
            ItemCountLE 0 {Mattekar}
            ItemCountLE 0 {Niffis}
            ItemCountLE 0 {Penguin}
            ItemCountLE 0 {Rabbit}
            ItemCountLE 0 {Sleech}
            ItemCountLE 0 {Snowman}
            ItemCountLE 0 {Thrungus}
        DO: SetState {CramPack}
```

```js
/ub globalframelimit 39 //active framerate
/ub bgframelimit 13  //inactive framerate

/ub resolution 1280 512
/vwt load 4window
/ub resolution 1280 1024
/vwt load 2window

/ub textures <landscape[0-4]> <landscapeDetail[0-1]> <environment[0-4]> <environmentDetail[0-1]>
/ub textures 4 0 4 0 1 1 //min
/ub textures 4 0 2 0 10 10 //quality

/ub resolution 1920 1024
/ub resolution 1920 512
/ub resolution 960 512

IF: All
    Expr {$stone=wobjectfindininventorybyname[Aetheria Mana Stone]}
    Expr {$unids=listfilter[wobjectfindininventorybyname[Coalesced Aetheria],`wobjectgetintprop[$1,218103849]==27702`]}
    Expr {listcount[$unids]}
    Expr {listmap[$unids,`actiontryapplyitem[$stone,$1]`]}
    Never
DO: None
^You use the desiccant on the aetheria to create an aetheria powder
42636 - red
42635 - blue

IF: All
    Expr {getvar[powderBlue]==True}
    Expr {getcombatstate[]==Peace}
    Any
      All
        ItemCountGE 1 {Blue Aetheria Chunk}
        ItemCountGE 1 {Aetheria Desiccant}
      All
        Expr {listcount[listfilter[wobjectfindallinventorybynamerx[`Coalesced Aetheria`],`wobjectgetintprop[$1,218103849]==27704`]]==0}
        Expr {getinventorycountbytemplatetype[42635]!=0}
        Expr {getvar[combineWOHammer]==True}
        ItemCountGE 1 {Coalesced Aetheria}
        ItemCountGE 1 {Aetheria Desiccant}
        ItemCountGE 0 {Lugian Aetheria Hammer}
    Any
      SecsInStateGE 2
      ChatMatch {^The two artifacts link together effortlessly}
  DO: DoAll
      DoExpr {actiontryapplyitem[wobjectfindininventorybyname[Aetheria Desiccant],wobjectfindininventorybyname[Blue Aetheria Chunk]]}
      SetState {BluePowder}

```
