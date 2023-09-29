```
 __   __  _______  ______      _______  __    _  _______  ______    __   __  _______  _______  _______  ______   
|  |_|  ||       ||    _ |    |       ||  |  | ||       ||    _ |  |  | |  ||       ||       ||       ||    _ |  
|       ||   _   ||   | ||    |    ___||   |_| ||       ||   | ||  |  |_|  ||    _  ||_     _||   _   ||   | ||  
|       ||  | |  ||   |_||_   |   |___ |       ||       ||   |_||_ |       ||   |_| |  |   |  |  | |  ||   |_||_ 
 |     | |  |_|  ||    __  |  |    ___||  _    ||      _||    __  ||_     _||    ___|  |   |  |  |_|  ||    __  |
|   _   ||       ||   |  | |  |   |___ | | |   ||     |_ |   |  | |  |   |  |   |      |   |  |       ||   |  | |
|__| |__||_______||___|  |_|  |_______||_|  |__||_______||___|  |_|  |___|  |___|      |___|  |_______||___|  |_|

```

# A simple payload and function name encryptor using the XOR function
**All output will be in C/C++ variable declaration format.**
## Usage

```
options:
  -h, --help            show this help message and exit
  -v, --version         show program's version number and exit
  -k <KEY STRING>, --encryption-key <KEY STRING>
                        The key to use for XOR ecnryption. A random key will be generated if no key is provided.
  -p <BINARY FILE NAME>, --payload-file <BINARY FILE NAME>
                        The file name of a binary (.bin) payload to encrypt with XOR.
  -s <TEXT FILE NAME>, --function-list-file <TEXT FILE NAME>
                        The file name of a list of strings to encrypt with XOR (one per line).
  -df True|False, --decrypt-verify True|False
                        Decrypt the function list to verify the encryption. (Default: Fasle)
  -o <TEXT FILE NAME>, --output-file <TEXT FILE NAME>
                        The file name where the output will be written. WARNING: The file will be created or overwritten!
```

## Sample Funcion list file
```
VirtualAlloc
VirtualAllocEx
RtlMoveMemory
WriteProcessMemory
NtCreateThreadEx
RtlCreateUserThread
```

## Sample output
```   
[!] A random key of non-printable characters was generated.
[!] Encrypting function list...
Original string: b'VirtualAlloc\x00'
Decrypted string: VirtualAlloc: b'VirtualAlloc\x00'
Original string: b'VirtualAllocEx\x00'
Decrypted string: VirtualAllocEx: b'VirtualAllocEx\x00'
Original string: b'RtlMoveMemory\x00'
Decrypted string: RtlMoveMemory: b'RtlMoveMemory\x00'
Original string: b'WriteProcessMemory\x00'
Decrypted string: WriteProcessMemory: b'WriteProcessMemory\x00'
Original string: b'NtCreateThreadEx\x00'
Decrypted string: NtCreateThreadEx: b'NtCreateThreadEx\x00'
Original string: b'RtlCreateUserThread\x00'
Decrypted string: RtlCreateUserThread: b'RtlCreateUserThread\x00'
[!] The key in hex format is:
char key[] = { 0x61, 0x35, 0x18, 0x41, 0x11, 0xc3, 0x39, 0x1a, 0xe7, 0xe5, 0x55, 0x6b, 0xdb, 0x80, 0x96, 0x23 };
[!] The encrypted output in hex format is:
unsigned char sVirtualAlloc[] = { 0x37, 0x5c, 0x6a, 0x35, 0x64, 0xa2, 0x55, 0x5b, 0x8b, 0x89, 0x3a, 0x8, 0xdb };
unsigned char sVirtualAllocEx[] = { 0x37, 0x5c, 0x6a, 0x35, 0x64, 0xa2, 0x55, 0x5b, 0x8b, 0x89, 0x3a, 0x8, 0x9e, 0xf8, 0x96 };
unsigned char sRtlMoveMemory[] = { 0x33, 0x41, 0x74, 0xc, 0x7e, 0xb5, 0x5c, 0x57, 0x82, 0x88, 0x3a, 0x19, 0xa2, 0x80 };
unsigned char sWriteProcessMemory[] = { 0x36, 0x47, 0x71, 0x35, 0x74, 0x93, 0x4b, 0x75, 0x84, 0x80, 0x26, 0x18, 0x96, 0xe5, 0xfb, 0x4c, 0x13, 0x4c, 0x18 };
unsigned char sNtCreateThreadEx[] = { 0x2f, 0x41, 0x5b, 0x33, 0x74, 0xa2, 0x4d, 0x7f, 0xb3, 0x8d, 0x27, 0xe, 0xba, 0xe4, 0xd3, 0x5b, 0x61 };
unsigned char sRtlCreateUserThread[] = { 0x33, 0x41, 0x74, 0x2, 0x63, 0xa6, 0x58, 0x6e, 0x82, 0xb0, 0x26, 0xe, 0xa9, 0xd4, 0xfe, 0x51, 0x4, 0x54, 0x7c, 0x41 };

```
