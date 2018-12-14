# homebrew-nsq

This is a fork of the [core Homebrew NSQ
formula](https://github.com/Homebrew/homebrew-core/blob/master/Formula/nsq.rb).  

There are two steps to using this fork:

1. If you have already installed the default nsq formula that comes with Homebrew, make sure that
   its stopped and uninstalled.

        brew services stop nsq
        brew uninstall nsq

2. Then install this fork and run its services like so:

        brew install btubbs/nsq/nsqlookup
        brew services start btubbs/nsq/nsqlookup
        brew services start btubbs/nsq/nsq

## Why does this fork exist?

If you do a `brew install nsq`, and then a `brew services start nsq`, you end up in a weird place
NSQ-wise.  While nsqd will be running, you won't have an nsqlookupd.  So most of the NSQ examples
you find online won't work.  If you start an nsqlookupd separately, it still won't work, because the
plist file created by the default formula doesn't start nsqd with the necessary arguments to find
and use an nsqlookupd.

This can be very frustrating for someone just trying to get a "Hello World"-level app working with
NSQ, on MacOS.

This repo solves the problem by having separate formulae for nsqd and nsqlookupd.  If you install
nsqlookupd from this repository, nsqd will also be installed.  And you'll be able to start both
services with Homebrew, with both of them talking to each other.



