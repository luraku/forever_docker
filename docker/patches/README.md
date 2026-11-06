# Patches applied to TrinityCore (forever branch)

Applied in name order right after the `git clone` (see the Dockerfile). The build stops if a patch no longer
applies: either it was merged into the branch (delete it) or it needs updating.

| File | What it fixes (found with packet logs of client 1.60.1.70450) |
|---|---|
| `0002-classic-surname-names.patch` | The 1.60 client shows and sends "Name Surname". `normalizePlayerName` keeps the first word only (add friend, ignore, guild, mail by name: no more "player not found"). Upstream only trims the surrounding blanks. |
| `0003-classic-contact-list-request.patch` | The 1.60 client's `CMSG_SEND_CONTACT_LIST` is 5 bytes: one byte (0) before the flags. Read as a uint32 it gave wrong flags (0x1500) and the server sent an empty friend list every time it was opened, although the friends were stored. |

## Merged upstream (removed)

| Former patch | Upstream |
|---|---|
| `0002` invite part (`CMSG_PARTY_INVITE` 70425+ layout) | `7b1bb00` "Party invite: read the target name length as 6 bits on the 70450 client" (#83), from sniffs |
| `0004-classic-360-action-buttons.patch` | `MAX_ACTION_BUTTONS` 360 and `sql/custom/characters/2026_10_13_00_characters_classic_action_buttons_360.sql` |
