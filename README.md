# obiblio-base
A simple installation of OpenBiblio with a few basic customizations

##Background
In Summer 2015, Lynne Jenne began working with the LBCC Library to identify a simple, easy-to-use library system that supports barcode copy cataloging and circulation tasks.  It also has to be used without intervention from anybody other than the library users.

I had previously used Openbiblio for another library project (http://wiki.tapinacademy.org/index.php?title=Category:Library), and was familiar with its installation process and community.

##About obiblio
Based on http://obiblio.sourceforge.net/



##Differences from stock openbiblio
Includes Fred LaPlante's lookup2 patch

Includes a cover image fetch patch

xelite25 contributed some helpful documentation


##How to install this on a Linux server

Change file with db credentials

Cron job: I also configured the check-in process so that all materials that are
"on the shelving cart" are moved back to the shelves automatically at
midnight daily.  This way, we won't have any items languishing on the
shelving cart after being checked in.
