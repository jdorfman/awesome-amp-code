# Amp FAQ

> A collection of the most common questions, edge-cases, and troubleshooting steps for the Amp CLI and Extension.  

---

## A simple `rm` command, takes forever. Infinite loading

Try adding this to your VS Code user settings:

`"amp.terminal.commands.environment": "node-spawn"`

Source: [X](https://x.com/Varkoffs/status/1944036104774025279)

## 413 Request Entity Too Large

If you get a 413 error it could be a large binary file in the project folder named `agent.md`. Delete it and try again.

```text
<html><head> <meta http-equiv="content-type" content="text/html;charset=utf-8"> <title>413
Request Entity Too Large</title> </head> <body text=#000000 bgcolor=#ffffff> <h1>Error: Request
Entity Too Large</h1> <h2>Your client issued a request that was too large.</h2></body>
</html>
```

Source: [Discord](https://discord.com/channels/1369018393407127613/1392299889550954596)

---

_Last updated: 2025-07-12_
