---
title: "Diplomacy screen"
date: 2025-11-30
image: /assets/2025-11-30_diplomacy.png
---

![Research screen](/Ancient-Star/assets/2025-11-30_diplomacy.png)

The diplomacy screen and audience subscreen are finished. There is a little mess left over to figure out with bar charts, I want them to be square sized (equally wide and high) but the framework doesn’t have a ready made solution for it. The hack that I put in place works at the first glance but doesn’t get the correct size when the screen is resized. I have an idea for another solution but I’ll postpone it for the polishing phase.

![Research screen](/Ancient-Star/assets/2025-11-30_audience.png)

Speaking of it, there is not much left to do before hitting that phase. The list of big missing is rather small now: qubit bonuses screen, breaking news screen and settings screen. And I’ve already started working on the news screen. It has a very simple layout but under the hood there was a tricky complication. When the game is turned off, the state of the current screen is saved and restored when the game is turned back on, giving the impression of continuing right where you left off. The complication arises when the screen state requires a specific game to be running and is tied to an entity in it. This problem first arose in the audience screen where the screen needs to know which player you are contacting. It turned out I don’t have a consistent way of referencing an individual player besides the object's memory address. I could have added such an identifier but then the news screen needs a way of identifying a news item that was last shown. So the solution was a bit more involved but it addressed all game objects, the screen state for those is basically a save game with some extra information.

