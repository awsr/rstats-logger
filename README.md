[![Python Versions](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12-blue)](https://github.com/awsr/rstats-logger)

# rstats

- Reads the rstats bandwidth usage file created by Tomato USB (router firmware), Asuswrt-Merlin, and others.
- Displays human readable format to console.
- Logs traffic stats to a JSON file.
- Attempts to gracefully handle instances of a bug with ASUS RT-AC68U where values will get corrupted and show up as being in the exabyte range.

### Usage:
`python rstats.py <filename> [--out <output-filename>]`

* `--out`: Path to save/load JSON

#### Log format update

If upgrading the script to a version with a different file format, you can either:
* Run `python update_log.py output.json` using [update_log.py](util/update_log.py)

or

* Put [update_log.py](util/update_log.py) in a `util` subfolder from the main script and it'll run automatically.

### Examples:

#### Print to console:

`python rstats.py tomato_rstats.gz`

#### Log to file:

`python rstats.py tomato_rstats.gz --out traffic.json`

---

### Warning

Python seems to be told the system time is in UTC instead of what the router is set to... except in some circumstances. For reliability, the system's `date` command is used to get time values.
