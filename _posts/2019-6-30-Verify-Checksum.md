---
layout: post
title: How to Verify Checksum
categories: [Security]
---

* Problem
* Solution
* Examples

*Navigate to directory where file is located*

**Windows**
Use Command Prompt or Powershell
```
certUtil -hashfile <FILENAME> <ALGORITHM>
```

Example
```
certUtil -hashfile kali-linux-2019.2-vmware-i386.7z SHA256
```

Output
```
SHA256 hash of kali-linux-2019.2-vmware-i386.7z:
c7f52865f5d0554ad1bc990684a0751eb46d1b8ab552d7c942d71e4fe20b7e67
```

**Linux**
Use terminal
```
<ALGORITHM> <FILENAME>
```

Example
```
sha256sum kali-linux-2019.2-vmware-i386.7z
```

Output
```
c7f52865f5d0554ad1bc990684a0751eb46d1b8ab552d7c942d71e4fe20b7e67  kali-linux-2019.2-vmware-i386.7z
```
