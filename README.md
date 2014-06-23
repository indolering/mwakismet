MediaWiki-Akismet
=================
This is a project to add Akismet support to MediaWiki.  It will currently
run all page edits through the Akismet servers and disallow saving if
Akismet decides an edit is spam.  There is the beginning of an admin
interface to mark edits as spam or ham, but it doesn't allow submitting
to the Akismet servers.

Requirements
------------
MediaWiki-Akismet requires a working installation of MediaWiki, PHP 5, and an
Akismet account.  The extension has been tested with MediaWiki 1.19 and
PHP 5.4, but it may work on earlier versions.

Installing
----------
1. Signup for Akismet and [retrieve your akismet key](https://akismet.com/account/).
2. Install Git and MediaWiki on your server.
3. Change your directory to the top MediaWiki directory and clone mwakismet: `git clone git://github.com/aag/mwakismet extensions/Akismet`.
4. Run `php ./maintenance/update.php` to create the mw_akismet_edits database table.
5. Edit LocalSettings.php in the MediaWiki root directory.  Add these three 
   lines near the end of the file, but before the `?>`:
   
```php
# Akismet extension
include("$IP/extensions/Akismet/Akismet.php");
$wgMWAkismetKey = 'yourAkismetKey';
$wgMWAkismetURL = 'http://www.YOURDOMAIN.com/';
```

License
-------
This code is released under the GPL 2 License.  See the COPYING file for
details.

