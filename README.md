# obiblio-base
A simple installation of OpenBiblio with a few basic customizations

##Background
In Summer 2015, Lynne Jenne began working with the LBCC Library to identify a simple, easy-to-use library system that supports barcode copy cataloging and circulation tasks.  It also has to be used without intervention from anybody other than the library users.

There are a number of apps and web services that would allow this.  We evaluated a number of these, but the large size of the ELA library placed it out of the free usage tier.  A subscription fee is not feasible for the ELA library at this time.

I had previously used Openbiblio for the Library at [Tap In Leadership Academy](http://wiki.tapinacademy.org/index.php?title=Category:Library) in Champaign, Illinois.  This experience gave me some familiarity with its installation process and community.  It is much simpler to use and administer than the Evergreen system used by the LBCC library.

##About obiblio
Based on http://obiblio.sourceforge.net/



##Differences from stock openbiblio
Openbiblio does not have all the features required by the ELA library.

The library needs to retrieve book data via ISBN.  Therefore, I included Fred LaPlante's lookup2 patch.

I had previously developed a [very small patch](https://github.com/tapinacademy/obiblio-covers) to include a cover image in catalog images.

[xelite25](https://github.com/xelite25), a work study student at LBCC, contributed some helpful documentation.  This documentation was almost entirely missing from the original.


##How to install this on a Linux server

Change file with db credentials

Cron job: I also configured the check-in process so that all materials that are
"on the shelving cart" are moved back to the shelves automatically at
midnight daily.  This way, we won't have any items languishing on the
shelving cart after being checked in.

##Further steps in this project
Version 1.0 of openbiblio is available as a beta.  While it looks very nice, it still has some issues that I'd like to see resolved before moving to the new version.
