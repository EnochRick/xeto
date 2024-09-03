#Overview

I am putting this together to help others build upon this work.  My goal is to try and make testing skyspark projects agains [ASHRAE's Guideline 36 equipment specifications](https://tpc.ashrae.org/?cmtKey=d536fedd-5057-4fc6-be3a-808233902f4c) ( [which can be purchased here](https://store.accuristech.com/ashrae/standards/guideline-36-2021-high-performance-sequences-of-operation-for-hvac-systems?product_id=2229690) easier for all.  

## URLs i've referenced in learning Xeto 

The youtube Channel where Brian Frank Gives some great overviews
https://www.youtube.com/@briansfrank

This is where I started digging to import my xeto files into my local instance of skyspark:
https://skyfoundry.com/forum/topic/8089

I cloned Haxall for development purposes locally.  
https://haxall.io/
https://github.com/haxall/haxall/releases

## My development process:
1) I cloned a local copy of Haxall in vscode and then worked off that cloned repository for building my modifications to GL36
2) I loaded up GL36 points lists (section 4 of the [guildeline](https://store.accuristech.com/ashrae/standards/guideline-36-2021-high-performance-sequences-of-operation-for-hvac-systems?product_id=2229690) ) and started modifying the ahsrae.g36 xeto files accordingly. 
3) I forked the Xeto reposisotry (where you're currently looking) and setup vscode to allow me to do git commits and pushes after I tested my code against my development clone.  I just copy & paste everything I do in the development clone. The final tested code ends up here once it complies and checks out againt my testing enviroment.

**Common Test commands I run in axon via terminal in vscode:**
    
    load(`https://project-haystack.org/example/download/charlie.zinc`)
    using("*")
    read(ahu).fitsExplain(G36SingleZoneAhu)

    xetoReload() (reloads all specs into memory)

**Build commands**

    ./xeto build ashrae.g36

## My testing process:
