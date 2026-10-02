# FarGoneSpy

This is a slightly enhanced version of https://github.com/gonespy/bstormps3 which changes the following:

- Supports server listing: For supported games, users connected to the same fargonespy instance can see and join
  each other's games
- Works on modern versions of Java (the original version only worked with Java 8 JRE)
- Fixes some performance issues that caused the server to unnecessarily use a lot of CPU

# Docker

Just clone repo and run with `docker compose`. Docker will build Java
and Go code and startup applications. Two knobs you can change
is (edit file `docker-compose.yml`):

* `ANSWER_IP=192.168.1.100` - is your IP address where Fargonespy is answer.
  *  If you play on LAN - this is your computer IP
  * If you play over Internet - this is you virtual/dedicated server public IP
* `FORWARD_IP=8.8.8.8:53` - is DNF forwarder for any other (such as PSN)
records. Should be in `inet:port` format

```shell
√ MacBook % git clone https://github.com/k0ste/fargonespy.git
√ MacBook % cd fargonespy
√ MacBook % docker compose up
```

Server is UP. Setup DNS to `ANSWER_IP` address and play!

# Ports used by the server

TCP: 80, 443, 28910, 29900, 29901, 29920

UDP: 53, 27900, 27901

# Tested games

| Game                                      | Works?      | Status                                                                                                                                                          |
|-------------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 50 Cent: Blood on the Sand                | Yes         | Need to be connected to the same fargonespy server to play co-op. Note that only the Japanese version has trophies.                                             |
| Blacklight: Tango Down                    | No          | Login doesn't work.                                                                                                                                             |
| Blitz: The League II                      | Potentially | Doesn't work, but it's potentially fixable. The game makes calls to two unimplemented, undocumented endpoints: GetServerInfo.asp and GetPlayerStats.asp         |
| CellFactor: Psychokinetic Wars            | Yes         | When connected to the same instance, players can join each other's lobbies.                                                                                     |
| Damage Inc.: Pacific Squadron WWII        | No          | Login doesn't work.                                                                                                                                             |
| Dungeon Defenders                         | Yes         | When connected to the same instance, players can join each other's lobbies. When connected to separate instances, players can be manually invited to the lobby. |
| F.E.A.R. 2: Project Origin                | No          | Login doesn't work.                                                                                                                                             |
| Fuel                                      | No          | Login doesn't work.                                                                                                                                             |
| Gotham City Imposters                     | No          | Login doesn't work.                                                                                                                                             |
| Guardians of Middle-earth                 | Potentially | Game crashes after attempting matchmaking, likely related to the fact that login doesn't work. May work with the right listing key.                             |
| Homefront                                 | Potentially | Game requires some unimplemented non-gamespy endpoints.                                                                                                         |
| JASF: Jane's Advanced Strike Fighters     | No          | Login doesn't work.                                                                                                                                             |
| Joe Danger 2: The Movie                   | No          | Login does not work.                                                                                                                                            |
| Mortal Kombat (Vita)                      | No          | Login doesn't work.                                                                                                                                             |
| Mortal Kombat 9                           | No          | Login doesn't work. Tested pre-patched version.                                                                                                                 |
| Mortal Kombat vs. DC Universe             | Potentially | Requires unimplemented, undocumented GameSpy endpoint.                                                                                                          |
| MUD - FIM Motocross World Championship    | No          | Login doesn't work.                                                                                                                                             |
| Saint's Row 2                             | No          | Login doesn't work.                                                                                                                                             |
| Section 8                                 | Potentially | Possible to create ranked matches, but more work is needed to be able to join them.                                                                             |
| SBK-09: Superbike World Championship      | No          | Login doesn't work.                                                                                                                                             |
| SBK Generations                           | No          | Login doesn't work.                                                                                                                                             |
| SBK Superbike World Championship          | No          | Login doesn't work.                                                                                                                                             |
| SBK 2011 FIM Superbike World Championship | No          | Login doesn't work.                                                                                                                                             |
| Superstars V8 : Next Challenge            | No          | Login doesn't work.                                                                                                                                             |
| Timeshift                                 | Potentially | Needs some fixes to attribute handling before it will work.                                                                                                     |
| UFC Undisputed 2010                       | No          | Login doesn't work.                                                                                                                                             |
| Unreal Tournament 3                       | Yes         | When connected to the same instance, players can join each other's lobbies.                                                                                     |
| WRC FIA World Rally Championship          | No          | Login doesn't work.                                                                                                                                             |
| WRC 2: FIA World Rally Championship       | No          | Login doesn't work.                                                                                                                                             |


# Credits

Most of the credit goes to the original author of https://github.com/gonespy/bstormps3

https://github.com/AdmiralCurtiss/nintendo_dwc_emulator was also very helpful in figuring out how certain aspects
of the GameSpy protocol work.
