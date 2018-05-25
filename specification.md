# Summary
This specification describes a command line screen scraping program to
retrieve release information for software packages tracked on freshmeat.net.

# Rational
We would like to graph the time line of the releases but freshmeat.net does
not provide a programmatic api to retrieve the data.

# Scope
Covers the command line interface and output format.

# Use Cases

|| Who || What || How || Result ||
| programmer | Retrieve timeline for an application | Run the command line program and pass the application name as an argument. | A. Success - csv written to standard out. Exit code 0. B. Failure - Error written to standard error. Exit code 4. |
| programmer | View program help | Run the command line program with no arguments or with --help | Displays brief description and usage. |

# Assumptions
* No character set handling is required.
* Website is public and requires no login.

# Implementation
The code will be written in Python 3 and will make use of the following
libraries:
* BeautifulSoup - HTML parsing and navigation
* <some option parser> - Options and arguments parsing library.
* <csv library> - Handles output of the csv file.

## Output
The csv output will contain the following fields. The separator character
may be changed from a comma to another character.
* version - This is the version of the software release.
* timestamp - The date and time of the release.
* note - The release note.

## Command Line
fmscraper [--help] [--separator <separator>] <application-name>

--help : Will display usage and exit.
--separator : Specify a separator character. Comma (,) is the default.
<application-name> : Retrieve timeline as csv for this application.
