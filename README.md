VR Zahlensuche HTL — Localization System
About the project
This project is based on an existing VR game available at https://github.com/HTL-Wolfsberg-Betriebsinformatik/VRZahlensucheHTL, developed by HTL Wolfsberg as a small interactive experience for prospective students ("Schnupperschüler").
The original game
The player enters a virtual reality environment where they are presented with a brief introduction to the application. There is a field showing "Secret Number: ???" — this number is only unlocked once the player has completed all the tasks.
The tasks include:

Object box: the player must place inside a designated area only the objects related to HTL. Above the box, a live counter shows "3/5 elements correct". Some objects are intentionally out of context (such as a Django framed picture) to confuse the player.
HTL branches menu: the player must select the correct branches of the school, again with a counter "2/4 correct". Some wrong options are serious and others are jokes.
Hidden button: the player must find and press a button hidden somewhere in the scene.

When all tasks are completed, a small victory sound plays and the secret number is revealed.
My contribution
Building on this base project, I implemented a localization system that allows switching between 3 languages in real time: German, English, and Portuguese.
What I implemented

A language selection panel inside the VR world, with 3 buttons clickable through the Meta Quest controllers.
A custom translation system in C# that manages all the game's text through a central translation dictionary.
Automatic update of all texts when the player switches language — no need to restart the scene.
Persistence of the user's choice between sessions (the selected language is saved and restored the next time the game is launched).

Technical architecture
The system consists of 3 scripts:

LocalizationSystem.cs — contains the translation dictionary and fires an event whenever the language changes.
LanguageButton.cs — component attached to each language button that calls the system when clicked.
LocalizedText.cs — component attached to each UI text that listens to the event and automatically updates its content.

It was also necessary to replace the default Graphic Raycaster with the Tracked Device Graphic Raycaster, in order to allow the VR controllers to interact with the buttons on the panel.
