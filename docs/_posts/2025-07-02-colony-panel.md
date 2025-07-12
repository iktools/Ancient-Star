---
title: "Colony panel"
date: 2025-07-01
---

Digressions out of the smallest things continue. Well, this is mostly due to having a bunch of “firsts” that I have to figure out “how” before making it. To make a colony panel there first needs to be a general selection panel that hosts it and has a close button (and back to multiple selection, if there was any).

![Colony panel and population description](/Ancient-Star/assets/2025-07-12-colony-description.png)

The colony panel itself started off easy until I noticed a few one liners in the old code for showing description dialogs (population limit and growth breakdowns, same for factories and troops). I reckon it would be better to address them now when I know where they are needed than to do them in a second pass and risk missing some. Man they are intense, there are so many components in them! Each one takes what feels like a half a day to make.

I managed to avoid making a skin for a checkbox until now and that’s another “first” that will need to be addressed. I’ll need them for colony management. I’ll also need a so-called flex layout, one where items are laid one after another and wrapped in the next row when space is filled. At the first glance it seemed like there is no out of the box solution for it in the LibGDX but then I accidentally found that functionality in a HorizontalGroup layout. It was advertised as a simplified one row table but I noticed it has a “wrap” property that could make it more than one row. I’m glad I won’t have to roll my own layouting.
