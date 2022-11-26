/usr/bin/getallscope

```python
#!/usr/bin/python3
import json
import requests
import random

url = "https://raw.githubusercontent.com/arkadiyt/bounty-targets-data/main/data/hackerone_data.json"
r = requests.get(url=url)
fullz = []
datas = json.loads(r.text)
for data in datas:
 if not "targets" in data: continue
 for target in data["targets"]["in_scope"]:
  if not target["asset_identifier"].startswith("*."): continue
  if not target["eligible_for_bounty"] == True: continue
  if not target["eligible_for_submission"] == True: continue
  fullz.append(target["asset_identifier"].replace("*.", ""))
random.shuffle(fullz)
print("\n".join(fullz))
getrandscope
#!/bin/bash
getallscope | shuf | head -n 10 | assetfinder -subs-only > tmpfile
``` 

/usr/bin/getrandscope

```bash
#!/bin/bash
getallscope | shuf | head -n 10 | assetfinder -subs-only > tmpfile
```

/usr/bin/autopwn

```
#!/bin/bash
rm probed;
rm foundvuln.txt;
rm tmpfile;
getrandscope;
cat tmpfile | shuf | httprobe -c 100 | tee -a probed;
nuclei -as -silent -s medium,high,critical -nc -l probed | xargs -L 1 sendwebhook | tee -a foundvuln.txt;
```

/usr/bin/sendwebhook (change webhook url to yours)

```bash
#!/bin/bash
argstr=$@;
argstr=$(echo $argstr | tr -d '"');
echo $argstr;
curl WEBHOOK_URL_HERE -H "Content-Type: application/json" --data "{\"name\":\"hello\", \"content\":\"$argstr\"}";
sleep 2;
```

/usr/bin/pwnforever

```
#!/bin/bash
while true; do 
 autopwn;
done
```

finally chmod +x all the scripts and run this command then exit out of your vps and wait for bugs to pop in your discord channel
```
nohup pwnforever &
```
