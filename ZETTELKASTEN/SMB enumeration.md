*02-06-2026, 23:52*
Tags: [[Cybersecurity]]

# SMB enumeration

> **SMB enumeration** is the process of extracting information from devices on a network that are running [[Server Message Block (SMB) protocol |SMB]] protocol services.

There are several tools capable of this, but we will focus on `smbclient` here.

## Listing shares

If we have the IP address of a device running SMB, we can list the shares it provides (assuming the server allows that without authentication).

The command used is `smbclient -N -L //[ip]`.

The `-N` option specifies we're connecting anonymously with no login. Of course, this will only work if the server doesn't require authentication. The `-L` option specifies we want to list the shares on this SMB server. Furthermore, note that `smbclient` assumes the default SMB port of `445` here. If a non-standard port is used instead, it must be specificed with `-p [port]` at the end of the command.

## Listing files on a share

Connecting to a share uses the following command

- `smbclient //[ip]/[share name] -U [username] [password]` - With creds
- `smbclient //[ip]/[share name] -N` - Null authentication

Once connected, you should be prompted to enter commands. You can run `ls` to view available files on the share.


___
# References
[🤖 SMB Protocol Explained - Claude](https://claude.ai/share/d3744b42-7e4b-40bc-b1bd-397e9ead1d82)
[🌐 SMB Enumeration Cheatsheet](https://0xdf.gitlab.io/cheatsheets/smb-enum#background)