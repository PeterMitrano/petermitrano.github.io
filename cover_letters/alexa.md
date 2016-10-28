# Amazon Alexa Team

I have made several Alexa skills, two of which are published in the store (US & UK only)

### My Skills:

 - [CollabLab Status](https://github.com/PeterMitrano/collablab_status) *Published*

    This was my first published skill. I made it to check whether or not the Makerspace Club I run at my school is open, and check who currently signed in. It's in python, as are all of my skills.

 - [My Finder](https://github.com/PeterMitrano/my_finder) *Published?*

    My Finder is current under certification as of 9/18/16. The idea is to tell your alexa device where you put stuff, and it will remember forever. For instance, your unpacking into a new apartment and you know you'll forget where you put box of school supplies. Tell alexa! The main challenge for this skill was that people have many names for their things. If you say "I put my bike helmet on the black rack by my bed", you might then ask "where is my helmet?". You might even ask "where did I put my bike thingy?". To handle this, I use the wildly popular Wordnet corpus in combination with FuzzyWuzzy. This allows me to both do fuzzy string matching to fix translation errors, and basic NLP. This way we can know that "towel" and "blanket" are similiar enough. To make this approximation clear to the user, I modified the speech output. On a perfect match, it will say "your <item> has location <location>". However, if it matches "blue bookbag" to "blue backpack", it will say "I don't know where the blue bookbag is, but I know blue backpack has location <location>". This way the user knows it wasn't an exact match, and in case we got it wrong the user won't be as frustrated".

 - [My Desk](https://github.com/PeterMitrano/my_desk)

    Controls the electric sit-stand desk I built.

 - [My Cookbook](https://github.com/PeterMitrano/my_cookbook)

    This is my most advanced and challening skill. The goal is to help you find and make recipies. It uses bigoven as it's recipe database, and I am developing the full workflow so users can find, and be walked step-by-step through making a recipe. Currently, the most challening piece is that most recipes are not design for voice only. They don't contain sufficient information about the amounts of ingredients used in each step to simply read of the instructions. Therefore, I need to consume the raw recipe and transform it into a more structured for before generating each step to read aloud. Additionally, the user will want to query alexa for more information about a step, such as repeating something, or asking which ingredients go where. This requires a fairly competant Q&A framework, and enough structure in recipes to find the information. Currently, I have worked out how to find recipes, get their ingredients & instructions. However, there isn't enough control over which recipe you get. For instance, the user cannot ask for "something quick for lunch", they have to ask for a specific recipe. And even then, there isn't a smooth or effective way for users to choose or explore among the many recipes there may be for one dish.


### My Workflow for Alexa Projects:

 - Vim, with ycm for static analysis and completion, and CtrlP for fuzzy file finding
 - nose for unit testing, coverage for code coverage checking, all run on Travis
 - Git (obviously)
 - Python 2.7.11 (matches version on Lambda)
 - AWS CLI & sketchy Makefiles for faster uploading

### What I'd like to do at Amazon:

As a developer, I've thought alot about the design decisions made by the Alexa team and how they impact what we can and cannot do. The one that has given me the most trouble though is as follows: If I am writing a skill, I am allowed to recieve any intent at any time. For instance, I may ask the user "do you want to create an event?" and they might say "Blue" to match some color intent I have. Of course, in this case, I must now handle the fact that the user has just spouted nonsene at me and gracefully proceed somehow. However, there are cases where ambiguity between intents could be better resolved if the skill was allow to present to the Alexa service which intents it "expected" the user to respond with. Similiar to how I imagine well defined slot types are better able to coerse speech into dates or places, we could coerse speech into intents that make more sense. For instance, one of my skills lets the user tell Alexa where they are putting some item, and ask Alexa later where they put it. For item and location, I have a "LocationIntent" with a custom slot type. When I ask "What's the item?" and they say "my backpack" I essentially get the raw text. What happens if the users says an item that is similiar to another intent I have? If they say the item is "backpack", but "backpack" is also a location for items, it might give the wrong kind of intent.

To put it simply, I would like to try to design an interface where skills include a list of "expected intents" in each "ask" response, and that is used as input to the voice model to make it more likely that intents are routed correctly. This is, of course, a trade-off between faithful text-to-speech, and giving the skill what it wants to hear. However, I think a balance can be made that will increase the overall success of voice interactions with custom skills.
