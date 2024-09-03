# (original) Overview

Xeto is a data-only type system.  The name is derived from the phrase "eXtensible
Explicitly Typed Objects".  Xeto defines a simple plain text format used to
declare types and to exchange typed data.  It is designed to build and validate
[Project Haystack](https://project-haystack.org/) data models.  But Xeto is general
purpose enough to use with any structured data including CSV, JSON, or SQL data.

This repository is used to manage the source code for the standard libraries.

**I am having issues in skyspark that I am not having with the CLI axon. ** 
I am working on it, right now be cautious with this fork and please realize it's a work in progress. 

# Update 9/3/2024 [^1]
I wrote up my process and references in a note file you can find here: [EnochRicksNotes](EnocRicksNotes.md).  This includes detailed step-by-step instructions on how to compile your xeto files and bring them into your SkySpark environment for use and testing! Please scroll to the bottom to see my process step-by-step. 

I also  implemented the "choice" type for the cooling signal and heating signal which fixed the ambiguous match exception.  Furthermore, I made the call to version ph.points and added the specs for things that were previously in the `ashrae.g36/misc-points.xeto` under `ashrae.g36`.  

Added entries to the bottom of the following files in `ph.points`:
- air-pressure.xeto
- damper.xeto
- fan.xeto

`ph.points` has been versioned with these changed to v0.1.2 and the `ashrae.g36/lib.xeto` now requires this updated version. 

Known Issues:

- [x] #1: Ambiguous types for : CoolingSignal and HeatingSignal – I tried to set these up as OR types (trying to test how dynamic I can make the “fit” function).  It throws an “Ambiguous match for Point: ashrae.g36::CoolingSignal” error when using the “fitsExplain()”.  This is likely my fault for not quite working this out per Xeto’s intended use of “or” types. I now see I need to make them a "choice" type and reference the applicable entity types for GL36. 

- [ ] #2: SiteAirPressureSensor was created, and it's intended to be a “Building Static Pressure” type, but I didn’t see a tag in Haystack for “whole building stuff” beyond the “site” tag.  Not sure the “site” tag’s intended use fits what I did here.  

- [x] 3# The `misc-points.xeto` now has some types that could probably be merged into specific ph.points files, which would fit their intent and clean up `misc-points.xeto`.  I may make these changes to the source, but I am still testing the waters with this, so in the meantime, please “bless this mess” 😉 

Cheers - EnochRick

# Update 8/30/24 
End of day update: Moved a bunch of new types into the misc-points.xeto.  Had to define some new things to fit the Guideline's intent for certain control sequences (like building pressure control). 

Late Morning, Update 2: Figured it out, my new code is here now! 

Capt'n's Log: AM: I just did a clone of this repository on a different machine first thing this morning and learned that I have not yet
fully understood how to push my changes up.  I am working on this today.  I'll post here once I have learned how to do this the way I expect 
(still reading the git manual https://git-scm.com/docs/user-manual)
Cheers - EnochRick

# Rick's Update 8/29/24
I forked this project for a couple of reasons:
1) I wanted to learn the GitHub workflow and put it into practice to learn how it's done
2) I wanted to learn Xeto and be able to build and use it in axon
3) I noticed the GL36 example wasn't how I'd personally interpret GL36 to be used in Xeto, so I updated it and provided comments.

I hope folks find my changes useful! Cheers - EnochRick

[^1]: All my updates will read chronologically from newest to oldest, with the newest at the top. That way you can read my struggles like a story. 
