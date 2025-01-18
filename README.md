# How to ssh to CSC server
Client OS: windows

## Without ssh-keys

### Connect from command line (cmd, git bash, powershell, ws2l)
```bash
ssh username@puhti.csc.fi
```

### Connect from VScode
ssh configuration:
```bash
Host Puhti
  HostName puhti.csc.fi
  User username
  MACs hmac-sha2-512
```

## With ssh-keys
- Step 1: Generate public and private keys:
```bash
ssh-keygen -o -a 100 -t ed25519
```

- Step 2: Copy public key to csc portal
  + [https://my.csc.fi/profile](https://my.csc.fi/profile) -> SSH PUBLIC KEYS -> Add key

### Connect from command line (cmd, git bash, powershell, ws2l)
```bash
ssh username@puhti.csc.fi -m hmac-sha2-512 -i <path_to_private_key>
```

### Connect from VScode
```bash
Host Puhti
  HostName puhti.csc.fi
  User username
  MACs hmac-sha2-512
  IdentityFile <path_to_private_key>
  IdentitiesOnly yes
```

___
## ISSUES
1. Corrupted MAC on input
- Fix: set MACs hmac-sha2-512

2. Private key file: Permission deny
- Detail solution can be found at <a href='https://stackoverflow.com/questions/64687271/how-to-avoid-permission-denied-publickey-ssh-key-windows'>How to avoid Permission denied (publickey) SSH key (Windows)</a>
- Note:
  + Reset file/folder permission on windows:
```bash
icacls.exe <path> /reset
```

___
## REFERENCES
- <a href='https://docs.csc.fi/computing/connecting/ssh-windows/'>SSH_client_on_Windows</a>
- <a href='https://docs.csc.fi/support/tutorials/remote-dev/#visual-studio-code-with-remote-ssh-plugin'>Developing scripts remotely</a>
- <a href='https://stackoverflow.com/questions/64687271/how-to-avoid-permission-denied-publickey-ssh-key-windows'>How to avoid Permission denied (publickey) SSH key (Windows)</a>







