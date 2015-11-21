# obiblio-base
A simple installation of OpenBiblio with a few basic customizations

##Background
In Summer 2015, Lynne Jenne began working with the LBCC Library to identify 


##About obiblio
Based on http://obiblio.sourceforge.net/



##Differences from stock openbiblio
Includes Fred LaPlante's lookup2 patch




##How to install this on a Linux server

Change file with db credentials

Cron job: I also configured the check-in process so that all materials that are
"on the shelving cart" are moved back to the shelves automatically at
midnight daily.  This way, we won't have any items languishing on the
shelving cart after being checked in.
