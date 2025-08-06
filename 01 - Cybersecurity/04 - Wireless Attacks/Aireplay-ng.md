Part of the [[Aircrack-Suite]]
Can send fake packets do bssid arround the area:

`aireplay.ng <switches> <interface>`

- Deauth attacks : `--deauth <count> -a <access-point> -d <target-station>`
- Fake auth attacks: `--fakeauth <tries> -a <access-point> -h <attacker-interface>`
- ARP replay attack: `--arpreplay -b <access-point> -h <attacker-interface>`
- Chop Chop attack: `--chopchop -b <access-point> -h <attacker-interface>`
- 