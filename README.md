## How to create rules and rulesets for MC servers

### Add custom ruleset
Create your own ruleset on github that contains domains of servers that you play or the offical sites of the servers.

### Edit rules in clash yaml
Say that the custom ruleset you created is called `Game-Site`, in the very first line of the rules, you should add:
```
- "AND,((RULE-SET,Game-Site),(NOT,((DST-PORT,25565)))),Game-Site"
```
And after the rule in which China IP is specified (Usually the line before `MATCH`), add:
```
- "DST-PORT,25565,Servers"
```
This assumes you already have two rules named `Game-Site` and `Servers`. `Game-Site` is usually the offical site of the server. With this config, when you open server sites, your traffic goes to `Game-Site`. And if you join their servers, your traffic is routed to `Servers`, with no need to add additional rulesets for the server.
