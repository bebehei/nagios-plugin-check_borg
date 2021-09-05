# check_borg

Check borg repository for date of latest archive.

Usable with nagios, icinga2 or any other nagios-fork.

# Usage

    ./check_borg [ -C CONF ] [ -R <borg-repo-url> ] [ -P <borg-archivename-prefix> ] [ -c <date> ] [ -w <date> ]

`<date>` can be any valid format parsable by the date-command. So `last day` or `12 hours ago` would be valid dates.

`-R` can be omitted, when `BORG_REPO` is set in the environment.

`CONF` is a file, which will get sourced. It can export variables like `BORG_PASSPHRASE` and `BORG_REPO`. You can separate with this file your borg specific secrets from the icinga2 configuration.

## Non-standard executable paths

- If your `borg` executable is not installed in your `$PATH` or is not called `borg`, you can define the environment variable `BORG` to point to the correct command.
- If the GNU `date` executable is not installed as `date`, you can set the environment variable `DATE` to point to the correct `date` command.

## Passwords

Export `BORG_PASSPHRASE`.

# Requirements

- GNU's version of `date`.
- [borgbackup](https://github.com/borgbackup/borg/)

# Warnings

- Be sure about the implications, when monitoring a repository secured with a passphrase.
- I don't know how to exclude checkpoints in `borg list` in combination with `--format='{time}{NUL}'`.
