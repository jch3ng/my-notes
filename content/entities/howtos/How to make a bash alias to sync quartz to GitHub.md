---
entity: "[[howto]]"
---
You might run  this when needed:

```
npx quartz sync --no-pull
```

... but sometimes you:
- close that terminal
- change directories

Add this to `~/.bash_profile`:

```bash
function qs {
  cd ~/workspace/github/quartz; npx quartz sync --no-pull
}
```


