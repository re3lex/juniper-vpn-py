Connecting to a Juniper VPN requires the generation of a DSID token.
Generating this token involves authentication and host checking. The
juniper-vpn.py script performs authentication, and the tncc.py script
performs host checking. The DSID token can then be passed to openconnect.

Alternatively, openconnect can perform the authentication steps on it's own
and utilize the tncc.py script for host checker functionality. This is
the recommended mode of operation. Instructions for using openconnect to
perform authentication and tncc.py to perform host checking are contained in:

README.host_checker

Alternate instructions to allow juniper-vpn.py to perform authentication and
tncc.py to perform host checking are contained in:

README.authenticator

# Requirements
Requires Python 3.

Python dependencies can be found at `requirements.txt` file.

Install dependencies:
`pip install mechanize netifaces pyasn1-modules pycurl urlgrabber`

## Installation on Windows
There is no way to install `pycurl` using `pip`.
Do the following:

 * `pip install mechanize netifaces pyasn1-modules`
 * download unofficial `pycurl` from this page as per your python version: https://www.lfd.uci.edu/~gohlke/pythonlibs/#pycurl
 * install it using command `pip install /path/to/file.whl`
 * install urlgrabber: `pip install urlgrabber`

Also urlgrabber is using `fcntl` module which is not supported on Windows.
Need to  change module source:

 * open `urlgrabber\grabber.py` module source for edit: `notepad++.exe "C:\Program Files\Python\3_7\lib\site-packages\urlgrabber\grabber.py"`
 * find all lines with `fcntl` occurences and remove them.
 * in `import` line just remove `fcntl` from imports

# Run
`python juniper-vpn.py -c sample.cfg`