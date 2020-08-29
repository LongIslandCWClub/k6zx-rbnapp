# Enhanced Reverse Beacon Network: rbn

The **rbnapp** package provides an enhanced Reverse Beacon Network (RBN)
client that adds some useful features to the standard RBN
functionality. 

This repository is the executable application respository. The source
code is contained in the *k6zx-rbn* repository.


## Table of Contents

* [General Info](#general_info)
* [Installation](#installation)
* [Invocation](#invocation)

<a name="general_info"></a>
## General Info

The RBN is a network of receiving stations listening to the amateur
bands and reporting what stations they hear transmitting. This
information is transmitted from the listening stations to a server
from which amateur radio operators can access these spot reports to
see who is operating on which frequencies, which operating modes, CW
speed, and the received signal strength from those stations at the
receiving stations. This allows one to see who is receiving your
transmissions and how well you are being heard. It also can show who
in your geographical area is being heard and by whom. 

The RBN has a web interface that one uses a browser to access and it
also has a telnet interface that allows for maximum throughput of the
spot data. RBN has two telnet access ports, one for CW, RTTY, and PSK
spots and another dedicated to FT8. It is the CW telnet interface that
the **rbn** package uses and then filtering of the spots is performed
as specified by the user's configuration. Access to FT8 spots is not
implemented. 

The **rbn** package allows one to connect to the RBN telnet stream and
filter the spots in many ways under the control of the user. Spots
that pass the filters and are displayed can be color-coded if the
station spotted is a member of a club (LICW and SKCC are currently
implemented). There is also a distance value that shows the location
of spotted station and the distance from that station to the user's
location. This is the added functionality provided by the **rbn**
package over and above what is available from RBN. 

This repository contains the executable applications of the **rbn**
package. The **rbn** package is implemented in Python and the
executables are created from the source code using the *pyinstaller*
Python module.  It has been tested on the following operating systems:

- Linux

*Note: Testing on MacOS and Windows 10 is planned for the future.*


<a name="installation"></a>
## Installation

The **rbn** application in the **rbnapp** package is a complete
standalone application that requires no other support files (*I
think*) in the host operating system. The applications are located in
the *rbnapp/dist/{os}* directory of the repository. The **rbn**
application need only to be copied to a desired location in the
computer's filesystem. Normally this would be a location that is in
the user's *PATH* so that it may be convieniently called from a
terminal window. 

The **rbn** package runs in a terminal session and is invoked from the
command line. Its operation is configured with either a configuration
file or optional command line arguments. While either way is
effective, using a configuration file is probably the easiest method
of use. A default configuration file can be written using:

    rbn.py --init <config_dir>

 where *config_dir* is a directory in which the program's
 configuration file is stored.

<a name="invocation"></a>
## Invocation

The **rbn** package is invoked as follows:

```
usage: rbn.py [-h] [--init INIT] [-b BAND] [-c CALLSIGN] [-l LOGGING] [--telnetdebug TELNETDEBUG]
              [--de_maid DEMAID] [--dx_maid DXMAID] [--de_ituzone DEITUZONE] [--dx_ituzone DXITUZONE]
              [--de_cqzone DECQZONE] [--dx_cqzone DXCQZONE] [--min_wpm MINWPM] [--max_wpm MAXWPM]
              [-m MODE] [-f CONFIGFILE] [--licw-file LICWFILE] [--cwops CWOPS] [--skcc-file SKCCFILE]
              [--qrz_username QRZUSERNAME] [--qrz_password QRZPASSWORD] [--latitude LATITUDE]
              [--longitude LONGITUDE] [--skcc] [--licw]

RBN spot filter program. Args that start with '--' (eg. --init) can also be set in a config file
(specified via -f). Config file syntax allows: key=value, flag=true, stuff=[a,b,c] (for details, see
syntax at https://goo.gl/R74nmi). If an arg is specified in more than one place, then commandline
values override config file values which override defaults.

optional arguments:  
  -h, --help            show this help message and exit  
  --init INIT           Initialize rbn configuration files  
  -b BAND, --band BAND  Display stations only on these bands  
  -c CALLSIGN, --callsign CALLSIGN  
                        Specify user's callsign  
  -l LOGGING, --logging LOGGING  
                        Enable program logging  
  --telnetdebug TELNETDEBUG  
                        Enable telnetlib debugging  
  --de_maid DEMAID      DE Maidenhead squares  
  --dx_maid DXMAID      DX Maidenhead squares  
  --de_ituzone DEITUZONE  
                        DE ITU Zone  
  --dx_ituzone DXITUZONE  
                        DX ITU Zone  
  --de_cqzone DECQZONE  DE CQ Zone  
  --dx_cqzone DXCQZONE  DX CQ Zone  
  --min_wpm MINWPM      Minimum CW WPM to show  
  --max_wpm MAXWPM      Maximum CW WPM to show  
  -m MODE, --mode MODE  Select transmission mode  
  -f CONFIGFILE, --config-file CONFIGFILE  
                        Config file path  
  --licw-file LICWFILE  LICW Callsign file  
  --cwops CWOPS         CWOps Callsign file  
  --skcc-file SKCCFILE  SKCCLogger local membership database  
  --qrz_username QRZUSERNAME  
                        QRZ username  
  --qrz_password QRZPASSWORD  
                        QRZ password  
  --latitude LATITUDE   Station latitude  
  --longitude LONGITUDE  
                        Station longitude  
  --skcc                Highlight SKCC members  
  --licw                Highlight LICW members  

Telnet to Reverse Beacon Network (RBN) server and capture CW spots. This program provides better
(IMHO) filtering of these spots. Provide the filtering parameters as command line arguments or in a
config file.
```





