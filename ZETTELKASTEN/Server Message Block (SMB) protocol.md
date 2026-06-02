*02-06-2026, 22:09*
Tags: [[Cybersecurity]]

# Server Message Block (SMB) protocol

> **Server Message Block (SMB)** is a network file sharing protocol that allows users to read, write, and request services from server applications over a network.

SMB enables shared access to files, printers, and other resources between nodes on a network. It operates on a **client-server model**, where any node in a network can act as a client, a server, or both simulatenously, depending on the use-case. In all such cases, the client makes a request and the server responds.

## Shares

A **share** is a folder (or resource) on a server that has been explicitly made accessible over the network. It's the unit of access in SMB — you don't connect to a server's whole filesystem, you connect to a specific share on it.

The server administrator of an SMB server picks a folder, gives it a nickname, sets permissions and publishes it as a share. Clients connect to the share without needing to know the underlying path it leads to on the server. So in short, shares are just blackboxed directories on the server that the admin has chosen to allow clients to connect to (if they have permission).

```
Server filesystem:         Network share:
/data/finance/reports  →   \\SERVER\FinanceReports
/data/hr/documents     →   \\SERVER\HR
C:\Users\              →   \\SERVER\Users
```

### Common default shares

| Share                | Points to                                         |
| -------------------- | ------------------------------------------------- |
| `C$`, `D$`           | Root of each drive — admin only                   |
| `ADMIN$`             | Windows installation directory                    |
| `IPC$`               | Inter-process communication (not a folder)        |
| `SYSVOL`, `NETLOGON` | Domain controller shares for Group Policy/scripts |


## Protocol steps

1. **Establish connection** — The client establishes a TCP connection to the server (usu. on port 445 for SMB)
2. **Negotiate version** — Client and server agree on an SMB version (dialect) to use
3. **Authenticate client** — Client authenticates using credentials
4. **Create session and connect to share** — The session is created and the client connects to a specific share on the server
5. **Operate on files** — Client sends requests (read, write, get, delete, etc.)
6. **Terminate connection** — Session and connection are closed cleanly

___
# References
