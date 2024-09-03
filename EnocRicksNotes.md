# Overview

I am putting this together to help others build upon this work.  My goal is to try and make testing skyspark projects agains [ASHRAE's Guideline 36 equipment specifications](https://tpc.ashrae.org/?cmtKey=d536fedd-5057-4fc6-be3a-808233902f4c) ( [which can be purchased here](https://store.accuristech.com/ashrae/standards/guideline-36-2021-high-performance-sequences-of-operation-for-hvac-systems?product_id=2229690) ) easier for all.  

## URLs i've referenced in learning Xeto 

The youtube Channel where Brian Frank Gives some great overviews
https://www.youtube.com/@briansfrank

This is where I started digging to import my xeto files into my local instance of skyspark:
https://skyfoundry.com/forum/topic/8089

https://skyfoundry.com/forum/topic/8131

https://skyfoundry.com/forum/topic/8084

https://project-haystack.org/forum/topic/1115#c9


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
First off I used VSCode to create a sort-of "prod" and "test" enviroment.  I do all my production in a clone of the [haxall](https://github.com/haxall/haxall) repository.  Then I copy those changes (after they build and test to my satisfaction) to this repo and push them up.  

> [!TIP]
> **Then to test in skyspark I do the following:**
> 1) copy the compliled xetolib file from my dev folder:
>    `\haxall\lib\xeto\ashrae.g36\ashrae.g36-0.X.X.xetolib`
>  and paste it into skysparks xeto lib folder:
>     `\skyspark\lib\xeto\ashrae.g36\`
> 3) reboot skyspark
> 4) Open my test project
> 5) goto "settings" app
> 6) goto "using" tab
> 7) enable the ashrae.g36 library (the version should match what you copied in)
> 8) goto the "tools" app
> 9) execute `xetoReload()` in the shell
> 10) execute `specLibs()` in the shell to see that lib:ashrae.g36 shows up
> 11) then run a test using the `fitsExplain()` command: example: `read(ahu).fitsExplain(G36SingleZoneAhu)` it should return something (usually whats missing for required points)
       
