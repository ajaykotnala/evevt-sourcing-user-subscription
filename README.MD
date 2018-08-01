# event-sourcing-example

Event Sourcing Example repo for the Node.js at Scale blog series

## Usage

git clone this repo and then

```
npm install
```


```
npm start
```

Console output:

```
--- Create events ---
Accounts are opened { Ajay: 1000, Ankur: 500, Ansuman: 0 }
Some money are transfered { Ajay: 0, Ankur: 1000, Ansuman: 500 }
Ajay closed her account { Ankur: 1000, Ansuman: 500 }
--- Process events ---
Rebuild accounts from event log { Ankur: 1000, Ansuman: 500 }
Undo last event { Ankur: 1000, Ansuman: 500, Ajay: 0 }
Undo last two event { Ankur: 1000, Ansuman: 0, Ajay: 500 }
Query first step { Ajay: 1000 }
Query second step { Ajay: 1000, Ankur: 500 }
```

Event log output (event_log.txt):

```
{"type":"open","id":"Ajay","balance":1000,"timestamp":1531979369166}
{"type":"open","id":"Ankur","balance":500,"timestamp":1531979369168}
{"type":"open","id":"Ansuman","balance":0,"timestamp":1531979369168}
{"type":"transfer","fromId":"Ajay","toId":"Ankur","amount":500,"timestamp":1531979369171}
{"type":"transfer","fromId":"Ajay","toId":"Ansuman","amount":500,"timestamp":1531979369171}
{"type":"close","id":"Ajay","balance":0,"timestamp":1531979369174}

```
