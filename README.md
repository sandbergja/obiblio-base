# obiblio-base
A simple installation of OpenBiblio with a few basic customizations

##Background
In Summer 2015, Lynne Jenne began working with the LBCC Library to identify a simple, easy-to-use library system for use in the ELA library.  The system needed to support copy cataloging by ISBN and circulation tasks by barcode.  Since the Library is unstaffed, the system also needed to be usable with a minimal level of intervention.

There are a number of apps and web services that would allow this.  We evaluated a number of these, but the large size of the ELA library placed it out of the free usage tier.  A subscription fee is not feasible for the ELA library at this time.

I had previously used Openbiblio -- an open source integrated library system -- for the Library at [Tap In Leadership Academy](http://wiki.tapinacademy.org/index.php?title=Category:Library) in Champaign, Illinois.  This experience gave me some familiarity with its installation process and community.  It is much simpler to use and administer than the Evergreen system used by the LBCC library, but it contains most of the features that Lynne sought.  I felt confident recommending this piece of software for use in the ELA library and setting aside a small portion of my time to getting it installed and making a few modifications.

##Modifications to a stock OpenBiblio Installation
Openbiblio 0.7.2 does not have all the features required by the ELA library, which meant that I needed to incorporate some customizations built by myself and others in the OpenBiblio community.

The library needs to retrieve book data via ISBN to save time during the cataloging process.  Fred LaPlante offers a very nice [lookup2](http://sourceforge.net/p/obiblio/patches/65/) patch that allows us to do this.  While by default, it uses the Library of Congress SRU server to collect data, we found that the CUNY SRU server included more of the books that are included in the ELA library.  It is worth noting that LC and CUNY use different schemata, and the [lookup patch only allows the use of one schema](https://bitbucket.org/mstetson/obiblio-10-wip/issues/23/lookup-must-allow-hosts-to-use-other-sru) at a time.  This makes switching between CUNY records and LC records a bit of a pain.

To make the lookup2 patch a bit more user-friendly, I also applied [Wolfram Sang's patch](http://sourceforge.net/p/obiblio/patches/87/) that simplifies the lookup2 interface.

I had previously developed a [very small patch](https://github.com/tapinacademy/obiblio-covers) to include a cover image in catalog images.  I added this to help with identifying desired books.

Finally, [xelite25](https://github.com/xelite25), a work study student at LBCC, contributed some helpful documentation.  This documentation was almost entirely missing from the original.


##How to install this on a Linux server

I made this cut of Openbiblio easy for me to install and update, in case other folks on campus were interested in similar setups.

The only file missing from this repository is [database_constants.php](https://bitbucket.org/mstetson/obiblio/src/babf99e9469d7f0be0eaff11cbadf92badb0a6f3/database_constants.php).  The only additional file -- which you can delete after installation -- is the database file [obiblio-base.sql](https://github.com/sandbergja/obiblio-base/blob/master/obiblio-base.sql).

To install obiblio-base on a Linux server (assuming MySQL runs on localhost):
1. Type `git clone https://github.com/sandbergja/obiblio-base.git` on the command line.

2. `cd obiblio-base`

3. Open mysql on the command line.

4. Type `CREATE DATABASE db_name` where db_name is the name you'd like to call your database.

5. Type `SOURCE obiblio-base.sql`

6. Close mysql by pressing `^D`

7. Create a database_constants.php file

I also created a cron job so that all materials that are
"on the shelving cart" are moved back to the shelves automatically at
midnight daily.  This way, the ELA  library won't have any items languishing on the
shelving cart after being checked in.  I accomplished this with the following one-liner:  `mysql -u username -ppassword -hhostname -e 'UPDATE biblio_copy SET status_cd="in" WHERE status_cd = "crt"' db_name`

##Further steps in this project
Version 1.0 of openbiblio is available as a beta.  While it looks very nice, it still has some issues that I'd like to see resolved before moving to the new version.

However, OpenBiblio 0.7.2 has not seen any major updates for over a year.  since I am running the ELA catalog with PHP 5.6, a lot of its code relies on deprecated functions, and I am having to suppress more warnings than I would like.  I am planning to keep an eye on the list of unresolved issues and possibly upgrade OpenBiblio during Summer 2016.
