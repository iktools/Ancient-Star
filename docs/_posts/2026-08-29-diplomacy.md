---
title: "Diplomacy"
date: 2026-08-29
image: /assets/2026-08-29-multiselect.png
---

![Galaxy map with multiselect panel](/Ancient-Star/assets/2026-08-29-multiselect.png)

The polish phase of the rewrite has caught up with what was done in the coarse phase. Galaxy map screen is done, all side panels are done, research, diplomacy and audience screens are done. There were few interesting challenges but their density per file was rather low. Bulk of the work was about adapting desktop components to mobile layouts, ensuring proper spacings and alignments, and switching to SDF images.

![Galaxy map with colony info panel](/Ancient-Star/assets/2026-08-29-colony-info.png)

The most visible hurdle was figuring out how to make text wrapping work. When a label (text rendering component) is set to wrap the text then its preferred component width becomes undefined which gets interpreted as zero. In other UI frameworks labels try to occupy as much horizontal space as their longest line needs and then reduce it by wrapping. In LibGDX you have to procure label width on your own. Took me a few experiments to figure out how to get that out of a table layout. This problem and solution also extended to dialogs describing game mechanics, output numbers, and tutorial messages which on their own were a pain to make look right. 

![Diplomacy screen](/Ancient-Star/assets/2026-08-29-diplomacy.png)

The diplomacy screen was deceptively tricky. It doesn’t look like much is going on there but I was hitting layout limitations all the time with it. I had to scrape the most niche table layout features to make the leaderboard fit the screen and have nicely distributed columns. Bar charts, like every charting solution, are a mix of primitive components that stretch the UI framework. In this case solid color images in a table aligned to the bottom. I had to make some compromises with spacing between bars but this looks ok too.

And finally, I’ve tested the waters with itch.io. The web build is published there despite the rewrite not being complete. This is more for me to see what the procedure is and which bureaucracy I have to do. The experience with the Play Store taught me to arm myself with patience. Fortunately itch.io is very straightforward. The game is marked as in development on that site so hopefully people will not trip on pot holes uninformed.
