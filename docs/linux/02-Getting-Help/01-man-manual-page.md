<h1>Manual Page</h1>

- Built-in help documents describing commands, their purpose, and available options.
- To view a man page for a command, use the man command: `man command`

Example : `man cal`

<Details>

```bash
 
 CAL(1)                                                                                                                                                                                  User Commands                                                                                                                                                                                 CAL(1)

NAME
       cal - display a calendar

SYNOPSIS
       cal [options] [[[day] month] year]

       cal [options] [timestamp|monthname]

DESCRIPTION
       cal displays a simple calendar. If no arguments are specified, the current month is displayed.

       The month may be specified as a number (1-12), as a month name or as an abbreviated month name according to the current locales.

       Two different calendar systems are used, Gregorian and Julian. These are nearly identical systems with Gregorian making a small adjustment to the frequency of leap years; this facilitates improved synchronization with solar events like the equinoxes. The Gregorian calendar reform was introduced in 1582, but its adoption continued up to 1923. By default cal uses the
       adoption date of 3 Sept 1752. From that date forward the Gregorian calendar is displayed; previous dates use the Julian calendar system. 11 days were removed at the time of adoption to bring the calendar in sync with solar events. So Sept 1752 has a mix of Julian and Gregorian dates by which the 2nd is followed by the 14th (the 3rd through the 13th are absent).

       Optionally, either the proleptic Gregorian calendar or the Julian calendar may be used exclusively. See --reform below.

OPTIONS
       -1, --one
           Display single month output. (This is the default.)

       -3, --three
           Display three months spanning the date.

       -n , --months number
           Display number of months, starting from the month containing the date.

       -S, --span
           Display months spanning the date.

       -s, --sunday
           Display Sunday as the first day of the week.

       -m, --monday
           Display Monday as the first day of the week.

       -v, --vertical
           Display using a vertical layout (aka ncal(1) mode).

       --iso
           Display the proleptic Gregorian calendar exclusively. This option does not affect week numbers and the first day of the week. See --reform below.

       -j, --julian
           Use day-of-year numbering for all calendars. These are also called ordinal days. Ordinal days range from 1 to 366. This option does not switch from the Gregorian to the Julian calendar system, that is controlled by the --reform option.

           Sometimes Gregorian calendars using ordinal dates are referred to as Julian calendars. This can be confusing due to the many date related conventions that use Julian in their name: (ordinal) julian date, julian (calendar) date, (astronomical) julian date, (modified) julian date, and more. This option is named julian, because ordinal days are identified as julian by
           the POSIX standard. However, be aware that cal also uses the Julian calendar system. See DESCRIPTION above.

       --reform val
           This option sets the adoption date of the Gregorian calendar reform. Calendar dates previous to reform use the Julian calendar system. Calendar dates after reform use the Gregorian calendar system. The argument val can be:

           •   1752 - sets 3 September 1752 as the reform date (default). This is when the Gregorian calendar reform was adopted by the British Empire.

           •   gregorian - display Gregorian calendars exclusively. This special placeholder sets the reform date below the smallest year that cal can use; meaning all calendar output uses the Gregorian calendar system. This is called the proleptic Gregorian calendar, because dates prior to the calendar system’s creation use extrapolated values.

           •   iso - alias of gregorian. The ISO 8601 standard for the representation of dates and times in information interchange requires using the proleptic Gregorian calendar.

           •   julian - display Julian calendars exclusively. This special placeholder sets the reform date above the largest year that cal can use; meaning all calendar output uses the Julian calendar system.

               See DESCRIPTION above.

       -y, --year
           Display a calendar for the whole year.

       -Y, --twelve
           Display a calendar for the next twelve months.

       -w, --week[=number]
           Display week numbers in the calendar according to the US or ISO-8601 format. If a number is specified, the requested week will be printed in the desired or current year. The number may be overwritten if day and month are also specified.

           See the NOTES section for more details.

       --color[=when]
           Colorize the output. The optional argument when can be auto, never or always. If the when argument is omitted, it defaults to auto. The colors can be disabled; for the current built-in default see the --help output. See also the COLORS section.

       -c, --columns=columns
           Number of columns to use. auto uses as many as fit the terminal.

 Manual page cal(1) line 1/167 55% (press h for help or q to quit)
```
</Details>
 

 
 ---
 Section  main page : 

 * **NAME** – Command name and brief description
* **SYNOPSIS** – Command usage examples and syntax
* **DESCRIPTION** – Detailed explanation of the command
* **OPTIONS** – List and explanation of command options
* **FILES** – Associated files used by the command
* **AUTHOR** – Creator of the command or man page
* **REPORTING BUGS** – How to report issues with the command
* **COPYRIGHT** – Copyright and licensing information
* **SEE ALSO** – References to related commands or documentation

---
By default, there are 9 sections of man pages:

1. General Commands
2. System Calls
3. Library Calls
4. Special Files
5. File Formats and Conventions
6. Games
7. Miscellaneous
8. System Administration Commands
9. Kernel Routines


>The `man` command searches sections in order and shows the first match; if none found, it returns an error.

Example : 
```bash
man zed                                          
# No manual entry for zed   
```

---
>The man -k command searches man page names and descriptions for a keyword, helping locate relevant pages.

Example : 

```bash
man -k copy                                               
# cp (1)               - copy files and directories                               
# cpgr (8)             - copy with locking the given file to the password or gr...
# cpio (1)             - copy files to and from archives                          
# cppw (8)             - copy with locking the given file to the password or gr...
#  dd (1)               - convert and copy a file                                  
# debconf-copydb (1)   - copy a debconf database                                  
# install (1)          - copy files and set attributes                            
# scp (1)              - secure copy (remote file copy program)                   
# ssh-copy-id (1)      - use locally available keys to authorize logins on a re...
```


<h1>Finding Commands and Documentation</h1>

* `whatis [command]` → shows man page section and description.
* Multiple entries can exist for the same command due to UNIX variants.
* Helps determine which command version runs when typed.

Example : 

```bash
whatis ls
# ls (1)               - list directory contents 
```

<h1>Where Are These Commands Located</h1>

* `whereis [command]` → finds command, source files, and man pages.
* Man pages usually end with `.gz` (compressed).
* Some commands may have multiple man pages; most have one.

Example : 

```bash
whereis ls
# ls: /bin/ls /usr/share/man/man1p/ls.1.gz /usr/share/man/man1/ls.1.gz
```


---
Find Any File or Directory : `locate Movie` 