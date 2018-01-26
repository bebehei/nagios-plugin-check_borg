# check_borg

Check borg repository for date of latest archive.

Usable with nagios, icinga2 or any other nagios-fork.

# Usage

    ./check_borg [ -C CONF ] [ -R <borg-repo-url> ] [ -c <date> ] [ -w <date> ]

`<date>` can be any valid format parsable by the date-command. So `last day` would be a valid date.

`-R` can be omitted, when `BORG_REPO` is set in the environment.

`CONF` is a file, which will get sourced. It can export variables like `BORG_PASSPHRASE` and `BORG_REPO`. You can separate with this file your borg specifc secrets from the icinga2 configuration.

## Passwords

Export `BORG_PASSPHRASE`.

# Warnings

- Be sure about the implications, when monitoring a repository secured with a passphrase.
- I don't know how to exclude checkpoints in `borg list` in combination with `--format='{time}{NUL}'`.
