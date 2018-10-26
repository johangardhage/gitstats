# gitstats

A Bash script for generating git statistics.

## Usage

```
Usage: gitstats [OPTION]... [FILE]...

Options:
 -h, --help
       Display this help and exit.
 -v, --verbose
       Enable verbose mode. This causes extra information to be written to standard error.
       Each instance of "-v" or "--verbose" on the command line increases the verbosity level by one.
 -a <pattern>, --authors=<pattern>
       Show commits from list of authors, separated by space.
 -s <date>, --since=<date>
       Show commits more recent than a specific date. Default is "2018-01-01".
 -u <date>, --until=<date>
       Show commits older than a specific date. Default is "today".
 -o <number>, --sort=<number>
       Sort statistics on column number.
 -f <pattern>, --format=<pattern>
       The format of the output. Options are "table" and "csv". Default is "table".
 -n <number>, --number=<number>
       Print the first number of entries.
 -g, --aggregate
       Aggregate the statistics.
 --grep=<pattern>
       Show commits containing specific commit message. Example:
        --grep="BSUC:FT12-23" will show commits for BSUC FT12-23.
 --igrep
       Limit the commits output to ones with log message that do not match the pattern specified with --grep=<pattern>.
 --files=<pattern>
       Show commits containing specific types of files. Example:
        --files="java$,Test" will show commits containing java files and with "Test" in the name.
        --files="java$,\!Test" will show commits containing java files and without "Test" in the name.
        --files="java$|js$" will show commits containing java or javascript files.
 --ifiles
       Limit the commits output to ones with files that do not match the pattern specified with --files=<pattern>.
```

## Example

### Generate top10 table

```
> gitstats ~/git/linux -n 10
        Author                                        Changed files   Added lines     Deleted lines   Engagement      Engagement (%)  Commits         Commits / day   Repository
        --------------------------------------------- --------------- --------------- --------------- --------------- --------------- --------------- --------------- -------------------------
     1  arnd@arndb.de                                 2168            3794            316821          320615          10.01           390             2.50            linux
     2  gregkh@linuxfoundation.org                    1047            830             292341          293171          9.15            137             0.88            linux
     3  sakari.ailus@linux.intel.com                  824             160             168670          168830          5.27            29              0.19            linux
     4  jesper@jni.nu                                 431             17              99983           100000          3.12            2               0.01            linux
     5  ebiggers@google.com                           368             25430           38475           63905           1.99            181             1.16            linux
     6  Feifei.Xu@amd.com                             60              53958           36              53994           1.68            44              0.28            linux
     7  dhowells@redhat.com                           757             8158            38319           46477           1.45            107             0.69            linux
     8  tom.stdenis@amd.com                           25              33495           96              33591           1.05            24              0.15            linux
     9  jhogan@kernel.org                             304             571             32397           32968           1.03            44              0.28            linux
    10  kuninori.morimoto.gx@renesas.com              444             15459           17029           32488           1.01            284             1.82            linux
```

### Generate csv file

```
> gitstats ~/git/linux -n 10 -f csv > ~/gitstats.csv
```

## License

Licensed under MIT license. See [LICENSE](LICENSE) for more information.

## Authors

* Johan Gardhage