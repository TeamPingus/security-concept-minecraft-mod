# Concept for cryptographically signing and checking Minecraft mods in order to verify their integrity

Concept by PassiHD and rooot

### DISCLAIMER: WE ARE NOT EXPERTS IN CRYPTOGRAPHY! WE JUST WANT TO SHARE OUR IDEAS - TAKE EVERYTHING IN HERE WITH A GRAIN OF SALT

## Signing:
- Cryptographically sign .jar files including their contents, signature appended at the end of the file (inspiration from android .apk signing)


## Server approach:
### Decentralised approach:
- A decentralised Network of servers, that all store the modid with the corresponding signature. If any server has been compromised, all the other servers would overrule it, therefore guaranteeing the integrity.
### Centralized approach:
- At least 3 servers that store the signatures. If one server has been messed with, the other 2 would overrule it. (kinda like a raid setup). Every server should use different credentials, but be linked up to sync databases of the keys=modid’s
- Downside: possibly increased costs for servers.
- Every server should have multiple managers with different credentials (at least 3 people, maybe) so that if one of the members, that manages the infrastructure goes rogue, other members can overrule them and deny access to the server, for that specific member.

### Serverless(-ish) approach:
- Every mod author should sign ALL their mods with the same signature*
- every modloader should always randomise the location of the keystore to make it harder to find. (maybe?)*
- if one mod has been tampered with, the modloader can check the signature of the mod with other mods or a local minecraft-specific keystore to check if the mod has been modified or not.
- Public keys should be available on mod hosting sites like Modrinth and CurseForge, eg. next to the file hashes of the mod JARs.*
- Mod authors should protect their private keys using secure passwords.*
- Mods should ALWAYS have to be signed (except in development environments)*
- In order to update a signature, a mod author can update the signature, the new signature being signed with the old signature*
- downside: if the private keys for the old signature is lost, a manual modification of the keystore would need to take place*
- maybe host a .well-known/mcsign.json on the package name for the signature checking or a TXT record for signature checking - better approach than whats described above (credits: Semisol#0001)



Everything marked with * can/should also be applied to the Server approach, if possible.

