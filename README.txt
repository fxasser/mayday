MAYDAY
A Twine (Harlowe 3) horror game starring Astrea
=================================================

Your survey ship crashes on an unnamed world. You wake up in a cave den with
your leg set in a bone splint, and something with fangs is watching you. She
learned to talk from your flight recorder, so she speaks in radio phrases and
can use your voice. She thinks your name is "Mayday".

48 passages, about 4,600 words total (one playthrough is ~2,000 words,
5 to 10 minutes). Seven real decisions, five endings. Every ending returns
to the title screen, which keeps track of the endings you've found and
reveals her name once you reach the good one.


WHAT'S IN THIS FOLDER
---------------------
  Mayday.twee                  The whole game. This is what you import.
  Mayday-twine-archive.html    The same game in Twine's archive format.
                               Use it only if your Twine won't take .twee.
  images/                      All the art, already named the way the game
                               expects.
  README.txt                   This file.


1. IMPORT INTO TWINE
--------------------
  Twine 2  >  Library  >  Import  >  choose Mayday.twee

  The story format should say Harlowe 3.x. If Twine ever complains about the
  format, open the story, go to Story > Details, and pick the newest Harlowe 3.

  The story map is laid out left to right in play order, color-coded by tag:
    blue    choice scenes            green   calm/kind reactions
    orange  threatening reactions    purple  fearful (prey) reactions
    yellow  mixed reactions          red     ending paths


2. TEST IT
----------
  Twine's Play/Test preview works for all the text and choices, but it
  CAN'T show pictures from the images folder. That's normal.

  Build > Test also shows a debug panel with the hidden variables live.

  To see it with art: Build > Publish to File, and save the .html into this
  folder, next to the images folder:

      Mayday/
        Mayday.html
        images/
          ...

  Open Mayday.html in a browser. Zip that whole folder to submit it.

  The endings tracker on the title screen is remembered by the browser,
  even after closing it. To reset it for a fresh test, open the game in a
  private/incognito window.

  (The fonts load from Google Fonts. With no internet the game still works,
  it just falls back to Georgia.)


3. THE ART
----------
  Backgrounds (2560 x 1440):
    bg-den.png      the cave, behind every scene inside the den
    bg-ridge.png    the ridge at dawn, behind the good ending's last scene

  Portraits (1500 x 2000, transparent):
    astrea-neutral.png      11 scenes
    astrea-curious.png       5
    astrea-hungry.png        6   (also the close-up in the Prey ending)
    astrea-snarl.png         5   (also the lunge in the Threat ending)
    astrea-suspicious.png    4
    astrea-startled.png      3
    astrea-soft.png          4   (also the sleeping face in the Prey ending)
    astrea-soft-dawn.png     1   the ridge scene only

  astrea-soft-dawn.png is the soft face relit for outdoor light. It's only
  used on the ridge, so the den scenes keep the cave lighting.

  To change which face a scene uses, edit the filename in that passage's
  first line, e.g.
    <img class="portrait" src="images/astrea-curious.png" alt="...">


4. HOW IT WORKS (hidden from the player)
----------------------------------------
  Three hidden numbers, all reset to 0 when a new game starts (in "Crash"):

    $threat   how dangerous you seem. Demanding, grabbing, the flare gun.
    $appeal   how much you seem like prey. Panicking, begging, fleeing.
    $bond     trust from key moments: explaining what "mayday" means,
              noticing her burn, treating it, telling the truth, and your
              final answer.

  Calm or honest choices lower BOTH threat and appeal by 1. Bold choices
  add 2 threat, fearful ones add 2 appeal. There's no visible meter: her
  expression and the italic line after each choice are the feedback.

  At the end, the invisible "Fate" passage picks the ending:

    threat 3+ AND appeal 3+          Vigil   (she can't figure you out)
    threat 5+                        Threat
    appeal 5+                        Prey
    bond 4+ and both meters 0-1      Crew    (the good ending)
    anything else                    Truce

  Some choices skip straight to a death: running for the tunnel, aiming
  the flare gun at her, and threatening her at the end. Saying "I'm
  nothing" at the end adds 3 appeal: calm players get let go, jumpy
  players get eaten.

  To make the game easier or harder, change the numbers in "Fate".

  Undo/redo arrows are hidden so choices stick. To bring them back, delete
  the line  tw-sidebar { display: none; }  from the Story Stylesheet.


5. WALKTHROUGHS (spoilers; every route below was tested)
---------------------------------------------------------
  Crew (good ending, the only one where you learn her name):
    "...Copy." > Tell her what "mayday" actually means > Ask about her hand
    > Don't flinch > Pick up the burn gel > "They're coming for me."
    > "Mayday."

  Truce:
    "Who are you?" > Tell her your real name > Ask her for the beacon
    > Offer her a ration bar > Leave her be > "They're coming for me."
    > "Crew."
    (Or play the Crew route but answer "I'm nothing" at the end.)

  Vigil:
    Scramble away > "Give that back." > Ease toward the flare gun
    > "Please don't eat me." > Leave her be > "They're coming for me."
    > "Crew."

  Threat:
    "Who are you?" > "Give that back." > Ease toward the flare gun
    > Don't flinch > Leave her be > Lunge for the beacon > "Crew."
    (Or aim the flare gun at her whenever it's offered.)

  Prey:
    Scramble away > Tell her your real name > Ask her for the beacon
    > "Please don't eat me." > Edge toward the tunnel
    > "Please don't break it." > "Crew."
    (Or shove her away and run when she says she's hungry.)

  Bonus: grab the flare gun, then set it down when you treat her hand.
  You can still get the Crew ending.
