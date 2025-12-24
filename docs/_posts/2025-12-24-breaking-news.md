---
title: "News screen"
date: 2025-12-24
image: /assets/2025-12-24_breaking_news.png
---

![Breaking news screen](/Ancient-Star/assets/2025-12-24_breaking_news.png)

The breaking news screen has been migrated to the new engine. It is a super simple screen actually so the bulk of the work was in recreating event images.

I also took time to play the game and hit most of those breaking news events. It made me take a good look at the normal gameplay too and realize that I’ve forgotten about star traits. There was a reason why I skipped them back then when I migrated the map rendering. Their graphics were in the absolutely most annoying format to translate. Without traits the map looks so bland, more bland then without filled stars. So I rolled my sleeves and did what had to be done to make traits show up. Filled stars will have to wait a bit more, they are genuinely complicating things up.

# Start screen polish

But not too long. I’ve started with the polish pass already by touching up the start screen. There is blur behind dialogs all now. It was needed for mode selection dialog but it was a good opportunity to unify creation logic and styling of all dialogs. The screen is tweaked to look good on both phone rotations (upright and horizontal) and on the desktop. Initially I was afraid this would take much more gymnastics because it looked like there was not enough room to show all buttons on the phone's horizontal layout. But by adjusting spacing and padding, and just a pinch of special case logic for the mobile made up a sufficient amount of space.

![Research screen](/Ancient-Star/assets/2025-12-24_dialog_blur.png)

Now I might finally do the settings screen or postpone it again and experiment with the music. Oh yes, there will be music. I made a selection of tracks and tested a naive implementation. But I need to dig through the docs deeper to figure out how to properly load and unload the music files. All basic examples deal with one file and it’s super simple to just play that one file, looping or otherwise. In the real game you’d want to rotate a couple of files and not have the system crash on you.

