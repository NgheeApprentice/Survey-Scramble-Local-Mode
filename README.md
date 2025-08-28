## So, you're hungry for some more Survey Scramble content, I see?
This mod aims to provide all news ways to interact with list and category content in The Jackbox Survey Scramble; through accessing more categories than typically viable, creating your own locally-based trivia lists, or even looking back at old historic list content. So what does this mod have to offer?

# Local Mode
An all new separate mode accessible on the main menu screen! Simply choose that mode for play to access a completely separate content pool featuring new categories with locally-based list content!
### Featuring three new categories:
- "NgheeApprentice's Jackbox "Tierlist""
- "Bible Books by Word Count (NIV)" / "Books of the Bible" (Speed alternative)
- "The Alphabet" (list for testing purposes)
### But remember, Local Mode is a proof-of-concept! We need *you* to create some content!
Look, making good content for this mode is a lot of work, especially if you make it a manual endeavour. That's why there isn't a lot of content here on release. But that's where I pass the torch onto you! I should hopefully have made it relatively accessible to mod in custom content of your own, and I hope to create the space for you guys in the community to create custom lists for this mode and keeps its legacy alive. Again, it's a lot of work to make a list for this game, but I hope that you can find some inspiration. "So how do I make my own content for this mode?" Stick around to find out (or figure it out on your own, I'm not your dad).

## "So what else is new?"
Why, some new settings of course to customise your gameplay with list content in the *vanilla* game! (not Local Mode)

# Settings
All of these new settings can be found under the new 'Modifications' tab in the settings menu. All of the settings below are 'toggles.'
|Setting|Description|
|-|-|
|Lenient Category Pool|Allows categories not supported by the servers, but supported by local files to be considered for play. Works best with United States English locale.|
|Ignore Up-To-Date Content Priority|When enabled, the most-voted category for play will always be selected unless completely unplayable, regardless of the state of list data in each category.|
|Historic List Content|When playing on United States English, uses oldest known surviving list content from the demo. Limits total categories to 136.|

As you can likely deduce, these settings have by far the most pronounced effect on the United States English locale (en-US). The effect the first two settings have on your game likely won't be very noticable outside of the United States English locale, but still provide some benefits, and the Historic List Content setting is disabled on every other locale. However, on the United States English locale, the Lenient Category Pool setting will massively increase the amount of unique categories you can find in the voting segment for regular play.

## Installing this mod
As with installing any mod, *it is strongly recommended that you backup any files you plan to replace and/or modify.*
All files in this mod start off in the game's main directory, `.\The Jackbox Survey Scramble\games\BigSurvey`. From there, if a file in this mod lives in a folder, particularly with the content files, follow the specified directories in this repository, and place them in their respective position in your game's main directory.
### Files to *replace*:
- `BigSurvey.swf`
- `Localization.json`
- `menu.jet`
- `settings.json`
- `.\content\manifest.jet`
- `.\swf\bigsurvey_menu.jet`

*It is strongly recommended that you backup any files you plan to replace and/or modify.*

### Files to *add*:
- `.\content\en\BigSurveyListDemo.jet`
- `.\content\{locale}\BigSurveyListLocal.jet`
- `.\content\{locale}\BigSurveyQuestionLocal.jet`

The {locale} tag refer to the content locales you wish to play in. All the required files for the English locale (en) are provided. If you wish to play Local Mode in any additional locales, you will need to create versions of these files for these additional locales on your own. Feel free to copy the English files as a base and make your own changes from there if you wish.

## And that's it! For general mod information, at least.
Have fun with your new Survey Scramble mod! May it enhance your Survey Scramble gameplay experience. **If you're here to *just play* the mod. Then you can finish reading here. If you want to learn how to create your own locally-based lists, but aren't condifent that you can figure it out on your own, feel free to keep reading. Here comes a quick crash-course on writing custom local content for The Jackbox Survey Scramble: Local Mode!**




# Creating your own categories for Local Mode:
First and foremost, you should know *where* exactly you should be creating content if you want to see it appear in Local Mode.
- ### Write *category metadata* in `BigSurveyQuestionLocal.jet`
- ### Write *list content* for specific categories in `BigSurveyListLocal.jet`

Nice! Now that we know where to edit, let's look at *what* to edit. Let's start off with the category-specific stuff:
## Creating content for `BigSurveyQuestionLocal.jet`
Now, the best way to learn how to create content is to study what's already there, but I'll help you out with some basic tags. Each category is stored in an object `{}`. It might look something like this:
```
{
   "id": "id-001",
   "x": false,
   "starterContent": true,
   "countrySpecific": false,
   "pickerTitle": "Short, but informative question title",
   "voteTitle": "Succinct esscence of question",
   "question": "Here's the full-length question that provides context for gameplay!",
   "preventedModes": [
      "Bounce"
   ],
   "reframeQuestions": [
      "Example prompt 1 for ScrollSearch mode!",
      "Example prompt 2 for ScrollSearch mode!"
   ]
}
```
So what does all this do? Well, take a look at this table to find out:
|Tag|Type|Description|Acceptable values|Default value|
|-|-|-|-|-|
|`"id"`|String|Used for identification. Allows categories to be rolled randomly, and can be called via dev commands to force content. **This is important to fill out, and is strongly recommended that it is not identical to any other ID in the same file.**|Any viable json-friendly text in quotations `""` (e.g. `"Hello!"`)|None `""`|
|`"x"`|Boolean|Filters this content from play if 'Family Friendly' is enabled.|`true` or `false`|`false`|
|`"countrySpecific"`|Boolean|Filters this content from play if 'US-Centric Content Filter' is enabled.|`true` or `false`|`false`|
|`"starterContent"`|Boolean|Allows this content to be played within a device's first three games of The Jackbox Survey Scramble.|`true` or `false`|`false`|
|`"pickerTitle"`|String|Text that appears for a category during the voting segment. Try to keep this short.|Any viable json-friendly text in quotations `""`|None `""`|
|`"voteTitle"`|String|Text that appears when a category successfully wins a vote, and remains as a header for the game mode in play. Try to keep this extra-short.|Any viable json-friendly text in quotations `""`|None `""`|
|`"question"`|String|Text that provides the full question of a category. This appears shortly after a category wins a vote, and on your controller as well.|Any viable json-friendly text in quotations `""`|None `""`|
|`"preventedModes"`|Array|Any mode(s) listed here will not be viable for play with this specific category.|Any number of *viable* strings `""` followed by commas, braced inside sqaure brackets `[]` (e.g. `["HighLow","Speed"]`). Viable answers include: `"HighLow"` (Hilo), `"Speed"` (Speed), `"TicTacToe"` (Sqaures), `"Bounce"` (Bounce), `"BetterOrWorse"` (Dares), `"HorseRace"` (Dash), `"Pegs"` (Pegs), `"ScrollSearch"` (Scroll)|None `[]` (not required)|
|`"reframeQuestions"`|Array|Any string of text listed here will be used as prompts for the beta 'Scroll' game mode.|Any number of strings `""` followed by commas, braced inside sqaure brackets `[]` (e.g. `["Entry 1","Entry 2"]`)|None `[]` (not required)|

Once you've decided on your tuneables, fill out these tags where needed, and boom! You should have some category framework! Keep in mind, code is *very* precise. If something doesn't load after you made some content, take a moment to check it. There may be some missing or misplaced punctuation somewhere. This goes for any content modding, including what's up next:

## Creating content for `BigSurveyListLocal.jet`
Now, this part of the process has less to know, sure. But this is likely where you'll be spending most of your time if you don't have any automation. Much like the categories, each list is stored in a object. This time, it'll look a bit more like this:
```
{
    "id":"id-001",
    "l":[
      {"a":["acceptablevalue1"],"d":"displayvalue1"},
      {"a":["acceptablevalue2"],"d":"displayvalue2"},
      {"a":["acceptablevalue3","anotheracceptablevalue3"],"d":"displayvalue3","x": true,"f":100}
    ]
}
```
Now, realistically speaking, your lists will be a *lot* longer than this, and it quite literally has to be. But hey, this is a tutorial. Let's take a look at what makes up a list:
|Tag|Type|Description|Acceptable values|Default value|
|-|-|-|-|-|
|`"id"`|String|Used for identification. **Make sure this value is the same as the id of the category you wish to attach this list data to.**|Any viable json-friendly text in quotations `""` (e.g. `"Hello!"`)|None `""`|
|`"l"`|Array|Contains all other required list data for gameplay. These store all answers in the order they'll be ranked in the game.|Any number of *viable* objects `{}` followed by commas, braced inside sqaure brackets `[]`|None `[]`|

Now, let's take a better look at this list data array, the `"l"` tag. What tags do a viable list entry require? Let's take a look.

## Creating a list entry for your list
A list entry uses the following tags to be used in-game:
|Tag|Type|Description|Acceptable values|Default value|
|-|-|-|-|-|
|`"a"`|Array|Acceptable values. Anything a player can submit to reveal this specific answer on the list. **Keep in mind, all submitted answers have spaces, capitals and punctuation removed. Make sure to account for this in any values you put here.**|Any number of strings `""` followed by commas, braced inside sqaure brackets `[]` (e.g. `["Entry 1","Entry 2"]`)|None `[]`|
|`"d"`|String|Display value. What you'll see on the list when this answer is revealed.|Any viable json-friendly text in quotations `""`|None `""`|
|`"x"`|Boolean|Filters this answer from play if 'Family Friendly' is enabled.|`true` or `false`|`false`|
|`"f"`|Integer|Used internally for vanilla lists on the server end by Jackbox; you'll see these in the vanilla lists. This has no effect on the game, and can be skipped.|Any viable non-decimal integer (e.g. `123`)|None `null`|

Once you create an answer object, place it somewhere in the `"l"` tag of your list content array that properly reflects its ranking on the overall list.

### Important things to keep in mind.
- **To link a category in `BigSurveyQuestionLocal.jet` to a list in `BigSurveyListLocal.jet`, make sure they both share the same value in the `"id"` tag.**
- **Answers in gameplay will be ranked based on their order of appearance in the `"l"` tag.** The `"f"` tag will do nothing to influence the rankings.
- Make sure your lists have a lot of answers! **On many game modes, a minimum of 15 viable answers in the `"l"` tag are required to play the category successfully**, and this may be higher for some others. Keep a **minumum of 15 answers**, but if you want your gameplay to run in the closest fashion to vanilla gameplay on each mode, try to aim for these milestones.

### Minimum no. of answers required to emulate vanilla gameplay:
- Hilo, Speed, Dares: At least 15 (non-negotiable)
- Squares: At least 71
- Bounce: At least 50
- Dash, Scroll: At least 100
- Pegs: Not sure, probably 1 tbh

Keep in mind, on the demo's release, many lists had less than eighty answers on certain locales. If a certain prompt doesn't make sense to have a whole bunch of answers, feel free to cut yourself some slack. Just make sure that you have at least 15 answers.

## Okay, NOW that's everything!
I hope you have fun with this mod, and I hope you can create some awesome new content for Local Mode! Thank you so much for your dedication; I look forward to seeing what you do with this mod. Have fun!
