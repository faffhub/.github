# Track your time

Faff is a local-first open standard ledger that helps you think about how you're choosing to spend your time. It serves you first - time is tracked on your device, and you choose what, when, and how to share that record with whomever you choose.

## The Philosophy of Time Tracking
Most time tracking services think first about billing and second about efficiency. If they think about you at all, it's as a distant third. But your time is yours, and the insights made possible from honest, accurate tracking are vital to _you_.

Faff brings intentionality to how you think about time. When you record an entry in the ledger, it can just be as simple as a title, start, and end time. But Faff invites you to take a step further and complete this sentence:

  As a ________, I am ________ to achieve ________, focused on ________.

And once the day is done, Faff encourages you to reflect, giving each block of time a simple score. Was it energising? Efficient? Frustrating?

Tracking your time in this way lets you reflect deeply on how you spend your days. How do you split your life between the many roles you play? How much time are you actually spending in meetings, and how many of those hours are directly in service of your most important goals?

## Quick Start

If you don't have it already, install **pipx**: https://pipx.pypa.io/stable/installation/

Then:
```
$ pipx install faff-cli
  installed package faff-cli 0.1.7, installed using Python 3.13.7
  These apps are now globally available
    - faff
```
```
$ faff init
Initializing faff ledger...
✓ Initialized faff ledger at /home/tom.linux/.faff.
```

Now you're ready to start tracking your time locally!

### Linking with an upstream time-tracker

If you want also to report your tracked time into a third-party time-tracker, we can set that up as a **remote**. Each third-party time-tracker is different, so we use a dedicated plugin written specially to sync data to/from Faff.

There's only one third-party time-tracker supported today, <a href="https://myhours.com/">myhours</a>, though writing plugins for other time-tracking services is designed to be as easy as possible. The <a href="https://github.com/faffhub/faff-plugin-my-hours">myhours plugin</a> is available on github, but we'll install it directly using the `faff` command line tool.

To set up a remote, we're going to install the myhours plugin, then configure an instance of it:

```
$ faff plugin install https://github.com/faffhub/faff-plugin-my-hours
Installing plugin 'faff-plugin-my-hours' from https://github.com/faffhub/faff-plugin-my-hours...
✓ Successfully installed plugin 'faff-plugin-my-hours' to /home/tom.linux/.faff/plugins/faff-plugin-my-hours

To create a remote using this plugin, run:
  faff remote add <remote-id> faff-plugin-my-hours
```
```
$ faff remote add my-employer faff-plugin-my-hours
Created remote 'my-employer' from plugin template
File: /home/tom.linux/.faff/remotes/my-employer.toml

Run: faff remote edit my-employer to configure
```
```
$ faff remote edit my-employer
```

Running `faff remote edit my-employer` will open the configuration file in your default editor. The basic configuration is _very_ basic - you just need to replace the example email address in the [conenction] section with your own. Then save the file.

```
id = "my-employer"
plugin = "faff-plugin-my-hours"

[connection]
email = "your.email@address.here"
```

Next, we'll pull the time-tracking data from my-hours:
```
$ faff pull
```

