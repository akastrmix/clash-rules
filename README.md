## How to create rules and rulesets for MC servers

### Add custom ruleset
Create your own ruleset on github that contains domains of servers that you play or the offical sites of the servers.

### Place ruleset in clash yaml
Say that the custom ruleset you created is called `Game-Site`, in the `rule-providers` category, paste:
```
Game-Site:
  type: http
  behavior: classical
  url: "https://raw.githubusercontent.com/<your name>/<your repo>/main/Game-Sites"
  proxy: <main proxy>
  interval: 86400
```
Modify the url and proxy to make it work for your config.

### Edit rules in clash yaml
In the very first line of the rules, you should add:
```
- "AND,((RULE-SET,Game-Site),(NOT,((DST-PORT,25565)))),Game-Site"
```
And after the rule in which China IP is specified (Usually the line before `MATCH`), add:
```
- "DST-PORT,25565,Servers"
```
This assumes you already have two rules named `Game-Site` and `Servers`. `Game-Site` is usually the offical sites of the servers. With this config, when you open server sites, your traffic goes to `Game-Site`. And if you join their servers, your traffic is routed to `Servers`, with no need to add additional rulesets for the server.
