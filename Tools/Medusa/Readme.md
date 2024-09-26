Intern ID : HPTI-SEP23-205

<img src="./Images/medusa-logo.svg">
<h1><a href="https://github.com/medusajs/medusa">Medusa</a></h1>

# Medusa 

Medusa is intended to be a speedy, massively parallel, modular, login brute-forcer. The goal is to support as many services which allow remote authentication as possible. The author considers following items as some of the key features of this application:   
 - Thread-based parallel testing. Brute-force testing can be performed against multiple hosts, users or passwords concurrently.
 - Flexible user input. Target information (host/user/password) can be specified in a variety of ways. For example, each item can be either a single entry or a file containing multiple entries. Additionally, a combination file format allows the user to refine their target listing.
  - Modular design. Each service module exists as an independent .mod file. This means that no modifications are necessary to the core application in order to extend the supported list of services for brute-forcing.
 - Multiple protocols supported. Many services are currently supported (e.g. SMB, HTTP, POP3, MS-SQL, SSHv2, among others).

# Installation

For Different Distros :

***Ubunut/Debian :***
```bash
    sudo apt install medusa
```

***Fedora :***
```bash
    sudo dnf install medusa
```

Installed Size : ```794 Kb```

# Manual
 - ```-h [TARGET]```

    Target hostname or IP address.

 - ```-H [FILE]```

    Reads target specifications from the file specified rather than from the command line. The file should contain a list separated by newlines.

 - ```-u [TARGET]```

    Target username.

 - -U [FILE]

    Reads target usernames from the file specified rather than from the command line. The file should contain a list separated by newlines.

 - -p [TARGET]

    Target password.

 - -P [FILE]

    Reads target passwords from the file specified rather than from the command line. The file should contain a list separated by newlines.

 - -C [FILE]

    File containing combo entries. Combo files are colon separated and in the following format: host:user:password. If any of the three fields are left empty, the respective information should be provided either as a single global value or as a list in a file.

    The following combinations are possible in the combo file: 1.) foo:bar:fud 2.) foo:bar: 3.) foo:: 4.) :bar:fud 5.) :bar: 6.) ::fud 7.) foo::fud

    Medusa also supports using PwDump files as a combo file. The format of these files should be user:id:lm:ntlm:::. We look for ':::' at the end of the first line to determine if the file contains PwDump output.

 - -O [FILE]

    File to append log information to. Medusa will log all accounts credentials found to be valid or cause an unknown error. It will also log the start and stop times of an audit, along with the calling parameters.

 - -e [n/s/ns]

    Additional password checks ([n] No Password, [s] Password = Username). If both options are being used, they should be specified together ("-e ns"). If only a single option is being called use either "-e n" or "-e s".

 - -M [TEXT]

    Name of the module to execute (without the .mod extension).

 - -m [TEXT]

    Parameter to pass to the module. This can be passed multiple times with a different parameter each time and they will all be sent to the module (i.e. -m Param1 -m Param2, etc.)

 - -d

    Dump all known modules.

 - -n [NUM]

    Use for non-default TCP port number.

 - -s

    Enable SSL.

 - -g [NUM]

    Give up after trying to connect for NUM seconds (default 3).

 - -r [NUM]

    Sleep NUM seconds between retry attempts (default 3).

 - -R [NUM]

    Attempt NUM retries before giving up. The total number of attempts will be NUM + 1.

 - -c [NUM]

    Set the number of usec that are waited during a test of the established network socket. Some services (e.g. FTP, IMAP, POP3, and SMTP) may be configured to drop connections after an arbitrary number of failed logon attempts. We try to reuse the established connection to send authentication attempts until this disconnect occurs, at which point the connection is reestablished. To accomplish this, we check the socket to see if it's still alive before authenticating within select modules. The default is perform a 1 usec check. It may be necessary to specify much larger values. For example, a 1000 usec was needed against our test vsftp server to avoid issues with its built-in anti-bruteforce mechanisms.

 - -t [NUM]

    Total number of logins to be tested concurrently. It should be noted that rougly t x T threads could be running at any one time. 381 appears to be the limit on my fairly boring Gentoo Linux host.

 - -T [NUM]

    Total number of hosts to be tested concurrently.

 - -L

    Parallelize logins using one username per thread. The default is to process the entire username before proceeding.

 - -f

    Stop scanning host after first valid username/password found.

 - -F

    Stop audit after first valid username/password found on any host.

 - -b

    Suppress startup banner

 - -q

    Display module's usage information. This should be used in conjunction with the "-M" option. For example, "medusa -M smbnt -q".

 - -v [NUM]

    Verbose level [0 - 6 (more)]. All messages at or below the specified level will be displayed. The default level is 5.

    The following is the breakdown of the verbose levels: 0) EXIT APPLICATION 1) MESSAGE WITHOUT TAG 2) LOG MESSAGE WITHOUT TAG 3) IMPORTANT MESSAGE 4) ACCOUNT FOUND 5) ACCOUNT CHECK 6) GENERAL MESSAGE

- -w [NUM]

    Error debug level [0 - 10 (more)]. All messages at or below the specified level will be displayed. The default level is 5.

    The following is the breakdown of the error levels: 0) FATAL 1) ALERT 2) CRITICAL 3) ERROR 4) WARNING 5) NOTICE 6) INFO 7) DEBUG 8) DEBUG - AUDIT 9) DEBUG - SERVER 10) DEBUG - MODULE

 - -V
    Display version

 - -Z [TEXT]

    Allows basic resuming of a previous scan. The supplied parameter describes which hosts were completed, which were partially tested and which had not been started. When Medusa receives a SIG‐INT, it will calculate and display a "resume map". This map can then be supplied to the next run. For example, "medusa [OPTIONS PREVIOUSLY USED] -Z h6u1u2h8.". In this particular example, hosts 1-5 were completed, host 6 was partially done (user 1 was partially completed and user 2 and beyond had not been started), host 7 was completed and host 8 and beyond had not been started. Medusa will parse this map and skip hosts and users accordingly. It should be noted that only host and user-level, not password-level, resuming is supported. If a user had been previously started, but was not completed, it will be tested from the start of its respective password list.


# Options Medusa Modules
 - afp.mod : Brute force module for AFP sessions
 - cvs.mod : Brute force module for CVS sessions
 - ftp.mod : Brute force module for FTP/FTPS sessions
 - http.mod : Brute force module for HTTP
 - imap.mod : Brute force module for IMAP sessions
 - mssql.mod : Brute force module for MSSQL sessions
 - mysql.mod : Brute force module for MySQL sessions
 - nntp.mod : Brute force module for NNTP sessions
 - pcanywhere.mod : Brute force module for PcAnywhere sessions
 - pop3.mod : Brute force module for POP3 sessions
 - postgres.mod : Brute force module for PostgreSQL sessions
 - rdp.mod : Brute force module for RDP (Microsoft Terminal Server) sessions
 - rexec.mod : Brute force module for REXEC sessions
 - rlogin.mod : Brute force module for RLOGIN sessions
 - rsh.mod : Brute force module for RSH sessions
 - smbnt.mod : Brute force module for SMB (LM/NTLM/LMv2/NTLMv2) sessions
 - smtp-vrfy.mod : Brute force module for verifying SMTP accounts (VRFY/EXPN/RCPT TO)
 - smtp.mod : Brute force module for SMTP Authentication with TLS
 - snmp.mod : Brute force module for SNMP Community Strings
 - ssh.mod : Brute force module for SSH v2 sessions
 - svn.mod : Brute force module for Subversion sessions
 - telnet.mod : Brute force module for telnet sessions
 - vmauthd.mod : Brute force module for the VMware Authentication Daemon
 - vnc.mod : Brute force module for VNC sessions
 - web-form.mod : Brute force module for web form
 - wrapper.mod : Generic Wrapper Module

# Usage

medusa is generally used as a brute force cracker.

```bash
 $ medusa
```
<img src = "./Images/Picture1.jpg">



to open the help manual use 

```bash
    $ medusa -h
```

<img src = "./Images/Picture3.jpg">

the following command is used for ssh cracking 

```bash
    $ medusa -h 10.0.2.15 -u user -P ~/Desktop/Password_List.txt -M ssh -n 22

```

Thus medusa is used for brutre force parallelized password cracking.
