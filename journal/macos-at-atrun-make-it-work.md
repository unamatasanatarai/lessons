# Cron but at | atrun on Macos

1. enable the at daemon: \
   `launchctl load -w /System/Library/LaunchDaemons/com.apple.atrun.plist`
1. allow full disk access to `/usr/libexec/atrun` in Security & Privacy
   - Open Security & Privacy
   - click on Full Disk Access
   - unlock the padlock
   - click `+`
   - hit `Cmd+Shift+G`
   - `/usr/libexec/`
   - select atrun
1. enjoy the `at -f path_to_scropt.sh at now +1 minute`


[read more](https://unix.stackexchange.com/a/478840/131514)
