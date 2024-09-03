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

2) I forked the Xeto reposisotry (where you're currently looking) and setup vscode to allow me to do git commits and pushes after I tested my code against my development clone.  I just copy everything I do in development here once it complies and checks out againt my testing enviroment.

Common Test commands I run in axon via terminal in vscode:
    load(`https://project-haystack.org/example/download/charlie.zinc`)
    using("*")
    xetoReload() (reloads all specs into memory)
    read(ahu).fitsExplain(G36SingleZoneAhu)

Build commands
    ./xeto build ashrae.g36
