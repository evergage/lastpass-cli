# Version 1.0.0-evg.1
 * Add support for confirming sharing key fingerprints when adding users to
   shared folders.

# Version 1.0.0
 * New command ```lpass status``` shows whether or not the user is logged
   in with agent, from Nick Knudson
 * ```lpass add``` can now be passed ```--note-type=X``` in order to add
   a secure note using a template.  Specifying an unknown note template will
   list the available templates.
 * ```lpass ls``` now shows username with ```--long```, from Alli Witheford
 * Bash completions are now installed with make install, from Eli Schwartz
 * Fish shell completions supplied by Joar Wanboarg
 * Initial support for adding (```lpass add --app```) and editing applications
 * Updates to manpage for ```ls```, ```passwd```, ```add```, and basic
   usage examples
 * lpass now follows XDG base directory specifications for its files on
   platforms that use it.  Set ```LP_HOME``` to ~/.lpass to keep the previous
   location
 * Bugfix: resolved syncing problems on some platforms (notably RHEL/CentOS)
   related to improper multiprocess usage of libcurl (github #166)
 * Bugfix: ```lpass show``` no longer crashes when a searched-for field is
   not found (github #167)
 * Bugfix: ```lpass``` no longer exits with an error if the blob is empty
   but otherwise without parsing errors.  This fixes the case where a new
   user could not use the application without first adding a site elsewhere.
 * ```LPASS_LOG_LEVEL``` learned level=8 with which lpass will also dump
   libcurl verbose logs showing all traffic for debugging (not recommended
   for general use due to potentially sensitive headers being logged).

# Version 0.9.0
 * Add support for accounts in the EU datacenter (lastpass.eu)
 * ```lpass ls``` now sorts its output and properly displays group folder
   account entries
 * ```lpass export``` output has been reworked to match that of the website,
   from Justen Walker
 * ```lpass share limit``` subcommand was added which allows displaying and
   modifying user-specific restrictions for shared folders
 * The new ```LPASS_LOG_LEVEL``` environment variable can be set to cause
   the lpass uploader process to log its actions, useful for debugging syncing
   issues.  Set it to 7 to get all debug logs; the logfile will be
   ~/.lpass/lpass.log.
 * Bugfix: syncing is fixed on systems that use XFS or other filesystems which
   do not support setting d_type in readdir()
 * Bugfix: ```lpass mv``` now works properly with linked accounts

# Version 0.8.1, 0.7.2, 0.6.1, 0.5.1
 * This update to all recent versions switches to the platform certificate
   store and adds pinning of LastPass public keys, in preparation for
   certificate changes at lastpass.com. Upgrade will be needed to avoid "Peer
   certificate cannot be authenticated with given CA certificates" errors
   when the cert changes are made.

# Version 0.8.0
 * New command ```lpass add``` works like ```lpass edit``` for new accounts
 * New command ```lpass mv``` can be used to move an account into a different (possibly shared) folder
 * New command ```lpass passwd``` can be used to change master password
 * Tab-completion for bash is now available; to use, source ```contrib/lpass_bash_completion``` from a bash startup file
 * ```lpass ls``` now interprets backslash properly for subfolder display
 * ```lpass edit``` gained the ability to edit all fields of an account at once by using a specially-formatted edit buffer
 * ```lpass show``` gained the ability to show multiple accounts at once, from Angus Galloway
 * ```lpass show``` now reformats SSH private key fields in secure notes into a usable form
 * ```lpass share useradd``` gained the ability to specify group names
 * ```lpass share``` got better documentation
 * Bugfix: logins with certain multifactors that support out-of-band authentication will now work correctly
 * Blob edits no longer reencrypt the entire database, just the changed accounts
 * Syncing operation is now much more robust in the face of server errors or
   invalid transactions.
 * OSX builds fixed for Xcode-less installations, with help from Wael Nasreddine
 * Corrections to FSF address from Tom Prince

# Version 0.7.1
 * This bugfix release fixes a build issue on OSX platforms without XCode. It is otherwise identical to 0.7.0.

# Version 0.7.0
 * ```lpass``` now supports aliases in order to set preferred switches or nicknames for commands. ```echo 'show -G' > ~/.lpass/alias.show```, for example, will turn regex matching on for ```lpass show```.
 * In addition to pinentry and in-process prompting, the ```LPASS_ASKPASS``` environment variable/config value is now checked for a binary to ask for passwords.  It uses the same conventions as ssh-askpass.
 * ```lpass show``` will now match account id when using regex or substring matching
 * ```lpass ls``` learned the ```-l [-u]```switches to show mod and use times, from Lloyd Zusman
 * Secure notes are now created by default when empty sites are edited with --notes, from Lloyd Zusman
 * The new ```LPASS_CLIPBOARD_COMMAND``` environment variable/config value can be used to configure the helper application for the system clipboard, from Tom Prince.  Among other things, you can use this to clear the clipboard after a certain number of pastes with ```xclip -l```.
 * Various code cleanups and documentation fixes from Tom Prince.
 * The license has been clarified to GPLv2 or later, plus the OpenSSL exception; please see individual files and the LICENSE.OpenSSL / COPYING files for details.  This was the intended license all along but it was not spelled out consistently.

# Version 0.6.0
 *  New share sub-command allows automating some common tasks with shared folders
 *  PBKDF2 speedups from Thomas Hurst
 *  Ungrouped entries now fall under "(none)" heading, from Gordon Celesta
 *  Documentation updates from Eli Young
 *  Cleanups from Björn Ketelaars

# Version 0.5.1
 * Update Thawte CA cert to support lastpass.com's new SHA-256 cert.

# Version 0.5.0
 *  OpenBSD support
 *  Updated build/install instructions for Cygwin, Debian, and RPM-based distributions
 *  Regex and substring searching for cmd-show
 *  Secure note parsing and field display
 *  Fixes for pinentry errors and hangs
