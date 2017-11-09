maildir-notifier
================

The **maildir-notifier** tool checks [Maildir][maildir] directories for new
mail. For each new message, it invokes [terminal-notifier][terminal-notifier]
to show a notification that contains the message `From` and `Subject` header.

Usage
=====

Invoking `maildir-notifier` without any arguments prints the usage:

```
usage: maildir-notifier [options] <maildir...>

options:
    -a <age>     number of seconds a cache entry remains fresh [86400]
    -c <cache>   message cache [~/.maildir-notifier-cache]
    -e <cmd>     command to execute when clicking notification []
    -s <sound>   name of sound to play for each new message [Submarine]
    -t <timeout> number of seconds to show notification [2]
    -d <delay>   seconds to wait between each mail [0]
```

To avoid duplicate notifications, the script keeps a cache to determine which
messages have been reported.

Integration
===========

Any application that fetches mail into a Maildir format can easily be
integrated with `maildir-notifier`. For example, [OfflineIMAP][offlineimap] can
execute a *post-sync hook*. This requries adding the following entry to your
`.offlineimaprc`:

```
[Account Test]
postsynchook = maildir-notifier ~/.mail/INBOX
```

License
=======

`maildir-notifier` is a POSIX-compliant shell script that comes with a
[3-clause BSD license](LICENSE).

[maildir]: https://en.wikipedia.org/wiki/Maildir
[terminal-notifier]: https://github.com/julienXX/terminal-notifier
[offlineimap]: http://www.offlineimap.org
