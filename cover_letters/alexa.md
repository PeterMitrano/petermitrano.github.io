## Amazon Alexa Team

I have made several Alexa skills, two of which are published in the store (US & UK only)

My Skills:

 - [CollabLab Status](https://github.com/PeterMitrano/collablab_status) *Published*

    This was my first published skill. I made it to check whether or not the Makerspace Club I run at my school is open, and check who currently signed in. It's in python, as are all of my skills.

 - [My Finder](https://github.com/PeterMitrano/my_finder) *Published?*

    My Finder is current under certification as of 9/18/16. The idea is to tell your alexa device where you put stuff, and it will remember forever. For instance, your unpacking into a new apartment and you know you'll forget where you put box of school supplies. Tell alexa! The main challenge for this skill was that people have many names for their things. If you say "I put my bike helmet on the black rack by my bed", you might then ask "where is my helmet?". You might even ask "where did I put my bike thingy?". To handle this, I use the wildly popular Wordnet corpus in combination with FuzzyWuzzy. This allows me to both do fuzzy string matching to fix translation errors, and basic NLP. This way we can know that "towel" and "blanket" are similiar enough. To make this approximation clear to the user, I modified the speech output. On a perfect match, it will say "your <item> has location <location>". However, if it matches "blue bookbag" to "blue backpack", it will say "I don't know where the blue bookbag is, but I know blue backpack has location <location>". This way the user knows it wasn't an exact match, and in case we got it wrong the user won't be as frustrated".

 - [My Desk](https://github.com/PeterMitrano/my_desk)
 - [My Cookbook](https://github.com/PeterMitrano/my_cookbook)


What I'd like to do at Amazon:


My Workflow for Alexa Projects:

 - Vim, with ycm for static analysis and completion, and CtrlP for fuzzy file finding
 - nose for unit testing, coverage for code coverage checking, all run on Travis
 - Git (obviously)
 - Python 2.7.11 (matches version on Lambda)
 - AWS CLI & sketchy Makefiles for faster uploading
