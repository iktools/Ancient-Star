---
title: "Reconstruction queue"
date: 2025-05-11
---

# Reconstruction queue
Turns out starting construction queue rewrite by making troopships repeatable was a good call. It introduced just enough problems of the right kind to warrant the rewrite. And again automated tests helped greatly at keeping the effort on track.

# History
This is the second time I rewrote this part of the game. In the beginning, when the game was blue stars on a white background, there was only one type of combat ship. It was an implicit repeatable project at the end of a queue. Any spare industry point would go into building it. Pure simplicity. And there were only 3 buttons for managing the queue: add colony ship, add troopship, and cancel the last item. Colony and troop ships would stack like today but that didn’t cause any complexity.

Then the “warship” got split into three distinct ship types and the whole thing got to be nuked and redone. There could be no implicit industry dump, the player has to spell out which combat ships will rotate. That’s an extra row of buttons on what was supposed to be a small and brief panel. And the queue rotation, that thing ended up being a nightmare! That’s why I have a bunch of automated tests for it. It’s such a pain to manually test every case again and again while going through multiple theories on what the implementation should be. The computer can do that for me in a fraction of time and most importantly, without me getting out of “the zone”.

# MVC
That’s why, ladies and gentlemen, I recommend model-view-controller architecture. This is a bit of a tangent inside of a tangent but here me out. I can’t recommend MVC enough as it saved my sanity more than any other practice. The idea of the architecture is to separate data and business/game logic (model) from presentation logic (view) and to have a middleman between them (controller).

Holding a model in view is a bad idea that becomes evident as soon as code complexity grows beyond a tutorial level. As soon as you have more than one scene or screen or window or page or whatever is a view unit in your case, you’ll have a question of how to share data between them. You’ll have to do all the logic for pushing data from one view to another, for each direction separately and to repeat that for every pair of views that communicate. It’s much less error prone to have the data somewhere “outside” that all views can see equally.

Controller it natural extension of that architecture. Not all views are interested in all of the data, they probably need some conveniences for data manipulation that data storage itself doesn’t provide and should not be bothered to do so, and sometimes you need to impose some restrictions to certain views. For example, when you tap on a colonized star in the Ancient Star you’ll see full colony information if it is yours and limited information otherwise. The view concerns itself with which buttons and text boxes to show, controller about which data is available depending on colony ownership and your fleet presence and model is just holding the collection of stars, each with a reference to a colony if there is one.

# Unit tests
Ability to swap views on top of controllers is very handy for making the game multiplatform. Even before LibGDX rewrite I need to run the game with multiple UIs including no UI. Computer players are playing the game through the same controllers the Android GUI is using for the human player. And similarly automated tests do the same but with a license to create the entire game and advance turns on their own. JUnit, the test framework is designed for unit tests and what I’m doing is halfway to an integration test. Sure it’s an overreach but I don’t know about a better approach, if you do please let me know! In any case, this works, fast, reliably, and ages well.

# Game changes
Tangent over! :D

With the v3.30 update the construction logic should have all of its quirks fixed. The colony should not lose all (or even more than present) of its population and troops. After ending a turn, the rotated projects will split and merge correctly.

As I’ve said in the intro, troopships are repeatable projects, just like combat ships. The distinction is that they’ll wait for the colony to train enough troops and pass their industry point investment to the next project in the meantime. Normally, troopships require 0.2 troops to get finished but with this update the colony has to be left with at least 1 troop. Meaning no troopships will be built if there is less than 1.2 troops on the colony. Same limit is imposed on colony ships. They won’t be built if they would drop the colony population below 1. That should prevent previous division by zero bug.
