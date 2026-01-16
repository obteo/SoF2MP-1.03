SoF2MP.exe v1.03 – Community Patched Version

File: sof2mp.exe
Version: 1.03
Packaged by: Teo
Websites:

https://www.yob.at

https://www.sof2.org

This is a community-patched version of Soldier of Fortune II Multiplayer executable.
The file combines several existing fixes into a single ready-to-use binary.

I did not create the original fixes — I only merged and packaged them into one working executable.

Description

This executable includes multiple known community fixes:

cl_guid overflow / validation fix

Quake 3 engine universal directory traversal fix (Windows) v0.1.1 (q3dirtravfix)

getstatus / getinfo fixes

Client-side cleanup patch

Updated masterserver address

Stability and security improvements

Hex-level modifications only (no source code)

All modifications were applied manually at binary level.

GUID Fix (cl_guid overflow protection)

This fix introduces a validation check on the cl_guid value to ensure it does not exceed 64 bytes (buffer size).
If a client sends an oversized cl_guid, the server correctly responds with "Banned", preventing overflow issues.

This behavior is based on the well-known sof2-103-guidfix.

Directory Traversal Fix (Quake 3 Engine)

This executable also includes the Quake 3 engine universal directory traversal fix (Windows) v0.1.1
(commonly known as q3dirtravfix).

This fix protects against directory traversal vulnerabilities in the Quake 3 engine network and file handling logic, which could otherwise allow malicious clients to access unintended paths or trigger unsafe behavior.

The fix is widely used in the community and is included here unchanged.

getstatus / getinfo Fixes

Server-side fixes that improve handling of network requests and prevent malformed packets from causing instability.
These are widely used community patches and are included here without functional changes.

Client-side Patch

The client binary was cleaned by:

Removing a redundant call block using NOP padding

Adjusting stack cleanup

Preserving original behavior while improving stability

No gameplay behavior is changed.

Masterserver Patch (1fx)

The original masterserver:

master.sof2.ravensoft.com


was replaced with:

master.1fxmod.org


This allows the game to continue functioning using the community-supported masterserver.

Important Note

This executable is only a repackaging of existing community fixes.
No claim is made over the authorship of the original patches.

The goal is preservation, accessibility, and convenience for the SoF2 community.

Credits (Original Authors)

All credit for the original research and fixes goes to:

Luigi Auriemma (aluigi)
https://aluigi.altervista.org/

sof2-103-guidfix

Quake 3 engine directory traversal fix (q3dirtravfix)

Various security-related engine fixes

1fx Mod Team
https://1fxmod.org/

Masterserver patch

Community maintenance patches

These contributors made the technical work possible.
This executable only combines their fixes into a single ready-to-use binary.
Packaging

Executable assembled and distributed by Teo

Websites:

https://www.yob.at

https://www.sof2.org

