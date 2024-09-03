# (original) Overview

Xeto is a data-only type system.  The name is derived from the phrase "eXtensible
Explicitly Typed Objects".  Xeto defines a simple plain text format used to
declare types and to exchange typed data.  It is designed to build and validate
[Project Haystack](https://project-haystack.org/) data models.  But Xeto is general
purpose enough to use with any structured data including CSV, JSON, or SQL data.

This repository is used to manage the source code for the standard libraries.

# Update 9/3/2024
I wrote up my process and references in a notes file you can find here: [EnochRicksNotes](EnocRicksNotes.md).  This includes a detailed step by step instruction on how to take your complied xeto files an bring them into your skyspark enviroment for use and testing!. 

Cheers - EnochRick

# Update 8/30/24 (read's chronologically from newest to oldest) 
End of day update: Moved a bunch of new types into the misc-points.xeto.  Had to define some new things to fit the Guideline's intent for certain control sequences (like building pressure control). 

Known Issues:

- [] #1: Ambiguous types for : CoolingSignal and HeatingSignal – I tried to set these up as OR types (trying to test how dynamic I can make the “fit” function).  Its throwing an “Ambiguous match for Point: ashrae.g36::CoolingSignal” error when using the “fitsExplain()”.  This is likely my fault for not quite working this out per Xeto’s intended use of “or” types. 

- [] #2: SiteAirPressureSensor was created, and its intended to be a “Building Static Pressure” type, but I didn’t see a tag in Haystack for “whole building stuff” beyond the “site” tag.  Not sure the “site” tag’s intended use fits what I did here.  

- [] 3# The misc-points.xeto now has some types that could probably be merged into specific ph.points files, which would fit their intent and clean up misc-points.xeto.  I may make these changes to the source, but I am still testing the waters with this, so in the mean time, please “bless this mess” 😉 

Late Morning, Update2: Figured it out, my new code is here now! 

Capt'n's Log: AM: I just did a clone of this repository on a different machine first thing this morning and learned that I have not yet
fully understood how to push my changes up.  I am working on this today.  I'll post here once I have learned how to do this the way I expect 
(still reading the git manual https://git-scm.com/docs/user-manual)
Cheers - EnochRick

# Rick's Update 8/29/24
I forked this project for a couple of reasons:
1) I wanted to learn the github workflow, and put it into practice to learn how its done
2) I wanted to learn Xeto and be able to build and use it in axon
3) I noticed the GL36 example wasn't how I'd personally interpret GL36 to be used in Xeto, so i updated it and provided comments.

I hope folks find my changes useful! Cheers - EnochRick
