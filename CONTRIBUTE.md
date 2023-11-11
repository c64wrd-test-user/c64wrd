# Contribution Guide

The most important thing to keep in mind is that this is **NOT** a credits database, we already [have one](https://csdb.dk), and there is no point duplicating the information available there. It would also make it unnecessarily hard to keep the two synced which would make this database quite sparse and incomplete.

The presentation and information storage is quite basic as it has to be served on githut pages which does not support any custom server side code. So we just use Jekyll, and try to shoehorn everything into existing mechanisms instead.

## Categories

Every effect (demo part) is separated into its own post. The posts are grouped into categories using the directory structure. Jekyll will then turn each directory level below the _posts directory into a category when processing the .md files (the posts) in that directory. It is hardcoded that the last level should be the name of the demo, and each previous level should be the demo group's name. In case it is a coproduction then there are at least 3 levels, otherwise there are exactly 2.

Examples:
```
/graffity/justinblue/_posts/2023-02-12-cheesboarding.md
/censor-design/oxyron/comaland/_posts/2015-06-20-plotballs.md
```
For example "graffity" is the demo group, "justinblue" is the demo, these will be turned into categories automatically. "2023-02-12-" is mandatory, as Jekyll expects this filename format for posts, use the release date from CSDb. "cheesboarding" is the name of the part, which must be how the part is called in the demo part itself or the demo credits or the demo note. If there is no such name given then you can use the filename (in case of old demos) or come up with a name or use "part1", "part2" etc. For example "plotballs" comes from the note on disk side 1 of Comaland.

It is very important to keep these group/demo/part names "slugified", which means that do not have spaces or special characters in them ("for example "comalight3"). If necessary use the short name of the group (for example "trsi") if exists, and use lowercase all the time, as these will be filenames and urls. If the name have a space and there is no short name (for example "Genesis Project") then use dash like "genesis-project". In demo names do not include the percentage (for example "99%") or similar.

In case the demo is a coproduction and only one group contributed code records (notable effects) then treat it as a non-coproduction (for example the other group are music composers). If more than one group contributed code records then decide yourself which top level directory you put the demo under (for example "/oxyron/censor-design/comaland/2015-06-20-plotballs.md"). Please **DO NOT** create a new pseudo-group for example "censor-design+oxyron", as that would ruin filtering.

Note that you cannot overwrite categories later in the front-matter (beginning section of the .md files), as a line like "categories: a b c" puts a, b and c at the end of the category list created from directory names and that would mess up group/demo rendering and linking.

You have to put the demo group's name and the demo's name into the appropriate files in "/demo" and "/group" otherwise Jekyll does not generate the filtered html file and the links to the group/demo will not work. (See "group\graffity.md" and "demo\justinblue.md" what information you need in the file - is is just the "category:" line.)

## Tags

You have to put the effects of the part into the front-matter (for example "tags: chessboard chessboard-zoomer") as tags. All tag names must be "slugified", lowercase and single word (for example "bitmapstretch"). Then create more specific effect tags by joining the broader effect category (here "chessboard") and the more specific word (here "zoomer") into a tagname (here "chessboard-zoomer"), and include **BOTH** the broad and narrow tagname in the front-matter. The reason for this is that we want to find that demo part when browsing the database, and it is better to include it more than once.

Create more specific effect tags **ONLY** when there are at least 20 entries for an already existing tag. If you do this then it is your responsibility to update **ALL** the already existing entries to have your new shiny effect tag if it applies to them. In this case you have to create the appropriate .md file in "/effect" as well, otherwise Jekyll does not generate the filtered html file and the links to the effect will not work.

How to name effects and what is and is not in the effect category is highly subjective, discuss it in the CSDb forum before starting a flamewar.

Do not create a "filler" or "powerpoint" or similar tag even if it would sound funny, if a demo part is just an animation either leave it out completely or give it no tag at all. Also skip rasters+logo+scroll or similar parts in old demos, the goal is not to collect all the parts, but instead collect all the effects and records.

## Posts

Each demo part should have its own .md file, which starts with the so called front-matter:
```
---
date: 2015-06-20 20
title:  "Plotballs"
csdb: 139278
coders:
  - name: "Axis"
    csdb: 331
  - name: "Bitbreaker"
    csdb: 1678
record: 384
size: 72x63
fps: 50
tags: plotter plotter-3d plotter-3d-hires
---
```
The "date:" has to be duplicated here unfortunately (it comes from the filename automatically), because we have to overwrite the hours (" 20" here) to have a monotonically decreasing number starting from the intro which should have "23". If the demo has more than 24 parts then you can use minutes here as well (for example "23:59"). The reason for this is that we want to have demos sorted by year in a way that the most recents are on the top, but also want to have the demo parts together in a way that the intro is at the top.

The "title:" is the non-"slugified" demo part name, you can use any text here and spaces or other characters as well.

The "csdb:" number is the release id on CSDb where you can download the demo itself (the same in all parts).

The "coders:" part is a YAML array, where every coder who worked on that part gets two lines. The "space_space-space_name:" is the string which will be displayed in the web pages. The "space_space_space_space_csdb:" number is the CSDb scener id. Note that the number of spaces is very important in YAML!

The "record:" part is optional information for single numeric things like the number of sprites in a multiplexer or the number of dots in this example.

The "size:" part is optional information if it is important in the effect, and if you take the time and effort to actually measure it. Note that it has to be in hires pixels, so with multicolor effects the first number should be even.

The "fps:" part is optional information if it is important in the effect, for example for music parts it is not important. Use values like 50/25/16/12/10 for 1,2,3,4 or 5 frame long updates.

The "tags:" part is where you put the effect tags which were described before.

Note that only the coders/record/size/fps is listed in filtered lists, there is no point adding more information here. This is deliberate, to make it easier to fill out values, as my experience is that it takes ages to update the database.

After the front-matter, start with a screenshot and the part's short description:
```
![Plotballs](/c64wrd/censor-design/oxyron/comaland/plotballs.png)

Hires XY with zoom plotter ball drawn into sprites roll down over the background.

<!--more-->
```
The image has to be uploaded to the demo's directory, and you can reference it by putting the "/c64wrd" string in front of the link. Give some meaningful name for "alt" tag.

The short description has to be short enough to fit into filtered lists, where the first image in the post is used at 30% maximum width and that determines the row's height. The short description ends at the "<!--more-->" string.

Then you can have more screenshots and a longer description. Note that if you are the author of the part and you cannot really describe why it is better or different than the other similar ones, then it is probably just a "filler" part.

For screenshots I used VICE PAL emulation screenshots (as PAL emulation does not work with media snapshots in VICE), then cropped the images not to include the VICE GUI and some empty border. Then when I realized that the size of these images is arbitrary (based on you VICE window size), I had to make VICE media snapshots as well to determine the effect size. But this is clearly a waste of time so it is entirely up to you how much time do you want to spend on that (for example for "plotballs.png" I just used the C64 Debugger screenshot feature).
