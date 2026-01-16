SoF2MP.exe v1.03 – Patched Version

File: sof2mp.exe
Version: 1.03
Author of patch: Teo
Websites:

https://www.yob.at

https://www.sof2.org

This is a custom patched version of Soldier of Fortune II Multiplayer executable, created to improve stability and security and to update masterserver functionality.

Description

This patch includes:

Fix for cl_guid overflow / validation (based on the old sof2-103-guidfix concept)

Additional server-side safety checks for oversized GUID values

Client-side call cleanup (NOP padding and stack fix)

Updated masterserver address

getstatus / getinfo fixes

Hex-level modifications only (no source code available)

GUID Fix (Hex-level patch)
Original bytes
5f c6 46 0c 01 5e 33 c0 5b 59 c3 5f 8b c6 5e 5b
59 c3 90 90 90 90 90 90 90 90 90 90 90 90 90 55
8b 6c 24 08 56 57 8d 45 04 68 b0 b3 55 00 50 e8
fb ca fe ff 8b 35 84 3c ba 00 83 c4 08 85 f6 8b
f8

Patched bytes
c6 46 0c 01 33 c0 5f 5e 5b 59 c3 8b c6 eb f7 8b
f8 32 c0 83 c9 ff f2 ae 83 f9 c0 7c 6f eb 20 55
8b 6c 24 08 56 57 8d 45 04 68 b0 b3 55 00 50 e8
fb ca fe ff 8b 35 84 3c ba 00 83 c4 08 eb d0 85
f6

Purpose of the fix

The added bytes implement a validation check on the cl_guid value to ensure it does not exceed 64 bytes (its buffer size).
If a client sends a cl_guid longer than allowed, the server will now correctly return a "Banned" error instead of risking overflow behavior.

The initial modified bytes are used to gain space for inserting the new validation logic.

getstatus / getinfo Fixes (Server-side)
Modified regions
00478A34  mov byte ptr [eax+40], cl
00478A37  lea eax, [esp+20]
00478A3B  jmp 00478AA6
...
00478AA2  xor ecx, ecx
00478AA4  jmp 00478A34


and

00478D4F  jmp 00478F61
...
00478F61  push eax
00478F62  xor ecx, ecx
00478F64  mov byte ptr [eax+40], cl
00478F67  lea edx, [esp+10]
00478F6B  jmp 00478D54


These changes improve stability and safety when handling network status/info requests.

Client-side Patch
Original code
0x004bb330: push $0x11a3ea0
...
0x004bb35c: push %eax

Patched behavior

The second call block has been replaced by NOP instructions, and stack cleanup was adjusted:

Removed redundant call sequence

Adjusted stack restore (add $0x38, %esp)

Improves consistency and avoids unnecessary operations

This results in cleaner execution without changing gameplay behavior.

Masterserver Patch (1fx)
Original string
master.sof2.ravensoft.com

Patched string
master.1fxmod.org


Hex-level modification:

Original:
6D 61 73 74 65 72 2E 73 6F 66 32 2E 72 61 76 65 6E 73 6F 66 74 2E 63 6F 6D

Patched:
6D 61 73 74 65 72 2E 31 66 78 6D 6F 64 2E 6F 72 67


This allows the game to continue functioning with a modern community-supported masterserver.

Notes

This patch was created by manual reverse engineering and hex editing.

No original Raven source code was used.

Intended for community preservation and compatibility.

Use at your own responsibility.

Credits

Patch by Teo
Websites:

https://www.yob.at

https://www.sof2.org
