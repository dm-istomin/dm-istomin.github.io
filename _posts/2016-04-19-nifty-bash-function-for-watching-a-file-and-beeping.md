---
title: Nifty Bash Function for Watching a File and Beeping on a Match
updated: 2016-04-19 23:17
---

Have you ever had a bug that shows up occasionally in the logs, but so
rarely that it feels like a waste of time to sit there and watch the output
from ```tail -f```? Well, get ready for some Unix magic.

```bash
function tail_beep {
  tail -f $1 | grep --line-buffered $2 | while read line; do echo '\a' && grep $2 <<< $line; done
}
```

Usage:

```term
$ tail_beep development.log 'thing that happens very rarely'
```

This function basically works the same way as ``` tail -f <file> | grep <search term>```,
but it makes a sound whenever there is a match for the term you want! I've
only tested in on Mac, but it should translate to Linux without any problems.

Now you can have a tab open with this running and do all of
your other important stuff, like browsing Facebook, without feeling irresponsible.
