# Overview

I am putting this together to help others build upon this work.  My goal is to try and make testing skyspark projects against [ASHRAE's Guideline 36 equipment specifications](https://tpc.ashrae.org/?cmtKey=d536fedd-5057-4fc6-be3a-808233902f4c) ( [which can be purchased here](https://store.accuristech.com/ashrae/standards/guideline-36-2021-high-performance-sequences-of-operation-for-hvac-systems?product_id=2229690) ) easier for all.  

## URLs I've referenced in learning Xeto 

The YouTube channel where Brian Frank Gives some great overviews
https://www.youtube.com/@briansfrank

This is where I started digging for workflow ideas, general knowledge and information on how to import my xeto files into my local instance of skyspark.  I eventually commented on one with this page. 
https://skyfoundry.com/forum/topic/8089

https://skyfoundry.com/forum/topic/8131

https://skyfoundry.com/forum/topic/8084

https://project-haystack.org/forum/topic/1115#c9

I am also reading and using the [Git manual](https://git-scm.com/book/en/v2).


I cloned Haxall for development purposes locally.  
https://haxall.io/
https://github.com/haxall/haxall/releases

## My development process:
1) I cloned a local copy of Haxall in VSCode and then worked off that cloned repository for building my modifications to GL36
2) I loaded up GL36 points lists (section 4 of the [guildeline](https://store.accuristech.com/ashrae/standards/guideline-36-2021-high-performance-sequences-of-operation-for-hvac-systems?product_id=2229690) ) and started modifying the ahsrae.g36 xeto files accordingly. 
3) I forked the Xeto repository (where you're currently looking) and setup VSCode to allow me to do git commits and pushes after I tested my code against my development clone.  I just copy & paste everything I do in the development clone. The final tested code ends up here once it complies and checks out against my testing environment.

**Common Test commands I run in Axon CLI via terminal in vscode:**
    
    load(`https://project-haystack.org/example/download/charlie.zinc`)
    using("*")
    read(ahu).fitsExplain(G36SingleZoneAhu)

    xetoReload() (reloads all specs into memory)

    print(ashrae.g36::CoolingSignal) //Prints the spec for the CoolingSignal

    print(G36SingleZoneAhu, {doc}) //Prints the spec for the G36 Single Zone AHU

    read(discharge and fan and run and cmd and point).fitsExplain(DischargeFanRunCmd) 

**Build commands**

    ./xeto build ashrae.g36

    ./xeto build ph.points

## My testing process:
First off I used VSCode to create a sort-of "prod" and "test" enviroment.  I do all my production in a clone of the [haxall](https://github.com/haxall/haxall) repository.  Then I copy those changes (after they build and test to my satisfaction) to this repo and push them up.  

> [!TIP]
> **Then to test in skyspark I do the following:**
> 1) use build command `./xeto build ashrae.g36` from in the `haxall/bin` folder
> 2) copy the compiled xetolib file from my dev folder:
>    `\haxall\lib\xeto\ashrae.g36\ashrae.g36-0.X.X.xetolib`
>  and paste it into skyspark's xeto lib folder:
>     `\skyspark\lib\xeto\ashrae.g36\`
> 3) Make sure to copy the src folders too:
>    `\haxall\src\xeto\*.* -> \skyspark\src\xeto\*.*`
> 5) reboot skyspark
> 6) Open my test project
> 7) goto "settings" app
> 8) goto "using" tab
> 9) enable the ashrae.g36 library (the version should match what you copied in)
> 10) goto the "tools" app
> 11) execute `xetoReload()` in the shell
> 12) execute `specLibs()` in the shell to see that lib:ashrae.g36 shows up
> 13) Then run a test using the `fitsExplain()` command: example: `read(ahu).fitsExplain(G36SingleZoneAhu)` it should return something (usually what is missing for required points)
       
Here is a picture of my setup:

![VsCode Screenshot](/EnochRicksFolder/ExampleOfHaxallVSCode.png)
